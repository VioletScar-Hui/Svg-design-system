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

## Example Gallery

These 10 SVG examples show the same information card rendered through the 10 named palettes. The business text is sample content only; the purpose is to demonstrate palette roles, contrast, hierarchy, and light/dark adaptation.

| Palette | Preview |
|---|---|
| 01 深海珊瑚 / Deep Sea Coral | ![Deep Sea Coral example](svg-design-system/examples/palette-01-deep-sea-coral.svg) |
| 02 酸性幻夜 / Acid Night | ![Acid Night example](svg-design-system/examples/palette-02-acid-night.svg) |
| 03 森林焦糖 / Forest Caramel | ![Forest Caramel example](svg-design-system/examples/palette-03-forest-caramel.svg) |
| 04 酒红鎏金 / Wine Gold | ![Wine Gold example](svg-design-system/examples/palette-04-wine-gold.svg) |
| 05 海风日光 / Sea Breeze Daylight | ![Sea Breeze Daylight example](svg-design-system/examples/palette-05-sea-breeze-daylight.svg) |
| 06 冷白警醒 / Cool White Alert | ![Cool White Alert example](svg-design-system/examples/palette-06-cool-white-alert.svg) |
| 07 奶油绿洲 / Cream Oasis | ![Cream Oasis example](svg-design-system/examples/palette-07-cream-oasis.svg) |
| 08 赛博霓虹 / Cyber Neon | ![Cyber Neon example](svg-design-system/examples/palette-08-cyber-neon.svg) |
| 09 荒野陶土 / Wild Terracotta | ![Wild Terracotta example](svg-design-system/examples/palette-09-wild-terracotta.svg) |
| 10 薄荷梦境 / Mint Dream | ![Mint Dream example](svg-design-system/examples/palette-10-mint-dream.svg) |

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

`svg-design-system` 是一个同时支持 Codex 和 Claude Code 的 SVG 图表设计系统 Skill。它面向文章可视化、产品分析、业务流程、系统架构、项目汇报和飞书/Lark 文档画板场景，帮助 Agent 生成有信息层级、有统一视觉规则、且可复用的 SVG 图。

它的核心不是“套模板画得漂亮”，而是把图表生成拆成一套稳定流程：

1. 先判断内容的真实结构。
2. 再选择合适的图表类型。
3. 先搭建五级信息层级。
4. 最后套用色彩、字号、网格、描边、阴影等视觉系统。

这样生成的图不只是好看，而是能让读者快速看懂主题、模块、关系、重点结论和记忆点。

### 版本更新摘要

| 版本 | 重点 | 更新内容 |
|---|---|---|
| v1.0 | SVG 图表设计系统首版 | 新增核心 Skill 指令、10 组三色命名配色、设计 token、7 类图表生成配方、示例 SVG 卡片，以及飞书/Lark 画板安全上传流程。 |

完整记录见 [`CHANGELOG.md`](CHANGELOG.md)。

### 可选前置条件：飞书/Lark 画板工具

普通 SVG 生成不需要额外依赖；Agent 可以直接在对话中产出 SVG，或在工作区写入 `.svg` 文件。

如果需要把图上传到飞书/Lark 文档画板，建议先检查：

```powershell
lark-cli --version
lark-cli auth status
npx -y @larksuite/whiteboard-cli@^0.2.11 -v
```

当飞书/Lark 权限或工具不可用时，Skill 仍然可以生成 board-safe SVG，并列出后续上传步骤。

### 给 AI Agent 的快速安装

Codex:

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

Claude Code:

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

安装后验证：

```powershell
Test-Path "$env:USERPROFILE\.codex\skills\svg-design-system\SKILL.md"
Get-Content "$env:USERPROFILE\.codex\skills\svg-design-system\SKILL.md" -TotalCount 8
```

Claude Code 用户把路径替换为 `$env:USERPROFILE\.claude\skills\svg-design-system\SKILL.md` 即可。

安装或更新后，需要重启 Codex 或 Claude Code，让 Skill 索引重新加载。

