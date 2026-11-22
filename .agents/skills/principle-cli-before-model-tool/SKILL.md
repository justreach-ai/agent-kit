---
name: principle-cli-before-model-tool
description: "Apply when giving agents a new capability. Give them a CLI and a skill that teaches it before adding a model tool, and build the CLI on verbs models already know."
---

# CLI before model tool

1. A CLI plus a skill first; a model tool (MCP or similar) only when a CLI can't do it.
2. Use verbs models already know, `gh`'s where they overlap.
3. Kubernetes-shaped, declarative config with drift detection over imperative sync commands.

Why: every tool adds to what the model weighs on every turn; a CLI costs nothing until it's used.
