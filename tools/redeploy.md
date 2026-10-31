---
operation: POST /servers/{serverId}/redeploy
title: Redeploy
risk: write
idempotent: false
---

Builds the live deploy's source again. Production keeps answering until the new deploy is live. Needs `deploys:write`.
