---
name: tracking-plan-review
description: >
  Review, audit, and improve an existing analytics tracking plan or event
  taxonomy. Use when events already exist and the user says "review my
  tracking plan", "audit my events", "check event coverage", "review my
  analytics", "are my events right", "event taxonomy review", "tracking plan
  audit", "clean up my events", "find gaps in my tracking", "review event
  naming", or provides existing events (a spreadsheet, a tool export, or a
  codebase) and wants feedback on naming, coverage, redundancy, or whether the
  events answer their questions.
argument-hint: "[tracking plan file, export, or codebase path] [platform]"
---

# Tracking Plan Review

Audit an existing tracking plan and lead with the few fixes that matter most.

## Inputs

Any format: spreadsheet, list of names, analytics tool export, a tracking plan from `event-definition` (`tracking/tracking-plan-*.md`), or the codebase. To find the events, follow "Find the existing tracking first" in `${CLAUDE_PLUGIN_ROOT}/references/naming-conventions.md`.

Also get, if not given: target platform(s), the questions the tracking should answer (`tracking/use-cases-*.md` if it exists), and the key user flows. Without questions, judge coverage against the flows and say so.

## Depth

- **Full audit (default):** production plans, roughly 15+ events, or when the user wants thoroughness. All seven checks.
- **Quick check:** small or early plans, spot checks, or "quick" / "just the big issues". Checks 1, 3, and 5 only, Critical and Warning findings only. Name the skipped checks and offer the full audit.

## Checks

Measure where you can and report the real ratio ("31 of 40 events follow Title Case Object-Action"). Never turn ratios into a score or pass/fail grade.

1. **Naming.** Detect the dominant convention per `naming-conventions.md`. Count events that break it on casing, separator, structure, or tense.
2. **Coverage.** For each key flow: is entry, each key step, completion, and abandonment or failure tracked? Are system actions that deliver value (AI output, notifications, renewals) tracked? Which use-case questions can't be answered?
3. **Redundancy.** Duplicates under different names, near-identical events that pass the parameterization test in `${CLAUDE_PLUGIN_ROOT}/references/decision-framework.md`, micro-interactions nobody analyses, and orphans with no identifiable use.
4. **Properties.** Same concept, different names (`source` / `origin` / `referrer`); same name, different types; missing context the questions need (actor, source, variant); undocumented categorical values; unflagged PII.
5. **Platform limits.** Check against `${CLAUDE_PLUGIN_ROOT}/references/platform-constraints.md`: name length and format, event type count, properties per event, value lengths and types, reserved names.
6. **User and group properties.** State sent as event properties on every event, `set` where `set_once` belongs, missing counters or first-time timestamps, missing account properties for B2B.
7. **Firing conditions.** Would two engineers implement each one identically? Are edge cases (auto-save vs manual, retries) and exclusions stated?

## Output

Keep it short. Depth is on request.

1. **Verdict:** one or two sentences on the state of the plan and the biggest risk.
2. **Top fixes (at most 5):** the changes with the most impact, highest first. For each: what's wrong, the events affected, the fix, and effort (low / medium / high). Flag fixes that break existing dashboards (renames, merges) and point to "Changing existing events" in the decision framework.
3. **Findings by check:** one line per check with the measured ratio or count, then Critical and Warning findings only. Put Info findings in one line at the end.

Offer, don't produce unasked: the full Info list, and a revised tracking plan in the `event-definition` format.
