---
name: principle-each-system-owns-its-data
description: "Apply when work crosses two systems or services. Each system owns its data and meets the others at a published contract; a platform shared by several tenants stays tenant-neutral."
---

# Each system owns its data

1. No reaching into another system's database. Integrate through its published contract.
2. A shared platform stays generic: no one tenant's vocabulary, data handling or token checks inside it.
   Each tenant integrates with it like any third party would, through the same public contract.
3. Repo-level `AGENTS.md` or `CLAUDE.md` is more specific and wins where it speaks.

Why: a shared database makes every schema change a coordinated release, and a harness that knows one
tenant can't serve the next.
