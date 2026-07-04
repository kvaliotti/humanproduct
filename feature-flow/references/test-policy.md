# Test policy — per-task, keyed to invariant-criticality

Not everything needs a test, and not everything needs the test first. The plan classifies **each task** into one of three policies. Default to the cheapest policy that's still safe.

## The three policies

| Policy | When | What it means |
|---|---|---|
| **test-first (TDD)** | Invariant-critical code: money / billing / usage arithmetic, exactly-once semantics, authn/authz & ownership checks, core pipeline correctness, data integrity. | Write the failing test **before** the implementation. Prove the invariant, then satisfy it. Money/mutation/admin routes get handler-level auth tests: 401 (no auth), 403 (foreign ownership), non-admin rejection. |
| **test-after** | Ordinary feature logic that isn't invariant-critical. | Implement, then cover the meaningful paths and edge cases. |
| **none** | Trivial view/copy/style: markup, CSS, static text, pure presentational tweaks. | No new tests. Don't pad the suite. |

## Config mapping

`.claude/feature-flow.local.md` → `test_policy.test_first` is a list of path/topic globs that force **test-first**. Anything not matched defaults to **test-after**, except paths matching `test_policy.skip`, which get **none**. A task can always be escalated to a stricter policy by judgment; never silently downgrade an invariant-critical task.

## Quality bar (all policies)

- **Never assert only on mocks you configured** — that tests the mock, not the code.
- A **test suite that fails to load counts as a failure**, not a skip.
- Prefer testing observable behavior over implementation details.
- Don't write mock-only "capture" tests that assert nothing real.
