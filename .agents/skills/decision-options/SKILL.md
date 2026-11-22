---
name: decision-options
description: Put a decision to a person so they can answer in one token - numbered, self-contained options with what happens under each, the recommendation marked in words, context in the same message, and an interactive page when there are many. Use whenever you need someone to choose before you can continue.
---

# Decision options

A decision is well posed when the person can answer "2.1" without scrolling, remembering or asking.

## Before you ask

1. **Answer what you can first.** Find every answer you can yourself, so the question carries answers and
   asks only what's left.
2. **Ask only once the direction is set.** While the person is still shaping it ("does that make
   sense?"), reflect their model back in a few lines and name your next step. Options posed too early get
   answered outside the options.
3. **Is it theirs to decide?** Craft calls are yours (see `principle-decide-craft-bring-policy`). Bring policy,
   permissions, security, merges, releases and one-way doors.

## Shape

> 4. **Where the nightly import runs** — 4.1 *a scheduled workflow* (recommended): it retries on its own
>    and shows in the run history, but it needs a secret added first · 4.2 *a cron job on one server*:
>    it can start tonight, but it stops whenever that server does

1. Two or three numbered options, recommended first, and **say which you recommend in words**: order
   alone isn't read as a recommendation.
2. **Each option is one line:** what concretely happens, and the one consequence that matters. Two labels
   with no scenario can't be answered.
3. Supporting facts go above the options, never nested inside them.
4. Keep the what and why to the minimum needed to decide.
5. Ask a few at a time; hold the overflow for the next round.

## Context travels with the decision

Assume the person has read nothing since the message they are answering. Every decision carries its own
context; when you ask again, repeat the information instead of pointing back to an earlier message.

## Many decisions

When there are many, or they need context the person doesn't have in view, put them on one interactive
page with each decision's context beside it. The person records answers and notes on the page; you read
them back, act on them, and update the page to show what remains.

## After the answer

If the reply doesn't name an option, say in one line how you read it, so it can be corrected. A decision,
once made, stays made for the rest of the work: don't re-raise it.
