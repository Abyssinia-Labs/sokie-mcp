---
operation: POST /servers/{serverId}/tools/{name}/description/pull-request
title: Propose a tool description
risk: external_effect
idempotent: false
hints:
  openWorld: true
---

On a server linked to a repository: opens a pull request that changes the tool's description. Production changes when it merges. A server without a repository answers `NO_REPOSITORY`; use `deployToolDescription`. Needs `tools:write`.
