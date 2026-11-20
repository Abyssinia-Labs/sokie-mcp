---
operation: POST /servers/{serverId}/secrets/{name}/remove
title: Remove a secret
---

Removes one of the server's secrets, from what's running too. Removing one it doesn't have changes nothing. `live` says what production did, as for `setSecret`. On a public server, or one open to its API's users, a key is refused, as for `setSecret`. Needs `secrets:write`.
