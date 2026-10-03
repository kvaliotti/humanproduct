---
name: analytics-use-cases
description: >
  Start here for new tracking. Defines the questions the data must answer, and
  the dashboards and conceptual events behind them, before any event is named.
  Use when the user says "what should we track", "what events should we track",
  "create a tracking plan", "set up analytics for [feature]", "define events for
  [feature]" with no use cases yet, "what questions do we need to answer",
  "analytics requirements", "what dashboards do we need", "what should we
  measure", "measurement plan", "what data do we need to collect", or hands over
  a PRD and asks for tracking. Hands off to event-definition.
argument-hint: "[feature, product, or PRD file]"
---

# Analytics Use Cases

Define what the data must answer before defining any events. Every event later must trace back to a use case here. Do not name events in this skill.

## Inputs

A feature or product description, a PRD, or just a conversation. If tracking already exists, find it first (see "Find the existing tracking first" in `${CLAUDE_PLUGIN_ROOT}/references/naming-conventions.md`) so you can mark which questions are already answerable.

## Process

1. **Who uses the data, and what do they ask?** Name the real consumers (product, growth, leadership, CS, sales, engineering). Write 3–7 specific questions each, only for groups that matter here.
2. **If the user doesn't know their questions,** propose starting ones from the description: lifecycle (sign up, activation, D1/D7/D30 retention), feature (how often used, by what share of users, what happens before and after), monetisation (free→paid, which usage predicts conversion). Ask them to confirm, cut, or add.
3. **Tag each question with its analysis type,** because the type sets the data needed:
   - Funnel: ordered events on one user ID
   - Retention: a start event, a return event, a time bucket
   - Segmentation: properties to group by
   - Trend / distribution: timestamped events, or a numeric property
   - Path: event sequences with no fixed order
   - Attribution: source/campaign properties on the conversion event
   - Experiment: a variant property plus a success event
   - Alert: an event with a threshold
4. **Describe the data each question needs** as concepts, not names: "a task gets created, with who created it (user or AI) and from where". Include user and group properties. Include things the system does for the user (AI output, notifications, renewals), not only clicks.
5. **Flag what events can't answer:** states, absence of action, and gradual change (see `${CLAUDE_PLUGIN_ROOT}/references/decision-framework.md`). Suggest a survey, recording, or derived metric instead.
6. **Prioritise:** P0 core metrics, activation, retention, billing; P1 feature adoption and funnels; P2 advanced segmentation and paths.

## Output

Write `tracking/use-cases-<feature>.md`:

1. **Use cases table:** priority, stakeholder, question, analysis type, data needed (conceptual events and properties). Sort P0 first.
2. **Dashboards:** for each, name, audience, and the 3–5 charts with the question each answers. Add chart type, filters, and refresh only if the user asks or already knows them.
3. **Can't answer with events:** each such question and what to use instead.

Keep it to one table plus short lists. In chat, show the P0 questions and the file path, and offer to run `event-definition` next.
