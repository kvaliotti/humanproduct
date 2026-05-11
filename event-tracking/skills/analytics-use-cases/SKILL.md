---
name: analytics-use-cases
description: >
  Define the analytical questions, dashboards, and use cases that drive event
  tracking decisions. Use when the user says "what questions do we need to
  answer", "define analytics requirements", "what dashboards do we need",
  "what should we measure", "analytics use cases for [feature]", "what data
  do we need to collect", "measurement plan", or wants to establish the
  WHY before defining WHAT to track. This skill MUST run before event
  definition to ensure every event has a purpose.
---

# Analytics Use Cases

Define what questions the data must answer BEFORE defining any events. Every event in the tracking plan must trace back to at least one use case defined here.

## Process

### Step 1: Identify Stakeholders and Their Questions

Ask the user (or infer from context) who will consume the analytics data:

- **Product team**: Feature adoption, user flows, activation metrics, engagement depth
- **Growth team**: Funnel conversion, acquisition channels, retention cohorts, experiment results
- **Engineering**: Error rates, performance, feature usage for deprecation decisions
- **Leadership/Board**: High-level KPIs, revenue metrics, growth rates
- **Marketing**: Campaign attribution, content engagement, conversion paths
- **Customer success**: Health scores, churn predictors, adoption patterns
- **Sales**: Product-qualified leads, usage-based triggers, expansion signals

For each relevant stakeholder group, define 3-7 specific questions they need answered.

### Step 2: Map Questions to Analysis Types

For each question, specify the analysis type — this determines what kind of events and properties are needed:

| Analysis type | What it requires | Example question |
|---|---|---|
| **Funnel** | Ordered sequence of events with consistent user ID | "What % of signups reach activation?" |
| **Retention** | A start event + a return event + time bucketing | "Do users who create 3+ tasks in week 1 retain better?" |
| **Segmentation** | Events with properties to group by | "How does feature usage differ by plan tier?" |
| **Trend** | Events with timestamps, aggregated over time | "Is daily task creation increasing or decreasing?" |
| **Distribution** | Numeric property on events | "How many tasks does a typical user create per week?" |
| **Path/Flow** | Sequence of events without a predefined order | "What do users do after viewing the dashboard?" |
| **Attribution** | Source/campaign properties on conversion events | "Which channels drive the most activated users?" |
| **Correlation** | Two or more properties/events analyzed together | "Is there a relationship between session length and task completion?" |
| **Experiment** | Events + variant property + success metric | "Does the new onboarding flow improve D7 retention?" |
| **Alerting** | Events with thresholds or anomaly detection | "Notify me when error rate exceeds 5%" |

### Step 3: Define Dashboard Specifications

For each major stakeholder group, outline the dashboard(s) needed. Match the level of detail to what the user can actually answer at this stage:

**Quick version (minimum viable — use when the user doesn't have details yet):**
```
Dashboard: [Name]
Audience: [Who views this]
Top 3-5 charts:
1. [Chart title] — answers: [which question from Step 1]
2. [Chart title] — answers: [which question]
3. [Chart title] — answers: [which question]
```

The goal is to connect charts to questions, not to fully design the dashboard. Chart types, filters, and dimensions can be refined later in the event-definition stage when the specific events and properties are known.

**Detailed version (use when the user has clear requirements or when designing for an existing analytics setup):**
```
Dashboard: [Name]
Audience: [Who views this and how often]
Refresh: [Real-time / Daily / Weekly]
Time range default: [Last 7 days / Last 30 days / etc.]

Charts:
1. [Chart title]
   - Type: [Line / Bar / Funnel / Table / Number / Cohort]
   - Metric: [What is being measured]
   - Dimensions: [What to break down by]
   - Filters: [Default filters]
   - Question answered: [Link to use case question]
```

Default to the quick version. Upgrade to detailed when the user provides enough context or explicitly asks for it.

### Step 4: Map Use Cases to Event Requirements

For each use case, specify the minimum data needed:

```
Use case: [Question]
Analysis type: [From Step 2]
Required events:
  - [Event concept — not a name yet, just what needs to happen]
    - Needed properties: [What context is required]
Required user properties: [If any]
Required group properties: [If any for B2B]
```

Do NOT name the events yet. Describe them conceptually. Event naming happens in the event-definition skill.

### Step 5: Identify Gaps and Priorities

After mapping all use cases:

1. **Flag questions that can't be answered with the proposed data** — either the product doesn't surface the information, or capturing it would require unreasonable implementation effort. Present these gaps to the user.

2. **Prioritize use cases** into:
   - **P0 (Must have)**: Core product metrics, activation/retention, billing events
   - **P1 (Should have)**: Feature adoption, engagement depth, funnel optimization
   - **P2 (Nice to have)**: Advanced segmentation, path analysis, predictive signals

3. **Sanity-check the implied event count**. There is no correct number — complex features and products naturally require more events. But if the count feels high relative to the number of analytical questions, run a consolidation check: are any implied events answering the same question? Could some be merged via properties? This is a sense-check, not a gate.

## Output Format

Produce a structured use cases document with:

1. **Stakeholder-Question Matrix**: Each stakeholder group with their 3-7 questions
2. **Analysis Type Mapping**: Each question tagged with the analysis type
3. **Dashboard Specs**: Outline of each dashboard with chart descriptions
4. **Event Requirements**: Conceptual events needed to answer each question (no naming yet)
5. **User/Group Property Requirements**: Properties that should live on user or group profiles
6. **Gaps and Risks**: Questions that can't be answered, data that's hard to capture
7. **Priority Classification**: P0/P1/P2 for each use case

This document becomes the input for the event-definition skill. Every event created in the next stage must trace back to at least one use case in this document.

## When the User Skips This Step

If the user provides a PRD or feature spec and says "just define the events," push back gently:

1. Acknowledge the request
2. Explain that events without use cases lead to tracking that nobody queries
3. Offer a fast-track: derive the use cases from the PRD in 5 minutes, then proceed to events
4. If the user still insists, proceed to event-definition but flag events that lack a clear analytical purpose

## When the User Can't Answer Questions

If the user doesn't know what questions their team needs answered:

1. Use the product/feature description to infer standard questions:
   - Lifecycle: "How many users sign up? How many activate? How many retain at D1/D7/D30?"
   - Feature: "How often is [feature] used? What % of users use it? What do they do before/after?"
   - Monetization: "What is the conversion rate from free to paid? What features correlate with conversion?"
2. Present these as starting hypotheses
3. Ask the user to confirm, modify, or add to them
4. Supplement with the codebase or existing analytics data if available — look at what's already tracked and what's missing
