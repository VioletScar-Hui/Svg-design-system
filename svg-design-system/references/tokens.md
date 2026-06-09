# Design tokens

Extracted from the reference cards. These are the knobs that make different diagrams feel like one
system. Reuse the values; they're tuned to read well at presentation scale.

## Canvas

- Reference card uses `width="1200" height="800" viewBox="0 0 1200 800"` (3:2). Keep `viewBox` so the
  SVG scales cleanly.
- Aspect ratio follows the **使用场景**: 公众号正文图 ~16:9 or 4:3; 小红书 3:4 (e.g. 1080×1440); PPT 16:9;
  flexible otherwise. Keep generous padding (~64px margin on a 1200-wide canvas).

## Typography

Font stacks (define once in `<defs><style>`):

```css
.font { font-family: Inter, 'SF Pro Display', 'Noto Sans SC', 'Microsoft YaHei', Arial, sans-serif; }
.mono { font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', monospace; }
```

Type scale (the four tiers do the hierarchy work — don't invent in-between sizes):

| Class | size | weight | tracking | Role |
| --- | --- | --- | --- | --- |
| `.title` | 58px | 800 | -1.6px | L1 main title |
| `.sub` | 24px | 600 | — | subtitle / section lead |
| `.small` | 18px | 600 | — | body labels inside nodes |
| `.tiny` | 14px | 700 | .8px | eyebrow / captions / palette tags (often uppercased) |

Scale these proportionally for other canvas sizes. Title in **ink**; the subtitle's emphasized half in
**accent**.

## Depth / shadow

Image mode — drop shadow filter:

```xml
<filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
  <feDropShadow dx="0" dy="24" stdDeviation="20" flood-color="rgba(0,0,0,.12)"/>
</filter>
```

- Light bg: `flood-color="rgba(0,0,0,.12)"`. Dark bg: `rgba(0,0,0,.45)`.
- **Board-safe mode: `filter` is unsupported.** Replace with a faux shadow — a second filled shape
  offset by ~`dy 12–24`, fill `rgba(0,0,0,.10)`, placed *behind* the element.

## Grid texture (optional background)

```xml
<pattern id="grid" width="48" height="48" patternUnits="userSpaceOnUse">
  <path d="M48 0H0V48" fill="none" stroke="rgba(0,0,0,.06)" stroke-width="1"/>
</pattern>
```

- Light bg stroke `rgba(0,0,0,.06)`; dark bg stroke `rgba(255,255,255,.08)`.

## Decorative language (the "atmosphere" layer, keep subtle)

- 2–3 large soft circles (blobs) in accent/ink, `opacity .11–.18`, bleeding off the canvas corners.
- One sweeping wave `path` along the bottom, `opacity ~.11`.

**Do NOT print the palette name or hex codes in the final SVG.** The reference sample cards carry a
footer "palette strip" with "03 森林焦糖" and `#F3F0D7 / #2F5D50 / #D96C2C` — that is sample/metadata
chrome, not part of a real deliverable. A finished diagram shows only its own content; the palette is a
choice you made, not a label the reader needs. If you want a signature bar, keep it an unlabeled thin
3-color ribbon at most.

## Shape & stroke conventions

| Element | Convention |
| --- | --- |
| Card / panel | `rx="28–36"`, subtle border `stroke rgba(0,0,0,.08)`, translucent fill |
| Node box | `rx="22–28"`, `stroke-width 3`, border in ink or accent |
| Pills / progress bars | `rx="7"`, height ~14px |
| Arrows / connectors | `stroke-width 5`, `stroke-linecap="round"`, `stroke-linejoin="round"`, arrowhead as a small open `path` |
| Emphasis (L4) | the **accent** color — a filled marker, a thick arrow, or a glow ring |

Connectors and emphasis carry the **L3/L4** information, so make them deliberate, not decorative.

### Node contrast — make every box clearly readable

A common failure: nodes drawn with a translucent fill (e.g. `rgba(255,255,255,.6)`) and a low-opacity
hairline border (e.g. `rgba(ink,.3)`) **wash out on a tinted/cream background** — they read as floating
text, not modules, which weakens L2. Give each node enough separation:

- **Fill solid (or near-solid)** — `#FFFFFF` on light backgrounds, not `rgba(white,.6)`.
- **Border at ≥45% opacity** of the ink color, `stroke-width 1.4–2`.
- **Add a small lift** so the box sits above its container: in image mode a subtle shadow
  (`feDropShadow dx0 dy3 stdDeviation4 rgba(0,0,0,.16)`); board-safe, a 2–3px offset shadow shape.

When a node sits inside an already-tinted band, the solid fill is what creates the layer separation —
translucent-on-translucent disappears.

## Light/dark adaptation rules

Decide mode from the **background luminance** (palettes 02/04/08 are dark; rest are light). Then flip the
neutral helper colors:

| Helper | Light bg | Dark bg |
| --- | --- | --- |
| grid / hairline stroke | `rgba(0,0,0,.06)` | `rgba(255,255,255,.08)` |
| shadow flood | `rgba(0,0,0,.12)` | `rgba(0,0,0,.45)` |
| secondary text | `rgba(0,0,0,.62)` | `rgba(255,255,255,.72)` |
| panel fill (glass) | `rgba(255,255,255,.55)` | `rgba(255,255,255,.08)` |
| panel border | `rgba(0,0,0,.08)` | `rgba(255,255,255,.10)` |

Primary text/structure = the palette **ink**; primary emphasis = the palette **accent**. The body text
on dark backgrounds is near-white, not pure ink.

Compare `assets/sample-light-card.svg` and `assets/sample-dark-card.svg` — same layout, only these
helpers and the 3 roles change.
