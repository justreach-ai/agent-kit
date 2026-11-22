---
name: principle-finished-work-merges
description: "Apply when wrapping up, handing over or taking over. Finished work left in a worktree or on a branch is a failure: find it and push it as a ready branch, or list it under Flagged."
---

# Finished work merges

1. Before you finish, check every worktree and branch you touched for work that never merged.
2. Push it as a ready branch or PR, or list it under Flagged with what it is and what blocks it.
3. Merging still follows `principle-merge-gate-on-current-head` and the `risk-ladder`; this widens
   neither.

Why: unmerged work is invisible to the next person, who rebuilds it or builds on the old state.
