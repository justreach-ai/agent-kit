---
name: pr-description
description: Write a PR description, review comment or commit message the team will read - problem and approach at a high level, what was tried, the value, what's not in it and how to run it; conventional commits; team-safe wording with no naming or blaming. Use whenever you open a PR, draft a review comment or commit.
---

# PR descriptions, review comments and commits

Write for the teammate reading it on their phone between meetings. The code is in the diff.

## PR description

1. **Problem** and **approach**, at a high level, in a few plain sentences.
2. **What was tried**, when it explains the approach.
3. **The value:** what changes for users or engineers.
4. **Not in this PR:** what was left out on purpose, with where it's tracked.
5. **To run it:** the commands or steps to see it working.
6. Keep it light. No line, file or test counts; no restating the diff.
7. **Carried-over work:** when the PR takes over or builds on someone else's PR or branch, link it and
   credit its author. Claim only the work that is yours.

## Team-safe

1. No naming and no blaming, in the title, body, commits or code comments.
2. Nothing alarming in the title: describe the change, not the danger.
3. No security-fix detail in anything broadly read; it goes to the people who need it.
4. Never write people's access reasons, private context or opinions about anyone into a PR.
5. Tag people only when the person you work for asked you to; one request to involve someone is not a
   standing rule for that kind of work.

## Review comments

"LGTM", or the concern: one specific check phrased as a question ("one thing worth checking is …?"), and
thanks to the author. Specific, kind, no list of nits. Draft them; a person posts unless you were told to.

## Commits

1. Conventional commits (`fix:`, `feat:`, `chore:`, …), matching the repo's log: they drive releases.
2. Small and often, one concern per commit, on a scoped branch named from the ticket.
3. Never `git add .`; stage what you mean.
4. No AI attribution or co-author lines.

## Plain writing

Short sentences, first person where it's yours. Nothing that sounds generated: no announcing openers, bold
labels in chat, summary closes, hedging, stock phrases or drama. Match the spelling already used in the
repo.
