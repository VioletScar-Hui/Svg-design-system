# SVG Design System Skill

[中文说明](README.md)

![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827)
![Claude Compatible](https://img.shields.io/badge/Claude-Compatible-6B46C1)
![SVG Diagrams](https://img.shields.io/badge/SVG-Diagrams-FFB000)
![Feishu/Lark Whiteboard](https://img.shields.io/badge/Feishu%2FLark-Whiteboard-00B96B)
![Language](https://img.shields.io/badge/Language-EN-blue)
![License](https://img.shields.io/github/license/VioletScar-Hui/Svg-design-system)
![Status](https://img.shields.io/badge/Status-Active-success)

**A reusable SVG visual design system for diagrams with real information hierarchy.**

`svg-design-system` is a Codex and Claude-compatible skill for turning articles, product notes, workflows, architecture descriptions, and abstract ideas into polished SVG diagrams. It provides named palettes, design tokens, layout recipes, a 5-level information hierarchy method, and a Feishu/Lark whiteboard-safe delivery pipeline.

This repository includes a `LICENSE` file. See [`CHANGELOG.md`](CHANGELOG.md) for major changes.

---

## Version Highlights

| Version | Focus | What Changed |
|---|---|---|
| v1.0 | Initial SVG design system release | Added the core skill instructions, 10 named three-color palettes, design tokens, diagram-type recipes, sample SVG cards, Feishu/Lark whiteboard pipeline, bilingual README files, and SVG example gallery. |

---

## Optional Prerequisite: Feishu/Lark Whiteboard Tools

The core SVG design system does not require any external dependency. It can draft SVG diagrams directly in chat or write `.svg` files in a workspace.

If the diagram must be uploaded into a Feishu/Lark document whiteboard, prepare these tools first:

```powershell
lark-cli --version
lark-cli auth status
npx -y @larksuite/whiteboard-cli@^0.2.11 -v
```

When Feishu/Lark delivery is unavailable, the skill can still generate board-safe SVG and explain the remaining upload steps.

---

## For AI Agents: Quick Install

Send this prompt to Codex or Claude Code and let the agent install or update the skill:

```text
帮我安装这个 skill：[VioletScar-Hui/Svg-design-system](https://github.com/VioletScar-Hui/Svg-design-system)
```

If you need to run the installation manually, or the agent needs executable commands, use the scripts below.

For Codex:

```powershell
$repoPath = "$env:USERPROFILE\.codex\skill-repos\Svg-design-system"
$skillPath = "$env:USERPROFILE\.codex\skills\svg-design-system"
if (Test-Path $repoPath) {
  Set-Location $repoPath
  git pull
} else {
  git clone https://github.com/VioletScar-Hui/Svg-design-system.git $repoPath
}
New-Item -ItemType Directory -Force $skillPath | Out-Null
Copy-Item -Path "$repoPath\svg-design-system\*" -Destination $skillPath -Recurse -Force
```

For Claude Code:

```powershell
$repoPath = "$env:USERPROFILE\.claude\skill-repos\Svg-design-system"
$skillPath = "$env:USERPROFILE\.claude\skills\svg-design-system"
if (Test-Path $repoPath) {
  Set-Location $repoPath
  git pull
} else {
  git clone https://github.com/VioletScar-Hui/Svg-design-system.git $repoPath
}
New-Item -ItemType Directory -Force $skillPath | Out-Null
Copy-Item -Path "$repoPath\svg-design-system\*" -Destination $skillPath -Recurse -Force
```

Then verify:

```powershell
Test-Path "$env:USERPROFILE\.codex\skills\svg-design-system\SKILL.md"
Get-Content "$env:USERPROFILE\.codex\skills\svg-design-system\SKILL.md" -TotalCount 8
```

For Claude Code, verify the same file under `$env:USERPROFILE\.claude\skills\svg-design-system\SKILL.md`.

Optional Feishu/Lark workflow verification:

```powershell
lark-cli auth status
npx -y @larksuite/whiteboard-cli@^0.2.11 -v
```

---

## Quick Start for Humans

### 1. Install the skill

Use the Codex or Claude Code install command above, then restart your agent.

### 2. Ask for a diagram

```text
Turn this article into an SVG architecture diagram for a newsletter.
```

```text
Draw this product workflow as a professional SVG flowchart.
```

```text
Make this Agent workflow board-safe for a Feishu/Lark document whiteboard.
```

### 3. Expected result

The agent should:

- Clarify the usage scenario and whether Feishu/Lark whiteboard upload is needed.
- Choose the diagram type from the content structure.
- Build the 5 information levels before styling.
- Apply one of the 10 named palettes and the design tokens.
- Output an SVG, PNG render, or Feishu/Lark whiteboard-safe SVG depending on the target.

---

## Example Gallery

These 10 SVG examples show the same information card rendered through the 10 named palettes. The business text is sample content only; the purpose is to demonstrate palette roles, contrast, hierarchy, and light/dark adaptation.

| Palette | Preview |
|---|---|
| 01 Deep Sea Coral | ![Deep Sea Coral example](svg-design-system/examples/palette-01-deep-sea-coral.svg) |
| 02 Acid Night | ![Acid Night example](svg-design-system/examples/palette-02-acid-night.svg) |
| 03 Forest Caramel | ![Forest Caramel example](svg-design-system/examples/palette-03-forest-caramel.svg) |
| 04 Wine Gold | ![Wine Gold example](svg-design-system/examples/palette-04-wine-gold.svg) |
| 05 Sea Breeze Daylight | ![Sea Breeze Daylight example](svg-design-system/examples/palette-05-sea-breeze-daylight.svg) |
| 06 Cool White Alert | ![Cool White Alert example](svg-design-system/examples/palette-06-cool-white-alert.svg) |
| 07 Cream Oasis | ![Cream Oasis example](svg-design-system/examples/palette-07-cream-oasis.svg) |
| 08 Cyber Neon | ![Cyber Neon example](svg-design-system/examples/palette-08-cyber-neon.svg) |
| 09 Wild Terracotta | ![Wild Terracotta example](svg-design-system/examples/palette-09-wild-terracotta.svg) |
| 10 Mint Dream | ![Mint Dream example](svg-design-system/examples/palette-10-mint-dream.svg) |

---

## When This Skill Triggers

Use this skill when the user needs to draw, design, or generate any of these diagram types:

- Flowchart
- Matrix or quadrant diagram
- Architecture diagram
- Timeline
- Relationship or node graph
- Cycle diagram
- Comparison chart

Also use it when the user describes the underlying need without naming the format, such as steps, process, pipeline, two-dimension classification, system layers, milestones over time, many-to-many relationships, closed feedback loops, A-vs-B comparison, converting text into a diagram, or placing a diagram into a Feishu/Lark document whiteboard.

---

## What It Produces

The skill can produce:

- Standalone SVG diagrams.
- Optional PNG renders for pasting into slides, docs, posts, or reports.
- Board-safe SVG variants for Feishu/Lark whiteboard workflows.
- Palette and token choices with clear semantic rationale.
- Diagram layouts that carry five information levels.

| Level | Question | Where It Lives |
|---|---|---|
| L1 | What is this diagram about? | Title block |
| L2 | What are the core modules? | Main boxes or nodes |
| L3 | How do modules relate? | Arrows, connectors, grouping, layout |
| L4 | What is the key takeaway? | Accent-color callout |
| L5 | What is the memory hook? | Distinctive symbol, metaphor, or shape |

---

## Core Features

### Content-First Diagram Selection

The skill chooses the diagram type by analyzing the content structure, not by visual preference. A sequential workflow becomes a flowchart, a two-axis classification becomes a matrix, layered modules become an architecture diagram, and repeated feedback becomes a cycle.

### 10 Named Palettes

Each palette has exactly three fixed roles:

| Role | Purpose |
|---|---|
| Background | Canvas fill and light/dark mode baseline |
| Ink | Text, borders, connectors, and structure |
| Accent | Key conclusion, critical arrow, or highest-value callout |

The palette names include `深海珊瑚`, `酸性幻夜`, `森林焦糖`, `酒红鎏金`, `海风日光`, `冷白警醒`, `奶油绿洲`, `赛博霓虹`, `荒野陶土`, and `薄荷梦境`.

### Design Tokens

The reference files define reusable rules for canvas ratios and margins, type scale and font stack, grid and spacing, strokes, corners, shadows, helper fills, light/dark adaptation, and board-safe replacements for unsupported SVG effects.

### Feishu/Lark Whiteboard Safety

For Feishu/Lark document whiteboards, the skill avoids unsupported SVG features such as `radialGradient`, `filter`, `clipPath`, and `mask`. When shadows are needed in board-safe output, it replaces filter shadows with offset translucent shapes.

---

## Repository Structure

```text
Svg-design-system/
  README.md
  README.en.md
  CHANGELOG.md
  LICENSE
  svg-design-system/
    README.md
    README.en.md
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

---

## Updating

For Codex:

```powershell
$repoPath = "$env:USERPROFILE\.codex\skill-repos\Svg-design-system"
$skillPath = "$env:USERPROFILE\.codex\skills\svg-design-system"
Set-Location $repoPath
git pull
Copy-Item -Path "$repoPath\svg-design-system\*" -Destination $skillPath -Recurse -Force
```

For Claude Code:

```powershell
$repoPath = "$env:USERPROFILE\.claude\skill-repos\Svg-design-system"
$skillPath = "$env:USERPROFILE\.claude\skills\svg-design-system"
Set-Location $repoPath
git pull
Copy-Item -Path "$repoPath\svg-design-system\*" -Destination $skillPath -Recurse -Force
```

Restart Codex or Claude Code after updating.

---

## Troubleshooting

### The skill does not trigger

Make sure the user request includes a visual-diagram intent, such as "draw this as an SVG architecture diagram" or "make a flowchart / matrix / timeline / comparison chart".

### The diagram looks decorative but not informative

Check whether the SVG contains all five information levels: title, core modules, relationships, key takeaway, and visual memory hook.

### Feishu/Lark whiteboard upload fails

Check that `lark-cli` works, `lark-cli auth status` shows a usable identity, `@larksuite/whiteboard-cli` is available, and the SVG is board-safe.

---

## License

This repository is released under the MIT License. See [`LICENSE`](LICENSE) for details.
