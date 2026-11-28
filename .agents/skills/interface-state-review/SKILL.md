---
name: interface-state-review
description: Use when testing an interactive screen across loading, interruption or a change of state. Verify what the person sees, can act on and can recover after the transition.
---

# Interface state review

1. Start at the real entry point. Pick the transition most likely to change the person's next action. Examples include an initially empty list finishing its load, a filter removing the selected row, and a refresh failing while old results remain.
2. Exercise the transition with controlled data. Distinguish a genuine empty result, a filter with no matches, and a request that failed. Preserve useful content during refresh where possible. Give the person a way back from a filter or an error. A loading placeholder should reserve the space the content will occupy.
3. Inspect the same task using the platform's ordinary inputs. For a phone list, check a large text size, the spoken label and selected state, and the return from detail. For a desktop list, check the keyboard focus and selection after the data changes. When motion explains a transition, check the reduced-motion presentation too.
4. Pair a behavior test with a view of the state that matters. A screenshot can establish what was visible. An interaction test can establish where an action led. Report which device, fixture or simulator you used and which part still needs a person or hardware.

**Example.** A search has results when a refresh goes offline. Keep the results usable and show how to retry. Clear the query and check that the restored list still identifies its selected item. A successful first-load screenshot alone cannot establish either behavior.
