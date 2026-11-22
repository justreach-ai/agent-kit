---
name: principle-roll-forward
description: "Apply when a release is ready or something breaks after one. Ship with a few tests, a decent review and backups before migrations; fix forward, and roll back only after a catastrophic mistake."
---

# Roll forward

1. A release needs a few tests, a decent review and a backup before its migrations.
2. Fix forward. Roll back (by snapshot) only after a catastrophic mistake.
3. Brief, non-catastrophic downtime is acceptable in favour of shipping; data loss, irreversible changes
   and long outages keep their gates. A declared freeze overrides this, and it never changes who approves
   a production action.
4. Every production environment of a tier gets the same release; a difference between them is drift to
   explain or fix.

Why: holding releases for perfect windows slows delivery more than the blips cost.
