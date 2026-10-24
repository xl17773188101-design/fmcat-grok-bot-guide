# 帝国落地执行清单（仅研究结论，未代执行）

> 依据 https://bot.fmcat.top/ 学习笔记。每项需陛下点头后再做；默认不创建例程、不装插件、不代发。

## P0 · 立刻可做（低风险）

- [ ] 总管核对五席 Description：补齐 Own/Sources/Output/Approval/Failure/Never；统一「只草稿不代发、不改价、不支付」。
- [ ] Settings → Auto-review：send/post/buy/transfer/delete/permissions = Ask first。
- [ ] Settings → Usage & Billing：确认套餐与重置倒计时；On-demand 关闭或 Monthly Limit 设低额。
- [ ] Settings → Bot → Timezone：手动 Asia/Shanghai。
- [ ] 审计各席 Routines：暂停「天天无变化还播报」的例程；加静默规则。
- [ ] 约定 `/workspace` 目录：如 `shopbot_repurchase/`、`crocodile-*/`、`handoffs/`，禁止群聊贴长文。

## P1 · 建议本周（需拍板）

- [ ] **省额度两段式**：代码盯梢对监控类任务写 cron 哨兵 + Webhook（参考第8/10章）；先 Test 再启用。
- [ ] **文案 Skill 化**：把三类客暖场/分流稿沉淀为 Skill，例程可选「工作日晚间提醒陛下发群」（只提醒不代发）。
- [ ] **会员店长晨报**：潜客/订单异常落盘静默；有单再喊人。
- [ ] **虚拟机服务管家**：为看门狗/打包一部署建 REGISTRY+restore（第5/21章）。
- [ ] 是否开通 **微信 ClawBot**（第22章提示词在 PROMPTS.md A）：陛下确认后再装插件扫码。

## P2 · 可选增强

- [ ] 飞书应用管家（多 Bot @派工）— 仅当团队主要办公在飞书。
- [ ] iOS 快捷指令知识入库（第16/22章）。
- [ ] Grok Bot Clipper 浏览器插件采集。
- [ ] 工具箱：Codex/Claude Code/gh 按需安装（工具页提示词）。

## 明确不做

- [ ] ~~个人 QQ 网页/协议登录代聊~~（教程无方案；官方网页不可用）。
- [ ] ~~Bot 代发微信群/QQ群软广~~。
- [ ] ~~多 Bot 拉群互聊协同~~。
- [ ] ~~高频网页轮询例程~~。
- [ ] ~~无审批自动改价/发帖/转账~~。

## 拍板卡片（留给总管问陛下）

1. 是否本周做「例程静默+cron 哨兵」省额度改造？
2. 是否接入微信 ClawBot 随身下旨？
3. 是否建虚拟机服务管家备份仓库（私有 Git 地址）？
4. U商对接微信号写死进文案？（与教程无关，业务债）

