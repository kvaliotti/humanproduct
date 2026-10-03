# Naming Conventions and Current State

Shared by `event-definition` and `tracking-plan-review`.

## Find the existing tracking first

Before naming or reviewing anything, find out what is already tracked. Ask only for what isn't clear.

- **Analytics tool connected via MCP** (Amplitude, Mixpanel, PostHog, GA4): pull existing event names and properties.
- **Codebase available:** grep for tracking calls, e.g. `track(`, `capture(`, `logEvent(`, `analytics.track`, `posthog.capture`, `mixpanel.track`, `amplitude.track`, `gtag('event'`. Record each event's name, properties, and the file where it fires.
- **Otherwise:** ask for the tracking plan, a spreadsheet, or a list of event names.

Also confirm the target platform(s). They set the constraints in `${CLAUDE_PLUGIN_ROOT}/references/platform-constraints.md`.

## Detect and match, don't impose

If events exist, detect the convention from them:

1. Casing: Title Case, snake_case, camelCase, SCREAMING_SNAKE_CASE
2. Separator: spaces, underscores, dots, hyphens, " - "
3. Structure: Object-Action, Action-Object, Area-Action, Area-Subarea-Action
4. Tense: past, present, imperative

State the detected convention and ask the user to confirm. Use it for every new event. If the existing events are inconsistent, report the dominant pattern with the share that follows it, and recommend one standard. Don't silently pick one.

## Default when nothing exists

```
[Area] - [Subarea (optional)] - [Verb in Past Tense] [Object/Modifier]
```

Examples: `Tasks - Created Task`, `Emails - Reply - Sent New Reply`, `Settings - Notifications - Updated Notification Preferences`.

Use a subarea only when the area has several distinct zones (Settings: Notifications, Profile, Billing) or two events would otherwise be ambiguous. Skip it when it repeats itself: `Tasks - Opened Task List`, not `Tasks - Task List - Opened Task List`.

Common alternatives: Object-Action in Title Case (`Product Viewed`, the Segment spec), snake_case object_action (`product_viewed`, required by GA4), and dot hierarchies (`checkout.payment.completed`; check the platform doesn't treat dots specially).

## Properties

- Pick one property naming style and keep it everywhere: snake_case by default, camelCase for Segment.
- The same concept gets the same name on every event: not `source` here and `origin` there.
- Property values for categories: one casing, documented values, `other`/`unknown` for catch-alls rather than null.
