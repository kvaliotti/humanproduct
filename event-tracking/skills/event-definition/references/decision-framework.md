# Event Design Decision Framework

## The Parameterization Test: One Event with Properties vs. Multiple Events

When the same or similar action happens in different contexts, apply these four questions in order:

### Question 1: Is this the same action?
If fundamentally the same action happens (creating, viewing, clicking, submitting), regardless of where, why, or who initiated it, it's a candidate for a single event. This applies to both user-initiated and system-initiated actions.

**Same action examples:**
- Creating a task from the Today view vs. from the Tasks list vs. via AI from an email → all "task creation." The actor and trigger are different, but the action and result are the same. Use properties to distinguish: `actor` (user / system), `creation_method` (manual / ai_from_email / ai_from_meeting).
- Sending a message from a thread vs. from a channel vs. from DMs → all "message sending"

**Different action examples:**
- Creating a task vs. completing a task → different verbs, different events
- Viewing a dashboard vs. editing a dashboard → different actions, different events

**Important: the actor is almost always an essential property.** When the same action can be performed by the user or by the system, a single event with an `actor` or `initiated_by` property (values: "user", "system", "ai", etc.) is usually the right design. The behavioral meaning is completely different — user-created tasks indicate engagement, AI-created tasks indicate system value delivery — but they're the same action and the same result, so they pass the parameterization test. The `actor` property lets analysts segment by who did it.

### Question 2: Is the result the same?
After the action, does the system end up in the same state regardless of context?

**Same result examples:**
- Task created from any source → a new task exists in the system
- User invited from settings vs. from a project → a new invitation exists

**Different result examples:**
- "Save" as auto-save vs. "Save" as explicit save → may have different data integrity implications worth tracking separately
- "Export" as CSV vs. "Export" as PDF → different output artifacts, potentially separate events if the format choice is analytically significant

### Question 3: Can the target analytics system segment by properties to answer every question you'd answer with separate events?
This is the practical test. If you can filter, break down, and group by a property value to get the same insight you'd get from separate events, use one event.

**Check specifically:**
- Can you build a funnel with property-filtered events? (Most modern tools: yes)
- Can you create a retention chart filtered by property? (Most: yes)
- Can you set up alerts/notifications on a specific property value? (Varies)
- Can you create a composite metric from property-filtered events? (Amplitude and Mixpanel: yes. GA4: limited)

### Question 4: Will it be clear to the person using analytics how to segment?
The property name and values must be self-explanatory. If someone opening the analytics tool wouldn't immediately know to filter by a specific property to get a specific insight, consider separate events.

**Clear:** Event "Task Created" with property "creation_source" having values "today_view", "tasks_list", "ai_from_email", "ai_from_meeting"
**Unclear:** Event "Task Created" with property "source" having values "1", "2", "3", "4"
**Unclear:** Event "Task Created" with property "context" having values that overlap with other "context" properties on other events

### Decision Matrix

| Same action? | Same result? | Can segment? | Clear to analyst? | Decision |
|---|---|---|---|---|
| Yes | Yes | Yes | Yes | **One event + properties** |
| Yes | Yes | Yes | No | One event, but **rename the property** to make it self-explanatory |
| Yes | Yes | No | - | **Separate events** (system limitation) |
| Yes | No | - | - | **Separate events** (different outcomes) |
| No | - | - | - | **Separate events** (different actions) |

### The Count/Batch Problem

When an action can produce one or many results (e.g., AI creates 5 tasks from a meeting):

**Approach A: One event per item**
- Event: "Task Created" fires 5 times
- Pro: Each task gets its own properties (title, priority, etc.)
- Pro: Simple counting — total tasks = count of events
- Con: A single AI action looks like 5 separate user actions in funnels

**Approach B: One batch event**
- Event: "Tasks Batch Created" fires once with property "count": 5
- Pro: Represents the single user action accurately
- Con: Harder to count total tasks (need to sum the count property)
- Con: Individual task properties are lost

**Approach C: Both (recommended when the analytics system supports composite events)**
- Fire "Task Created" for each individual task (with a "batch_id" property linking them)
- Fire "Tasks Batch Created" once for the batch (with "count" and "source")
- Use composite events in the analytics tool to build dashboards that merge both perspectives
- This approach works in Amplitude (custom events), Mixpanel (custom events), PostHog (actions)
- This does NOT work well in GA4 (no composite events) or Segment alone (routing only)

**Approach D: One event per item with batch metadata**
- Fire "Task Created" for each task
- Include properties: "batch_id" (to group), "batch_size" (total in this batch), "batch_index" (position), "creation_method" (e.g., "ai_batch_from_meeting")
- Pro: Maximum flexibility in analytics — can count individual tasks, identify batches, and analyze batch patterns
- Con: Slightly more complex implementation
- Con: If batch sizes are large (e.g., AI creates 50 tasks), this fires 50 events that can inflate funnel step counts and engagement metrics. Standard funnel views will show 50 separate actions, not one batch action.

**Choosing the right approach:**
There is no single default — the right approach depends on the analytical question:

