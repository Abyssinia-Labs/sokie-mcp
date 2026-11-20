---
operation: POST /servers
title: Create a server
---

Makes an empty server, open only to its workspace, with the `serverId`, `slug` and address (`url`) it keeps. Deploy to it with `createUpload`, then `deploy`. A key must be one given every server. Needs `servers:write` and `deploys:write`.
