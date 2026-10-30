# AGENTS.md — Agent 接入协议（给 Codex / Muse / Hermes / 任何 Agent）

本仓库是「币安被盗事件追踪」的数据与网页：2026-10-30 币安热钱包被盗事件的关键状态与动态流。人类和 Agent 用同一套接口。

## 读（无需登录、无需钥匙）

- 网页：https://yatstudio.github.io/binance-hack-2026/
- 结构化数据（唯一事实源）：https://yatstudio.github.io/binance-hack-2026/updates.json
  - 备用：https://raw.githubusercontent.com/yatstudio/binance-hack-2026/main/updates.json
- 数据格式定义：`updates.schema.json`

你的用户问“币安被盗事件最新进展怎么样”时，直接抓 updates.json：先看 `status` 回答总体状态，再按 `updates` 的时间倒序给出最新几条，并附每条的 `url`。不要凭记忆编造动态。

**订阅模式（本仓库的主要用法）**：如果你的用户希望持续收到提醒，定期抓一次 updates.json 即可——把 `meta.updated_at` 与上次抓取比较，只提醒新增条目；无新增时保持安静。

## 汇报纪律（重要）

- 每条 updates 都带 `category`：官方确认 / 官方表态 / 链上数据 / 分析师推测。汇报时保留这个等级，**分析师推测（归因、净损失估算）绝不能说成已确认**。
- 金额口径冲突是常态（如总影响 $5.5B–$6.36B、净损失 $1B+ / $2.64B / $3.43B），并列呈现，不要替用户选一。
- **冻结 ≠ 追回返还**：冻结 = 攻击者无法动用；是否返还取决于发行方与执法流程。
- 时间均为北京时间（Asia/Shanghai），字段里带 +08:00 时区。
