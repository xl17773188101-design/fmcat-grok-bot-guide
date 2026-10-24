# Grok Bot 新手指南 · 全文学习笔记

> 学习时间：2026-10-24（Asia/Shanghai）
> 源站：https://bot.fmcat.top/ （社区非官方；订阅规则以 2026-10-12 The X Subscription 为准）
> 约束：本笔记只研究落盘，未创建例程、未装插件、未代发消息。

## 0. 总览：学完后总管应改变的工作方式

1. **只报拍板，不报流水**：日常由五席自转；总管只汇总「上线/发帖/花钱/改生产」类决策，附建议。
2. **中心辐射，禁止横向互聊**：总管单向派活；交接一律 `/workspace` 落盘，严禁多 Bot 群聊互唤（烧额度）。
3. **先 Skill 后 Routine**：跑通→沉淀技能→再设定时；监控类用 Linux cron 轻量比对，有变化再 Webhook 唤醒。
4. **人闸默认 Ask first**：发帖、发邮件、支付、删库、改配置必须弹卡；微信/社群内容只出草稿不代发。
5. **省额度三板斧**：单任务单会话；长文落盘只回路径；关掉或严限 On-demand；例程无变化静默退出。
6. **通道选型**：随身调度走微信 ClawBot（纯文本、白名单）；团队派工走飞书长连接；图文入库走快捷指令+Webhook。
7. **QQ/个人微信群代发**：教程不支持个人 QQ 聊天接入；微信 ClawBot 非群发机器人；社群软广继续「草稿+陛下手发」。

## 1. 站点地图（章节标题 + URL）

