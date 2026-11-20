---
operation: POST /servers/{serverId}/resume
title: Follow the default branch again
---

After a restore on a server linked to a repository: production follows the default branch again and its newest commit deploys. `pin` on getServer says whether production is held on a restore. A server that isn't answers `NOT_PINNED`. Needs `deploys:write`.
