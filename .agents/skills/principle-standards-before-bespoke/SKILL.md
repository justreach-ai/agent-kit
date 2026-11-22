---
name: principle-standards-before-bespoke
description: "Apply when designing an interface, choosing a library or vendor, or about to write glue. Ask what the standard is, then the upstream component, then what the repo already proves, before building anything."
---

# Standards before bespoke

1. Ask what the standard is first (OIDC, OpenAPI, CloudEvents, AG-UI, Idempotency-Key, ETag), and borrow
   before building. Borrow, unless the thing is the product itself.
2. Prefer platform-native, free and open source, self-hostable, permissively licensed tools; own the stack
   and the data.
3. Integrate third-party tools only through their officially supported methods. No patched dependencies.
4. One toolchain across repos: choose it once, latest stable, pinned, upgraded often; copy how existing
   pieces are done.
5. Check the licence before using third-party data, models, media or code.
6. A contained, documented workaround only after upstream versions and config are exhausted, with the
   proper fix named as the follow-up.

Why: standards bring tools and fixes for free, and one toolchain lets people and agents move between
repos without relearning.
