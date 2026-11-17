---
operation: GET /servers/{slug}
title: Get a server
risk: read
---

One server by its slug, with the `serverId` the other routes take. It finds only servers in the workspace this connection reaches; `listServers` lists those. A server in another workspace answers not found: the person connects again and chooses that workspace. Needs `servers:read`.
