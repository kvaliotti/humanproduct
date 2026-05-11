# Common Property Patterns

## Universal Properties (attach to most events)

These properties are typically auto-captured by SDKs, but verify they're available in your implementation:

| Property | Type | Source | Notes |
|---|---|---|---|
| timestamp | datetime | Auto (SDK) | When the event fired |
| user_id | string | Auto (SDK) | Identified user |
| anonymous_id | string | Auto (SDK) | Pre-identification |
| session_id | string | Auto (SDK) | Groups events in a session |
| platform | string | Auto (SDK) | web, ios, android |
| app_version | string | Auto/manual | Current app version |
| page_url / screen_name | string | Auto (SDK) | Where the event fired |

## Context Properties (attach based on event type)

### Navigation/View events
| Property | Type | Example values |
|---|---|---|
| page_name / screen_name | string | "Dashboard", "Settings" |
| referrer | string | Previous page/screen |
| view_type | string | "list", "grid", "detail" |

### Creation/Modification events
| Property | Type | Example values |
|---|---|---|
| creation_method | string | "manual", "ai_generated", "imported", "duplicated" |
| source_view | string | "today", "inbox", "project_board" |
| item_type | string | Depends on domain |
| has_attachments | boolean | true/false |

### Interaction events (clicks, toggles, selections)
| Property | Type | Example values |
|---|---|---|
| element_type | string | "button", "link", "toggle", "dropdown" |
| element_name | string | "save_button", "filter_dropdown" |
| element_location | string | "header", "sidebar", "main_content", "modal" |
| previous_value | string/number | Value before change |
| new_value | string/number | Value after change |

### Search events
| Property | Type | Example values |
|---|---|---|
| query | string | The search query text |
| query_length | number | Character count |
| results_count | number | How many results returned |
| has_results | boolean | true/false |
| filters_applied | string | Comma-separated filter names |
| selected_result_position | number | Which result was clicked (1-indexed) |

### Error/Failure events
| Property | Type | Example values |
|---|---|---|
| error_type | string | "validation", "network", "permission", "timeout" |
| error_code | string | "ERR_401", "FIELD_REQUIRED" |
| error_message | string | Human-readable error description |
| attempted_action | string | What the user was trying to do |

### Batch/Bulk action events
| Property | Type | Example values |
|---|---|---|
| batch_id | string | UUID linking related events |
| batch_size | number | Total items in the batch |
| batch_index | number | Position of this item (1-indexed) |
| batch_source | string | "ai_from_meeting", "csv_import" |
| batch_success_count | number | Items that succeeded |
| batch_failure_count | number | Items that failed |

### Timing/Duration events
| Property | Type | Example values |
|---|---|---|
| duration_seconds | number | How long the action/session took |
| time_to_action_seconds | number | Time from page load to this action |
| is_first_time | boolean | First time the user performed this action |

### Feature adoption events
| Property | Type | Example values |
|---|---|---|
| feature_name | string | Name of the feature |
| is_first_use | boolean | First time this user used this feature |
| discovery_source | string | "onboarding_tooltip", "menu", "search", "direct_url" |
| variant | string | A/B test variant if applicable |

## Common User Properties

### Identity & demographics
| Property | Type | Update method | PII? |
|---|---|---|---|
| email | string | set | Yes |
| name | string | set | Yes |
| created_at | datetime | set_once | No |
| signup_source | string | set_once | No |
| first_seen_at | datetime | set_once | No |

### Product state
| Property | Type | Update method | PII? |
|---|---|---|---|
| plan | string | set | No |
| role | string | set | No |
| is_admin | boolean | set | No |
| team_size | number | set | No |
| features_enabled | list | set | No |

### Engagement counters
| Property | Type | Update method | PII? |
|---|---|---|---|
| total_projects_created | number | increment | No |
| total_tasks_completed | number | increment | No |
| last_active_at | datetime | set | No |
| session_count | number | increment | No |

### Lifecycle
| Property | Type | Update method | PII? |
|---|---|---|---|
| lifecycle_stage | string | set | No |
| onboarding_completed | boolean | set | No |
| first_value_moment_at | datetime | set_once | No |
| activation_date | datetime | set_once | No |

## Common Group/Account Properties (B2B)

| Property | Type | Update method | PII? |
|---|---|---|---|
| company_name | string | set | Quasi-PII |
| company_domain | string | set | Quasi-PII |
| industry | string | set | No |
| company_size | string | set | No |
| plan | string | set | No |
| mrr | number | set | No |
| total_seats | number | set | No |
| active_seats | number | set | No |
| created_at | datetime | set_once | No |
| account_manager | string | set | Quasi-PII |

## Property Value Standards

### Enums / Categorical values
- Use consistent casing across all properties (snake_case recommended for code-facing, human-readable for analyst-facing)
- Document all possible values for each categorical property
- Use "other" or "unknown" for catch-all cases, never null for a categorical value that was simply unrecognized
- Add new values explicitly; don't allow arbitrary strings without documentation

### Boolean naming
- Prefix with "is_" or "has_" (e.g., "is_first_time", "has_attachments")
- Use true/false as the canonical value in your tracking plan and in platforms that support booleans (Amplitude, Mixpanel, PostHog, Segment)
- GA4 does NOT support booleans. When GA4 is a target, convert to 0/1 integers in the GA4 payload. The platform-formatter skill handles this automatically — define the property as boolean in the spec, and the formatter will emit 0/1 for GA4.
- Never use "yes"/"no" strings — they create parsing ambiguity

### Numeric values
- Always specify units in the property name when ambiguous (e.g., "duration_seconds" not "duration")
- Use consistent precision (e.g., always 2 decimal places for currency)
- Use -1 or null for "not applicable," never 0 (which might be a valid value)

### Dates/Times
- Always use ISO 8601 format: "2025-01-15T10:30:00Z"
- Always include timezone (preferably UTC)
- For date-only values, use "2025-01-15" format

### Arrays/Lists
- GA4 does NOT support arrays. Convert to comma-separated strings if GA4 is a target.
- Amplitude, Mixpanel, PostHog, Segment all support arrays in properties.
- For cross-platform compatibility, consider storing arrays as comma-separated strings with a separate "count" property.
