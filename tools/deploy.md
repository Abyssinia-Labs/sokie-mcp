---
operation: POST /servers/{serverId}/deploys
title: Deploy uploaded files
---

A deploy's second step: deploys the files at `sourceKey` and answers with the deploy, queued. Follow it with `getDeploy`. It's held for an owner or admin whenever the same person's deploy from the CLI would be. On a server linked to a repository, the next push to its default branch replaces it. Needs `deploys:write`.
