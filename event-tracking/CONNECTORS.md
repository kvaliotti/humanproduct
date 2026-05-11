# Connectors

## How tool references work

Plugin files use `~~category` as a placeholder for whatever tool the user connects in that category. Plugins are tool-agnostic — they describe workflows in terms of categories rather than specific products.

## Connectors for this plugin

| Category | Placeholder | Options |
|---|---|---|
| Analytics tool | `~~analytics tool` | Amplitude, Mixpanel, PostHog, GA4 |
| CDP | `~~cdp` | Segment |
| Project tracker | `~~project tracker` | Linear, Asana, Jira, Notion |

### How connectors are used

- **~~analytics tool**: When the user has an analytics tool connected via MCP, the plugin can pull existing event names, properties, and usage data to detect naming conventions and identify gaps. This is optional — the plugin works without a connected analytics tool.
- **~~cdp**: When Segment or another CDP is in the stack, the plugin adjusts its output to format events for the CDP layer and documents downstream transformations.
- **~~project tracker**: When a project tracker is connected, the plugin can create implementation tickets for engineering with the event specifications.