| 分区 | 标题 | URL | 本地正文约字符 |
| --- | --- | --- | ---: |
| 首页 | index.md | https://bot.fmcat.top/ | 1033 |
| 专题·Grok vs Grok Bot | Grok 和 Grok Bot 有什么区别 | https://bot.fmcat.top/part1/grok-vs-grok-bot | 2528 |
| 第1章 | 第 1 章 Grok Bot 是什么：一个自带电脑的 AI 同事 | https://bot.fmcat.top/part1/01-what-is | 6131 |
| 第2章 | 第 2 章 方案与订阅：先选对档位 | https://bot.fmcat.top/part1/02-plans | 7193 |
| 第3章 | 第 3 章 安装登录与第一个 Bot | https://bot.fmcat.top/part1/03-install | 5422 |
| 第4章 | 第 4 章 交代任务：消息、附件与一次好的交接 | https://bot.fmcat.top/part1/04-handoff | 6942 |
| 第5章 | 第 5 章 共享云电脑：文件、浏览器与接管 | https://bot.fmcat.top/part1/05-computer | 6749 |
| 第6章 | 第 6 章 记忆：让 Bot 越用越懂你 | https://bot.fmcat.top/part1/06-memory | 6500 |
| 第7章 | 第 7 章 连接应用：插件、邮箱与 Secrets | https://bot.fmcat.top/part1/07-apps | 5175 |
| 第8章 | 第 8 章 技能与例程：把一次成功变成每天自动跑 | https://bot.fmcat.top/part1/08-skills-routines | 8082 |
| 第9章 | 第 9 章 群聊与团队 Bot：从一个 Bot 到一组 Bot | https://bot.fmcat.top/part1/09-group-team | 6882 |
| 第10章 | 第 10 章 额度与成本：让一周用量撑满一周 | https://bot.fmcat.top/part1/10-usage | 8817 |
| 第11章 | 第 11 章 权限、安全与人闸 | https://bot.fmcat.top/part1/11-safety | 8540 |
| 第12章 | 第 12 章 案例：自媒体与内容团队 | https://bot.fmcat.top/part2/12-content | 11986 |
| 第13章 | 第 13 章 案例：在 X 上做内容与运营 | https://bot.fmcat.top/part2/13-x-ops | 9576 |
| 第14章 | 第 14 章 案例：工程与研发团队 | https://bot.fmcat.top/part2/14-engineering | 11588 |
| 第15章 | 第 15 章 案例：电商与生活实操 | https://bot.fmcat.top/part2/15-ecommerce | 6656 |
| 第16章 | 第 16 章 案例：知识自动入库与微信打通 | https://bot.fmcat.top/part2/16-knowledge | 5214 |
| 第17章 | 第 17 章 案例：GTM、销售与幕僚长 | https://bot.fmcat.top/part2/17-gtm | 16805 |
| 第18章 | 第 18 章 案例：一人公司与 AI 团队 | https://bot.fmcat.top/part2/18-solo | 10688 |
| 第19章 | 第 19 章 团队编排：章程、岗位与放权 | https://bot.fmcat.top/part3/19-orchestration | 12519 |
| 第20章 | 第 20 章 可靠的自动化：定时、Webhook 与事件触发 | https://bot.fmcat.top/part3/20-automation | 6909 |
| 第21章 | 第 21 章 备份与恢复：电脑重置也不慌 | https://bot.fmcat.top/part3/21-backup | 8650 |
| 第22章 | 第 22 章 接入飞书与微信 | https://bot.fmcat.top/part3/22-feishu-wechat | 6462 |
| 第23章 | 第 23 章 团队版与企业落地 | https://bot.fmcat.top/part4/23-enterprise | 11172 |
| 第24章 | 第 24 章 按岗位组建你的 AI 团队 | https://bot.fmcat.top/part4/24-roles | 9161 |
| 第25章 | 第 25 章 常见问题与排错 | https://bot.fmcat.top/part4/25-faq | 7843 |
| 案例库 | 案例库 | https://bot.fmcat.top/cases/ | 1166 |
| 案例·中文长文 | 中文长文精选 | https://bot.fmcat.top/cases/cn | 6214 |
| 案例·英文上 | 英文长文精选（上） | https://bot.fmcat.top/cases/en1 | 6144 |
| 案例·英文下 | 英文长文精选（下） | https://bot.fmcat.top/cases/en2 | 6500 |
| 案例·铁柱 | 铁柱的实战长文与推文 | https://bot.fmcat.top/cases/tiezhu | 6519 |
| 案例·X热帖 | X 热帖案例精选 | https://bot.fmcat.top/cases/x-hot | 8280 |
| 工具箱 | tools__index.md | https://bot.fmcat.top/tools/ | 1289 |
| Bot直聘 | bots__index.md | https://bot.fmcat.top/bots/ | 827 |
| 周边生态 | ecosystem__index.md | https://bot.fmcat.top/ecosystem/ | 157 |
| Clipper插件 | ecosystem__grok-bot-clipper.md | https://bot.fmcat.top/ecosystem/grok-bot-clipper | 1199 |
| 更新日志 | changelog__index.md | https://bot.fmcat.top/changelog/ | 45574 |
| 关于 | 关于铁柱AGI | https://bot.fmcat.top/about | 843 |
| 付费答疑群 | 付费答疑群 | https://bot.fmcat.top/group | 438 |
| agently-cli | agently-cli（Agent 邮箱命令行） | https://bot.fmcat.top/tools/agently-cli | 581 |
| agy | Antigravity CLI（agy） | https://bot.fmcat.top/tools/agy | 611 |
| claude-code | Claude Code | https://bot.fmcat.top/tools/claude-code | 563 |
| codex | Codex CLI | https://bot.fmcat.top/tools/codex | 614 |
| cursor-cli | Cursor CLI | https://bot.fmcat.top/tools/cursor-cli | 560 |
| egress-proxy | 固定出口代理（SSH 隧道） | https://bot.fmcat.top/tools/egress-proxy | 559 |
| feishu-bot | 飞书机器人长连接 | https://bot.fmcat.top/tools/feishu-bot | 597 |
| ffmpeg | FFmpeg | https://bot.fmcat.top/tools/ffmpeg | 463 |
| gemini-cli | Gemini CLI | https://bot.fmcat.top/tools/gemini-cli | 606 |
| gh | GitHub CLI（gh） | https://bot.fmcat.top/tools/gh | 589 |
| lark-cli | 飞书 CLI（lark-cli） | https://bot.fmcat.top/tools/lark-cli | 552 |
| mcp-connectors | MCP 连接器 | https://bot.fmcat.top/tools/mcp-connectors | 543 |
| muse2api | muse2api | https://bot.fmcat.top/tools/muse2api | 562 |
| nodejs | Node.js 与 npm | https://bot.fmcat.top/tools/nodejs | 499 |
| pi | Pi Coding Agent | https://bot.fmcat.top/tools/pi | 558 |
| playwright | Playwright | https://bot.fmcat.top/tools/playwright | 508 |
| x-api | X API 发帖（OAuth 1.0a PIN） | https://bot.fmcat.top/tools/x-api | 611 |
| yt-dlp | yt-dlp | https://bot.fmcat.top/tools/yt-dlp | 491 |

### 抓取缺口

- ecosystem__index.md — https://bot.fmcat.top/ecosystem/ — 157 chars — 正文过短或 SPA 壳页
- `bots/`、`changelog/`、`ecosystem/`、首页等为 VitePress 动态页：已用 SSR HTML 文本补全要点；changelog 体量大已落盘。
- 工具页本身就是「短说明+安装提示词」结构，约 300–500 字属正常。
- 社区飞书外链长文未全文镜像（仅章节内摘要）；需要时可另开任务抓飞书 wiki。

