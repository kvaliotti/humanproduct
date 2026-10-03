# Event Tracking Plugin

Define, review, and format analytics event tracking for any product or feature. Every event must trace back to a question someone will ask of the data.

## Skills

| Skill | Use it when | Writes |
|---|---|---|
| **analytics-use-cases** | Starting new tracking: "what should we track", "set up analytics for [feature]" | `tracking/use-cases-<feature>.md` |
| **event-definition** | Use cases exist and you need event specs; also "format for Amplitude / Mixpanel / PostHog / Segment / GA4" | `tracking/tracking-plan-<feature>.md` |
| **tracking-plan-review** | Events already exist: "audit my events", "review my tracking plan" | Review in chat |

Run them in that order for new tracking, or start at whichever matches where you are. Claude Code picks the skill from what you ask.

## What it holds to

- No event without a use case. No property nobody will filter or break down by.
- One event with properties beats several near-identical events, when the parameterization test says so.
- Record whether the user or the system (AI, background job) did the action.
- Detect and match your existing naming convention. The default, when nothing exists, is `Area - Subarea (optional) - Verb in Past Tense`.
- Vendor limits live in one file, `references/platform-constraints.md`. Verify them against current vendor docs.

## Supported platforms

Amplitude, Mixpanel, PostHog, Segment (as a CDP), and GA4. If an analytics tool is connected via MCP, or a codebase is available, the skills read existing events from it.
