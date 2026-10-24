---
name: Grok Bot 省额度
description: >-
  Use when trimming Grok Bot Super usage, auditing noisy routines, or writing
  long research that should not flood chat.
---
# Grok Bot 省额度

Apply when usage is high, routines chatter, or research produces long text.

## Rules
1. One task per session when possible; do not wake extra bots for FYI.
2. Long pages, logs, dumps: write under `/workspace/...`, reply with conclusion + absolute path only.
3. Monitoring routines: if nothing material changed, exit silent — never send「一切正常」.
4. Prefer Linux cron / lightweight compare, then Webhook wake only on change (not high-frequency full Bot polls).
5. Keep On-demand off or tightly capped unless the user asks otherwise.
6. Multimodal bulk (many screenshots/videos): process via CLI to text summary first; do not paste raw media into chat when avoidable.
7. Hub-and-spoke: coordinator dispatches; do not start multi-bot group chats for coordination.

## Deliverable style
- Short answer first; paths for evidence.
- Offer a Skill after a flow is proven twice; then a Routine if it must repeat on a schedule.