## 2. 分章要点（3–8 条）

### Grok 和 Grok Bot 有什么区别
- URL：https://bot.fmcat.top/part1/grok-vs-grok-bot
- Grok=对话产品；Grok Bot=带云电脑的常驻 Agent。
- 网页 Grok 充值不抵扣 Bot 周额度。
- Bot 适合自动化与跨工具；纯问答用网页/App 更省。

### 第 1 章 Grok Bot 是什么：一个自带电脑的 AI 同事
- URL：https://bot.fmcat.top/part1/01-what-is
- 底座(Harness)常驻云电脑 + 模型按需调度；关机任务可继续跑。
- 同账号所有 Bot **共享一台云电脑**（路径/Cookie/登录态不隔离）。
- 适合：固定流程、跨工具、可验收、高危可闸门；不适合：即时问答、本地调试、无闸门群发/删库。
- 岗位六行合同：Own / Sources / Output / Approval / Failure / Never。
- 密码/2FA/付款用 Take over；勿在聊天发明文密码。

### 第 2 章 方案与订阅：先选对档位
- URL：https://bot.fmcat.top/part1/02-plans
- 2026-10-12 起 The X Subscription：Plus($8) **不含** Grok Bot；入门 Premium($30/4x)。
- Super $100/15x，Ultra $200/50x；年付=月付×10。
- Cursor 与 SuperGrok **周额度不叠加**，只取更高一侧。
- 勿在手机 App 内升级以免丢第三方模型用量；网页开通更稳。
- On-demand 须设 Monthly Limit；周额度耗尽且未开按需则自动化停摆。

### 第 3 章 安装登录与第一个 Bot
- URL：https://bot.fmcat.top/part1/03-install
- 入口：cursor.com/dashboard/bot 或 x.ai/bot；旧 Privacy Mode Legacy 须升级。
- 首 Bot 用六行合同，禁止空泛「全能助手」。
- 手机：监控/审批/接管；深度操作（Teach≤10min、Test run、Recover）回桌面。
- 登录循环：清 Cookie / 无痕 / 等订阅同步 30–60 分钟。
- 首任务五要素：目标、只读边界、落盘规格、接管点、验收。

### 第 4 章 交代任务：消息、附件与一次好的交接
- URL：https://bot.fmcat.top/part1/04-handoff
- 好交接=材料说明+对照规则+交付规格+禁止改源文件。
- 先交计划再批量执行；事实与推测分栏。
- 反例：模糊「回一下邮件/看看竞品」→ 必须草稿+审批、证据链。
- 一 Bot 一核心任务，勿在同一会话塞写推文+算账+盯竞品。
- 附件与路径优先于聊天里贴大段原文。

### 第 5 章 共享云电脑：文件、浏览器与接管
- URL：https://bot.fmcat.top/part1/05-computer
- 共享 /workspace 与浏览器态；跨 Bot 必须文件交接。
- Update 电脑：保留 /workspace 与登录态，**清空 apt/cron 等系统层**。
- Reset 更狠，作最后手段；Recover 保现场重建。
- 「虚拟机服务管家」：REGISTRY + restore 脚本 + 私有 Git，密钥永不入库。
- 本地执行须单独授权 Settings→Execution on Local Computer。

### 第 6 章 记忆：让 Bot 越用越懂你
- URL：https://bot.fmcat.top/part1/06-memory
- 记忆分层：LIVE SOURCE / TEAM SKILL / TEAM MEMORY / PRIVATE NOTE / TASK STATE。
- 晋升流程：观察→分类→核实→晋升→重核；重要决策禁止只靠记忆。
- Base Instructions 全账号通用人闸；Role/Current Focus 写进 Description。
- Duplicate 会丢对话与 learned memory，须 10 行内交接卡。
- 章程与定义备份到 /workspace/bots-backup/。

### 第 7 章 连接应用：插件、邮箱与 Secrets
- URL：https://bot.fmcat.top/part1/07-apps
- 连接器/插件/MCP/Secrets：密钥走加密卡片，禁止聊天明文。
- 专属 Bot 邮箱无传统收件箱 UI；外发默认审批卡。
- Vault（较新版本）可存登录/支付信息供自动填，仍受人闸约束。
- 私有技能开关在 Connected Apps。
- 连接失败先查授权范围与团队策略，勿盲重装。

