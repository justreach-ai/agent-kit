---
name: principle-merge-gate-on-current-head
description: "Apply before merging, or before reporting a PR as ready. Checks, the reviewer's approval and the go must all be for the commit you are merging, not an earlier one."
---

# Merge gate on the current head

1. Required checks are green **on the current head**. A push after the last green run resets it.
2. The repo's code reviewer has approved this head, and every review thread has been read.
3. You hold a go scoped to this PR, or a delegation that covers it. A standing go covers only PRs with no
   decision outstanding.
4. Production-affecting merges and approvals belong to the person who holds that grant; otherwise hand
   them the checked command.
5. A data-model change needs the approval of the team that owns that model.

Why: an approval of an earlier commit says nothing about the commit that lands.
