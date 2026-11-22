---
name: principle-compatibility-for-deployed-consumers
description: "Apply when changing an interface, schema or format. Owe compatibility only to consumers that are deployed; make clean breaks for anything that never shipped."
---

# Compatibility for deployed consumers only

1. Never shipped: break it cleanly. No shims, rename migrations, defensive flags or soak periods.
2. Deployed: change additively, migrate dependents first, and avoid enum changes that force a coordinated
   client release.
3. Remove dead code once usage data proves it unused (see `principle-evidence-before-claims`).
4. A feature flag is for a staged rollout with a named gate, not defensive plumbing.

Why: compatibility for things that never shipped is pure cost, but real consumers must never break.
