# Platform-Specific Format Templates

## Amplitude

### SDK initialization (JavaScript)
```javascript
import * as amplitude from '@amplitude/analytics-browser';

amplitude.init('YOUR_API_KEY', {
  defaultTracking: {
    sessions: true,
    pageViews: true,
    formInteractions: true,
    fileDownloads: true,
  },
});
```

### Track event
```javascript
amplitude.track('Event Name', {
  property_name: 'value',
  numeric_property: 42,
  boolean_property: true,
  list_property: ['a', 'b', 'c'],
});
```

### Identify user
```javascript
const identifyEvent = new amplitude.Identify();
identifyEvent.set('plan', 'pro');
identifyEvent.setOnce('first_login_at', new Date().toISOString());
identifyEvent.add('session_count', 1);
amplitude.identify(identifyEvent);
```

### Set user ID
```javascript
amplitude.setUserId('user-123');
```

### Group identify
```javascript
amplitude.setGroup('company', 'Acme Corp');

const groupIdentify = new amplitude.Identify();
groupIdentify.set('plan', 'enterprise');
groupIdentify.set('employee_count', 500);
amplitude.groupIdentify('company', 'Acme Corp', groupIdentify);
```

### Revenue event
```javascript
const revenue = new amplitude.Revenue();
revenue.setProductId('product-123');
revenue.setPrice(49.99);
revenue.setQuantity(1);
revenue.setRevenueType('purchase');
amplitude.revenue(revenue);
```

### API payload format
```json
{
  "api_key": "YOUR_API_KEY",
  "events": [
    {
      "user_id": "user-123",
      "event_type": "Task Created",
      "time": 1234567890000,
      "event_properties": {
        "creation_method": "manual",
        "source_view": "today"
      },
      "user_properties": {
        "$set": {
          "plan": "pro"
        },
        "$add": {
          "total_tasks_created": 1
        }
      }
    }
  ]
}
```

---

## Mixpanel

### SDK initialization (JavaScript)
```javascript
mixpanel.init('YOUR_TOKEN', {
  track_pageview: true,
  persistence: 'localStorage',
});
```

### Track event
```javascript
mixpanel.track('Event Name', {
  property_name: 'value',
  numeric_property: 42,
  boolean_property: true,
  list_property: ['a', 'b', 'c'],
});
```

### Identify user
```javascript
mixpanel.identify('user-123');

// Set properties (overwrites)
mixpanel.people.set({
  plan: 'pro',
  last_login: new Date().toISOString(),
});

// Set once (only if not already set)
mixpanel.people.set_once({
  first_login_at: new Date().toISOString(),
});

// Increment numeric properties
mixpanel.people.increment('session_count', 1);

// Append to list properties
mixpanel.people.append('features_used', 'tasks');
```

### Super properties (attached to every subsequent event)
```javascript
mixpanel.register({
  plan: 'pro',
  app_version: '2.1.0',
});

// Set once (won't overwrite)
mixpanel.register_once({
  first_referrer: document.referrer,
});
```

### Group analytics
```javascript
mixpanel.set_group('company', 'Acme Corp');

mixpanel.get_group('company', 'Acme Corp').set({
  plan: 'enterprise',
  employee_count: 500,
});
```

### API payload format
```json
{
  "event": "Task Created",
  "properties": {
    "distinct_id": "user-123",
    "token": "YOUR_TOKEN",
    "time": 1234567890,
    "$insert_id": "unique-event-id",
    "creation_method": "manual",
    "source_view": "today"
  }
}
```

---

## PostHog

### SDK initialization (JavaScript)
```javascript
import posthog from 'posthog-js';

posthog.init('YOUR_API_KEY', {
  api_host: 'https://us.i.posthog.com', // or https://eu.i.posthog.com
  person_profiles: 'identified_only',
  capture_pageview: true,
  capture_pageleave: true,
  autocapture: true,
});
```

### Track event
```javascript
posthog.capture('event_name', {
  property_name: 'value',
  numeric_property: 42,
  boolean_property: true,
  list_property: ['a', 'b', 'c'],
  nested_object: { key: 'value' },
});
```

### Identify user and set person properties
```javascript
posthog.identify('user-123', {
  email: 'user@example.com', // $set
  plan: 'pro',
}, {
  first_login_at: new Date().toISOString(), // $set_once
});

// Or update properties later:
posthog.capture('$set', {
  $set: { plan: 'enterprise' },
  $set_once: { first_login_at: new Date().toISOString() },
});
```

