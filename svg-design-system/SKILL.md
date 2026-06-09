---
name: svg-design-system
description: >
  A reusable visual design system for drawing SVG diagrams that look professional AND carry real
  information hierarchy. Use this skill WHENEVER the user needs to draw, design, or generate any of
  these diagram types — a flowchart (流程图), a matrix/quadrant diagram (矩阵图), an architecture
  diagram (架构图), a timeline (时间轴), a relationship/node graph (关系图 / 节点图), a cycle diagram
  (循环图), or a comparison chart (对比图) — including when they describe the underlying need (steps /
  process, two-dimension classification, system layers/modules, milestones over time, many-to-many
  relationships, a closed loop, or A-vs-B comparison) without naming the format, or when they want to
  turn article/text content into such a diagram. Also use when placing one of these diagrams into a
  Feishu/Lark document whiteboard (飞书文档画板). Provides 10 named three-color palettes, design tokens
  (canvas, type scale, shadow, grid, stroke), light/dark adaptation rules, a 5-level
  information-hierarchy method, per-diagram-type recipes, and the exact Feishu whiteboard upload
  pipeline.
---

# SVG Design System

A design language + workflow for producing SVG diagrams that are not just pretty, but **structured**.
The core belief: a mature SVG has *layers of information*. Pretty without hierarchy is decoration, not
communication.

## The pipeline — run these steps in order, every time

### Step 1 — Clarify intent (ask, don't assume)

Before drawing, ask the user two things:

1. **使用场景 (where will this image be used?)** — 公众号 / 小红书 / PPT / 飞书文档 / 汇报 / 网页 等。
   This decides aspect ratio, density, and whether full visual effects are allowed.
2. **是否直接上传到飞书文档画板？(upload to a Feishu doc whiteboard?)** — If yes, the output must be
   **board-safe** (see constraint below) and you will run the Feishu pipeline in `references/feishu-pipeline.md`.

If the user already answered these in their request, don't re-ask — just confirm your reading and move on.

### Step 2 — Choose the diagram type *from the content*, not by taste

Read the article/text and pick the form that matches its underlying structure. Do not default to a
flowchart for everything. Selection rules and recipes live in `references/diagram-types.md`. Quick guide:

| If the content is about… | Use |
| --- | --- |
| time order / steps / causal chain (先A后B、输入→处理→输出) | **流程图 Flowchart** |
| two-dimension classification / comparison (2×2、象限、优先级) | **矩阵图 Matrix** |
| system composition / layers / static module relationships | **架构图 Architecture** |
| evolution / milestones over time | **时间轴 Timeline** |
| many-to-many relationships between entities | **关系/节点图 Network** |
| a closed loop (e.g. Agent loop, PDCA) | **循环图 Cycle** |
| A vs B side-by-side | **对比图 Comparison** |

If two forms fit, tell the user the trade-off and let them pick.

### Step 3 — Build the skeleton with the 5-level information hierarchy

This is the heart of the method. **Before** styling anything, lay out the diagram so it answers all five
levels. After drawing, run this as a self-check: *for each level, point at where in the SVG it lives.* If
a level is missing, the diagram is incomplete — add it.

| Level | Question | Where it lives in the SVG |
| --- | --- | --- |
| **L1 一级信息** | 这张图讲什么 (what is this diagram about) | Title block — one clear sentence/topic |
| **L2 二级信息** | 核心模块有哪些 (what are the core modules) | The main boxes / nodes |
| **L3 三级信息** | 模块之间什么关系 (how do they relate) | Arrows / connectors / layout & grouping |
| **L4 四级信息** | 重点结论是什么 (what is the key takeaway) | One emphasized callout in the **accent color** |
| **L5 五级信息** | 视觉记忆点是什么 (what is the memory hook) | One distinctive symbol / metaphor / shape |

Designing this way keeps you from producing a "pretty but flat" image. L1–L3 are structure; L4 is the
argument; L5 is what the reader remembers tomorrow.

### Step 4 — Apply the design system (palettes + tokens)

Only now style it. Read:
- `references/palettes.md` — pick one of the 10 named three-color palettes by *semantic fit* (each
  palette has a note like "冷静底色 + 高能决策点"). Each palette has 3 roles: **底色 background / 主墨色
  ink (structure + text) / 高能强调 accent**.
- `references/tokens.md` — canvas, type scale, font stack, shadow, grid, stroke conventions, decorative
  language, and the **light/dark adaptation rules** (on dark backgrounds the helper rgba colors flip to
  white-based).

### Step 5 — Output

- **Image scenarios** (公众号/小红书/PPT/网页): write the `.svg`, optionally render a 2–3× PNG for
  pasting. Full effects allowed (filter shadows, gradients).
- **Feishu whiteboard**: follow `references/feishu-pipeline.md` exactly. The board is vector and
  editable, but has hard constraints (below).

## 🔑 Board-safe constraint (Feishu whiteboard only)

The Feishu doc whiteboard does **not** support `radialGradient`, `filter`, `clipPath`, or `mask`.
The sample cards use a `filter` drop-shadow — that must be replaced. When targeting Feishu:

- Replace `filter` drop-shadows with a faux shadow: an offset, semi-transparent filled `rect`/shape
  behind the element.
- Avoid `radialGradient` (use solid fills or a `linearGradient`).
- No `clipPath`, no `mask`.

For non-Feishu image output, all effects are fine.

## Reference files

- `references/palettes.md` — the 10 named three-color palettes, hex, roles, light/dark, semantic notes.
- `references/tokens.md` — design tokens + light/dark rules + board-safe variants.
- `references/diagram-types.md` — the 7 diagram types: when to use each + a build recipe per type, each
  mapped to the 5 information levels.
- `references/feishu-pipeline.md` — the exact 6-step SVG → Feishu doc whiteboard upload pipeline.

## Assets

- `assets/palettes.json` — machine-readable version of the 10 palettes.
- `assets/sample-light-card.svg` — a finished card on a **light** background (visual reference for the
  token system; the FDE×AI PM business text is just sample content, not a required template).
- `assets/sample-dark-card.svg` — the same layout on a **dark** background, showing the light/dark flip.
