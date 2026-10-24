---
name: 多 Bot 中心辐射
description: >-
  Use when coordinating several Grok Bots, assigning roles, or preventing bots
  from chatting each other in a group.
---
# 多 Bot 中心辐射

## Pattern
- One coordinator speaks to the user and assigns work.
- Specialists report to the coordinator (or deliver in their own chat with the user).
- Hand off via files under `/workspace/...`, not by @-mention chains in a group.

## Do
1. Give each bot a clear Own / Sources / Output / Approval / Never in its description.
2. Coordinator only escalates decisions that need the user (post, pay, go-live, delete keys).
3. Include a recommendation whenever offering choices.

## Don't
- Do not create a multi-bot group for bots to talk among themselves (burns usage).
- Do not let specialists change another specialist's area; they report the issue instead.
- Do not auto-send, auto-post, or auto-pay; draft or ask first.
