# Platform Constraints Reference

## Amplitude

| Constraint | Limit |
|---|---|
| Max event types | 2,000 |
| Properties per event | Unlimited |
| Property name length | 1,024 characters |
| Property value length | 100,000 characters (events), 10,000 characters (user properties) |
| Event name format | Any (snake_case recommended) |
| Case sensitivity | Case-sensitive |
| User properties | Yes, via identify() |
| Group analytics | Yes, via groups |
| Composite/custom events | Yes |
| Rate limit | 100 batches/sec, 1,000 events/sec |
| User property update limit | 1,800/hour per user |

### Amplitude-specific notes
- Supports "Govern" feature for taxonomy management and enforcement
- Custom events allow combining multiple events into one metric
- Has a Data Planning Playbook for taxonomy design
- Revenue events have special properties: price, quantity, revenue, productId, revenueType

### Amplitude property format
```json
{
  "event_type": "Task Created",
  "event_properties": {
    "source": "Manual from Email",
    "task_type": "Action Item",
    "priority": "High"
  },
  "user_properties": {
    "plan": "Pro",
    "total_tasks_created": 47
  }
}
```

## Mixpanel

| Constraint | Limit |
|---|---|
| Max event types | 5,000 (soft limit; beyond this, events are ingested but not indexed in autocomplete) |
| Properties per event | 255 |
| Property name length | 255 characters |
| Property value length | 255 characters |
| Event name format | Any (Title Case recommended) |
| Case sensitivity | Case-sensitive (sign_up and Sign_Up are different events) |
| User properties | Yes, via people profiles (set, set_once, increment, append, union, remove, unset) |
| Group analytics | Yes, via group profiles |
| Composite/custom events | Yes |
| Hot shard limit | Single user sending >15,000 events in a 3-hour window triggers rate limiting |

### Mixpanel-specific notes
- Lexicon feature for managing, auditing, and documenting events/properties
- Supports Lookup Tables for enriching events with external data
- Has a concept of "super properties" that are automatically attached to every event
- Profile properties support $set (overwrite), $set_once (set only if not already set), $add (increment numeric), $append (add to list), $union (add unique to list), $remove (remove from list), $unset (remove property)

### Mixpanel property format
```json
{
  "event": "Task Created",
  "properties": {
    "source": "Manual from Email",
    "task_type": "Action Item",
    "priority": "High",
    "$insert_id": "unique-id-123",
    "time": 1234567890
  }
}
```

## PostHog

| Constraint | Limit |
|---|---|
| Max event types | Unlimited |
| Properties per event | Unlimited |
| Property name length | Flexible (no documented hard limit) |
| Property value length | Flexible |
| Event name format | Any (snake_case common in practice) |
| Case sensitivity | Case-sensitive |
| User properties | Yes, via person properties (set, set_once) |
| Group analytics | Yes, via groups (up to 5 group types) |
| Composite/custom events | Yes, via Actions |
| Autocapture | Yes (clicks, pageviews, form submissions captured automatically) |

### PostHog-specific notes
- Autocapture means many basic interaction events are already tracked without manual instrumentation
- Actions allow combining multiple events (including autocaptured ones) into composite events
- Supports both anonymous and identified events
- Person properties: $set (overwrite), $set_once (set only if not already set)
- Has built-in session recording, feature flags, experiments, and surveys alongside analytics
- Group analytics limited to 5 group types (e.g., "organization", "project", "team")
- Supports HogQL for advanced querying

### PostHog property format
```json
{
  "event": "task_created",
  "properties": {
    "source": "manual_from_email",
    "task_type": "action_item",
    "priority": "high",
    "$set": {
      "plan": "pro",
      "total_tasks_created": 47
    },
    "$set_once": {
      "first_task_created_at": "2025-01-15T10:30:00Z"
    }
  }
}
```

## Segment (CDP)

