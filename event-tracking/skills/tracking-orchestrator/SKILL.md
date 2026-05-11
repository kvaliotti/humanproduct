---
name: tracking-orchestrator
description: >
  Entry point for defining analytics event tracking for a product or feature.
  Use when the user says "define events", "create a tracking plan", "set up
  analytics tracking", "what events should we track", "design event taxonomy",
  "help me with analytics instrumentation", "tracking plan for [feature]",
  "define analytics for [product]", or wants end-to-end guidance on what to
  track and how. Routes to the appropriate sub-skill based on where the user
  is in the process.
---

# Event Tracking Orchestrator

Route the user through the event tracking pipeline. The pipeline has four stages; enter at whichever stage matches the user's current state.

## Stage Assessment

Determine which stage to enter based on what the user provides:

1. **No context yet** (user says "help me define tracking" with no supporting material) → Start at Stage 1: Analytics Use Cases
2. **Has a feature/product description but no analytical questions defined** (user provides a PRD, spec, or feature description) → Start at Stage 1, but use the provided material as input
3. **Has analytical questions / knows what dashboards they want but no events defined** → Start at Stage 2: Event Definition
4. **Has existing events but wants them reviewed, audited, or extended** → Start at Stage 3: Tracking Plan Review
5. **Has a complete tracking plan and needs platform-specific output** → Start at Stage 4: Platform Formatter

## Information Gathering

Before routing, establish context. Ask only what is not already clear from the user's request:

1. **What product or feature?** — Name, brief description, and current state (new product, new feature in existing product, or updating existing tracking)
2. **Target analytics platform(s)?** — Which system(s) will receive the events? (~~analytics tool). This determines naming constraints and property formats.
3. **Existing tracking?** — Does the product already have events tracked? If yes, ask the user to provide the existing tracking plan, or offer to pull it from ~~analytics tool via MCP, or examine the codebase.
4. **Naming convention?** — Does the team have an existing convention? If yes, detect it. If no, offer the default: Area - Subarea (optional) - Verb in Past Tense with Modifiers.

### Detecting existing conventions

If the user has existing events (from their analytics tool, codebase, or a document):
- Read the existing event names
- Detect the pattern: casing, separator, structure (Object-Action, Area-Verb, etc.), tense
- Present the detected convention to the user for confirmation
- Use the detected convention for all new events unless the user overrides it

### Connecting to existing systems

If the user has ~~analytics tool connected via MCP:
- Pull existing event names and properties
- Detect the naming convention
- Use this as the baseline for new events

If the user has a codebase connected:
- Search for analytics/tracking code (look for track(), capture(), logEvent(), analytics.track, posthog.capture, mixpanel.track, amplitude.logEvent, etc.)
- Extract existing event names, properties, and firing conditions
- Map where in the codebase each event fires

## Routing

After gathering context, invoke the appropriate skill:

- **Stage 1**: Tell the user you're starting with defining analytical use cases, then invoke the `analytics-use-cases` skill
- **Stage 2**: Tell the user you're moving to event definition, then invoke the `event-definition` skill
- **Stage 3**: Tell the user you're reviewing the existing tracking plan, then invoke the `tracking-plan-review` skill
- **Stage 4**: Tell the user you're formatting for the target platform, then invoke the `platform-formatter` skill

## Pipeline Flow

The full pipeline runs as: Use Cases → Event Definition → Review → Format.

After each stage, ask the user if they want to proceed to the next stage or stop. Do not automatically chain stages without checking.

When proceeding between stages, carry forward all context:
- Analytics use cases document (from Stage 1)
- Existing events list (if any)
- Naming convention
- Target platform(s)
- Feature/product description

## Handling Different Scopes

### Single feature in an existing product
- Focus events on the feature's user flows
- Cross-reference with existing events to avoid duplication
- Consider: does the feature introduce new user properties? Does it extend existing event properties?

### New product with no existing tracking
- Request full product understanding first: key user flows, core value proposition, monetization model
- Start with lifecycle events (signup, activation, engagement, retention, monetization)
- Then layer feature-specific events on top
- Generate a full implementation instruction document alongside the tracking plan

### Updating/extending existing tracking
- Pull existing tracking plan first
- Identify gaps relative to the analytical questions
- Propose additions and modifications, never a full rewrite unless requested
- Flag deprecated or redundant existing events
