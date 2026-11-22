---
name: design-doc
description: Design a load-bearing change before building it - ground it in the real code and governing docs, a decision ledger, options with trade-offs and a recommendation, the ideal beside the shippable slice, structure over prose (diagrams, sample contracts, schema diffs, a glossary), an adversarial review, and ADRs merged to main. Use when designing a feature, migration or system, or writing a design doc or ADR.
---

# Design docs

Design first when the change is load-bearing: a new table, API, boundary, identity rule or migration.

## Ground it

1. Read the real code and the governing docs (ADRs, the system's architecture docs, the repo's
   `AGENTS.md`) before proposing anything.
2. Look for earlier thinking first: the repo's specs, plans and ADRs, and the tickets. Don't re-derive a
   spec that exists.
3. Check what's already solved upstream (`principle-standards-before-bespoke`).

## Contents

1. **A decision ledger:** each item with its status, who decided and when, and rejected options kept with
   their reasons.
2. **Options with trade-offs and a recommendation**, the one-way doors named
   (`principle-ship-the-slice-name-the-ideal`).
3. **The ideal and the shippable slice side by side.**
4. **Structure, not prose:** a diagram of where things connect, sample contracts (request, response,
   event), a matrix for rules, a glossary for terms. If it reads as word soup, restructure it.
5. **Schema changes as a git-style diff per table,** with unchanged columns and indexes kept as context and
   one line per change.

## Review and land it

1. Get an independent, adversarial review from a separate agent (`review-severity`, design questions), in
   rounds until clean.
2. Planned ADRs are brought up to date and merged to main as planned work. A design left in a draft PR is
   one agents won't find.
3. Docs are claims about a live system: one canonical page per fact, updated in the PR that changes the
   behaviour, short and linking out rather than restating.
