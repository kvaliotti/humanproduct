---
name: debug
description: "Use when a bug, test failure, or unexpected behavior appears — trigger on \"debug this\", \"why is this failing\", \"this test is broken\", \"unexpected behavior\", \"fix this bug\", or when /ship's verify stage reports a failure. Confirms the intended behavior, finds the ROOT CAUSE before any fix, then fixes at the source."
argument-hint: "<what's failing>"
allowed-tools: Read, Edit, Write, Bash, Grep, Glob, AskUserQuestion
---

# debug — intended behavior first, then root cause, then fix

Random fixes waste time and create new bugs. Symptom patches mask the real issue.

**Two things must be true before you change a line:** you know *what correct looks like*, and you know *why it's currently wrong*. Skip either and you fix the wrong thing or fix nothing.

## The Iron Law

```
NO FIX WITHOUT (1) CONFIRMED INTENDED BEHAVIOR AND (2) ROOT CAUSE
```

## Phase 0 — Confirm intended behavior (before diagnosing)

A fix aimed at the wrong target is worse than no fix. Before investigating *why* it's broken, be sure you know *what it should do*.

1. **State the expected behavior** — for this failing input/state, what is the correct output/result?
2. **Is it unambiguous** from the spec, the plan, the test's intent, the types, or nearby working code? → proceed to Phase 1.
3. **Are you inferring or guessing it?** → **STOP and ask the user** (or check the plan/spec/failing-test intent). One clarifying question is far cheaper than a confident wrong fix.

Do not proceed while the target is a guess. Only once you know **both** what correct looks like *and* (after Phase 1–3) the root cause, do you implement.

## Phase 1 — Root cause investigation (before ANY fix)

1. **Read the error carefully** — full stack trace, line numbers, paths, codes. The message often contains the answer.
2. **Reproduce consistently** — exact steps, every time? If not reproducible, gather more data — don't guess.
3. **Check recent changes** — `git diff`, recent commits, new deps, config/env changes.
4. **In multi-component systems, instrument the boundaries** — log what enters and exits each component boundary and whether env/config propagates. Run once to see *where* it breaks, then dig into that component. Measure the failing layer; don't theorize it.
5. **Trace the data flow** — when the error is deep in the stack, trace backward: where did the bad value originate, what passed it in, up to the source. Fix at the source. See `${CLAUDE_PLUGIN_ROOT}/skills/debug/root-cause-tracing.md`.

## Phase 2 — Pattern analysis

1. **Find working examples** — similar code in the same codebase that works.
2. **Compare against references** — read any reference implementation completely, not skimmed.
3. **List every difference** between working and broken — however small; don't assume "that can't matter."
4. **Understand dependencies** — config, environment, assumptions it relies on.

## Phase 3 — Hypothesis and testing

1. **State one hypothesis** — "X is the root cause because Y." Specific, written down.
2. **Test minimally** — the smallest change that tests it, one variable at a time.
3. **Verify before continuing** — worked → Phase 4. Didn't → form a *new* hypothesis, don't stack fixes.
4. **When you don't know, say so** — research or ask; don't pretend.

## Phase 4 — Implementation

1. **Create a failing test first** — simplest reproduction, automated if possible. Have it before you fix.
2. **Implement a single fix** — address the root cause, one change, no "while I'm here" refactoring.
3. **Verify** — test passes, nothing else broke, the behavior from Phase 0 now holds.
4. **If it doesn't work** — STOP. Count attempts. Under 3: return to Phase 1 with new info. **3+: question the architecture** — don't attempt fix #4 blind. Each fix revealing new coupling elsewhere, or requiring "massive refactoring," means the approach is wrong, not the hypothesis. Discuss before more fixes. Then consider `${CLAUDE_PLUGIN_ROOT}/skills/debug/defense-in-depth.md`.

## Red flags — STOP and go back

- "Quick fix now, investigate later" · "Just try changing X" · "Add several changes, run tests"
- "Skip the test, I'll verify manually" · "It's probably X" · listing fixes before tracing data flow
- Fixing before you can state the intended behavior (Phase 0) · "one more fix attempt" after 2+ failures

## Common rationalizations

| Excuse | Reality |
|--------|---------|
| "Issue is simple, skip the process" | Simple issues have root causes too; the process is fast for them. |
| "Emergency, no time" | Systematic is faster than guess-and-check thrashing. |
| "I'll write the test after the fix" | Untested fixes don't stick; the failing test first proves the cause. |
| "Multiple fixes at once saves time" | You can't isolate what worked, and you add new bugs. |
| "I know what it should do" | If you can't state it precisely, you're guessing — confirm it (Phase 0). |
| "One more attempt" (after 2+ failures) | 3+ failures = wrong approach. Question it, don't fix again. |

## Supporting techniques (this directory)

- `root-cause-tracing.md` — trace a bug backward through the call stack to the original trigger.
- `defense-in-depth.md` — after finding the cause, validate at every layer to make the bug structurally impossible.
- `condition-based-waiting.md` (+ `condition-based-waiting-example.ts`) — replace arbitrary sleeps in flaky tests with condition polling.
- `find-polluter.sh` — bisect which test pollutes shared state.