- "How many total tasks exist?" → Approach A or D (count events)
- "How often does AI batch-create tasks?" → Approach B or C (need a batch-level event)
- "What's the typical batch size?" → Approach B, C, or D (need batch_size property)
- "What properties does each created task have?" → Approach A or D (need per-item properties)
- "What does the user journey look like — does batch creation inflate engagement?" → Approach C is safest (separate event for the batch action, separate events for items, composite events to merge them)

When in doubt, ask: will the individual item events distort the analyses that matter most? If the primary analysis is funnels or engagement depth, lean toward Approach C (both). If the primary analysis is item-level counting and segmentation, lean toward D.

## The Dashboard Test

For every event in the tracking plan, answer:
1. What specific chart, dashboard, or alert will use this event?
2. What question does this chart answer?
3. Who looks at this chart and how often?

If you cannot answer all three, the event is either premature (save it for later) or redundant (it duplicates insight from another event).

This does NOT mean every event must be on a dashboard today. Some events are foundational (e.g., basic lifecycle events like Sign Up, Login) and will be used across many future analyses. The test is: can you name at least one concrete analytical use?

## Right-Sizing the Event Count

There is no correct number of events per feature. A small feature might need 2; a large feature that functions as a small product might need 25+. The event count should match the analytical need, not an arbitrary cap.

That said, two useful reference points from industry data:
- For a typical product, 20-30 core events answer ~90% of recurring analytical questions. This doesn't mean cap at 30 — it means if you have 30+ events, every one beyond that should clearly serve a question the first 30 don't.
- When event counts feel high, it's worth running a consolidation check — not to force a reduction, but to catch accidental duplication or events that could be parameterized without losing analytical power.

**Consolidation check (apply when helpful, not as a gate):**
- Are any of these the same action in different contexts? (Candidate for parameterization)
- Are any of these intermediate steps that don't answer a unique question? (Candidate for removal)
- Are any of these duplicating insight from an existing event? (Candidate for reuse)

## Event Versioning and Migration

When modifying existing events, the change type determines the migration strategy:

**Safe changes (no migration needed):**
- Adding a new optional property to an event — old events simply won't have it, which is fine for analytics (filter/breakdown will show "not set" for historical data)
- Adding new enum values to an existing property — existing values continue to work

**Moderate changes (need documentation and transition period):**
- Making an optional property required — requires a code change and coordination. Old events without the property still exist in the database. Document when the property became required so analysts know the data completeness boundary.
- Changing a property's type (e.g., string to number) — some analytics tools handle this gracefully, others don't. If changing types, use a new property name and deprecate the old one.
- Adding a new property that replaces an old one — keep both during a transition period. Document the cutover date.

**Breaking changes (need a migration plan):**
- Renaming an event — this breaks all existing dashboards, saved reports, funnels, and retention charts that reference the old name. Options: (a) create the new event and keep the old one firing in parallel for a transition period; (b) use composite/custom events in the analytics tool to merge old and new names; (c) just rename and accept the historical break (only acceptable for low-stakes events).
- Removing an event — verify nothing depends on it first. Mark as deprecated, stop firing it, but don't delete the definition immediately.
- Splitting one event into multiple — this is effectively a rename + new events. Follow the rename strategy above.

**Version tracking in the spec:**
Every event spec should have a STATUS field with one of:
- `proposed` — designed but not yet implemented
- `active` — implemented and firing in production
- `deprecated` — still firing but scheduled for removal. Include deprecation date and replacement event.
- `removed` — no longer firing. Keep in the tracking plan for historical reference with removal date.

## User Properties vs. Event Properties

### Use event properties when:
- The value is specific to this action instance (e.g., "source" of a task creation)
- The value changes with each occurrence (e.g., "page_url" on a page view)
- You need historical point-in-time analysis ("what plan was the user on when they did this?")

### Use user properties when:
- The value describes the user's current state (e.g., "plan", "role", "company_size")
- The value persists across events (e.g., "email", "signup_date", "account_type")
- You want to segment ANY event by this dimension without attaching it to every event

### Use group/account properties when:
- The value describes a team, company, or workspace rather than an individual user
- Multiple users share the same value (e.g., "company_name", "company_plan", "team_size")
- You want to analyze behavior at the organizational level

### Common mistakes:
- Putting "plan" on every event as an event property instead of a user property → wastes space, creates inconsistency risk
- Using user properties for values that change per-action → loses historical context (user property overwrites, events are immutable)
- Not using $set_once for truly immutable properties like "first_signup_source" → risks overwriting the original value

## PII Classification

Tag every property as one of:
- **PII**: Contains or could contain personally identifiable information (email, name, phone, IP, device ID, location coordinates, etc.)
- **Quasi-PII**: Could identify a person when combined with other data (zip code, birth year, job title at a small company)
- **Non-PII**: Cannot identify a person (plan type, feature used, button clicked)

PII properties require:
- Explicit justification for why this data is needed in analytics
- Consent verification (is the user's consent scope sufficient?)
- Consideration of whether the property should be excluded from certain destinations (e.g., send to internal analytics but not to third-party tools)
