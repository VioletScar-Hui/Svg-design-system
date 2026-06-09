# SVG Design System

[中文说明](README.zh-CN.md)

This directory contains the installable `svg-design-system` skill.

`svg-design-system` helps Codex and Claude Code generate professional SVG diagrams with clear information hierarchy. It includes a 5-level hierarchy method, 10 named palettes, reusable design tokens, diagram-type recipes, and a Feishu/Lark whiteboard-safe delivery pipeline.

## Install Location

For Codex, copy this directory into:

```powershell
$env:USERPROFILE\.codex\skills\svg-design-system
```

For Claude Code, copy this directory into:

```powershell
$env:USERPROFILE\.claude\skills\svg-design-system
```

Restart the agent after installation.

## Contents

```text
svg-design-system/
  README.md
  README.zh-CN.md
  SKILL.md
  assets/
    palettes.json
    sample-dark-card.svg
    sample-light-card.svg
  examples/
    palette-01-deep-sea-coral.svg
    palette-02-acid-night.svg
    palette-03-forest-caramel.svg
    palette-04-wine-gold.svg
    palette-05-sea-breeze-daylight.svg
    palette-06-cool-white-alert.svg
    palette-07-cream-oasis.svg
    palette-08-cyber-neon.svg
    palette-09-wild-terracotta.svg
    palette-10-mint-dream.svg
  references/
    diagram-types.md
    feishu-pipeline.md
    palettes.md
    tokens.md
```

## Core Workflow

1. Clarify the usage scenario and whether Feishu/Lark whiteboard upload is needed.
2. Choose the diagram type from the content structure.
3. Build the 5 information levels before styling.
4. Apply the palette and design tokens.
5. Output SVG, optional PNG, or board-safe SVG for Feishu/Lark.

## Reference Files

- [`references/palettes.md`](references/palettes.md): 10 named three-color palettes.
- [`references/tokens.md`](references/tokens.md): canvas, typography, grid, stroke, shadow, and light/dark rules.
- [`references/diagram-types.md`](references/diagram-types.md): selection rules and recipes for 7 diagram types.
- [`references/feishu-pipeline.md`](references/feishu-pipeline.md): SVG to Feishu/Lark whiteboard workflow.

## Assets

- [`assets/palettes.json`](assets/palettes.json): machine-readable palette source.
- [`assets/sample-light-card.svg`](assets/sample-light-card.svg): light-background sample card.
- [`assets/sample-dark-card.svg`](assets/sample-dark-card.svg): dark-background sample card.

## Example Gallery

The `examples/` directory contains 10 SVG examples, one for each named palette:

| Palette | Preview |
|---|---|
| 01 Deep Sea Coral | ![Deep Sea Coral example](examples/palette-01-deep-sea-coral.svg) |
| 02 Acid Night | ![Acid Night example](examples/palette-02-acid-night.svg) |
| 03 Forest Caramel | ![Forest Caramel example](examples/palette-03-forest-caramel.svg) |
| 04 Wine Gold | ![Wine Gold example](examples/palette-04-wine-gold.svg) |
| 05 Sea Breeze Daylight | ![Sea Breeze Daylight example](examples/palette-05-sea-breeze-daylight.svg) |
| 06 Cool White Alert | ![Cool White Alert example](examples/palette-06-cool-white-alert.svg) |
| 07 Cream Oasis | ![Cream Oasis example](examples/palette-07-cream-oasis.svg) |
| 08 Cyber Neon | ![Cyber Neon example](examples/palette-08-cyber-neon.svg) |
| 09 Wild Terracotta | ![Wild Terracotta example](examples/palette-09-wild-terracotta.svg) |
| 10 Mint Dream | ![Mint Dream example](examples/palette-10-mint-dream.svg) |

## License

See [`../LICENSE`](../LICENSE).
