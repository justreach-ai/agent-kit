---
name: principle-evidence-before-claims
description: "Apply before you say done, unused, safe to delete, fixed, can't or doesn't exist. Each of those words needs the evidence named here, gathered on fresh ground, or the claim goes under Flagged with the check that would settle it."
---

# Evidence before claims

Nothing you ship, claim or report says more than is true, including who did the work.

1. **Fresh ground.** Re-check the latest `origin/main`, live state and today's date before claiming.
   Analysis built on a stale checkout is wrong by default.
2. **Done:** suites run after the last change, with counts; images built and run; the rollout checked
   live; every acceptance criterion checked; the work pushed and seen on origin.
3. **Unused:** the search spelled out (which repos, including mobile apps already shipped), live usage
   data, the PR that introduced it, and the zero confirmed a second way.
4. **Safe to delete:** where it came from, the unused evidence, whether live DNS, user data or kept logs
   are touched, the option that keeps history, and the list shown before deleting.
5. **Fixed:** a test that fails without the fix, the exact red job now green, the root cause addressed.
6. Label each claim **run**, **read** or **inferred**, with a `path:line`, an annotated PR or a dated
   command.
7. A claim resting on an absence, an impossibility or an absolute goes under Flagged with the check that
   would settle it, when a decision leans on it.

Why: "it compiles", a green summary or a plausible story has hidden serious faults before, and an absence
usually means the search was too narrow.
