---
name: principle-facts-are-appended
description: "Apply when modelling data that changes over time, or an edit or rollback. Store facts in append-only ledgers with current-state projections; an edit is a new version."
---

# Facts are appended

1. Append-only ledgers with HEAD (current-state) projections; edits are new versions.
2. One field per concept, in a real column, edge or constraint. Derived values are computed.
3. Every row has a UUID; slugs are NULL until set and immutable after.
4. Model anything new on the system's existing data model first. A new table outside it needs a written
   case.
5. Rollback is a snapshot restore, never a down-migration.

Why: history you overwrite can't be audited or recovered, and personal and regulated data needs both.
