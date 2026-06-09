# SVG Design System Skill

![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827)
![Claude Compatible](https://img.shields.io/badge/Claude-Compatible-6B46C1)
![SVG Diagrams](https://img.shields.io/badge/SVG-Diagrams-FFB000)
![Feishu/Lark Whiteboard](https://img.shields.io/badge/Feishu%2FLark-Whiteboard-00B96B)
![Language](https://img.shields.io/badge/Language-ZH%20%2B%20EN-blue)
![License](https://img.shields.io/github/license/VioletScar-Hui/Svg-design-system)
![Status](https://img.shields.io/badge/Status-Active-success)

**A reusable SVG visual design system for diagrams with real information hierarchy.**

`svg-design-system` is a Codex and Claude-compatible skill for turning articles, product notes, workflows, architecture descriptions, and abstract ideas into polished SVG diagrams. It provides named palettes, design tokens, layout recipes, a 5-level information hierarchy method, and a Feishu/Lark whiteboard-safe delivery pipeline.

`svg-design-system` 是一个同时支持 Codex 和 Claude Code 的 Skill，用于生成专业、清晰、可复用的 SVG 图表。它不是简单“画得好看”，而是帮助 Agent 先识别内容结构，再选择流程图、矩阵图、架构图、时间轴、关系图、循环图或对比图，并用统一的色彩、字号、阴影、网格和信息层级完成视觉表达。

This repository includes a `LICENSE` file. See [`CHANGELOG.md`](CHANGELOG.md) for major changes.

---

## Version Highlights

| Version | Focus | What Changed |
|---|---|---|
| v1.0 | Initial SVG design system release | Added the core skill instructions, 10 named three-color palettes, design tokens, diagram-type recipes, sample SVG cards, and Feishu/Lark whiteboard pipeline. |

See [`CHANGELOG.md`](CHANGELOG.md) for full details.

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

If a user asks you to install this skill, install or update it from GitHub, then restart the agent so the skill index reloads.

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
把这段文章整理成一张适合公众号使用的 SVG 架构图。
```

```text
帮我把这个产品流程画成流程图，输出 SVG，风格要偏冷静专业。
```

```text
把这套 Agent 工作流做成飞书文档画板可用的图，注意要 board-safe。
```

### 3. Expected result

The agent should:

- Clarify the usage scenario and whether Feishu/Lark whiteboard upload is needed.
- Choose the diagram type from the content structure.
- Build the 5 information levels before styling.
- Apply one of the 10 named palettes and the design tokens.
- Output an SVG, PNG render, or Feishu/Lark whiteboard-safe SVG depending on the target.

---

## When This Skill Triggers

Use this skill when the user needs to draw, design, or generate any of these diagram types:

- Flowchart / 流程图
- Matrix or quadrant diagram / 矩阵图
- Architecture diagram / 架构图
- Timeline / 时间轴
- Relationship or node graph / 关系图 / 节点图
- Cycle diagram / 循环图
- Comparison chart / 对比图

Also use it when the user describes the underlying need without naming the format, such as:

- steps, process, pipeline, causal chain
- two-dimension classification or priority mapping
- system layers, modules, architecture, stack
- milestones over time
- many-to-many relationships
- closed feedback loop
- A-vs-B comparison
- converting article or text content into a diagram
- placing a diagram into a Feishu/Lark document whiteboard

---

## What It Produces

The skill can produce:

- Standalone SVG diagrams.
- Optional PNG renders for pasting into slides, docs, posts, or reports.
- Board-safe SVG variants for Feishu/Lark whiteboard workflows.
- Palette and token choices with clear semantic rationale.
- Diagram layouts that carry five information levels:

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
| Background / 底色 | Canvas fill and light/dark mode baseline |
| Ink / 主墨色 | Text, borders, connectors, and structure |
| Accent / 高能强调 | Key conclusion, critical arrow, or highest-value callout |

The palette names include `深海珊瑚`, `酸性幻夜`, `森林焦糖`, `酒红鎏金`, `海风日光`, `冷白警醒`, `奶油绿洲`, `赛博霓虹`, `荒野陶土`, and `薄荷梦境`.

### Design Tokens

The reference files define reusable rules for:

- Canvas ratios and margins.
- Type scale and font stack.
- Grid and spacing.
- Strokes, corners, shadows, and helper fills.
- Light/dark adaptation.
- Board-safe replacements for unsupported SVG effects.

### Feishu/Lark Whiteboard Safety

For Feishu/Lark document whiteboards, the skill avoids unsupported SVG features such as:

- `radialGradient`
- `filter`
- `clipPath`
- `mask`

When shadows are needed in board-safe output, it replaces filter shadows with offset translucent shapes.

---

## Repository Structure

```text
Svg-design-system/
  README.md
  CHANGELOG.md
  LICENSE
  svg-design-system/
    README.md
    SKILL.md
    assets/
      palettes.json
      sample-dark-card.svg
      sample-light-card.svg
    references/
      diagram-types.md
      feishu-pipeline.md
      palettes.md
      tokens.md
```

---

## Updating

If you already installed the skill:

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

Make sure the user request includes a visual-diagram intent, such as:

```text
请把这段内容画成 SVG 架构图。
```

```text
帮我做一张流程图 / 矩阵图 / 时间轴 / 对比图。
```

### The diagram looks decorative but not informative

Check whether the SVG contains all five information levels:

- L1 title
- L2 core modules
- L3 relationships
- L4 key takeaway
- L5 visual memory hook

### Feishu/Lark whiteboard upload fails

Check:

- `lark-cli --version` works.
- `lark-cli auth status` shows a usable identity.
- `@larksuite/whiteboard-cli` is available.
- The SVG is board-safe and does not use unsupported filters, masks, clip paths, or radial gradients.

---

## 中文说明

### 这是什么？

`svg-design-system` 是一个面向 Agent 的 SVG 图表设计系统。它把“画图”拆成三个动作：先判断内容结构，再搭建信息层级，最后套用视觉系统。这样生成的图不只是好看，而是能让读者快速看懂主题、模块、关系、重点结论和记忆点。

### 适合什么场景？

适合把文章、产品笔记、业务流程、系统架构、用户旅程、竞品对比、项目路线图、Agent 工作流等内容转成 SVG 图。

### 不适合什么场景？

如果用户只是要普通文字总结、代码修复、产品推荐，或者不需要图表表达，就不应该触发这个 skill。

### 核心方法

每张图必须回答五个问题：

1. 这张图讲什么？
2. 核心模块有哪些？
3. 模块之间是什么关系？
4. 最重要的结论是什么？
5. 读者明天还能记住什么？

### 维护建议

后续可以继续补充：

- 更多示例 SVG。
- 更多飞书画板上传验证案例。
- 不同内容类型的图表 prompt 示例。
- 自动渲染 PNG 的脚本或测试用例。

---

## License

This repository is released under the MIT License. See [`LICENSE`](LICENSE) for details.