| Constraint | Limit |
|---|---|
| Max event types | Unlimited (Segment is a router, not a storage system) |
| Properties per event | Unlimited |
| Property name length | Flexible |
| Property value length | Flexible |
| Event name format | Object Action in Title Case (spec standard) |
| Case sensitivity | Depends on downstream destination |
| User properties | Yes, via identify() with traits |
| Group analytics | Yes, via group() call |
| Composite/custom events | No (Segment routes, it does not aggregate) |
| Max destinations per source | Unlimited |
| Mapping limit | 50 mappings per destination instance |

### Segment-specific notes
- Segment is a Customer Data Platform (CDP), not an analytics tool. It collects and routes data to downstream tools.
- The Segment Spec defines standard calls: identify, track, page, screen, group, alias
- Property naming should follow the conventions of the MOST restrictive downstream destination
- Segment Protocols feature allows defining a tracking plan with expected events/properties and blocking non-conforming data
- When using Segment, name events according to Segment's spec and let Segment's integrations handle any platform-specific transformation

### Segment track call format
```json
{
  "type": "track",
  "event": "Task Created",
  "properties": {
    "source": "Manual from Email",
    "task_type": "Action Item",
    "priority": "High"
  },
  "context": {
    "traits": {
      "plan": "Pro"
    }
  }
}
```

## GA4 (Google Analytics 4)

| Constraint | Limit |
|---|---|
| Max event types | 500 distinct event names |
| Properties (parameters) per event | 25 custom parameters |
| Event name length | 40 characters |
| Parameter name length | 40 characters |
| Parameter value length | 100 characters |
| Event name format | snake_case ONLY. Must start with alphabetic character. Only letters, numbers, underscores. |
| Case sensitivity | Case-sensitive |
| User properties | Yes (up to 25 custom user properties) |
| Group analytics | No |
| Composite/custom events | No (limited calculated metrics) |
| Reserved prefixes | Names starting with "ga_", "google_", "firebase_" are reserved |

### GA4-specific notes
- Most constrained platform. Design for GA4 constraints first if GA4 is a target.
- Has automatically collected events (page_view, session_start, first_visit, etc.) and recommended events (purchase, sign_up, login, etc.) with predefined parameter names
- Custom parameters must be registered in the GA4 admin before they appear in reports (up to 50 custom event parameters, 25 custom user properties)
- Event names are case-sensitive: "task_created" and "Task_Created" are different events
- Conversion events: any event can be marked as a conversion
- Enhanced measurement auto-tracks: scrolls, outbound clicks, site search, video engagement, file downloads
- No support for arrays or nested objects in parameters

### GA4 event format
```json
{
  "name": "task_created",
  "params": {
    "source": "manual_from_email",
    "task_type": "action_item",
    "priority": "high",
    "engagement_time_msec": 5000
  }
}
```

## Cross-Platform Compatibility

When targeting multiple platforms, do NOT blanket-apply the most restrictive limits to all events. Instead:

1. **Identify which events go to which platforms.** Not every event needs to reach every destination. When using Segment or a CDP, events can be selectively routed — a detailed feature-usage event might go only to PostHog, while a conversion event goes everywhere.

2. **Apply constraints per-destination, not globally.** For events routed to GA4, enforce GA4 limits (40-char names, 25 params, no arrays). For events that only go to PostHog or Amplitude, use those platforms' more generous limits.

3. **For events that DO go everywhere**, these are the binding constraints (the most restrictive across platforms):

| Aspect | Most restrictive limit | Source |
|---|---|---|
| Event name length | 40 chars | GA4 |
| Event name format | snake_case, starts with letter, alphanumeric + underscore only | GA4 |
| Properties per event | 25 custom parameters | GA4 |
| Property name length | 40 chars | GA4 |
| Property value length | 100 chars | GA4 |
| Property value types | String, Number only (booleans as 0/1, no arrays/objects) | GA4 |

4. **When Segment is the CDP**, name events per Segment spec (Title Case Object Action) and let Segment's destination integrations handle platform-specific transformations. Flag cases where transformation may lose data (e.g., truncating property values, dropping array properties for GA4, converting booleans to integers).

5. **When an event has more than 25 properties but needs GA4**, decide which 25 are most important for GA4 and document which properties are excluded from GA4 specifically. The full property set still reaches other platforms.
