---
name: principle-infrastructure-through-git
description: "Apply when changing anything live: cloud, cluster, DNS, secrets, CI. Every change lands through a reviewed change in git and runs through CI, and what is applied is exactly what was reviewed."
---

# Infrastructure through git

1. Everything live is declared in a repository (infrastructure as code, GitOps). The order is plan,
   staging, review, then production.
2. Changes apply on merge only when a fresh plan matches the reviewed one, through CI; never from a task on
   an agent's own judgement.
3. Secrets never in state, plans or logs; no resource configured unlike its siblings.
4. Prefer portable, permissively licensed tools that run the same on any cloud or on your own hardware.
5. Names follow one naming scheme, agreed before a resource is created.

Why: a hand-applied change is one nobody reviewed and the next apply undoes.
