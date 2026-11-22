---
name: principle-fail-closed-and-loud
description: "Apply when handling ambiguity, a missing dependency or a delete. Refuse rather than guess, never fail silently, and refuse to remove something others still depend on."
---

# Fail closed and loud

1. Ambiguous state is refused. A missing secret disables the feature. Unknown shows as unknown.
2. Nothing fails silently: no swallowed errors, no clamped values that hide a fault.
3. Archiving or deleting something others depend on fails with an error naming the dependents, so deletes
   go in dependency order. A "delete dependents too" option comes later, with an access check on each.
4. Archive (reversible) sits beside a permissioned real erase.

Why: a silent fallback turns a visible outage into invisible wrong data.
