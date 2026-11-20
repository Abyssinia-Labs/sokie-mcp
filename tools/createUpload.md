---
operation: POST /servers/{serverId}/uploads
title: Get an upload URL
---

A deploy's first step. PUT the server's folder to `url` as one JSON object of each file's path and text, `{"files": {"sokie.json": "…", "openapi.yaml": "…"}}`, exactly `bytes` long. Then send `key` to `deploy` as `sourceKey`. Needs `deploys:write`.
