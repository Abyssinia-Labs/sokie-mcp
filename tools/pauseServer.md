---
operation: POST /servers/{serverId}/pause
title: Pause a server
---

Stops the server answering: every call to it is refused until `resumeServer`. What's deployed, its secrets and its settings stay as they are. `active` on getServer says whether it's running. Needs `servers:write`.