### 人类用户快速开始

安装后可以直接向 Agent 提出这类请求：

```text
把这段文章整理成一张适合公众号使用的 SVG 架构图。
```

```text
帮我把这个产品流程画成流程图，输出 SVG，风格要偏冷静专业。
```

```text
把这套 Agent 工作流做成飞书文档画板可用的图，注意要 board-safe。
```

正常情况下，Agent 应该完成：

- 确认使用场景和是否需要上传到飞书/Lark 画板。
- 根据内容结构选择图表类型。
- 先搭建五级信息层级，再进行视觉设计。
- 从 10 组命名配色中选择合适方案。
- 输出 SVG、可选 PNG，或飞书/Lark 画板安全版本。

### 示例画廊

下面 10 张 SVG 示例展示同一张信息卡片在 10 组命名配色下的效果。卡片里的 FDE × AI PM 文案只是示例内容，不是固定模板；它主要用于展示配色角色、明暗适配、信息层级和强调色使用方式。

| 配色 | 预览 |
|---|---|
| 01 深海珊瑚 / Deep Sea Coral | ![深海珊瑚示例](svg-design-system/examples/palette-01-deep-sea-coral.svg) |
| 02 酸性幻夜 / Acid Night | ![酸性幻夜示例](svg-design-system/examples/palette-02-acid-night.svg) |
| 03 森林焦糖 / Forest Caramel | ![森林焦糖示例](svg-design-system/examples/palette-03-forest-caramel.svg) |
| 04 酒红鎏金 / Wine Gold | ![酒红鎏金示例](svg-design-system/examples/palette-04-wine-gold.svg) |
| 05 海风日光 / Sea Breeze Daylight | ![海风日光示例](svg-design-system/examples/palette-05-sea-breeze-daylight.svg) |
| 06 冷白警醒 / Cool White Alert | ![冷白警醒示例](svg-design-system/examples/palette-06-cool-white-alert.svg) |
| 07 奶油绿洲 / Cream Oasis | ![奶油绿洲示例](svg-design-system/examples/palette-07-cream-oasis.svg) |
| 08 赛博霓虹 / Cyber Neon | ![赛博霓虹示例](svg-design-system/examples/palette-08-cyber-neon.svg) |
| 09 荒野陶土 / Wild Terracotta | ![荒野陶土示例](svg-design-system/examples/palette-09-wild-terracotta.svg) |
| 10 薄荷梦境 / Mint Dream | ![薄荷梦境示例](svg-design-system/examples/palette-10-mint-dream.svg) |

### 适合什么场景？

当用户需要绘制、设计或生成以下图表时，应触发这个 Skill：

- 流程图 / Flowchart
- 矩阵图 / Matrix
- 架构图 / Architecture
- 时间轴 / Timeline
- 关系图 / 节点图 / Network
- 循环图 / Cycle
- 对比图 / Comparison

即使用户没有说出具体图表名称，只要描述的是下面这些结构，也适合使用：

- 步骤、流程、管线、因果链。
- 两个维度交叉分类、优先级矩阵。
- 系统层级、模块组成、技术架构。
- 时间演进、里程碑、路线图。
- 多实体之间的复杂关系。
- 闭环反馈、增长飞轮、Agent loop。
- A 与 B 的并列对比。
- 把文章或长文本转成一张图。
- 把图放入飞书/Lark 文档画板。

### 不适合什么场景？

如果用户只是要普通文字总结、代码修复、产品推荐、闲聊解释，或者不需要图表表达，就不应该触发这个 Skill。

### 输出内容

Skill 可以产出：

- 独立 SVG 图表。
- 适合粘贴到 PPT、文档、公众号或报告里的 PNG 渲染图。
- 适合飞书/Lark 文档画板的 board-safe SVG。
- 带有语义说明的配色和 token 选择。
- 覆盖五级信息层级的图表布局。

### 核心方法

每张图必须回答五个问题：

1. 这张图讲什么？
2. 核心模块有哪些？
3. 模块之间是什么关系？
4. 最重要的结论是什么？
5. 读者明天还能记住什么？

