---
name: 微信 ClawBot 接入
description: >-
  Use when the user wants to message a Grok Bot from WeChat via the official
  WeChat ClawBot / iLink path (not group spam).
---
# 微信 ClawBot 接入

Official outbound long-poll via iLink (`ilinkai.weixin.qq.com`). Not for mass group messaging. Only start after the user clearly asks to connect WeChat this way.

## Steps
1. Research current iLink `getupdates` / `sendmessage` usage; outbound only; no public inbound port.
2. Create a Webhook-triggered routine (e.g.「微信下旨入口」). Tell the user to copy Webhook URL + key from the routine panel into the encrypted secret form — never paste secrets in chat.
3. On the box, run a small forwarder: WeChat message → POST routine; after handling, reply script sends plain text back to WeChat and mirrors a short note in the main bot chat.
4. User enables WeChat plugin「微信ClawBot」(iOS ≥ 8.0.70 / Android ≥ 8.0.69). Generate QR (~5 min) + backup link; user scans.
5. User must send the first message in the ClawBot chat to obtain `context_token`.
6. Whitelist: only the bound user. Replies: plain text only (WeChat does not render Markdown).
7. Document restart: how to relaunch the forwarder after box reboot; on error `-14`, user re-scans.

## Safety
- Stop at each human step; do not bypass scan or auth.
- Do not use this channel to spam groups or auto-market.
- Full prompt library may live under `/workspace/fmcat-grok-bot-guide/PROMPTS.md` section A if present.
