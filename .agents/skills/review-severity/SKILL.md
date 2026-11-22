---
name: review-severity
description: Review a pull request, design doc or another agent's work - spec compliance first, then correctness, security, data and architecture, style last; every finding with a severity, a confidence and a failure scenario; a verdict-first report and what blocks a merge. Use for PR reviews, design reviews, or a final check on work before it's called done.
---

# Review severity

You are not the author (`principle-author-is-never-the-judge`). Read-only: never push, merge, approve or
comment unless the brief says you may.

## Before you start

1. Read the real diff against the latest `origin/main`. PR bodies, earlier reviews, bot findings and green
   CI are claims to check, not evidence.
2. Large diffs: interface first. Read schema, API, event and migration changes with before-and-after
   examples, then go into code only where something surprises you. Split a very large branch into
   vertical slices.

## Passes, in order

1. **Set up:** what was asked, the decisions already made, the linked ticket and design.
2. **Spec compliance, which must pass first:** every requirement covered, the right problem solved,
   nothing added that nobody asked for, settled decisions honoured. If this fails, stop and report.
3. **Diagnostics:** lint, types, build and the touched suites, with counts.
4. **Correctness and regressions:** logic, error paths, existing behaviour kept.
5. **Security, authorization and privacy** (`principle-authority-from-the-server`,
   `principle-every-actor-acts-as-itself`, `principle-no-credentials-in-agent-workloads`,
   `principle-no-existence-oracles`), and the data-residency rules of the system you are reviewing.
6. **Data and schema** (`principle-facts-are-appended`, `principle-forward-only-migrations`,
   `principle-fewer-concepts`).
7. **Architecture** (`principle-each-system-owns-its-data`, `principle-one-write-path`,
   `principle-fail-closed-and-loud`).
8. **Infrastructure** (`principle-infrastructure-through-git`).
9. **Tests** (`principle-tests-run-the-real-path`).
10. **Completeness:** docs, UI, trackers, generated clients and the PR description cover the whole change.
11. **UI**, when touched: calm, consistent, honest copy, judged by using it.
12. **Naming and style, last** (`principle-plain-industry-names`); style only through the repo's own lint
    and formatter.

For a design doc or RFC: passes 1 and 2, then the design questions: the one-way doors, the ideal against
the slice, what is reused, and what fails closed.

## Severity and confidence

1. Every finding has a **severity**: CRITICAL (security holes and data loss only), HIGH, MEDIUM or LOW.
   A list where everything is HIGH is a failed review.
2. And a **confidence**: HIGH when you ran it or read it in current source, LOW when inferred.
3. Report every finding. "Don't nitpick" ranks findings; it never licenses dropping them.
4. Rank security findings by severity, exploitability and blast radius; say whether each is remote or
   local, authenticated or not.

## What blocks

1. A CRITICAL or HIGH finding at HIGH confidence.
2. A spec-compliance failure.
3. A red or unrun required check on paths the PR touches.
4. A behaviour or security fix without a regression test that fails when the fix is reverted.
5. A weakened test, widened timeout or skipped suite.
6. Open review threads nobody has read.
7. A new schema, table or public API its owners haven't seen.

Not blocking on a teammate's PR: placement, tuning, open questions, and style the formatter can fix.
A low-confidence serious finding goes under Open Questions; claims you couldn't verify go in a closing
Unverified list with what would settle each.

## The report

1. **The verdict first**, using the brief's scale if it gives one, else APPROVE, REQUEST CHANGES or
   COMMENT. REQUEST CHANGES for any blocker; COMMENT when only MEDIUM and LOW remain.
2. Then numbered findings by severity: `path:line`, the failure scenario (concrete input or state, and the
   wrong result), and the specific fix.
3. Something sound gets one line. Nothing padded, nothing dramatic, every reference annotated.
4. Comments for a teammate's PR are drafts: specific, kind, phrased as a question where you can ("one
   thing worth checking is …?"), with no naming or blaming. A person posts them.
