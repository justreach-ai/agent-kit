---
name: principle-encode-corrections-in-structure
description: "Apply when the same correction comes up a second time. Turn it into a skill, a hook, a lint or a check in the repo it is about, so every engineer's agents get it."
---

# Encode corrections in structure

1. A rule about one repo goes into that repo: `.agents/skills/<name>/SKILL.md` with a `.claude/skills`
   symlink, a lint rule, a CI check or a hook.
2. Prefer something that runs (a check, a hook) over more instructions.
3. Propose it through a PR so the team sees and owns it.
