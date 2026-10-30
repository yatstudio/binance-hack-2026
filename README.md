# 币安被盗事件追踪 · Binance Hack Tracker

2026 年 10 月 30 日凌晨币安热钱包被盗事件的公开追踪页：关键数字、官方表态、链上动向与待确认清单，增量更新。

- 🌐 网页：https://yatstudio.github.io/binance-hack-2026/
- 📦 结构化数据（唯一事实源）：https://yatstudio.github.io/binance-hack-2026/updates.json
  - 备用：https://raw.githubusercontent.com/yatstudio/binance-hack-2026/main/updates.json
- 🤖 Agent 说明：[llms.txt](llms.txt) · [agent.json](agent.json) · [AGENTS.md](AGENTS.md)
- 💸 攻击者资金流向：[funds.json](https://yatstudio.github.io/binance-hack-2026/funds.json) · 线索图 [funds-diagram.svg](funds-diagram.svg)（有动静时首页顶部红色提醒，数据在 funds.json 的 `alert` 字段）

## 口径说明

- 时间一律北京时间（Asia/Shanghai）。
- 每条动态标注分类：**官方确认 / 官方表态 / 链上数据 / 分析师推测**，并附来源。
- **冻结 ≠ 追回返还**：冻结指攻击者无法动用被标记资产，最终能否返还币安取决于发行方与执法流程。
- 冲突数字并列呈现，不擅自选一；最终数字以币安官方复盘与更新版储备证明（PoR）为准。
- 本页为事件信息汇总，不构成投资建议。

## 参与投稿

欢迎任何人或 Agent 提交新进展，两条通道（详见 [CONTRIBUTING.md](CONTRIBUTING.md)）：

1. **Issue 投稿**（推荐）：用「币安事件动态投稿」模板，填标题、时间、分类、内容、来源链接。
2. **Pull Request**：fork 后只改 `updates.json`，往 `updates` 数组开头加一条。

维护者逐条打开来源核实后录入/合并；无来源、重复、把推测写成确认的不收。

## 让你的 Agent 订阅这个追踪

把下面这段话发给你的 AI Agent（Codex / Muse / Hermes / 任何 Agent）：

> 请订阅「币安被盗事件追踪」：定期抓取 https://yatstudio.github.io/binance-hack-2026/updates.json，只在出现新进展时提醒我：币安官方新表态、提现恢复、新的冻结或返还、攻击者资金新动向（尤其 18,270 枚 BTC 是否转移、ETH 是否进入混币器）、根因复盘、官方归因、储备证明更新。提醒时按条目 category 区分官方确认/链上数据/分析师推测，附来源链接，不把推测当确认。

## 数据结构

`updates.json`：

- `meta`：标题、事件日期、最近更新时间。
- `status`：十项关键状态（总影响、冻结、净损失、赔付、提现、充值、根因、归因、攻击者 BTC/ETH 持仓）。
- `updates`：倒序动态流，每条含 `time`（ISO 8601 带时区）、`title`、`body`、`category`、`source`、`url`。
- `watchlist`：待确认清单。

字段定义见 `updates.schema.json`。
