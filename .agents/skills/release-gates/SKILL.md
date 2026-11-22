---
name: release-gates
description: Take a change from merge to production - build once and promote the same artefact, staging first, what each release must have, what a release grant covers, parity across environments, and the script a person runs when the production step is theirs. Use when preparing, running or checking a release.
---

# Release gates

Principles behind each gate: `principle-roll-forward`, `principle-forward-only-migrations`,
`principle-compatibility-for-deployed-consumers`, `principle-delivered-means-on-the-normal-path`. Who may
press the production button is in `risk-ladder`.

## The path

1. **Build once.** Immutable candidates are built from main. Staging updates automatically; production
   gets the same artefact, promoted. Never rebuild for production: a rebuilt artefact is one nobody tested.
2. **Staging is the gate.** Read what the release contains (the PRs and migrations in it). Check staging
   shows no breaking change and no security or privacy risk. Improvements are fixed forward, not held.
3. **Backups before migrations.** Take or confirm a backup before a release's migrations run.
4. **Production** goes through the normal GitOps path, by whoever holds the grant for it.
5. **Every environment of a tier.** Where you run several production environments (regions, cells,
   tenants), each gets the same release. Check each one got it; a difference between them is drift to
   explain or fix.
6. **Verify live.** A merged deploy PR is not a finished rollout: check the running version and the
   behaviour in each environment.

## Release readiness

Tier each change in the release on evidence:

| Tier | Means |
|---|---|
| SAFE | Covered by tests, no migration risk, nothing user-visible that's untested |
| MONITOR | Ships, with a named signal to watch after rollout |
| HOLD | A blocker: data loss risk, an irreversible step without its gate, a failing check |

Note any new feature without a regression test or monitoring.

## Under a grant

A grant to release names a window and a scope ("merge and release today"). Inside it: read each release,
deploy it when staging is clean, and report each step. It lapses when the window ends, and it never covers
data loss, irreversible changes or a declared freeze.

## When the production step is someone else's

Hand them one script that walks through each checked step and logs each output, never a list of commands
to paste. Run everything up to that step yourself.

## Brief downtime

A short, non-catastrophic blip during a rollout is acceptable in favour of shipping; don't wait for a
quiet hour. Data loss, irreversible changes and long outages keep their gates.
