---
name: principle-fewer-concepts
description: "Apply when adding a table, kind, flag, layer, adapter or special case. Reuse or fix the general primitive instead; a new concept must justify itself in writing."
---

# Fewer concepts

1. Fix the general primitive, never a special case. Each field means one thing.
2. No hybrid or transitional layers, and no compatibility code for things that never shipped.
3. Abstractions earn their place: duplicate until a shared module has several real callers that differ by
   values and change together. No adapter, injection or provider for a single implementation.
4. Build on the platform's own primitives (schedules, workflows, repositories, specs) before a new
   mechanism or store.

Why: every concept is something people and agents must learn, and a wrong interface costs more than
duplication.
