---
name: principle-no-existence-oracles
description: "Apply when shaping errors, responses or counts on anything holding personal or sensitive data. Responses look the same whether or not the thing exists or the caller may see it."
---

# No existence oracles

1. Identical responses whether or not an account exists; one non-revealing access error.
2. Fields present but empty for callers without access; no leaked counts.
3. Privacy wins over a feature when they conflict.

Why: where the data is sensitive, presence itself is a disclosure.
