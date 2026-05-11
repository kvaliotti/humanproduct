# Naming Conventions Reference

## Default Convention: Area - Subarea - Verb (Past Tense)

The default naming convention unless the user provides a different one or has an existing convention in their analytics tool or codebase.

### Structure

```
[Area] - [Subarea (optional)] - [Verb in Past Tense] [Object/Modifier]
```

- **Area**: The product area or feature domain (e.g., Tasks, Emails, Settings, Onboarding)
- **Subarea**: Optional subdivision. Only use when the area has clearly distinct functional zones. Omit when it adds no clarity.
- **Verb + Object/Modifier**: What happened, in past tense. Include modifiers when needed to distinguish from similar actions.

### Examples

| Event Name | Area | Subarea | Action |
|---|---|---|---|
| Emails - New Email - Sent New Email | Emails | New Email | Sent New Email |
| Emails - Opened Emails List | Emails | (none) | Opened Emails List |
| Emails - Reply - Sent New Reply | Emails | Reply | Sent New Reply |
| Tasks - Created Task | Tasks | (none) | Created Task |
| Settings - Notifications - Updated Notification Preferences | Settings | Notifications | Updated Notification Preferences |
| Onboarding - Completed Step | Onboarding | (none) | Completed Step |

### When to Use Subareas

Use a subarea when:
- The area contains 3+ functionally distinct zones (e.g., Settings has Notifications, Profile, Billing)
- Without the subarea, two events in the same area would be ambiguous
- The subarea represents a clear navigation or conceptual boundary in the product

Skip subareas when:
- The area is small enough that the action alone is unambiguous
- Adding the subarea creates redundancy (e.g., "Tasks - Task List - Opened Task List" should just be "Tasks - Opened Task List")

## Alternative Conventions

### Object-Action (Segment standard)
```
[Object] [Action in Past Tense]
```
Examples: Product Viewed, Account Created, Form Submitted

### snake_case Object-Action (GA4-compatible)
```
[object]_[action_past_tense]
```
Examples: product_viewed, account_created, form_submitted
Note: GA4 REQUIRES this format. Names must start with a letter, use only alphanumeric + underscore, max 40 chars.

### Dot-Separated Hierarchy
```
[area].[subarea].[action]
```
Examples: checkout.payment.completed, onboarding.step.viewed
Note: Some systems interpret dots as separators. Verify with the target platform.

## Convention Detection

When the user has existing events (from their analytics tool via MCP, from their codebase, or from a document), detect the convention by examining:

1. **Casing**: Title Case, snake_case, camelCase, SCREAMING_SNAKE_CASE
2. **Separator**: spaces, underscores, dots, hyphens, dashes with spaces
3. **Structure**: Object-Action, Action-Object, Area-Action, Area-Subarea-Action
4. **Tense**: past tense, present tense, imperative

Match the detected convention for all new events. If the existing convention is inconsistent (mixed casing, mixed separators), flag this to the user and recommend normalizing to one standard.

## Property Naming

### Human-readable (default for systems that accept it)
Property names: Title Case or Sentence case (e.g., "Task Source", "Created By")
Property values: Human-readable (e.g., "Manual from Email", "AI Background")

### snake_case (for systems that require it, or when integrating with code)
Property names: snake_case (e.g., "task_source", "created_by")
Property values: snake_case (e.g., "manual_from_email", "ai_background")

### Platform-specific rules
- **Amplitude**: Accepts any format. Recommend human-readable for events, snake_case for properties that will be used programmatically.
- **Mixpanel**: Case-sensitive. Title Case for events, snake_case for properties is most common. Be consistent.
- **PostHog**: Accepts any format. Commonly uses snake_case for both events and properties.
- **Segment**: Object-Action in Title Case for events. camelCase for properties (their spec standard).
- **GA4**: snake_case ONLY. No spaces, no special characters, must start with alphabetic character. Max 40 chars for event names, 40 chars for parameter names.
