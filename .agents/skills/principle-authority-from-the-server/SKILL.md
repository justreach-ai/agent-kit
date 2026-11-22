---
name: principle-authority-from-the-server
description: "Apply when deciding who may do what. Authority comes from the server's own data and one permission kernel, never from the client, the payload or a token's claims."
---

# Authority from the server

1. Derive the actor server-side from the request envelope; tokens only establish who is calling.
2. Decide access from the service's own data and explicit, named grants.
3. Never trust actor fields in payloads, client metadata, role names, or group membership standing in for
   access.
4. No auth bypass, even in tests.

Why: anything the client can say, an attacker or a prompt-injected agent can say too.
