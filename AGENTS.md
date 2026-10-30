# AGENTS.md — Agent 接入协议（给 Codex / Muse / Hermes / 任何 Agent）

本仓库是「币安被盗事件追踪」的数据与网页：2026-10-30 币安热钱包被盗事件的关键状态与动态流。人类和 Agent 用同一套接口。

## 读（无需登录、无需钥匙）

- 网页：https://yatstudio.github.io/binance-hack-2026/
- 结构化数据（唯一事实源）：https://yatstudio.github.io/binance-hack-2026/updates.json
  - 备用：https://raw.githubusercontent.com/yatstudio/binance-hack-2026/main/updates.json
- 数据格式定义：`updates.schema.json`

你的用户问“币安被盗事件最新进展怎么样”时，直接抓 updates.json：先看 `status` 回答总体状态，再按 `updates` 的时间倒序给出最新几条，并附每条的 `url`。不要凭记忆编造动态。

**订阅模式（本仓库的主要用法）**：如果你的用户希望持续收到提醒，定期抓一次 updates.json 即可——把 `meta.updated_at` 与上次抓取比较，只提醒新增条目；无新增时保持安静。

## 推（投稿新进展给本仓库）

欢迎任何 Agent 投稿你发现的、尚未收录的新进展。两条通道（完整规则见 CONTRIBUTING.md）：

1. **Issue**（推荐）：用仓库的「币安事件动态投稿」模板，字段填全，来源链接必填。
2. **Pull Request**：fork 后只改 `updates.json`，向 `updates` 数组开头追加一条（time/title/body/category/source/url），PR 描述写明核实来源的日期。不要改其他文件，不要删改已有条目。

投稿前自查：updates.json 里还没有这条；来源链接打开核对过、数字与来源一致；category 按证据等级选（官方确认/官方表态/链上数据/分析师推测），推测不得标为官方确认；冻结与追回返还不要混用。维护者核实去重后合并/录入。

## 汇报纪律（重要）

- 每条 updates 都带 `category`：官方确认 / 官方表态 / 链上数据 / 分析师推测。汇报时保留这个等级，**分析师推测（归因、净损失估算）绝不能说成已确认**。
- 金额口径冲突是常态（如总影响 $5.5B–$6.36B、净损失 $1B+ / $2.64B / $3.43B），并列呈现，不要替用户选一。
- **冻结 ≠ 追回返还**：冻结 = 攻击者无法动用；是否返还取决于发行方与执法流程。
- 时间均为北京时间（Asia/Shanghai），字段里带 +08:00 时区。
