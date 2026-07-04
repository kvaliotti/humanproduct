# PRD Evaluation Checklist

Highest-value questions per category. Work through every applicable category for the PRD being evaluated. Skip categories that genuinely don't apply (e.g., scheduling gaps for a static content feature).

## 1. State & lifecycle gaps

- What is its initial state when created, and what defaults are set?
- What happens when it's deleted — soft or hard delete, and can it be undone?
- What happens to dependent objects when the parent changes state?

**Common miss:** Creation side effects. When entity A is created, what other entities need to be created, updated, or notified? Example: creating a calendar event should add the creator as an accepted attendee, create a notification for invitees, and block the time on the creator's calendar.

## 2. Empty, zero, and boundary states

- What does the UI show when the list is empty, or on first use before any data exists?
- Is there a maximum number of items, and what happens at the limit?
- What about zero quantities, null values, or a single item (singular vs. plural UI)?

**Common miss:** First-time user experience. The PRD describes the feature working with data, but not what happens the very first time when there's nothing there.

## 3. Multi-actor & permission gaps

- Who else can see, edit, or delete this — and what does a viewer see differently from an editor?
- What happens if two users edit simultaneously, or a user's permissions change mid-flow?
- What happens to a resource when its creator/owner leaves the organization or is deactivated?

**Common miss:** Ownership transfer and orphaned resources. When a user is deactivated, what happens to everything they own?

## 4. Error & failure handling

- What error message does the user see on failure, and is there automatic retry?
- What happens to data already entered if the submission fails partway — can the user recover without starting over?
- What's the timeout, and what does the user see when rate-limited or the service is down?

**Common miss:** Partial failure in multi-step operations. "Save the form" might involve writing to 3 different services — what if the 2nd one fails?

## 5. Notification & communication gaps

- Who gets notified, through what channel, and can they act directly from the notification (deep link)?
- Is the notification content enough to be useful without opening the app?
- Can notifications be configured, muted, or batched for high-frequency events?

**Common miss:** The notification itself is specified, but not what happens when the user taps/clicks it. Where do they land? What state is the app in?

## 6. Temporal & scheduling gaps

- How are time zones and daylight saving handled, and whose time zone is displayed?
- What's the conflict resolution for overlapping events/bookings, especially between selection and confirmation?
- Is there a deadline or expiration, and what happens when it passes?

**Common miss:** The PRD mentions scheduling but doesn't specify conflict handling or what happens when a time slot becomes unavailable between selection and confirmation.

## 7. UI/UX micro-interactions

- What's the loading state, and is there a confirmation dialog before destructive actions?
- What feedback does the user get on success, and can they cancel a long-running operation?
- What happens when the user hits back or refreshes mid-flow?

**Common miss:** Back button and refresh behaviour. Multi-step flows often break if the user navigates backward unexpectedly.

## 8. Data integrity & consistency

- What happens to child records when a parent is deleted?
- What's displayed when a referenced entity no longer exists?
- How is consistency maintained across cached and live views, and what about migrating existing records?

**Common miss:** Display of deleted references. "Assigned to: [Deleted User]" — the PRD doesn't specify what this looks like.

## 9. Onboarding & progressive disclosure

- How does the user discover this feature for the first time?
- Is there a walkthrough or contextual help, and can it be dismissed and recalled later?

**Common miss:** Feature discovery. The PRD builds the feature but doesn't specify how users learn it exists.

## 10. Accessibility & inclusivity

- Can the entire flow be completed with keyboard only, with appropriate ARIA labels for screen readers?
- Do colour-coded elements have non-colour alternatives, and is the text readable at 200% zoom?
- Does the flow work on mobile / small screens?

## 11. Performance & scale implications

- What happens with 10x the expected data volume?
- Is pagination or infinite scroll needed, and what's the page size?
- Are there background jobs or expensive async operations, and what's their failure handling?

**Common miss:** Scale of adjacent data. The feature might work for 10 items but the PRD doesn't consider what happens at 10,000.

## 12. Integration & system boundary gaps

- What's the API contract, and what happens when the external system changes its API?
- Is there a webhook — what's the payload, what triggers it, and what about retries/idempotency on failure?
- What about rate limits and quotas from external services?

**Common miss:** Webhook reliability. The PRD specifies a webhook but doesn't address retry logic, idempotency, or what happens on delivery failure.
