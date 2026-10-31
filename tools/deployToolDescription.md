---
operation: POST /servers/{serverId}/tools/{name}/description/deploy
title: Deploy a tool description
risk: write
idempotent: false
---

On a server with no repository: changes the tool's description and deploys the result, straight to production, with no review. `base` is the server's `liveDeploymentId`; if production has moved on, nothing changes and it answers `STALE_BASE`. A linked server answers `LINKED`; use `proposeToolDescription`. Needs `tools:write`.