### 第 8 章 技能与例程：把一次成功变成每天自动跑
- URL：https://bot.fmcat.top/part1/08-skills-routines
- 别直接设定时；先沉淀 Skill，再组装 Routine。
- 每 Bot≤50 例程；最短间隔 5 分钟；删例程不可逆。
- 默认工作日跑，要周末须写明；时区建议手动 Asia/Shanghai。
- Webhook：Bearer key；HTTP 200≠业务成功；密钥勿贴聊天。
- Slack 触发严禁「全频道任意消息」；Test=真执行真扣费。
- 两段式：cron 轻量比对 → 有变化 Webhook 唤醒模型。

### 第 9 章 群聊与团队 Bot：从一个 Bot 到一组 Bot
- URL：https://bot.fmcat.top/part1/09-group-team
- 群聊会广播唤醒所有 Bot → 额度杀手。
- 正确结构：一个主导 + Subagents/A2A 单向派活 + 文件落盘。
- 团队 Bot 可有固定 Description；个人靠首条消息记住规则。
- 闲置 Bot 确认无例程后删除，防误唤醒。
- 跨 Bot 信任链默认不可信，高危要二次确认。

### 第 10 章 额度与成本：让一周用量撑满一周
- URL：https://bot.fmcat.top/part1/10-usage
- 消耗≈唤醒次数×每次重读上下文长度；长会话是黑洞。
- 陷阱：多 Bot 群聊、对话喂图视频、15 分钟轮询、无保护重试、盲目 On-demand。
- 省额：关/限按需；单任务单会话；长文落盘；代码分流 CLI/Cloud Agent。
- 例程无变化必须静默退出；工作日 9–17 每小时 vs 全天每 15 分钟差一个数量级。
- 耗尽后前端锁对话，Linux 仍可接管手动 git/脚本。

### 第 11 章 权限、安全与人闸
- URL：https://bot.fmcat.top/part1/11-safety
- Auto-review：send/post/buy/transfer/delete/permissions → Ask first。
- 审批卡约 10 分钟超时 Expired；无人值守任务勿卡审批。
- Never 清单写进章程；高危拆「起草 Bot / 发布人闸」。
- 共享云电脑无安全隔离=勿把互不信任业务硬塞同机。
- 误贴密钥：立刻作废轮换，勿仅删聊天记录。

### 第 12 章 案例：自媒体与内容团队
- URL：https://bot.fmcat.top/part2/12-content
- 内容流水线拆岗：选题/起草/校对/排期/复盘，一岗一 Bot。
- 只起草不代发；发布保留人工闸门。
- 上游 Markdown 落盘供下游读，禁止群里互灌长文。
- 可抄：岗位清单、目录结构、审批节点表。
- 勿做：自动点赞互动、无审稿直接群发。

### 第 13 章 案例：在 X 上做内容与运营
- URL：https://bot.fmcat.top/part2/13-x-ops
- X 运营：检索/起草/排期；响应边界「只起草不代发」。
- X 搜索有速率限制但不扣周额度；对话只回 3–5 要点。
- 发帖走官方连接器/审批卡，禁止脚本硬发绕过人闸。
- 可抄：晨报/竞品监听 Skill 结构。
- 勿做：自动刷互动、无审批发帖。

### 第 14 章 案例：工程与研发团队
- URL：https://bot.fmcat.top/part2/14-engineering
- 研发：Issue 复现、日志提取、PR 摘要；合并/生产变更必须人闸。
- 长代码分流 Cursor Cloud Agent / Codex / Claude Code，主 Bot 做调度验收。
- 夜间巡检用静默+熔断，连续失败报警。
- 可抄：缺陷复现报告模板、/workspace 状态机文件。
- 勿做：无人值守合并主分支、无备份乱 Reset 云电脑。

### 第 15 章 案例：电商与生活实操
- URL：https://bot.fmcat.top/part2/15-ecommerce
- 电商：库存/订单异常晨报、客服草稿、竞品价监控。
- 改价、发券、批量邮件=高危，必须人工兑或审批。
- 与帝国会员店匹配：专享 C 走社群卖点+人工兑，不改价上线。
- 可抄：异常阈值+落盘报表+静默无异常。
- 勿做：Bot 直接改商城价格/自动群发促销。

### 第 16 章 案例：知识自动入库与微信打通
- URL：https://bot.fmcat.top/part2/16-knowledge
- 知识入库：iOS 快捷指令 → Webhook → /workspace/knowledge。
- 微信 ClawBot 官方插件+iLink，宣称合规无封号（白名单单聊）。
- 合并转发前须点开加载附件，否则 ZIP 缺媒体。
- filebin 中转 ID≥8 位随机；分享快捷指令前清空密钥。
- 可抄：入库回执（要点+路径）；勿做：全群监听耗额度。

