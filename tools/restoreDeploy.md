---
operation: POST /servers/{serverId}/deploys/{number}/restore
title: Restore a deploy
risk: write
idempotent: false
---

Deploys an earlier deploy's files again. On a server linked to a repository, production stops following the default branch until it's resumed. Needs `deploys:write`.
