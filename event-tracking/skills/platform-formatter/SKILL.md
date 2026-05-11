---
name: platform-formatter
description: >
  Format a tracking plan for a specific analytics platform, generating
  platform-compliant event names, property formats, and sample payloads.
  Use when the user says "format for Amplitude", "export for PostHog",
  "format for Mixpanel", "generate tracking plan spreadsheet", "format
  events for GA4", "Segment spec", "platform-specific format",
  "implementation-ready spec", "generate payloads", "export tracking plan",
  or has a completed tracking plan and needs it adapted for their specific
  analytics tool(s).
---

# Platform Formatter

Transform a tracking plan into platform-specific output: compliant event names, formatted properties, sample payloads, and implementation-ready specifications.

## Inputs

1. **Tracking plan** — the output from the event-definition skill, or any event list with names, properties, and firing conditions
2. **Target platform(s)** — one or more of: Amplitude, Mixpanel, PostHog, Segment, GA4
3. **Naming convention override** (optional) — if the platform requires a different convention than what the tracking plan uses

Read `references/platform-formats.md` for platform-specific formatting rules and templates.

## Process

### Step 1: Apply Platform Constraints

For each event in the tracking plan, check against the target platform's constraints:

**Name compliance:**
- Length limits (GA4: 40 chars, Mixpanel: 255 chars, etc.)
- Format requirements (GA4: snake_case only, must start with letter)
- Reserved name conflicts (GA4: no "ga_", "google_", "firebase_" prefixes)
- Case sensitivity implications

**Property compliance:**
- Number of properties per event (GA4: 25 custom params max)
- Property name length (GA4: 40 chars)
- Property value length (GA4: 100 chars, Mixpanel: 255 chars)
- Supported data types (GA4: no arrays/objects)
- Reserved property names

For each violation, generate a compliant alternative and explain the transformation.

### Step 2: Generate Platform-Specific Names

If the source tracking plan uses a convention that doesn't match the target platform:

| Source convention | Amplitude | Mixpanel | PostHog | Segment | GA4 |
|---|---|---|---|---|---|
| Area - Verb (Title Case) | Keep as-is | Keep as-is | Convert to snake_case (recommended) | Keep as-is | Convert to snake_case, truncate to 40 chars |
| Object Action (Title Case) | Keep as-is | Keep as-is | Keep or convert to snake_case | Keep as-is (native) | Convert to snake_case, truncate to 40 chars |
| snake_case | Keep or convert to Title Case | Convert to Title Case (recommended) | Keep as-is (native) | Convert to Title Case | Keep as-is (native) |

Generate a mapping table:
```
| Source Event Name | [Platform] Event Name | Transformation Applied |
|---|---|---|
| Tasks - Created Task | task_created | Converted to snake_case, removed area prefix (GA4 40-char limit) |
```

### Step 3: Format Properties

For each event's properties, format according to platform convention:

**Property name format:**
- Amplitude: snake_case or camelCase (recommend snake_case for consistency)
- Mixpanel: snake_case (properties) with human-readable values
- PostHog: snake_case
- Segment: camelCase (per Segment spec)
- GA4: snake_case, max 40 chars, alphanumeric + underscore only

**Property value format:**
- Amplitude: human-readable strings, numbers, booleans, arrays, objects supported
- Mixpanel: strings (max 255 chars), numbers, booleans, lists supported. No nested objects.
- PostHog: all types supported including nested objects
- Segment: all types supported
- GA4: strings (max 100 chars), numbers only. No booleans (convert to 0/1), no arrays, no objects.

### Step 4: Generate Sample Payloads

For each event, generate the exact JSON payload as the platform's SDK/API expects it. Use the payload formats from `references/platform-formats.md`.

Include:
- The track/capture/logEvent call
- All event properties
- User property updates (if this event triggers them)
- Any platform-specific metadata (insert_id for Mixpanel, device_id for Amplitude, etc.)

### Step 5: Generate User Property Setup

For each user property in the tracking plan, generate the platform-specific identify/set call:

- Amplitude: `amplitude.identify(new Identify().set('property', value))`
- Mixpanel: `mixpanel.people.set({'property': value})`
- PostHog: `posthog.identify(userId, {property: value})`
- Segment: `analytics.identify(userId, {property: value})`
- GA4: `gtag('set', 'user_properties', {property: value})`

### Step 6: Generate Implementation Code Snippets

For each target platform, generate SDK code snippets in the most common language (JavaScript/TypeScript by default, or the language the user specifies):

```javascript
// Event: Task Created
analytics.track('Task Created', {
  creation_method: 'manual',
  source_view: 'today',
  task_type: 'action_item',
  has_due_date: true
});
```

### Step 7: Multi-Platform Routing (Segment)

If Segment is in the stack as CDP:
1. Format all events per Segment spec (Title Case Object Action)
2. Document which properties need transformation at each destination
3. Flag properties that will be lost or truncated at specific destinations
4. Generate Segment Protocols schema if requested

## Output Formats

### Tracking Plan Spreadsheet (default)
Generate a structured table suitable for a spreadsheet:

| Event Name | [Platform] Name | Category | Description | Fires When | Property | Type | Required | Values | PII | Platform Notes |
|---|---|---|---|---|---|---|---|---|---|---|

### JSON Schema
Generate a JSON schema for each event that can be used for validation:
```json
{
  "event": "Task Created",
  "properties": {
    "type": "object",
    "required": ["creation_method"],
    "properties": {
      "creation_method": {
        "type": "string",
        "enum": ["manual", "ai_generated", "imported", "duplicated"]
      }
    }
  }
}
```

### SDK Implementation Guide
Generate a complete implementation file with:
- SDK initialization code
- Helper functions for common patterns (e.g., batch event tracking)
- Each event as a typed function call
- User property setup functions
- Testing/validation utilities

### Segment Protocols Schema
If Segment is a target, generate the Protocols-compatible tracking plan JSON that can be imported into Segment's tracking plan feature.