### Group analytics
```javascript
posthog.group('company', 'company-id-123', {
  name: 'Acme Corp',
  plan: 'enterprise',
  employee_count: 500,
});
```

### API payload format
```json
{
  "api_key": "YOUR_API_KEY",
  "event": "task_created",
  "distinct_id": "user-123",
  "properties": {
    "creation_method": "manual",
    "source_view": "today",
    "$set": {
      "plan": "pro"
    },
    "$set_once": {
      "first_task_created_at": "2025-01-15T10:30:00Z"
    },
    "$groups": {
      "company": "company-id-123"
    }
  },
  "timestamp": "2025-01-15T10:30:00Z"
}
```

---

## Segment

### SDK initialization (JavaScript)
```javascript
import { AnalyticsBrowser } from '@segment/analytics-next';

const analytics = AnalyticsBrowser.load({
  writeKey: 'YOUR_WRITE_KEY',
});
```

### Track event
```javascript
analytics.track('Event Name', {
  propertyName: 'value', // camelCase per Segment spec
  numericProperty: 42,
  booleanProperty: true,
  listProperty: ['a', 'b', 'c'],
});
```

### Identify user
```javascript
analytics.identify('user-123', {
  email: 'user@example.com',
  plan: 'pro',
  createdAt: new Date().toISOString(),
  name: 'John Doe',
});
```

### Group
```javascript
analytics.group('company-id-123', {
  name: 'Acme Corp',
  plan: 'enterprise',
  employeeCount: 500,
});
```

### Page view
```javascript
analytics.page('Category', 'Page Name', {
  title: 'Dashboard - My App',
  url: 'https://app.example.com/dashboard',
});
```

### API payload format (track call)
```json
{
  "type": "track",
  "userId": "user-123",
  "event": "Task Created",
  "properties": {
    "creationMethod": "manual",
    "sourceView": "today",
    "taskType": "actionItem"
  },
  "context": {
    "page": {
      "url": "https://app.example.com/tasks",
      "title": "Tasks - My App"
    }
  },
  "timestamp": "2025-01-15T10:30:00Z",
  "messageId": "unique-message-id"
}
```

---

## GA4 (Google Analytics 4)

### SDK initialization (gtag.js)
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXX');
</script>
```

### Track event
```javascript
gtag('event', 'task_created', {
  creation_method: 'manual',     // max 40 char name, 100 char value
  source_view: 'today',
  task_type: 'action_item',
  has_due_date: 1,               // booleans as 0/1
});
```

### Set user properties
```javascript
gtag('set', 'user_properties', {
  plan: 'pro',
  role: 'admin',
  // max 25 custom user properties
});
```

### Set user ID
```javascript
gtag('config', 'G-XXXXXXXX', {
  user_id: 'user-123',
});
```

### Recommended events (use these names when applicable)
GA4 has predefined recommended events with specific parameter names. When your event matches one, use the GA4 name:

| Your event concept | GA4 recommended event | Required parameters |
|---|---|---|
| User signed up | sign_up | method |
| User logged in | login | method |
| Purchase completed | purchase | currency, transaction_id, value, items |
| Content shared | share | method, content_type, item_id |
| Search performed | search | search_term |
| Item added to list | add_to_wishlist | currency, value, items |
| Tutorial completed | tutorial_complete | (none) |

### API payload format (Measurement Protocol)
```json
{
  "client_id": "client-id-123",
  "user_id": "user-123",
  "events": [
    {
      "name": "task_created",
      "params": {
        "creation_method": "manual",
        "source_view": "today",
        "task_type": "action_item",
        "has_due_date": 1,
        "engagement_time_msec": 5000
      }
    }
  ]
}
```

### GA4 conversion rules
- Mark critical events as conversions in the GA4 admin
- Conversion events: purchase, sign_up, generate_lead, or any custom event
- A conversion can only count once per session by default (configurable)

---

## Multi-Platform: Segment as CDP

When Segment routes to multiple destinations, format events for Segment spec and document transformations:

```
Source (Segment):        Task Created
→ Amplitude:            Task Created (no change)
→ Mixpanel:             Task Created (no change)
→ PostHog:              task_created (auto-converted by integration)
→ GA4:                  task_created (auto-converted, check 40-char limit)

Property: creationMethod (Segment camelCase)
→ Amplitude:            creation_method (may need mapping)
→ Mixpanel:             creation_method (may need mapping)
→ PostHog:              creation_method (auto-converted)
→ GA4:                  creation_method (auto-converted, check 40-char limit)
```

Note: Segment's destination integrations handle some transformations automatically, but not all. Always verify the actual data in each destination after initial setup.
