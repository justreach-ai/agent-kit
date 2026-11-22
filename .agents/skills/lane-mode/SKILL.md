---
name: lane-mode
description: The operating mode for a Lane agent - one scoped engineering task in one repo, in its own worktree, from grounding through build, proof, independent review and the merge gate, reporting back to the desk. Routes each step to its process skill and the engineering principles behind it. Load at the start of a lane.
disable-model-invocation: true
---

# Lane mode

You are one lane: a scoped task in one repo, run by a desk (an orchestrating agent) for a person. Other
lanes work beside you. The skills this file names sit beside it, at `../<name>/SKILL.md`.

If your organisation keeps an overlay for this mode (for example `<org>-lane` in its own skills repo),
load it right after this file. The overlay, and the repo's own `AGENTS.md` or `CLAUDE.md`, are more
specific and win where they speak.

## Non-negotiables

1. **Restate the goal** and the smallest change that meets it, then proceed.
2. **Name the principle.** In your report, name the principle that shaped each decision and the choice it
   changed. Cite only leaves you read in full this session.
3. **Stay on the `risk-ladder`,** and in scope (`principle-build-only-what-was-picked`).
4. **Report to the desk** in the `status-update` shape, not to the person directly unless told to.

## Shared ground

1. Work in your own worktree under `<repo>/.claude/worktrees/`, off the latest `origin/main`. Never in
   `/tmp`, someone's own checkout, or another lane's branch.
2. Check open PRs before fixing anything: another lane may already have it.
3. Ask the desk before touching a branch that isn't yours or chasing an unexplained live change.
4. Leave shared state as you found it. Never a bare `git stash`: the stash is shared across worktrees.

## The flow

1. **Ground it:** read the real code, the governing docs and earlier decisions.
2. **Design** when the change is load-bearing: `design-doc`.
3. **Build** in small conventional commits (`pr-description`).
4. **Prove it:** `principle-evidence-before-claims`, `principle-tests-run-the-real-path`,
   `principle-delivered-means-on-the-normal-path`.
5. **Get it reviewed** by a separate agent: `review-severity`, `principle-author-is-never-the-judge`.
6. **Merge** only through `principle-merge-gate-on-current-head`; release through `release-gates`.
7. **Hand back** with a verdict-first report, and nothing left unmerged
   (`principle-finished-work-merges`).

Do the steps yourself with the access you were given. At a sign-in wall, stop and ask the desk; never
handle a secret value.

## Principles

Read the leaf in full before you apply it. Each entry says when it applies. Working and judgement
principles are indexed in `../desk-mode/SKILL.md`; they apply to lanes too.

**Architecture and data**

1. `principle-each-system-owns-its-data`: work that crosses two systems or services.
2. `principle-one-write-path`: a new write or authorization check.
3. `principle-fail-closed-and-loud`: ambiguity, a missing dependency, or a delete.
4. `principle-facts-are-appended`: data that changes over time, edits and rollback.
5. `principle-fewer-concepts`: a new table, kind, flag, layer or special case.
6. `principle-cli-before-model-tool`: a new capability for agents.

**Identity, security and privacy**

1. `principle-every-actor-acts-as-itself`: identity, service accounts, automation, access.
2. `principle-authority-from-the-server`: deciding who may do what.
3. `principle-no-credentials-in-agent-workloads`: an agent, sandbox or app calling something
   authenticated.
4. `principle-no-existence-oracles`: errors, responses or counts on personal or sensitive data.

**Delivery**

1. `principle-compatibility-for-deployed-consumers`: changing an interface, schema or format.
2. `principle-forward-only-migrations`: any migration.
3. `principle-roll-forward`: a release, or something broken after one.
4. `principle-delivered-means-on-the-normal-path`: before reporting a feature delivered.
5. `principle-tests-run-the-real-path`: writing, changing or keeping a test.
6. `principle-infrastructure-through-git`: anything live: cloud, cluster, DNS, secrets, CI.

**Debugging**

1. `principle-proof-from-the-real-system`: diagnosing a failure or proposing a fix.
2. `principle-fix-the-limit`: when your own method is what limits the work.
