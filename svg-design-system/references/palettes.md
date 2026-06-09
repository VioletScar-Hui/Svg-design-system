# Palettes — 10 named three-color schemes

Each palette is **three colors with fixed roles**. Assign them, don't improvise:

- **底色 / background** — the canvas fill. Decides light vs dark mode (see `tokens.md`).
- **主墨色 / ink** — structure and text: borders, connectors, body copy, node outlines.
- **高能强调 / accent** — the one high-energy color. Use it *sparingly*, reserved for **L4 (key
  takeaway)** and the most important arrow/marker. If everything is accent, nothing is.

Pick a palette by **semantic fit**, not just looks — match the "note" to the article's mood/topic.

| # | Name | Background (底色) | Ink (主墨色) | Accent (高能强调) | Mode | Semantic fit (note) |
| --- | --- | --- | --- | --- | --- | --- |
| 01 | 深海珊瑚 | `#F7F5EF` | `#0B1026` | `#FF4D5A` | light | 冷静底色 + 高能决策点 |
| 02 | 酸性幻夜 | `#111827` | `#C7FF33` | `#D8B4FE` | dark | 黑夜系统 + 酸性增长信号 |
| 03 | 森林焦糖 | `#F3F0D7` | `#2F5D50` | `#D96C2C` | light | 稳态产品框架 + 温暖业务洞察 |
| 04 | 酒红鎏金 | `#3A0D1A` | `#F5C9C6` | `#D6A84F` | dark | 战略感 + 高价值落地 |
| 05 | 海风日光 | `#C8F7E2` | `#102A43` | `#FFD166` | light | 清爽协作 + 明确优先级 |
| 06 | 冷白警醒 | `#F8F9FA` | `#1446A0` | `#E63946` | light | 理性仪表盘 + 风险报警 |
| 07 | 奶油绿洲 | `#F6E8D7` | `#3B2F2F` | `#41C9B4` | light | 温和体验 + 智能工作流 |
| 08 | 赛博霓虹 | `#050505` | `#8B5CF6` | `#00F5FF` | dark | Agent 中控台 + 未来感执行 |
| 09 | 荒野陶土 | `#F1E4D1` | `#5C3A21` | `#C65D3A` | light | 从混沌需求里挖出产品真相 |
| 10 | 薄荷梦境 | `#EFFFF8` | `#264653` | `#A78BFA` | light | 轻量 AI 协作 + 灵感原型 |

## Notes on a few palettes

- **02 酸性幻夜 / 04 酒红鎏金 / 08 赛博霓虹** are dark-background. On these, the *ink* role is light
  and the helper rgba colors flip to white-based (see `tokens.md` → light/dark rules).
- In dark palettes the "ink" is the structural/brand color and the **text** uses a near-white derived
  from it or `rgba(255,255,255,.72)` for secondary text.

## Two-accent palettes

Palettes 02, 04, 08 effectively carry two vivid colors (ink is also vivid). Use the **second vivid
color for secondary emphasis** (e.g., a secondary arrow) and keep the true accent for L4 only.

## Machine-readable source

`assets/palettes.json` holds the same data as `[{name, hex:[bg, ink, accent], note}]` for
programmatic use.
