---
name: event-definition
description: >
  Define specific analytics events with names, properties, firing conditions,
  and user properties for a product or feature. Use when the user says "define
  events for [feature]", "create event spec", "what events do I need", "event
  specification", "tracking spec", "define tracking for [feature]", "create
  event taxonomy", "event properties for [feature]", "specify events", or has
  analytical use cases ready and needs to turn them into concrete event
  definitions. Also use when the user provides a PRD, feature spec, or user
  flow and wants events derived from it.
---

# Event Definition

Turn analytical use cases (or a feature description) into concrete event specifications with names, properties, firing conditions, and user property updates.

## What Events Are (and Aren't)

Events are windows into behavior — they help us understand what is happening. They are not feature documentation and they are not self-important. Two types of behavior matter:

1. **User behavior**: Actions the user takes (creates a task, opens a page, clicks a button)
2. **System behavior that affects the user**: Actions the system takes on behalf of or in response to the user (AI creates tasks from a meeting, a notification is sent, a subscription auto-renews, a background job generates a report)

Both types are analytically important. A "Task Created" event means something very different when the user typed it vs. when AI generated it from a meeting — even though the database result is identical. The actor (user vs. system) and the trigger (manual vs. automated) are almost always essential properties because the behavioral meaning is completely different.

**What events can't track:**
- **Continuous states**: Events capture moments, not durations. "User is confused" isn't an event. "User viewed help page 4 times in 2 minutes" is a sequence of events that might indicate confusion — but the interpretation happens in analysis, not in the event itself.
- **Absence of action**: A user NOT doing something is often more analytically important than doing it — but events don't fire for things that didn't happen. Absence analysis (e.g., "signed up but never created a task") requires comparing event populations, not a single event.
- **Gradual changes**: Sentiment, satisfaction, and skill development don't produce discrete moments. Events can capture proxy signals (support ticket opened, feature used for the first time, setting changed) but not the underlying shift.

Keep these limitations in mind when mapping use cases to events. Some analytical questions are better answered by session recordings, surveys, or derived metrics than by adding more events.

## Inputs Required

Before defining events, ensure you have:

1. **Naming convention** — detected from existing events, provided by the user, or defaulting to: Area - Subarea (optional) - Verb in Past Tense with Modifiers. Read `references/naming-conventions.md` for full details.
2. **Target platform(s)** — determines constraints on names, properties, and formats. Read `references/platform-constraints.md` for limits.
3. **Analytical use cases** (ideal) — the output from the analytics-use-cases skill. OR a feature description / PRD / user flow from which to derive events.
4. **Existing events** (if any) — to avoid duplication and ensure consistency.

If analytical use cases are not available, derive them inline: identify the key user flows, infer the questions the team would need answered, then define events against those questions.

## Process

### Step 1: Map User Flows

If not already provided, outline the key flows for the feature. Include both user-initiated and system-initiated flows:

**User-initiated flow:**
```
Flow: [Flow name]
Actor: User
Steps:
1. User [action] → [system response]
2. User [action] → [system response]
3. ...
Outcome: [What the user achieved]
Alternative paths: [Error states, edge cases, branching paths]
```

**System-initiated flow:**
```
Flow: [Flow name]
Actor: System (triggered by: [what triggers it — schedule, webhook, AI, background job, external event])
Steps:
1. System [action] → [result for user]
2. System [action] → [result for user]
3. ...
Outcome: [What the user now has or sees]
User visibility: [Does the user see this happen? Is it silent? Is there a notification?]
```

System-initiated flows are easy to overlook but often represent the product's core value (AI doing work for you, automated reports, smart notifications). Track these with the same rigor as user actions — they tell you whether the system is actually delivering value.

Each step in a flow is a candidate for an event. But not every step needs an event — apply the dashboard test from `references/decision-framework.md`.

### Step 2: Define Events

For each event, produce a specification block:

```
EVENT: [Event Name — following the naming convention]
AREA: [Product area]
DESCRIPTION: [One sentence: what happened and why it matters analytically]
FIRES WHEN: [Precise trigger condition. Be specific: "User clicks Save button on the edit form AND the save succeeds" not "User saves"]
FIRES WHERE: [client | server | both — see guidance below]
DOES NOT FIRE WHEN: [Exclusions if ambiguous — e.g., "Does not fire on auto-save, only manual save"]

PROPERTIES:
| Property | Type | Required | Values | Description |
|---|---|---|---|---|
| [name] | string/number/boolean/datetime | Yes/No | [enum values or format] | [What this property captures] |

USER PROPERTIES UPDATED:
| Property | Update Method | Value | Description |
|---|---|---|---|
| [name] | set / set_once / increment | [value or formula] | [Why this updates] |

GROUP PROPERTIES UPDATED: (if B2B)
| Property | Update Method | Value | Description |
|---|---|---|---|

USE CASES SERVED: [List which analytical questions this event answers — trace back to use cases]
PLATFORM NOTES: [Any platform-specific constraints or transformations needed]
PII: [Yes/No — if yes, which properties are PII]
STATUS: proposed
```

### Step 2b: Determine Firing Location (Client vs. Server)

For each event, decide where it fires:

**Fire server-side when:**
- The event represents a business-critical action: purchases, subscription changes, account creation, permission changes
- Data reliability matters more than speed — client-side events on web get blocked by ad blockers (15-30% data loss typical)
- The event is triggered by a backend process: webhook receipt, scheduled job, background AI task, payment processor callback
- The event needs to be tamper-proof (e.g., revenue events, compliance-related actions)

**Fire client-side when:**
- The event captures UI interaction: button clicks, page views, form interactions, navigation
- The event needs client-only context: viewport size, scroll depth, client-side feature flag variant, element position
- Speed matters more than completeness (e.g., real-time engagement tracking where 15-30% loss is acceptable)

