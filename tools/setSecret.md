---
operation: POST /servers/{serverId}/secrets/{name}
title: Set a secret
---

Sets one of the server's secrets, and hands it to what's running. The value is never returned or logged. `live` is `updated` when production has it now, `not_deployed` when nothing is deployed yet, and `failed` when production couldn't take it now: its next deploy will. On a public server, or one open to its API's users, a key is refused: a person sets it in the app or with `sokie`. Needs `secrets:write`.
