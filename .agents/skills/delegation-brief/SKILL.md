---
name: delegation-brief
description: Hand work to another agent or session without losing what matters - a brief that carries the source material and what to keep, the author never judging their own work, handoff files before context runs out, prompts passed as files, and estimates in agent time. Use when you spawn a subagent, hand over to another session, or are about to compact.
---

# Delegation briefs

A brief is the only context the other agent has. Whatever it leaves out is lost.

## The brief

1. **Say what to keep as well as what to change.** A redesign briefed only with the changes will throw
   out what already works.
2. **Point at the source material the person named** (a transcript, earlier iterations, a ticket, a
   design doc), and read it yourself first.
3. State the goal, what is already ruled out, the decisions already made, and the scope, narrowly.
4. Say what "done" means and what evidence to bring back (see `principle-evidence-before-claims`).
5. Give the brief the material, not your conclusion, when you want an independent view.

## The author is never the judge

When the work comes back, it is reviewed by a different agent, never by the one that wrote it
(`principle-author-is-never-the-judge`).

## Context is perishable

1. Before compaction or a handover, write a handoff file: goal, decisions made, state of each piece of
   work, what's next, open questions.
2. Decisions made in a session stay made. If someone asks "I thought we…?", you dropped one.
3. A prompt for another session goes in a file, with one command that runs it, never a long block to
   copy out of a reply.
4. After a handover, check that the process that was asked for, and the requests already queued, survived
   it.

## Look for earlier thinking first

Before researching, search the repo's specs, plans and ADRs, the tickets, and earlier decisions. A research
pass that re-derives a spec written days earlier wastes the time it was meant to save.

## Estimate in agent time

Give build time and gate time (review, CI, staging, approvals) separately. Estimates in human developer-days
read as inflated and get used to split work into phases it doesn't need.

## Repeated corrections become durable

When the same correction comes up twice, turn it into a skill, a hook or a rule in the repo it is about
(`.agents/skills/<name>/SKILL.md` with a `.claude/skills` symlink), so every engineer's agents get it.
