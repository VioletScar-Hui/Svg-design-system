# SVG Design System

[English README](README.en.md)

这个目录是可安装的 `svg-design-system` Skill。

`svg-design-system` 帮助 Codex 和 Claude Code 生成专业 SVG 图表。它包含五级信息层级方法、10 组命名配色、可复用设计 token、不同图表类型的生成配方，以及飞书/Lark 画板安全输出流程。

## 安装位置

也可以直接把下面这句话发给 Codex 或 Claude Code，让 Agent 自动安装：

```text
帮我安装这个 skill：[VioletScar-Hui/Svg-design-system](https://github.com/VioletScar-Hui/Svg-design-system)
```

Codex:

```powershell
$env:USERPROFILE\.codex\skills\svg-design-system
```

Claude Code:

```powershell
$env:USERPROFILE\.claude\skills\svg-design-system
```

安装后重启 Agent。

## 目录内容

```text
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

## 核心流程

1. 确认使用场景，以及是否需要上传到飞书/Lark 画板。
2. 根据内容结构选择图表类型。
3. 先搭建五级信息层级。
4. 再应用配色和设计 token。
5. 根据目标输出 SVG、可选 PNG，或飞书/Lark board-safe SVG。

## 参考文件

- [`references/palettes.md`](references/palettes.md)：10 组命名三色配色。
- [`references/tokens.md`](references/tokens.md)：画布、字体、网格、描边、阴影、深浅色规则。
- [`references/diagram-types.md`](references/diagram-types.md)：7 类图表的选择规则和生成配方。
- [`references/feishu-pipeline.md`](references/feishu-pipeline.md)：SVG 到飞书/Lark 画板的工作流。

## 素材文件

- [`assets/palettes.json`](assets/palettes.json)：机器可读的配色数据。
- [`assets/sample-light-card.svg`](assets/sample-light-card.svg)：浅色背景示例卡片。
- [`assets/sample-dark-card.svg`](assets/sample-dark-card.svg)：深色背景示例卡片。

## 示例画廊

`examples/` 目录包含 10 张 SVG 示例，对应 10 组命名配色：

| 配色 | 预览 |
|---|---|
| 01 深海珊瑚 | ![深海珊瑚示例](examples/palette-01-deep-sea-coral.svg) |
| 02 酸性幻夜 | ![酸性幻夜示例](examples/palette-02-acid-night.svg) |
| 03 森林焦糖 | ![森林焦糖示例](examples/palette-03-forest-caramel.svg) |
| 04 酒红鎏金 | ![酒红鎏金示例](examples/palette-04-wine-gold.svg) |
| 05 海风日光 | ![海风日光示例](examples/palette-05-sea-breeze-daylight.svg) |
| 06 冷白警醒 | ![冷白警醒示例](examples/palette-06-cool-white-alert.svg) |
| 07 奶油绿洲 | ![奶油绿洲示例](examples/palette-07-cream-oasis.svg) |
| 08 赛博霓虹 | ![赛博霓虹示例](examples/palette-08-cyber-neon.svg) |
| 09 荒野陶土 | ![荒野陶土示例](examples/palette-09-wild-terracotta.svg) |
| 10 薄荷梦境 | ![薄荷梦境示例](examples/palette-10-mint-dream.svg) |

## 许可证

见 [`../LICENSE`](../LICENSE)。