**Fire both when:**
- You need client context (which page, which element) AND server reliability (order completion). Fire a client-side event for the user interaction, fire a server-side event for the confirmed outcome. Link them with a shared ID property.

### Step 2c: Check for Autocapture Overlap

If the target platform has autocapture (PostHog, Amplitude, GA4 enhanced measurement):

1. Check if autocapture already captures this interaction. PostHog autocaptures clicks, pageviews, and form submissions. GA4 enhanced measurement tracks scrolls, outbound clicks, site search, video engagement, file downloads.
2. If autocapture covers it, ask: does the autocaptured event have sufficient properties for the analytical question? Autocaptured events have generic properties (element text, URL) but lack business-context properties (task type, plan tier, source view).
3. If autocapture has the data you need, don't duplicate with a custom event. Reference the autocaptured event in the tracking plan and note any required Actions/composite event configuration.
4. If autocapture lacks needed properties, define a custom event. Note in the spec that autocapture should be considered for suppression on this specific element to avoid double-counting, or that analysis should filter out one of the two.

### Step 3: Apply Decision Framework

For every event, run the parameterization test from `references/decision-framework.md`:

1. **Same action?** — Check if another event already captures the same action in a different context
2. **Same result?** — Check if the outcome is identical regardless of context
3. **Can segment?** — Verify the target platform can filter/break down by the distinguishing property
4. **Clear to analyst?** — Ensure the property name and values are self-explanatory

If the answer to all four is "yes," merge into one event with a property. Present the merge decision to the user with reasoning.

### Step 4: Handle Batch/Bulk Actions

When an action can produce multiple results (e.g., AI creates 5 tasks from a meeting):

Read the batch/count section in `references/decision-framework.md` for four approaches (A through D) with trade-offs.

There is no universal default — the right approach depends on the analytical questions:
- If the primary analyses are funnels or engagement flows, individual item events will inflate step counts. Lean toward Approach C (both a batch event and per-item events, linked by batch_id, with composite events to merge them in the analytics tool).
- If the primary analyses are item-level counting and segmentation, Approach D (one event per item with batch metadata) gives maximum flexibility.
- If the analytics tool doesn't support composite events (GA4, Segment-only), Approach D is the safest single-approach option.

Present the trade-off to the user with their specific analytical questions in mind, and let them choose.

### Step 5: Define User Properties

Review all events and determine if any should update user properties. Read `references/decision-framework.md` (User Properties vs Event Properties section) and `references/property-patterns.md` for guidance.

Common triggers for user properties:
- First-time actions → set_once (e.g., first_task_created_at)
- Cumulative counters → increment (e.g., total_tasks_created)
- State changes → set (e.g., plan, role, onboarding_completed)
- Lifecycle milestones → set_once (e.g., activation_date)

### Step 6: Validate Against Constraints

Check every event and property against the target platform's constraints from `references/platform-constraints.md`:

- Event name length and format
- Number of event types (will this push us over the limit?)
- Properties per event
- Property name/value lengths
- Supported data types
- Reserved names

Flag violations and propose fixes.

### Step 7: Cross-Reference Existing Events

If existing events are available:
- Identify events that already cover a use case → annotate "use existing event [name]" instead of defining a new one
- Identify existing events that need new properties → annotate "extend [event name] with property [name]"
- Identify existing events that the new feature's flow should reference (e.g., a generic "Page Viewed" event)
- Flag existing events that may become redundant with the new tracking

### Step 8: Generate Sample Payloads

For each event, generate a sample JSON payload for the target platform. Use the formats from `references/platform-constraints.md`.

If multiple platforms are targeted, generate one payload per platform.

## Output Format

The final tracking plan should include:

1. **Summary**: Total events defined, total user properties, total group properties, naming convention used
2. **Event Specifications**: Full spec block for each event (from Step 2)
3. **User Property Specifications**: All user properties with update methods
4. **Group Property Specifications**: All group properties (if B2B)
5. **Event Flow Diagrams**: For each user flow, annotate which events fire at which step
6. **Merge Decisions Log**: Where events were parameterized instead of multiplied, with reasoning
7. **Platform Constraint Violations**: Any flags from Step 6
8. **Existing Event References**: Events reused or extended from the existing tracking
9. **Sample Payloads**: JSON payloads per event per platform

## Implementation Guidance

When the product has no existing tracking coverage, also generate:

1. **Implementation Priority**: Order events by P0/P1/P2 priority
2. **SDK Setup Instructions**: Which SDK(s) to install, initialization code
3. **Where to Instrument**: For each event, the code location / component / API endpoint where the tracking call should be placed
4. **Testing Checklist**: How to verify each event fires correctly with correct properties
5. **QA Validation Steps**: How to validate in the analytics tool that events appear correctly

## Guardrails

The number of events should match what's needed to answer the analytical questions — no more, no less. Some features need 3 events; some large features that function as small products need 30+. The count is not the guardrail. These three tests are:

- **Every event must serve at least one use case.** This is the primary filter. If an event doesn't trace back to a specific analytical question, dashboard, chart, or alert, flag it as "no analytical purpose identified" and recommend deferral. Don't track it just because something happened — track it because someone will query it.
- **Every property must be queryable.** Don't add properties "just in case." Every property should appear in at least one filter, breakdown, or aggregation. If nobody will ever segment or filter by a property, it's noise.
- **Firing conditions must be unambiguous.** An engineer reading the spec should implement it identically to any other engineer. If the firing condition says "when the user completes the action," specify what "completes" means (button click? API success response? animation end?).

When the event count feels high, apply the parameterization test from `references/decision-framework.md` to check whether any events can be consolidated. But if the events survive all three tests above, they belong in the plan regardless of count.
