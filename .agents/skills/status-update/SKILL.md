---
name: status-update
description: Shape a status update, catch-up or "what changed" report - a coverage block per workstream, then What changed, Flagged and What's needed, in numbered points that end on the reader's actions. Use whenever you report progress to a person or to another agent.
---

# Status updates

The reader should be able to act after reading only the headlines. Everything below serves that.

## Shape

A coverage block, then exactly three sections in this order. The update ends with the reader's actions.

```
Checkout                 ████████░░   new payment form in staging
Search                   █████░░░░░   index rebuild half done
Mobile app               ██░░░░░░░░   crash on sign-out found
Reporting                ░░░░░░░░░░   —
```

Ten-cell bars, a workstream on the left, a few words on the right. List the areas with nothing in them too:
an empty area is information. Use the areas the organisation really works in.

| Section | Holds |
|---|---|
| **What changed** | Shipped outcomes, with the impact in the same line |
| **Flagged** | Shaky claims, your own errors, small findings that need the reader's eye |
| **What's needed** | Grouped as *Do*, *Decide* and *Pass on*; this closes the update |

When the update covers what agents did, write it as an action log grouped by area: one line each with the
time, the reference, a state word, and the what and why, e.g.
`09:12 (08:12 UTC)  shop#412  merged  "retries a failed card charge once…"`.

## Each line

1. **Numbered points, never `-` bullets.** A leading hyphen reads as a removed line in a diff, and numbers
   let the reader point at one ("do 4.2"). Sub-points are decimal.
2. **Headline, then the decision taken, then the consequence**, left to right.
3. **Annotate every reference:** `shop#57 (caches the product list for a minute)`, never a bare ticket or PR number.
4. **Paraphrase jargon** that isn't shared vocabulary, even when you understand it.
5. **Link file paths short:** `[retry-policy.md](url)`, not the full repo path.
6. **Own your mistakes in the line where they land**, in the same voice, without hedging.
7. Times in the reader's time zone, with UTC beside them.
8. Keep it brief: cut connective text, signposting and padding.

## What earns a place in Flagged

A claim that rests on an **absence** ("there's nothing there" usually means "I didn't find it"), an
**impossibility** ("doesn't work" usually means "didn't work the way I tried") or an **absolute**, when a
decision leans on it. Say what check would settle it. Also: your own errors, and docs or comments that
have outlived the decision they describe.

## Diff blocks

Use them for real before-and-after state. Caption each one directly above with what it is and where it
came from, so the reader never has to guess:

> `search-indexer` replicas · live, `kubectl <context>`
> ```diff
> - 3 ready of 3
> + 1 ready of 3 — two pods restarting on out-of-memory
> ```

## Asked again

When someone asks about something you already answered, check what could have changed first (merged PRs,
deploys, other people's and agents' work). Lead with any change; if nothing changed, point back to the
earlier answer and list what you checked.

## Don't

Each of these makes an update harder to read:

1. Tag vocabularies (`CLAIM`, `STALE`, …), tables of flagged items, or colour-coded emoji markers.
2. Extra sections beside the three, such as a separate impact or minor-items section: they overlap with
   the three, and minor items at the end push the reader's actions out of the closing place.
3. `-` bullets anywhere.
