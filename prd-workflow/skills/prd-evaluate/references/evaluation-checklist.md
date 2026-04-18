# PRD Evaluation Checklist

Detailed questions to ask for each evaluation category. Work through every applicable category for the PRD being evaluated. Skip categories that genuinely don't apply (e.g., scheduling gaps for a static content feature).

## 1. State & lifecycle gaps

For every entity/object in the PRD:

- What is its initial state when created? What defaults are set?
- What are all possible state transitions? Are they documented?
- What happens when it's deleted? Soft delete or hard delete?
- Can the action be undone? Within what timeframe?
- What happens to dependent objects when the parent changes state?
- Who can trigger each state transition?
- Is there an audit trail / history of state changes?
- What happens if the entity is in an unexpected state? (corrupted data, manual DB edit)

**Common miss:** Creation side effects. When entity A is created, what other entities need to be created, updated, or notified? Example: creating a calendar event should add the creator as an accepted attendee, create a notification for invitees, and block the time on the creator's calendar.

## 2. Empty, zero, and boundary states

For every list, collection, or count in the PRD:

- What does the UI show when the list is empty? (empty state design)
- What happens on first use before any data exists?
- Is there a maximum number of items? What happens at the limit?
- What about zero quantities, zero-length strings, null values?
- What if only one item exists? (singular vs. plural UI)
- What does "no results" look like in search/filter contexts?
- What happens with very long text, very large numbers, or very large files?

**Common miss:** First-time user experience. The PRD describes the feature working with data, but not what happens the very first time when there's nothing there.

## 3. Multi-actor & permission gaps

For every action in the PRD:

- Who else can see this? Who can edit it? Who can delete it?
- What happens if two users edit simultaneously?
- What does a viewer (non-editor) see differently from an editor?
- What about admin vs. regular user views?
- What if the user's permissions change while they're mid-flow?
- What if the creator/owner leaves the organization or is deactivated?
- Can actions be delegated? Can permissions be shared?
- What about external users / guests? What's their view?

**Common miss:** Ownership transfer and orphaned resources. When a user is deactivated, what happens to everything they own?

## 4. Error & failure handling

For every action that involves a network call, data write, or external service:

- What error message does the user see on failure?
- Is there automatic retry? How many times? With what backoff?
- What happens to data already entered if the submission fails partway?
- Can the user recover without starting over?
- What if the external service is down for hours?
- What's the timeout? What happens when it's exceeded?
- Are there rate limits? What does the user see when rate limited?
- What happens on validation error? Which fields are highlighted? What messages appear?

**Common miss:** Partial failure in multi-step operations. "Save the form" might involve writing to 3 different services — what if the 2nd one fails?

## 5. Notification & communication gaps

For every significant action or state change:

- Who gets notified? (direct actors, observers, admins)
- Through what channel? (in-app, email, push, SMS)
- Can they act directly from the notification? (deep link, action button)
- Can notifications be configured, muted, or turned off?
- What's the notification content? (especially: does it give enough context to be useful without opening the app?)
- What about digest/batching for high-frequency events?
- What about "quiet hours" / do-not-disturb respect?

**Common miss:** The notification itself is specified, but not what happens when the user taps/clicks it. Where do they land? What state is the app in?

## 6. Temporal & scheduling gaps

For any feature involving time, dates, or scheduling:

- How are time zones handled? Whose time zone is displayed?
- What about daylight saving time transitions?
- What happens with recurring events when one instance is modified?
- What's the conflict resolution for overlapping events/bookings?
- Is there a deadline or expiration? What happens when it passes?
- What about past dates? Can users create/modify things in the past?
- What's the minimum/maximum time range or duration?
- How does the feature handle "all day" vs. specific time?

**Common miss:** The PRD mentions scheduling but doesn't specify conflict handling or what happens when a time slot becomes unavailable between selection and confirmation.

## 7. UI/UX micro-interactions

For every user-facing action:

- What's the loading state while waiting for a response?
- Is there a confirmation dialog before destructive actions?
- What feedback does the user get on success? (toast, animation, redirect)
- What happens when the user clicks the back button mid-flow?
- What happens when the user refreshes the page mid-flow?
- Can they cancel a long-running operation?
- Is there a progress indicator for multi-step flows?
- What's the keyboard shortcut, if any?
- Does the UI update optimistically or wait for server confirmation?

**Common miss:** Back button and refresh behaviour. Multi-step flows often break if the user navigates backward unexpectedly.

## 8. Data integrity & consistency

For every data relationship:

- What happens to child records when a parent is deleted?
- Are there circular references possible? How are they prevented?
- What's displayed when a referenced entity no longer exists?
- How is data consistency maintained across cached and live views?
- What about data migration from the old experience to the new one?
- Are there data format changes that affect existing records?

**Common miss:** Display of deleted references. "Assigned to: [Deleted User]" — the PRD doesn't specify what this looks like.

## 9. Onboarding & progressive disclosure

For new features or complex flows:

- How does the user discover this feature for the first time?
- Is there a walkthrough, tooltip, or contextual help?
- Can the onboarding be dismissed and recalled later?
- What's the minimal viable path for a new user to get value?
- Are advanced features hidden until the user is ready?

**Common miss:** Feature discovery. The PRD builds the feature but doesn't specify how users learn it exists.

## 10. Accessibility & inclusivity

- Can the entire flow be completed with keyboard only?
- Are there appropriate ARIA labels for screen readers?
- Do colour-coded elements have non-colour alternatives?
- Is the text readable at 200% zoom?
- Does the flow work on mobile / small screens?
- Are there time-limited interactions that need extensions?
- Is the language inclusive and free of jargon?

## 11. Performance & scale implications

- What happens with 10x the expected data volume?
- Is pagination or infinite scroll needed? What's the page size?
- Are there expensive operations that should be async?
- What's the expected response time? Is it specified?
- Should there be client-side caching? What's the invalidation strategy?
- Are there background jobs? What's their failure handling?

**Common miss:** Scale of adjacent data. The feature might work for 10 items but the PRD doesn't consider what happens at 10,000.

## 12. Integration & system boundary gaps

For every external system interaction:

- What's the API contract? (request/response format, versioning)
- What happens when the external system changes its API?
- What data is sent externally? Any privacy/PII concerns?
- Is there a webhook? What's the payload? What triggers it?
- What's the authentication/authorization flow with external systems?
- What about rate limits and quotas from external services?

**Common miss:** Webhook reliability. The PRD specifies a webhook but doesn't address retry logic, idempotency, or what happens on delivery failure.
