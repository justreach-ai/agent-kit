# Agent kit

A public kit for agents that build software: how to scope work, prove it, get it reviewed, merge it,
release it and report on it, and the engineering rules that keep it safe. It holds skills today; hooks and
agent configurations will join them here. It is written for teams running agents in
[Reach](https://justreach.ai), and the skills work with any agent that reads `.agents/skills/`.

## What's here

### Skills

| Kind | Skills | Purpose |
|---|---|---|
| Routers | `desk-mode`, `lane-mode` | Loaded once at the start of a session. Each sends every kind of task to its process skill and lists the principles with when each applies. |
| Process | `status-update`, `critical-thinking`, `strategic-thinking`, `impact-assessment`, `strategy-brief`, `decision-options`, `delegation-brief`, `risk-ladder`, `review-severity`, `release-gates`, `pr-description`, `design-doc` | How to do one recurring job |
| Principles | `principle-*` (28) | One rule, when it applies and why, in a few lines |

`.agents/skills/<name>/SKILL.md` holds each skill; `.claude/skills` is a symlink to the same folder, so
Claude Code and other tools find them in either place. [AGENTS.md](AGENTS.md) says which router to load and
what wins over these skills.

**Desk** and **lane** are the two roles the routers serve: a desk is an orchestrating agent that works for
one person and runs lanes; a lane is one scoped task in one repo, in its own worktree.

## Using the skills in Reach

Reach loads skills from its own platform skills (`reach-*`), skills managed for a space, the Reach
repositories an agent spec names in `spec.skills.repositories`, and, when the agent spec turns it on,
the workspace. This repo is on GitHub, so it comes in through the workspace. The agent looks for workspace
skills only in `.agents/skills/` or `.claude/skills/` in its working folder or a folder above it, so a
clone further down isn't found on its own. Link the kit's skills into the working folder. Its working
folder is the sandbox spec's `agentDir`, else its `workingDir`, else `/workspace`.

1. **Sandbox spec:** a boot step that checks this repo out at one commit you choose, in
   `/workspace/github.com/justreach-ai/agent-kit` (see [where clones go](#where-clones-go)), and links its
   skills into the working folder. It fetches the commit only when it isn't there yet, so a reboot costs
   nothing, and nothing in it fails the boot: without the commit it keeps the copy it had, or runs
   without the kit.

   ```yaml
   spec:
     agentDir: /workspace
     init:
       - name: install-agent-kit
         dir: /workspace
         env:
           # A full commit id from this repo: `git ls-remote https://github.com/justreach-ai/agent-kit main`.
           AGENT_KIT_COMMIT: 719ac4c7aa7b0f67dba78b499a0554ba1b2db0e5
         run: |
           set -euo pipefail
           kit=/workspace/github.com/justreach-ai/agent-kit
           if [ ! -d "$kit/.git" ]; then
             mkdir -p "$kit"
             git -C "$kit" init --quiet
             git -C "$kit" remote add origin https://github.com/justreach-ai/agent-kit.git
           fi
           if ! git -C "$kit" cat-file -e "${AGENT_KIT_COMMIT}^{commit}" 2>/dev/null; then
             git -C "$kit" fetch --quiet --depth 1 origin "$AGENT_KIT_COMMIT" ||
               echo "agent-kit: could not fetch ${AGENT_KIT_COMMIT}" >&2
           fi
           if ! git -C "$kit" -c advice.detachedHead=false checkout --quiet --force --detach "$AGENT_KIT_COMMIT" 2>/dev/null; then
             echo "agent-kit: ${AGENT_KIT_COMMIT} is not available; keeping what was there before, if anything" >&2
             exit 0
           fi
           mkdir -p /workspace/.agents
           if [ -L /workspace/.agents/skills ] || [ ! -e /workspace/.agents/skills ]; then
             ln -sfn "$kit/.agents/skills" /workspace/.agents/skills
           else
             echo "agent-kit: /workspace/.agents/skills is already a folder, so the kit is not linked" >&2
           fi
   ```

   If `/workspace/.agents/skills` is already a folder of your own, the step leaves it alone and says so:
   link the kit's skills into it one by one instead, as [using the skills locally](#using-the-skills-locally)
   does.

2. **Agent spec:** turn on workspace skills (off by default), and name the router in the prompt:

   ```yaml
   spec:
     skills:
       workspace: true
     systemPrompt: |
       At the start of each session, load the `lane-mode` skill and follow it.
   ```

   Use `desk-mode` for an orchestrating agent. Both routers load only when named.

Checked against Reach 10.86.0: its agent-spec validator accepts `spec.skills.workspace` and refuses a
non-boolean, and its skill loader, given a working folder set up as above, finds all 38 skills in the pinned revision only
when workspace skills are on. The boot step was run on a fresh boot, a reboot, a move to another commit,
a commit that doesn't exist (on a fresh boot and over an earlier copy) and an existing skills folder.

With workspace skills on, any `.agents/skills/` or `.claude/skills/` in the working folder or above it adds
to the agent's prompt. Keep them off for an agent that clones code from people you don't trust, such as
one that reviews outside pull requests.

**Moving to a newer kit.** Your agents run the commit you pinned, so a change here reaches them only after
you have read it. To move: read what changed (`git log --oneline <pinned>..<new>` in a clone, or the
compare view on GitHub), set `AGENT_KIT_COMMIT` to the new full commit id, and apply the sandbox spec. Each
sandbox checks the new commit out the next time it boots; one already running keeps the old one until then.
Following `main` instead (a `git pull` in the step) would put every merge here into your agents' prompts
with no review on your side.

Reach's own `reach-*` skills, and the skills managed for a space, win any name collision; nothing here uses
that prefix.

To keep rules of your own, put them in a private repo the same sandbox clones: an overlay per role
(`<org>-desk`, `<org>-lane`) that loads after the router here, plus your own principles. The overlay
indexes them, and wins where it speaks.

## Using the skills locally

Claude Code reads skills from `~/.claude/skills/` (every project) or a repo's `.claude/skills/` (that repo
only):

```bash
git clone https://github.com/justreach-ai/agent-kit.git ~/src/github.com/justreach-ai/agent-kit
mkdir -p ~/.claude/skills
for s in ~/src/github.com/justreach-ai/agent-kit/.agents/skills/*/; do
  d=~/.claude/skills/"$(basename "$s")"
  if [ -e "$d" ] || [ -L "$d" ]; then echo "skipped $(basename "$s"): already exists"; else ln -s "$s" "$d"; fi
done
```

The loop never replaces a skill you already have; it names each one it skips. Pull to update: linked skills
follow, and a skill added later needs the loop run again. Start a session in a role by asking for it: "use desk-mode" or "use lane-mode". Tools that read
`.agents/skills/` can point at the clone directly.

## Where clones go

Clone every repo to `<root>/<host>/<org>/<repo>`, all lowercase, with the full host name:

| Where | Root | This repo |
|---|---|---|
| A Reach sandbox | `/workspace` | `/workspace/github.com/justreach-ai/agent-kit` |
| Your machine | any folder you keep code in, e.g. `~/src` | `~/src/github.com/justreach-ai/agent-kit` |

Two repos with the same name under different organisations or hosts then never collide, and a path says
exactly which repo it is, for people and agents alike.

## Contributing

1. **Every change goes through a pull request.** Nobody pushes to `main`.
2. **One rule per principle.** A new principle is a new `principle-<rule>` folder, named for the rule, with
   its reason ("why") and a description that says when it applies. Add it to the index in `desk-mode` or
   `lane-mode`.
3. **General, not one organisation's.** No company, product, repo or region names, no people's names, no
   quotes from private conversations. Examples are invented. A rule that only holds for one organisation
   belongs in that organisation's own skills.
4. **Rules about one repo go in that repo**, in its own `.agents/skills/`.
5. **Short.** A principle fits on one screen; a process skill says how to do one job.

## License

[Apache License 2.0](LICENSE).
