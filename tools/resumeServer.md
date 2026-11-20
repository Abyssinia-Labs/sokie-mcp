---
operation: POST /servers/{serverId}/unpause
title: Resume a server
---

Starts a paused server answering again. A server past its plan's server limit stays paused and answers `PLAN_LIMIT_SERVERS`. After a restore, following the default branch again is `resumeDeploys`. Needs `servers:write`.
