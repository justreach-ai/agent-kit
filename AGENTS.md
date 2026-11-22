# Agents working with this kit

This kit is for agents that build software. It holds skills today: two role routers, process skills for
recurring jobs, and principles that each state one rule, when it applies and why. Hooks and agent
configurations will join them. The kit suits any team running agents in Reach, or anywhere that reads
`.agents/skills/`.

## Which router to load

Load one router at the start of a session. It sends each kind of task to its process skill and lists the
principles with when each applies.

| You are | Load | Then |
|---|---|---|
| An orchestrating agent working for one person: running other agents, preparing their decisions, reporting, reviewing | `desk-mode` | your organisation's desk overlay, if it has one |
| One scoped engineering task in one repo, run by a desk or a person | `lane-mode` | your organisation's lane overlay, if it has one |
| Neither: a one-off job | the process skill or principle for that job, directly | |

Both routers are marked `disable-model-invocation`: load them on purpose, by name. Process skills and
principles load on their own when their description matches the task.

## Precedence

More specific wins:

1. The repo you are working in: its `AGENTS.md`, `CLAUDE.md` and `.agents/skills/`.
2. Your organisation's overlay and skills (for example a private repo with `<org>-desk` and `<org>-lane`).
3. These skills.

Where a principle here and a repo's rule disagree, follow the repo and say so in your report.

## Working with them

1. **Name the principle.** In each report, name the principle that shaped each decision. Cite only skills
   you read in full in this session.
2. **Read the leaf before applying it.** A router's one-line index says when a principle applies; the
   rule itself is in the principle's own `SKILL.md`.
3. **Stay on the `risk-ladder`.** It says what you may do alone, what you report after, and what needs an
   explicit go.

## Where repos are

Repos are cloned to `<root>/<host>/<org>/<repo>`, lowercase, full host: in a Reach sandbox,
`/workspace/github.com/<org>/<repo>`, so this one is `/workspace/github.com/justreach-ai/agent-kit`. Clone
the same way when you clone anything yourself, and refer to repos by that path.

## Changing this repo

See [README.md](README.md#contributing). Skills here stay general: no organisation's names, repos,
regions, people or private context.
