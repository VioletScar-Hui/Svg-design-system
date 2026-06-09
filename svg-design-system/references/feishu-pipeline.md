# Feishu / Lark document whiteboard pipeline

How to put a generated SVG into a **Feishu doc whiteboard (飞书文档画板)** as an editable vector board.
The board *is* vector and editable — but it has hard feature constraints, so the SVG must be authored
board-safe first.

Run this only when the user chose to upload to a Feishu whiteboard (Step 1 of the main pipeline).

## Prerequisites

- `lark-cli` configured and authenticated (`lark-cli whoami` to verify). The `whiteboard` and
  `docs +update --api-version v2` commands require a recent `lark-cli`.
- `node` / `npx` available for `@larksuite/whiteboard-cli`.
- The target document id (`doc_id`).

## 🔑 Board-safe authoring (do this in Step 4 of the main pipeline, before converting)

The whiteboard does **not** support these SVG features — avoid them entirely:

- `radialGradient`
- `filter` (so no `feDropShadow` — use a faux offset shape for shadow instead)
- `clipPath`
- `mask`

Solid fills and `linearGradient` are fine. If you started from the sample cards, strip the
`<filter id="shadow">` and the `filter="url(#shadow)"` usages first.

## The 6 steps

### 1. Prepare the SVG
Generate it (or use a provided file), making sure it avoids the unsupported features above
(`radialGradient` / `filter` / `clipPath` / `mask`).

### 2. Render + validate locally (fix problems locally, don't pollute Feishu)
```bash
# render a preview PNG
npx -y @larksuite/whiteboard-cli@^0.2.11 -i diagram.svg -o diagram.png -f svg
# check for text-overflow / node-overlap
npx -y @larksuite/whiteboard-cli@^0.2.11 -i diagram.svg -f svg --check
```
Resolve any `text-overflow` / `node-overlap` warnings by editing the SVG, then re-check.

A benign warning you can ignore: a `node-overlap` between the full-canvas background rect and a
decorative blob/wave that sits on top of it. Any "background + decoration" layering trips it. Only chase
overlaps **between content nodes** (chips, boxes, badges). `errors: 0` is the gate to proceed.

### 3. Convert SVG → Feishu whiteboard OpenAPI JSON (the key transform)
```bash
npx -y @larksuite/whiteboard-cli@^0.2.11 -i diagram.svg -f svg --to openapi --format json > diagram.json
```
**Extract the payload.** `diagram.json` is wrapped by the CLI as `{code, data:{to, result:{nodes:[…]}, metadata}, error}`.
The whiteboard write expects only the inner `{nodes:[…]}`. Pull it out first:
```bash
node -e "const d=require('./diagram.json'); require('fs').writeFileSync('payload.json', JSON.stringify(d.data.result))"
```

### 4. Append an empty whiteboard block to the doc, capture its block_token

If the user gave a **wiki URL** (`/wiki/<token>`), resolve it to the underlying docx token first — the
docs API needs the `obj_token`, not the wiki node token:
```bash
lark-cli wiki +node-get --node-token "<wiki URL or token>" --as user --json
# use data.obj_token (obj_type=docx) as <doc_id> below
```

```bash
lark-cli docs +update --api-version v2 --doc <doc_id> --command append \
  --content '## 标题

<whiteboard type="blank"></whiteboard>' --as user --json
# Returns data.document.new_blocks[] — the one with block_type=whiteboard carries the board token
```
Use `--content` with `--command append` (in lark-cli 1.0.47 the `--help` lists `--markdown`/`--mode`,
but the runtime requires `--command`/`--content`). Content is Lark-flavored Markdown; `## ` makes a
heading. `--command append` adds at the end of the doc (non-destructive).

### 5. Write the payload into that whiteboard (overwrite)
```bash
lark-cli whiteboard +update --whiteboard-token <token> \
  --source "@./payload.json" --input_format raw \
  --idempotent-token <10+ char unique string> --as user --overwrite
```
Feed `payload.json` (the extracted `{nodes}` from step 3), not the raw `diagram.json` wrapper. The
`--idempotent-token` must be unique per write (min length 10) — e.g. `arch$(date +%s)x`. On success the
response lists `created_node_ids`.

### 6. Verify (export the board's preview image, confirm CN text / layout survived)
```bash
lark-cli whiteboard +query --whiteboard-token <token> --output_as image --output ./verify --as user
```
`--output ./verify` is a filename prefix → the image lands at `./verify.png` (not a directory). Open it
and confirm Chinese text and layout didn't break. If something shifted, fix the SVG and re-run from step
2 — keep the iteration local until the preview is clean. (Re-running step 5 with `--overwrite` and a new
idempotent-token replaces the board content in place.)

## Notes

- Always validate locally (steps 2–3) before touching the document, so a broken diagram never lands in
  Feishu.
- If `lark-cli` here lacks `whiteboard` / `--api-version v2` (an older build like a bare `lark.exe`),
  fall back to: render a 2–3× PNG and insert it as an image block, and/or `lark-cli drive upload` the
  `.svg` source — but that loses the editable-vector benefit, so prefer upgrading `lark-cli`.
