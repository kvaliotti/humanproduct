# Event Design Decisions

Shared by `event-definition` and `tracking-plan-review`.

## The parameterization test: one event with properties, or several events?

Ask four questions in order:

1. **Same action?** Creating a task from the Today view, the Tasks list, or by AI from an email is one action. Creating vs completing a task are two.
2. **Same result?** Does the system end up in the same state? Export as CSV vs PDF produces different artifacts; split them only if the format matters to analysis.
3. **Can the platform segment by the property** to answer every question separate events would? Check funnels, retention, alerts, and composite metrics on a property-filtered event. GA4 is the usual "no".
4. **Clear to the analyst?** `creation_source` = `today_view` / `ai_from_email` is clear. `source` = `1` / `2` / `3` is not.

| Same action | Same result | Can segment | Clear | Decision |
|---|---|---|---|---|
| Yes | Yes | Yes | Yes | One event + property |
| Yes | Yes | Yes | No | One event; rename the property |
| Yes | Yes | No | - | Separate events (platform limit) |
| Yes | No | - | - | Separate events |
| No | - | - | - | Separate events |

## The actor is almost always a required property

When the user or the system can do the same action, use one event with an `actor` / `initiated_by` property (`user`, `system`, `ai`). A user-created task means engagement. An AI-created task means the system delivered value. Same database row, different behaviour. Track system-initiated actions (AI output, notifications sent, auto-renewals, background jobs) as rigorously as user actions; they often are the product's core value.

## What events can't capture

- **States and durations.** "User is confused" is not an event. "Viewed help 4 times in 2 minutes" is a sequence you interpret in analysis.
- **Absence.** Nothing fires when a user doesn't act. "Signed up but never created a task" comes from comparing event populations.
- **Gradual change.** Sentiment and skill growth have no discrete moment. Events give proxies at best.

Some questions are better answered by session recordings, surveys, or derived metrics than by more events. Say so instead of inventing an event.

## Batch actions (AI creates 5 tasks at once)

- **A. One event per item.** Easy counting and per-item properties; one AI action looks like five user actions in funnels.
- **B. One batch event** with `count`. Accurate as one action; per-item properties are lost.
- **C. Both, linked by `batch_id`,** merged with composite events. Safest for funnels and engagement. Needs composite events (Amplitude, Mixpanel, PostHog Actions); not GA4 or Segment alone.
- **D. One event per item with batch metadata** (`batch_id`, `batch_size`, `batch_index`, `creation_method`). Most flexible for counting; large batches inflate funnel steps.

No default. If the key analyses are funnels or engagement depth, lean C. If they are item counts and segmentation, lean D. Without composite events, D. Present the trade-off against the user's actual questions and let them choose.

## The dashboard test

For each event name: what chart, dashboard, or alert uses it, what question it answers, and who looks at it. If none, the event is premature or redundant. Foundational lifecycle events (sign up, login) pass with one concrete future use.

There is no right event count. Event count is not the guardrail; traceability is. When the count feels high, check for the same action in different contexts, intermediate steps that answer no unique question, and duplicates of existing events.

## User, event, or group property

- **Event property:** specific to this occurrence, or needed point-in-time ("what plan were they on when they did this?").
- **User property:** the user's current state, used to segment any event (plan, role, signup date).
- **Group property:** describes the account or workspace (company plan, seats).

Common mistakes:
- `plan` sent on every event instead of as a user property. Wasteful and drifts out of sync.
- Per-action values stored as user properties. They overwrite and lose history.
- `set` instead of `set_once` for values that must never change (`first_signup_source`).

## Property value rules

- Booleans start with `is_` / `has_` and use true/false. Never "yes"/"no" strings.
- Put units in the name when ambiguous: `duration_seconds`.
- "Not applicable" is null, never 0 when 0 is a real value.
- Dates in ISO 8601 with timezone, preferably UTC.

## Changing existing events

- **Safe:** adding an optional property or a new enum value.
- **Needs a documented cutover date:** making a property required; changing a property's type (use a new name and deprecate the old one); replacing a property (keep both during the transition).
- **Breaking:** renaming, removing, or splitting an event breaks every dashboard, funnel, and saved report that uses it. Either fire old and new in parallel for a transition, merge them with a composite event, or accept the historical break for low-stakes events. Deprecate before removing.

Track status on each event: `proposed`, `active`, `deprecated` (with date and replacement), `removed`.

## PII

Tag each property PII (email, name, phone, IP, device ID, precise location), quasi-PII (identifying in combination: zip code, job title at a small company), or non-PII. Each PII property needs a reason it must be in analytics, a consent check, and a decision on which destinations may receive it.
