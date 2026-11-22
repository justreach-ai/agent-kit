---
name: principle-proof-from-the-real-system
description: "Apply when diagnosing a failure or proposing a fix. Find the smoking gun in the real system (logs, live state, the exact code path) before you name a cause or change anything."
---

# Proof from the real system

1. Reproduce, or read the live evidence, before you diagnose. A plausible story is not a diagnosis.
2. Name the exact code path, and check that the explanation fits first principles.
3. Fix where the system first went wrong, and every other place with the same fault, not where the
   symptom surfaced.
4. Don't defer an investigation you could do now with the access you have.

Why: fixes built on a guess move the symptom, and the next person inherits both the bug and the guess.
