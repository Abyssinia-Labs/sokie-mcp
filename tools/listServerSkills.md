---
operation: GET /servers/{serverId}/skills
title: List skills
risk: read
---

The skills production serves, by name: what each is for, how many tools it names and how many of those ask first, what the checks found, and its reads and downloads over the last 30 days. Set `tool` to see only the skills that name that tool. Read one with `getServerSkill`. Needs `tools:read`.
