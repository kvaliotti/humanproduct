---
name: event-definition
description: >
  Turn analytical use cases into concrete event specs (names, properties, firing
  conditions, user and group property updates), and optionally format them for
  Amplitude, Mixpanel, PostHog, Segment, or GA4 with payloads and SDK snippets.
  Use when use cases already exist and the user says "now define the events",
  "turn these use cases into events", "build the event taxonomy", "name the
  events", "event properties for these use cases", "create an event spec",
  "tracking spec", or hands over a measurement plan or dashboard spec. Also use
  for "format for Amplitude", "export for PostHog", "format events for GA4",
  "Segment spec", "generate payloads", "implementation-ready spec", or "export
  the tracking plan". If there are no use cases yet, start with
  analytics-use-cases instead.
argument-hint: "[use-cases file or feature] [platform]"
---

# Event Definition

Turn use cases into event specs an engineer can implement identically to any other engineer. Read `${CLAUDE_PLUGIN_ROOT}/references/decision-framework.md` before step 3.

## Before you start

1. **Use cases.** Look for `tracking/use-cases-*.md` or use cases in the conversation. If there are none, say that events without use cases become tracking nobody queries, and offer to run `analytics-use-cases` first (fast when a PRD exists). If the user insists on skipping, derive a short visible list of use cases from what they gave you and tag every event with the one it came from.
2. **Current state and convention.** Follow `${CLAUDE_PLUGIN_ROOT}/references/naming-conventions.md`: find existing events, detect the convention, confirm it with the user. Match it. Use the default only when nothing exists.
3. **Target platform(s).** Their limits are in `${CLAUDE_PLUGIN_ROOT}/references/platform-constraints.md`.

Scope: for a new product with no tracking, define lifecycle events (sign up, activation, core action, billing) first, then feature events. For an existing product, propose additions and changes, never a full rewrite unless asked.

## Process

1. **Map the flows.** List user-initiated and system-initiated flows step by step, with outcomes, error paths, and whether the user sees system actions. Each step is a candidate event, not a required one; apply the dashboard test.
2. **Choose spec depth.** Full spec by default: production plans, anything handed to engineering, anything touching revenue, compliance, or PII. Quick spec for a single add-on event, a prototype, an internal tool, or when the user asks. Quick changes the write-up, not the thinking. Any revenue, compliance, or PII event gets the full spec anyway.
3. **Apply the decisions** in `decision-framework.md`: the parameterization test for every similar pair, an `actor` property wherever user and system can both act, the batch approach (present the A–D trade-off against their questions and let them choose), and user vs event vs group properties.
4. **Decide where each event fires.**
   - Server: purchases, subscription and permission changes, account creation, anything triggered by a backend job, webhook, or AI task, anything that must be tamper-proof. Ad blockers drop a share of client-side web events; if exact counts matter, fire server-side.
   - Client: UI interactions and client-only context (viewport, scroll, element, client-side flag variant).
   - Both: client context plus a confirmed outcome. Link the two with a shared ID.
5. **Check autocapture** (PostHog autocapture, Amplitude default tracking, GA4 enhanced measurement). If autocapture already has the properties the question needs, reuse it instead of adding a custom event. If it lacks business context, define the custom event and note the double-count risk.
6. **Validate against platform limits.** Flag every violation with a fix.
7. **Cross-reference existing events.** Mark "use existing [event]", "extend [event] with [property]", or "makes [event] redundant". Changing an existing event follows "Changing existing events" in the decision framework.

## Spec formats

Full:
```
EVENT: [name per convention]
DESCRIPTION: [what happened and why it matters analytically]
FIRES WHEN: [precise trigger, e.g. "Save clicked on edit form AND save succeeds"]
DOES NOT FIRE WHEN: [exclusions, e.g. auto-save]
FIRES WHERE: client | server | both
PROPERTIES: | Property | Type | Required | Values | PII |
USER/GROUP PROPERTIES UPDATED: | Property | set / set_once / increment | Value |
USE CASE: [the question it answers]
STATUS: proposed
```

Quick:
```
EVENT: [name]
FIRES WHEN: [precise trigger]
KEY PROPERTIES: [property (type): meaning, flag PII inline]
USE CASE: [the question it answers]
```

## Guardrails

- **Every event serves at least one use case.** If not, flag "no analytical purpose identified" and recommend deferring it.
- **Every property is queryable.** It must appear in a filter, breakdown, or aggregation. No "just in case" properties.
- **Firing conditions are unambiguous.** Spell out what "completes" means: click, API success, or animation end.
- Event count is not the guardrail. If events pass these three tests, they belong, however many there are.

## Output

Write `tracking/tracking-plan-<feature>.md`:

1. One line: number of events, user properties, group properties, and the convention used.
2. Event specs, grouped by flow, in the chosen depth.
3. User and group properties with update methods.
4. Decisions: merges made by the parameterization test, the batch approach chosen, and why. One line each.
5. Problems: limit violations, events with no use case, existing events reused, extended, or made redundant.

In chat, show the event list and the file path. Offer the format step below, and `tracking-plan-review` for a second look.

Implementation priority (P0/P1/P2), where to instrument each event in the code, and a QA checklist only when the user asks or the product has no tracking yet.

## Optional: format for a platform

When the user names a platform or asks for payloads, code, or an export, read `references/platform-formats.md` and produce for each target platform:

1. A name mapping table (source name → platform name → transformation) for every renamed event or property.
2. A sample payload per event, with user property updates.
3. SDK snippets for track, identify, and group calls, in JavaScript/TypeScript unless the user names a language.
4. On request: a spreadsheet-style table, a JSON Schema per event, or a Segment Protocols tracking plan.

Only GA4 payloads convert booleans to 0/1 and arrays to strings. The spec stays typed.