### 第 17 章 案例：GTM、销售与幕僚长
- URL：https://bot.fmcat.top/part2/17-gtm
- GTM/幕僚长：统一调度，先一个 Chief 再拆销售岗。
- 外联邮件只进草稿箱；权限按可逆性分层。
- 可抄：客户拓展流水线与证据链要求。
- 勿做：草稿群发核心客户、无阈值乱标商机。

### 第 18 章 案例：一人公司与 AI 团队
- URL：https://bot.fmcat.top/part2/18-solo
- 一人公司：少量专职 Bot + 总管调度，避免角色膨胀。
- 日常运营例程低频+静默；批量规则计算放终端脚本。
- 可抄：最小编制表与周审计 15 分钟流程。
- 勿做：4+ Bot 互聊、主会话归档十年邮件。

### 第 19 章 团队编排：章程、岗位与放权
- URL：https://bot.fmcat.top/part3/19-orchestration
- 章程>岗位>放权；一人一岗、记忆边界、审批范围写死。
- 内部草拟与外部发布拆开；交接走文件不走群广播。
- 中心辐射拓扑；禁止 Bot 横向串联。
- 可抄：编制表、目录约定、status.json 状态机。
- 放权阶梯：只读→起草→受限执行→（极少）自动外发。

### 第 20 章 可靠的自动化：定时、Webhook 与事件触发
- URL：https://bot.fmcat.top/part3/20-automation
- 可靠自动化=定时+Webhook+事件；优先事件驱动。
- 验收：时区、空数据熔断、审批拦截、落盘检查四步。
- 计算机更新后重装 cron/全局工具。
- 密钥走 Secrets 卡片；例程 Save 后网关才生效。
- 与第8章互补：本章偏「可靠性工程」。

### 第 21 章 备份与恢复：电脑重置也不慌
- URL：https://bot.fmcat.top/part3/21-backup
- 备份对象：章程、技能说明、REGISTRY、restore 脚本、自写源码。
- 密钥永不进 Git；OAuth/扫码步骤标「需真人」。
- 更新后按 restore-all 验收健康检查清单。
- Reset 慎用；优先 Recover。
- 换账号靠私有仓库带走设定。

### 第 22 章 接入飞书与微信
- URL：https://bot.fmcat.top/part3/22-feishu-wechat
- 三条通道皆无公网 IP：飞书长连接 / 微信 ClawBot / 快捷指令 Webhook。
- 飞书：群内仅 @自己 或 @所有人；高危飞书卡片同意/驳回。
- 微信 ClawBot：纯文本、白名单单聊、须首条拿 context_token；错码 -14 重扫。
- 微信版本 iOS≥8.0.70 / Android≥8.0.69；二维码约 5 分钟有效。
- 群聊无过滤会 1–2 天耗尽周额度。
- 教程无 QQ 个人聊天、无「代管微信群群发」。

### 第 23 章 团队版与企业落地
- URL：https://bot.fmcat.top/part4/23-enterprise
- 团队席位共享配额；成员免单独批席（以官方/章节描述为准）。
- 企业落地重权限基线与审计，而非多建 Bot。
- SSO/Sign in with Grok 企业席位路径。
- 可抄：团队 Base Instructions 与目录权限约定。

### 第 24 章 按岗位组建你的 AI 团队
- URL：https://bot.fmcat.top/part4/24-roles
- 按岗位组建：调研/写作/工程/客服/幕僚等模板。
- 严禁代发消息与替人类做决策（章节强调）。
- 与帝国五席映射：总管=Chief；代码盯梢=工程巡检；文案=起草岗；会员店长=电商/客服；链上顾问=只读研究。
- 可抄：岗位说明书字段（输入/输出/禁止）。

### 第 25 章 常见问题与排错
- URL：https://bot.fmcat.top/part4/25-faq
- 排错顺序：服务状态→网络/插件→云电脑→额度；勿盲 Reset。
- 绑错 Cursor 账号难自助迁移，需人工客服。
- Couldn't reach / 断连：等重试、彻底退出、Recover。
- 例程不跑：Paused、时区、周末、Webhook Save/密钥。

## 2b. 实战篇与案例库要点

### 第 12 章 案例：自媒体与内容团队
- URL：https://bot.fmcat.top/part2/12-content
- 内容流水线拆岗：选题/起草/校对/排期/复盘，一岗一 Bot。
- 只起草不代发；发布保留人工闸门。
- 上游 Markdown 落盘供下游读，禁止群里互灌长文。
- 可抄：岗位清单、目录结构、审批节点表。
- 勿做：自动点赞互动、无审稿直接群发。

