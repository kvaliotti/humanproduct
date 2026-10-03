# Platform Constraints

The single source of truth for vendor limits in this plugin. `event-definition` and `tracking-plan-review` read this file. Do not restate these numbers elsewhere.

**Vendor limits change.** Verify these figures against each platform's current official docs before relying on them for capacity planning, and say so in the output when a limit decides a design.

## Amplitude

| Constraint | Limit |
|---|---|
| Max event types | 2,000 |
| Properties per event | Unlimited |
| Property name length | 1,024 characters |
| Property value length | 100,000 characters (events), 10,000 (user properties) |
| Event name format | Any |
| Case sensitivity | Case-sensitive |
| User / group properties | Yes (identify, groups) |
| Composite events | Yes (custom events) |
| Rate limits | 100 batches/sec, 1,000 events/sec; 1,800 user property updates/hour per user |

- Revenue events have reserved properties: price, quantity, revenue, productId, revenueType.

## Mixpanel

| Constraint | Limit |
|---|---|
| Max event types | 5,000 (soft; beyond this, events are ingested but not indexed in autocomplete) |
| Properties per event | 255 |
| Property name length | 255 characters |
| Property value length | 255 characters |
| Event name format | Any |
| Case sensitivity | Case-sensitive (`sign_up` and `Sign_Up` are different events) |
| User / group properties | Yes (people and group profiles: set, set_once, increment, append, union, remove, unset) |
| Composite events | Yes (custom events) |
| Hot shard limit | One user sending >15,000 events in a 3-hour window gets rate-limited |

- Super properties attach to every event. Use them for context like app version, not for state that belongs on the profile.

## PostHog

| Constraint | Limit |
|---|---|
| Max event types | Unlimited |
| Properties per event | Unlimited |
| Property name / value length | No documented hard limit |
| Event name format | Any (snake_case common) |
| Case sensitivity | Case-sensitive |
| User properties | Yes (person properties: $set, $set_once) |
| Group analytics | Yes, up to 5 group types |
| Composite events | Yes (Actions) |
| Autocapture | Clicks, pageviews, form submissions |

## Segment (CDP)

Segment routes events; it does not store or analyse them.

| Constraint | Limit |
|---|---|
| Max event types | Unlimited |
| Properties per event | Unlimited |
| Event name format | Object Action in Title Case (Segment spec) |
| Case sensitivity | Depends on the destination |
| User / group properties | Yes (identify traits, group) |
| Composite events | No |
| Mapping limit | 50 mappings per destination instance |

- Name properties for the most restrictive destination that will receive them.
- Protocols can block events that don't match the tracking plan.

## GA4

| Constraint | Limit |
|---|---|
| Max event types | 500 distinct event names |
| Custom parameters per event | 25 |
| Event name length | 40 characters |
| Parameter name length | 40 characters |
| Parameter value length | 100 characters |
| Event name format | snake_case only. Starts with a letter. Letters, numbers, underscores. |
| Case sensitivity | Case-sensitive |
| User properties | Up to 25 custom |
| Group analytics | No |
| Composite events | No |
| Reserved prefixes | `ga_`, `google_`, `firebase_` |
| Value types | String and number only. No booleans (use 0/1), no arrays, no nested objects. |

- The most constrained platform. If GA4 is a target, design for it first.
- Custom parameters must be registered in GA4 admin before they appear in reports.
- Enhanced measurement already tracks scrolls, outbound clicks, site search, video engagement, and file downloads.

## Multiple platforms

Do not apply the most restrictive limits to every event. Instead:

1. Decide which events go to which platforms. Not every event needs every destination. With a CDP, a detailed feature event can go only to PostHog while a conversion event goes everywhere.
2. Apply each platform's limits only to the events routed there.
3. For events that go everywhere, GA4 sets the binding limits (rows above).
4. With Segment as the CDP, name events per the Segment spec and let destinations transform them. Flag transformations that lose data: truncated values, dropped arrays for GA4, booleans turned into integers.
5. If an event needs more than GA4's parameter limit, choose which parameters GA4 gets and document the ones it doesn't. The full set still reaches other platforms.
