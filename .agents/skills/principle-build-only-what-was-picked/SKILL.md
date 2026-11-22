---
name: principle-build-only-what-was-picked
description: "Apply when a decision is open, or when you notice work nobody asked for. Build the option that was chosen and the scope that was asked, nothing beside it."
---

# Build only what was picked

1. Scope is what was asked: no changes to repos, CI or files nobody mentioned. Real side problems go in
   one consolidated ticket or a TODO.
2. While a decision is open, its options stay unbuilt. A standing go to keep working covers only work with
   no decision outstanding.
3. When asked to plan, plan; don't implement. Once the plan is approved, build it properly, not as a mock.

Why: building ahead of a decision turns a choice into a sunk cost, and unrequested changes cost the
reviewer time to find and judge.