### 第 13 章 案例：在 X 上做内容与运营
- URL：https://bot.fmcat.top/part2/13-x-ops
- X 运营：检索/起草/排期；响应边界「只起草不代发」。
- X 搜索有速率限制但不扣周额度；对话只回 3–5 要点。
- 发帖走官方连接器/审批卡，禁止脚本硬发绕过人闸。
- 可抄：晨报/竞品监听 Skill 结构。
- 勿做：自动刷互动、无审批发帖。

### 第 14 章 案例：工程与研发团队
- URL：https://bot.fmcat.top/part2/14-engineering
- 研发：Issue 复现、日志提取、PR 摘要；合并/生产变更必须人闸。
- 长代码分流 Cursor Cloud Agent / Codex / Claude Code，主 Bot 做调度验收。
- 夜间巡检用静默+熔断，连续失败报警。
- 可抄：缺陷复现报告模板、/workspace 状态机文件。
- 勿做：无人值守合并主分支、无备份乱 Reset 云电脑。

### 第 15 章 案例：电商与生活实操
- URL：https://bot.fmcat.top/part2/15-ecommerce
- 电商：库存/订单异常晨报、客服草稿、竞品价监控。
- 改价、发券、批量邮件=高危，必须人工兑或审批。
- 与帝国会员店匹配：专享 C 走社群卖点+人工兑，不改价上线。
- 可抄：异常阈值+落盘报表+静默无异常。
- 勿做：Bot 直接改商城价格/自动群发促销。

### 第 16 章 案例：知识自动入库与微信打通
- URL：https://bot.fmcat.top/part2/16-knowledge
- 知识入库：iOS 快捷指令 → Webhook → /workspace/knowledge。
- 微信 ClawBot 官方插件+iLink，宣称合规无封号（白名单单聊）。
- 合并转发前须点开加载附件，否则 ZIP 缺媒体。
- filebin 中转 ID≥8 位随机；分享快捷指令前清空密钥。
- 可抄：入库回执（要点+路径）；勿做：全群监听耗额度。

### 第 17 章 案例：GTM、销售与幕僚长
- URL：https://bot.fmcat.top/part2/17-gtm
- GTM/幕僚长：统一调度，先一个 Chief 再拆销售岗。
- 外联邮件只进草稿箱；权限按可逆性分层。
- 可抄：客户拓展流水线与证据链要求。
- 勿做：草稿群发核心客户、无阈值乱标商机。

### 第 18 章 案例：一人公司与 AI 团队
- URL：https://bot.fmcat.top/part2/18-solo
- 一人公司：少量专职 Bot + 总管调度，避免角色膨胀。
- 日常运营例程低频+静默；批量规则计算放终端脚本。
- 可抄：最小编制表与周审计 15 分钟流程。
- 勿做：4+ Bot 互聊、主会话归档十年邮件。

### 案例库
- URL：https://bot.fmcat.top/cases/
- 小节：X 热帖案例精选
- 小节：中文长文精选
- 小节：英文长文精选（上）
- 小节：英文长文精选（下）
- 小节：铁柱的实战长文与推文

### 中文长文精选
- URL：https://bot.fmcat.top/cases/cn
- 小节：入门上手与基础机制
- 小节：自媒体运营与个人 IP
- 小节：工程研发与代码协同
- 小节：电商经营与日常实操
- 小节：团队编排与组织协同

### 英文长文精选（上）
- URL：https://bot.fmcat.top/cases/en1
- 小节：机制理解与实操起步
- 小节：中枢调度与团队规章
- 小节：市场拓展与社媒运营
- 小节：一人公司与工程交付

### 英文长文精选（下）
- URL：https://bot.fmcat.top/cases/en2
- 小节：自动化研发与工程运维
- 小节：团队架构与岗位拆解
- 小节：一人公司与实战指令
- 小节：记忆工程与成本控制

### 铁柱的实战长文与推文
- URL：https://bot.fmcat.top/cases/tiezhu
- 小节：订阅方案与算力额度精打细算
- 小节：自动化入库与外部协同网络
- 小节：虚拟机防灾与记忆资产备份
- 小节：架构演进、业务实战与生态选型

### X 热帖案例精选
- URL：https://bot.fmcat.top/cases/x-hot

## 2c. 进阶/团队/工具/生态

### index.md
- URL：https://bot.fmcat.top/

### 第 19 章 团队编排：章程、岗位与放权
- URL：https://bot.fmcat.top/part3/19-orchestration
- 章程>岗位>放权；一人一岗、记忆边界、审批范围写死。
- 内部草拟与外部发布拆开；交接走文件不走群广播。
- 中心辐射拓扑；禁止 Bot 横向串联。
- 可抄：编制表、目录约定、status.json 状态机。
- 放权阶梯：只读→起草→受限执行→（极少）自动外发。

