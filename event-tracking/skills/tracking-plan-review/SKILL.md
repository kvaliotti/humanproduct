---
name: tracking-plan-review
description: >
  Review, audit, and improve an existing analytics tracking plan or event
  taxonomy. Use when the user says "review my tracking plan", "audit my
  events", "check event coverage", "review my analytics", "are my events
  right", "event taxonomy review", "tracking plan audit", "clean up my
  events", "find gaps in my tracking", "review event naming", or provides
  an existing set of events and wants feedback on completeness, naming
  consistency, redundancy, or alignment with analytical goals.
---

# Tracking Plan Review

Audit an existing tracking plan for naming consistency, coverage gaps, redundancy, property quality, and platform compliance.

## Inputs

Accept the tracking plan in any format:
- Spreadsheet / table of events
- List of event names
- Export from an analytics tool (via ~~analytics tool MCP)
- Code grep of tracking calls from a codebase
- A document describing what's tracked
- Informal description from the user

Also request (if not provided):
- Target analytics platform(s)
- Analytical questions / use cases the tracking should answer (if the analytics-use-cases skill output exists, use it)
- Product description or key user flows

## Audit Dimensions

### 1. Naming Consistency

Check every event name for:
- **Consistent casing**: Are all events in the same case? Flag mixed casing (e.g., "Task Created" alongside "task_deleted")
- **Consistent structure**: Do all names follow the same pattern? Flag structural inconsistencies (e.g., "Task Created" alongside "Created a New Task")
- **Consistent tense**: Are all verbs in past tense? Flag present tense or imperative (e.g., "Create Task" instead of "Task Created" or "Created Task")
- **Consistent separators**: Same separator throughout? Flag mixed separators (e.g., spaces vs underscores vs dots)
- **Naming convention detected**: State the detected convention and note any deviations

Score: % of events conforming to the dominant convention

### 2. Coverage Analysis

Map events against:
- **User lifecycle stages**: Awareness → Acquisition → Activation → Engagement → Retention → Revenue → Referral. Flag gaps.
- **Key user flows**: For each major flow, verify that entry, key steps, and completion/abandonment are tracked.
- **Feature coverage**: For each product feature, verify at least basic usage tracking exists.
- **Error/failure states**: Are failure events tracked alongside success events?

Score: % of critical user flows with adequate event coverage

### 3. Redundancy Detection

Identify:
- **Duplicate events**: Events that track the same action with different names (e.g., "Task Created" and "New Task Added")
- **Events that should be parameterized**: Events that could be a single event with a property (e.g., "Clicked Save Button", "Clicked Cancel Button", "Clicked Delete Button" → one "Button Clicked" event with a "button_name" property)
- **Over-instrumented flows**: Flows with events for every micro-interaction when only key steps need tracking
- **Orphan events**: Events that don't serve any identifiable analytical purpose

Apply the parameterization test from the decision framework for each candidate merge.

Score: Number of events that could be consolidated / total events

### 4. Property Quality

For each event's properties:
- **Consistency**: Is the same concept named the same way across events? (e.g., "source" vs "origin" vs "referrer" for the same concept)
- **Completeness**: Do events have enough properties to answer the analytical questions? Missing common properties (like source, variant, method)?
- **Type consistency**: Is the same property always the same type? (e.g., "count" is a number everywhere, not sometimes a string)
- **PII flag**: Are PII properties identified? Are any unmarked properties PII?
- **Value documentation**: Are categorical property values documented?
- **Naming standard**: Do property names follow a consistent convention?

Score: % of properties conforming to standards

### 5. Platform Compliance

Check against the target platform's constraints:
- Event name length and format requirements
- Number of event types vs platform limit
- Properties per event vs limit
- Property name/value length limits
- Data type support (arrays, nested objects)
- Reserved names conflicts

Read the platform-constraints reference from the event-definition skill (`skills/event-definition/references/platform-constraints.md`) for platform-specific limits. Key thresholds to check: GA4 has 500 event types, 25 params/event, 40-char names (snake_case only); Mixpanel has 255 properties/event, 255-char values; Amplitude has 2,000 event types. See that file for the full matrix.

Score: Number of violations / total events

### 6. User Property Assessment

Review user properties for:
- Properties that should be user properties but are only event properties (e.g., "plan" attached to every event but not set as a user property)
- User properties with wrong update method (e.g., "first_login_date" using set instead of set_once)
- Missing computed/derived user properties (e.g., no "total_tasks_created" counter)
- Group/account properties missing for B2B products

### 7. Firing Condition Clarity

For each event, assess:
- Is the firing condition specific enough that two engineers would implement it identically?
- Are edge cases addressed? (auto-save vs manual save, retry vs first attempt, etc.)
- Are exclusion conditions stated?

Score: % of events with unambiguous firing conditions

## Output Format

### Summary Scorecard

| Dimension | Score | Status |
|---|---|---|
| Naming Consistency | X% | Pass/Warn/Fail |
| Coverage | X% | Pass/Warn/Fail |
| Redundancy | X events mergeable | Pass/Warn/Fail |
| Property Quality | X% | Pass/Warn/Fail |
| Platform Compliance | X violations | Pass/Warn/Fail |
| User Properties | X issues | Pass/Warn/Fail |
| Firing Conditions | X% clear | Pass/Warn/Fail |

Thresholds: Pass ≥ 90%, Warn 70-89%, Fail < 70%

### Detailed Findings

For each finding:
```
FINDING: [Short title]
SEVERITY: Critical / Warning / Info
DIMENSION: [Which audit dimension]
EVENTS AFFECTED: [List of event names]
ISSUE: [What's wrong]
RECOMMENDATION: [Specific fix]
EFFORT: Low / Medium / High
```

Sort by severity (Critical first), then by effort (Low first within each severity).

### Recommended Changes

Group recommendations into:
1. **Quick wins** (Critical + Low effort) — fix immediately
2. **Important improvements** (Critical + Medium/High effort) — plan for next sprint
3. **Nice to have** (Warning/Info) — address when convenient
4. **Structural changes** (Convention changes, event merges) — requires coordination

### Revised Tracking Plan

If the user requests it, produce an updated tracking plan incorporating all recommendations, using the same format as the event-definition skill output.