对应到 SVG 中：

| 层级 | 问题 | 在图中体现为 |
|---|---|---|
| L1 一级信息 | 这张图讲什么？ | 标题区 |
| L2 二级信息 | 核心模块有哪些？ | 主盒子 / 主节点 |
| L3 三级信息 | 模块之间是什么关系？ | 箭头、连线、分组、布局 |
| L4 四级信息 | 重点结论是什么？ | 强调色 callout |
| L5 五级信息 | 视觉记忆点是什么？ | 独特符号、隐喻或形状 |

### 核心能力

#### 根据内容选择图表

Skill 会根据内容结构选择图表类型，而不是默认把所有内容都画成流程图。比如：顺序步骤适合流程图，两个独立维度适合矩阵图，系统模块适合架构图，时间演进适合时间轴，闭环反馈适合循环图。

#### 10 组命名配色

每组配色固定为三个角色：

| 角色 | 用途 |
|---|---|
| 底色 / Background | 画布背景，决定浅色或深色模式 |
| 主墨色 / Ink | 文字、边框、连线和主体结构 |
| 高能强调 / Accent | 核心结论、关键箭头、最高价值提示 |

目前包含：`深海珊瑚`、`酸性幻夜`、`森林焦糖`、`酒红鎏金`、`海风日光`、`冷白警醒`、`奶油绿洲`、`赛博霓虹`、`荒野陶土`、`薄荷梦境`。

#### 设计 Token

`references/tokens.md` 定义了：

- 画布比例和边距。
- 字号层级和字体栈。
- 网格和间距。
- 描边、圆角、阴影和辅助色。
- 深色/浅色适配规则。
- 飞书/Lark 画板安全替代方案。

#### 飞书/Lark 画板安全约束

飞书/Lark 文档画板不支持部分 SVG 特性。面向画板输出时，Skill 会避免：

- `radialGradient`
- `filter`
- `clipPath`
- `mask`

如果需要阴影，会用偏移的半透明形状模拟，而不是使用 `filter`。

### 仓库结构

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

### 更新方式

Codex:

```powershell
$repoPath = "$env:USERPROFILE\.codex\skill-repos\Svg-design-system"
$skillPath = "$env:USERPROFILE\.codex\skills\svg-design-system"
Set-Location $repoPath
git pull
Copy-Item -Path "$repoPath\svg-design-system\*" -Destination $skillPath -Recurse -Force
```

Claude Code:

```powershell
$repoPath = "$env:USERPROFILE\.claude\skill-repos\Svg-design-system"
$skillPath = "$env:USERPROFILE\.claude\skills\svg-design-system"
Set-Location $repoPath
git pull
Copy-Item -Path "$repoPath\svg-design-system\*" -Destination $skillPath -Recurse -Force
```

更新后重启 Codex 或 Claude Code。

### 常见问题

#### Skill 没有触发

确认请求中包含图表生成意图，例如：

```text
请把这段内容画成 SVG 架构图。
```

```text
帮我做一张流程图 / 矩阵图 / 时间轴 / 对比图。
```

#### 图看起来好看但信息不够清楚

检查 SVG 是否包含完整五级信息：

- L1 标题。
- L2 核心模块。
- L3 模块关系。
- L4 重点结论。
- L5 视觉记忆点。

#### 飞书/Lark 画板上传失败

检查：

- `lark-cli --version` 是否可用。
- `lark-cli auth status` 是否有可用身份。
- `@larksuite/whiteboard-cli` 是否可用。
- SVG 是否为 board-safe，没有使用不支持的 `filter`、`mask`、`clipPath` 或 `radialGradient`。

### 维护建议

后续可以继续补充：

- 更多示例 SVG。
- 更多飞书画板上传验证案例。
- 不同内容类型的图表 prompt 示例。
- 自动渲染 PNG 的脚本或测试用例。

---

## License

This repository is released under the MIT License. See [`LICENSE`](LICENSE) for details.