### 第 20 章 可靠的自动化：定时、Webhook 与事件触发
- URL：https://bot.fmcat.top/part3/20-automation
- 可靠自动化=定时+Webhook+事件；优先事件驱动。
- 验收：时区、空数据熔断、审批拦截、落盘检查四步。
- 计算机更新后重装 cron/全局工具。
- 密钥走 Secrets 卡片；例程 Save 后网关才生效。
- 与第8章互补：本章偏「可靠性工程」。

### 第 21 章 备份与恢复：电脑重置也不慌
- URL：https://bot.fmcat.top/part3/21-backup
- 备份对象：章程、技能说明、REGISTRY、restore 脚本、自写源码。
- 密钥永不进 Git；OAuth/扫码步骤标「需真人」。
- 更新后按 restore-all 验收健康检查清单。
- Reset 慎用；优先 Recover。
- 换账号靠私有仓库带走设定。

### 第 22 章 接入飞书与微信
- URL：https://bot.fmcat.top/part3/22-feishu-wechat
- 三条通道皆无公网 IP：飞书长连接 / 微信 ClawBot / 快捷指令 Webhook。
- 飞书：群内仅 @自己 或 @所有人；高危飞书卡片同意/驳回。
- 微信 ClawBot：纯文本、白名单单聊、须首条拿 context_token；错码 -14 重扫。
- 微信版本 iOS≥8.0.70 / Android≥8.0.69；二维码约 5 分钟有效。
- 群聊无过滤会 1–2 天耗尽周额度。
- 教程无 QQ 个人聊天、无「代管微信群群发」。

### 第 23 章 团队版与企业落地
- URL：https://bot.fmcat.top/part4/23-enterprise
- 团队席位共享配额；成员免单独批席（以官方/章节描述为准）。
- 企业落地重权限基线与审计，而非多建 Bot。
- SSO/Sign in with Grok 企业席位路径。
- 可抄：团队 Base Instructions 与目录权限约定。

### 第 24 章 按岗位组建你的 AI 团队
- URL：https://bot.fmcat.top/part4/24-roles
- 按岗位组建：调研/写作/工程/客服/幕僚等模板。
- 严禁代发消息与替人类做决策（章节强调）。
- 与帝国五席映射：总管=Chief；代码盯梢=工程巡检；文案=起草岗；会员店长=电商/客服；链上顾问=只读研究。
- 可抄：岗位说明书字段（输入/输出/禁止）。

### 第 25 章 常见问题与排错
- URL：https://bot.fmcat.top/part4/25-faq
- 排错顺序：服务状态→网络/插件→云电脑→额度；勿盲 Reset。
- 绑错 Cursor 账号难自助迁移，需人工客服。
- Couldn't reach / 断连：等重试、彻底退出、Recover。
- 例程不跑：Paused、时区、周末、Webhook Save/密钥。

### tools__index.md
- URL：https://bot.fmcat.top/tools/
- 18 个云电脑工具，各附可复制安装提示词（Codex/Claude Code/gh/飞书/Playwright/X API 等）。
- agently-cli 对接腾讯 QQ/Agent **邮箱**，不是 QQ 即时聊天。

### bots__index.md
- URL：https://bot.fmcat.top/bots/
- Bot 直聘：现成模板（飞书应用管家、额度省省助手、微信文章捕手、记账管家、记忆管家等），导入即用。
- 与帝国相关：优先评估「飞书应用管家」「额度省省助手」「记忆管家」。

### ecosystem__index.md
- URL：https://bot.fmcat.top/ecosystem/

### ecosystem__grok-bot-clipper.md
- URL：https://bot.fmcat.top/ecosystem/grok-bot-clipper
- 第三方浏览器插件：选区/截图/社交分享/材料篮打包发给 Bot。
- 非官方；连接自有账户，无需本地连接器。

### changelog__index.md
- URL：https://bot.fmcat.top/changelog/
- 官方更新中文摘要；截至抓取日含 Vault、邮件转发、自动化频次提升等。
- 以官方原文为准；社区有解读标签。

### 关于铁柱AGI
- URL：https://bot.fmcat.top/about
- 小节：我在做什么
- 小节：开源项目
- 小节：Bot 模板
- 小节：怎么找到我

### 付费答疑群
- URL：https://bot.fmcat.top/group
- 小节：群里聊什么
- 小节：适合谁
- 小节：怎么加入

## 3. 与帝国五席最相关的可落地方案 Top 10（按优先级）

