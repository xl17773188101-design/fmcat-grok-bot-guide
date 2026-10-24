---
name: Cron 哨兵监控
description: >-
  Use when turning a noisy polling routine into a cheap cron compare that wakes
  the bot only on real changes.
---
# Cron 哨兵监控

## Goal
Cut usage: shell/cron does the cheap check; Webhook wakes the bot only when the snapshot changed.

## Steps
1. Define the check (HTTP status, file hash, API field, process alive).
2. Write a small script that writes a fingerprint to a state file under `/workspace/...`.
3. Install a user crontab (or systemd timer) at a sane interval (minutes, not every few seconds).
4. On change only: POST the bot routine Webhook with a short payload (what changed + path to evidence).
5. Routine prompt: read payload, act or report; if duplicate/stale, stay silent.
6. Test once manually before enabling; log failures without waking the user every time.

## Don't
- Do not schedule a full Bot conversation every few minutes「just to look」.
- Do not page the user when nothing changed.
