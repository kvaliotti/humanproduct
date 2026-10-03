# Platform Formatting

Used by `event-definition`'s optional format step. Limits (lengths, counts, reserved names, value types) live in `${CLAUDE_PLUGIN_ROOT}/references/platform-constraints.md`; check there, not here. This file covers only conventions and gotchas. Write the SDK calls from your own knowledge of each platform's current SDK.

## Event name conversion

| Source convention | Amplitude | Mixpanel | PostHog | Segment | GA4 |
|---|---|---|---|---|---|
| Area - Verb (Title Case) | Keep | Keep | snake_case (recommended) | Keep | snake_case, shorten to GA4's limit |
| Object Action (Title Case) | Keep | Keep | Keep or snake_case | Keep (native) | snake_case, shorten to GA4's limit |
| snake_case | Keep or Title Case | Title Case (recommended) | Keep (native) | Title Case | Keep (native) |

When shortening for GA4, drop the area prefix before cutting words from the action, and show every rename in a mapping table: source name, platform name, transformation applied.

## Property names

- Amplitude, Mixpanel, PostHog, GA4: snake_case.
- Segment: camelCase, per the Segment spec.

## Gotchas worth stating in the output

- **Mixpanel:** send `$insert_id` so retries don't double-count. Case-sensitive event names mean one typo creates a new event.
- **PostHog:** set person properties through `$set` / `$set_once` on the event or via identify. With `person_profiles: 'identified_only'`, anonymous events create no person profile.
- **Amplitude:** use `setOnce` for first-time values and `add` for counters in the Identify call.
- **GA4:** booleans become 0/1 and arrays become comma-separated strings in the GA4 payload only. Keep the spec typed as boolean/array. Register custom parameters in admin or they won't show in reports. Measurement Protocol needs `engagement_time_msec` for events to count toward engagement.
- **Segment:** destinations convert some names and properties automatically but not all. List which properties need a mapping per destination, and tell the user to verify the data in each destination after setup.

## GA4 recommended events

When an event matches one of these, use the GA4 name and parameter names so built-in reports work.

| Concept | GA4 event | Required parameters |
|---|---|---|
| Signed up | sign_up | method |
| Logged in | login | method |
| Purchase completed | purchase | currency, transaction_id, value, items |
| Content shared | share | method, content_type, item_id |
| Search performed | search | search_term |
| Tutorial completed | tutorial_complete | (none) |

## Segment as the CDP

Format events for Segment, then show what each destination receives:

```
Task Created / creationMethod
→ Amplitude: Task Created / creation_method (may need mapping)
→ PostHog:   task_created / creation_method
→ GA4:       task_created / creation_method (check length limit)
```