| 优先级 | 方案 | 主要席位 | 教程依据 | 落地要点 |
| ---: | --- | --- | --- | --- |
| 1 | 省额度改造：例程静默 + cron/Webhook 两段式 | 总管 / 代码盯梢 | 第8/10/20章 | 先审计现有 Routines；监控类改脚本哨兵；关或严限 On-demand |
| 2 | 五席章程六行合同 + Base 人闸 Ask first | 总管 | 第1/3/11/19/24章 | 统一 Never：不代发、不改价、不支付；Description≤300字 |
| 3 | `/workspace` 交接规范与目录 | 全体 | 第5/9/19章 | 禁用多 Bot 群聊互唤；产物路径约定；status 文件 |
| 4 | 微信 ClawBot 随身下旨（可选） | 总管 | 第22/16章 | 白名单单聊纯文本；密钥加密框；不代发微信群 |
| 5 | 社群/X 文案：只起草不代发流水线 | 文案助手 | 第12/13章 | 继续现网「草稿交陛下手发」；可沉淀 Skill |
| 6 | 会员店经营晨报与异常静默 | 会员店长 | 第15/10章 | 订单/潜客指标落盘；无异常一行不刷；专享C人工兑 |
| 7 | 知识入库：快捷指令→Webhook | 文案/总管 | 第8/16/22章 | 微信合并转发归档；回执含路径 |
| 8 | 虚拟机服务管家 + 备份仓库 | 代码盯梢 | 第5/21章 | REGISTRY/restore；打包一/看门狗类部署可登记 |
| 9 | 飞书多 Bot 派工（若团队要用飞书） | 总管 | 第22章 + bots模板 | @分流；卡片二次授权；非必须可缓 |
| 10 | 编码分流：Codex/Claude Code/Cloud Agent | 代码盯梢 | 工具箱+第14章 | 主 Bot 调度验收；长改码不进主会话 |

## 4. 可直接抄 vs 勿做

### 微信 ClawBot
- **可抄**：第22章完整接入提示词；白名单单聊；纯文本回复；首条拿 context_token；错误 -14 重扫。
- **勿做**：当微信群机器人群发；回 Markdown；开放非绑定微信号；密钥明文聊天；无过滤监听。

### 飞书
- **可抄**：飞书应用管家模板批量建应用；群内仅 @响应；高危卡片同意/驳回；长连接出站。
- **勿做**：漏「获取群内@机器人消息」权限；断线后手动二次补发；跨 Bot 无白名单互调。

### Webhook 例程
- **可抄**：事件驱动入库/门铃；Bearer 鉴权；200 后看聊天/落盘验收；Save 后再生效。
- **勿做**：5 分钟网页空轮询；聊天贴 key；Paused 未查就怪网关；Test 当干跑。

### 多 Bot 协作
- **可抄**：中心辐射、文件交接、一人一岗、Subagents 跑完退出。
- **勿做**：多 Bot 拉群互聊；横向串联；主会话塞高负载归档。

### 额度省用法
- **可抄**：第10章提示词库（瘦身/静默/重试≤2/Duplicate交接/OpenRouter分流）。
- **勿做**：全天每15分钟例程；对话喂长视频；盲目开按需无月限；群聊广播。

### 电商 / 自媒体案例
- **可抄**：异常晨报、客服草稿、选题-起草-校对拆岗、证据链与静默规则。
- **勿做**：自动改价发券；自动发帖点赞；无审批群发客户；编造缺失数据。

## 5. QQ / 个人微信群代发 — 结论

| 诉求 | 教程是否覆盖 | 能否做 | 说明 |
| --- | --- | --- | --- |
| 个人 QQ 聊天看消息/回人 | **否**（仅 agently-cli QQ/Agent **邮箱**） | **不能**按教程接入即时聊天 | 与官方 WebQQ 已关一致；继续手机 QQ + 草稿手发 |
| 微信 ClawBot 单聊调度 Bot | **是**（第22/16章） | **能**（官方插件+iLink） | 纯文本、白名单、不代发群消息 |
| Bot 代发微信群/软广 | **否**（明确只起草/人闸） | **不应做** | 封号/合规/额度风险；帝国现状「只草稿不代发」正确 |
| 微信群内容入库 | **是**（快捷指令+Webhook） | **能** | 合并转发ZIP→filebin→例程归档 |

## 6. 原始正文与提示词位置

- 分章纯文本：`/workspace/fmcat-grok-bot-guide/text/`
- 可复制提示词汇编：`/workspace/fmcat-grok-bot-guide/PROMPTS.md`
- 执行清单：`/workspace/fmcat-grok-bot-guide/ACTION-CHECKLIST.md`
- 原始 HTML/md.js：`/workspace/fmcat-grok-bot-guide/raw/`

