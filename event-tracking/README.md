# Event Tracking Plugin

Define, structure, and review analytics event tracking plans for any product or feature. Produces platform-ready event specifications with naming conventions, properties, firing conditions, user properties, and sample payloads.

## Skills

| Skill | What it does | Trigger phrases |
|---|---|---|
| **tracking-orchestrator** | Entry point. Routes you through the pipeline based on where you are in the process. | "define events", "create tracking plan", "set up analytics" |
| **analytics-use-cases** | Defines what questions the data must answer before any events are created. | "what should we measure", "analytics requirements", "what dashboards do we need" |
| **event-definition** | Turns use cases into concrete event specs with names, properties, and firing conditions. | "define events for [feature]", "create event spec", "tracking spec" |
| **tracking-plan-review** | Audits an existing tracking plan for naming consistency, coverage gaps, and redundancy. | "review my tracking plan", "audit my events", "check event coverage" |
| **platform-formatter** | Formats a tracking plan for specific analytics platforms with sample payloads and code snippets. | "format for Amplitude", "export for PostHog", "generate payloads" |

## Pipeline

The recommended flow is:

1. **Analytics Use Cases** — Define what questions need answering
2. **Event Definition** — Create events that answer those questions
3. **Tracking Plan Review** — Audit for quality
4. **Platform Formatter** — Generate platform-specific output

You can enter at any stage. The orchestrator skill routes you to the right starting point.

## Supported Platforms

Amplitude, Mixpanel, PostHog, Segment (as CDP), and GA4. The plugin knows each platform's constraints (event limits, property limits, naming rules) and adapts output accordingly.

## Naming Convention

Default: `Area - Subarea (optional) - Verb in Past Tense with Modifiers`

The plugin detects existing conventions from your analytics tool or codebase and matches them. You can override with any convention.

## Connectors

See `CONNECTORS.md` for optional tool integrations (analytics tools, CDPs, project trackers).
