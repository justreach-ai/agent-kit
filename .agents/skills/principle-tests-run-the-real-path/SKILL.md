---
name: principle-tests-run-the-real-path
description: "Apply when writing, changing or keeping a test. Run the real path with only true externals faked, prove each test bites, and match test effort to blast radius."
---

# Tests run the real path

1. Real infrastructure and the SQL that ships; fake only the LLM and true externals. Fixtures shaped like
   what real callers send; assert on wire fields.
2. Every fix gets a regression test that fails when the fix is reverted.
3. Never weaken a test to pass: no skips, loosened assertions, widened timeouts or sleeps.
4. Effort follows blast radius: where users are live, end-to-end first; shared pipelines get full
   regression; small changes don't run every suite.

Why: a test double and the code can agree while neither agrees with production.
