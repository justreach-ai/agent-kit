---
name: principle-no-credentials-in-agent-workloads
description: "Apply when an agent, sandbox or client app needs to call something authenticated. Real credentials never enter it; a trusted broker or gateway holds them."
---

# No credentials in agent workloads

1. Sandboxes get phantom tokens and CLI shims; keys stay in the gateway or a trusted broker.
2. Prefer keyless workload identity and default-deny egress.
3. Never print or store a secret, and never log in or handle a secret value for a person: wait at the
   wall and ask.
4. Output scrubbing or environment-variable scoping is not a security boundary.

Why: a prompt-injected agent can do anything its credentials allow.
