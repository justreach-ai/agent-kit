---
name: principle-one-write-path
description: "Apply when adding a write, a query that changes state, or an authorization check. Every write and every authorization decision has one intended path, enforced where all paths cross."
---

# One write path

1. Data is written only through its one intended layer (for example a set of database functions or one
   service), and access is decided by one permission model. Handlers and resolvers stay thin.
2. Stray SQL that writes or decides access is an authorization hole, however convenient.
3. No feature-owned authorization and no caches that hold access decisions.

Why: a second path is where checks are forgotten.
