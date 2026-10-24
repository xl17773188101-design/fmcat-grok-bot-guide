# X API 发帖（OAuth 1.0a PIN）

Source: https://bot.fmcat.top/tools/x-api

> 介绍在 Grok Bot 云电脑上配置 X API 发帖功能的方法。将页面提示词发送给助理完成准备，由用户自行填入开发凭证并确认授权链接，即可在终端协同发布推文与管理动态。

基于 OAuth 1.0a PIN 授权的 X 官方接口调用方案，适合让 Bot 在 云电脑 上安全执行发帖、传图与删帖任务。

## 发给 Bot 的提示词

复制下方整段内容发送给你的 Grok Bot，它会在云电脑上自动安装并验证，遇到登录或配置密钥时会暂停等待你操作。

```
帮我在你的云电脑上配置 X API 发帖（https://docs.x.com/resources/fundamentals/authentication/oauth-1-0a/pin-based-oauth），以后发帖、传图和管理推文用它。需要填密钥时请提醒我自己填，需要登录授权时把链接发给我。
```

## 需要你自己做的事

- 在 X 开发者平台创建应用并开通读写权限。
- 打开授权链接并在收到页面 PIN 码后发送给 Bot。

## 来源

- X 官方文档：PIN-based OAuth

> 本页为社区非官方整理，与该工具厂商、xAI 均无隶属关系，命令以官方文档为准。

← 返回目录
