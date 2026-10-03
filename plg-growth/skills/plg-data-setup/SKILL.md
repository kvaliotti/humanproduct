---
name: plg-data-setup
description: "Find the data gaps that block PLG work, using TASE (Track, Analyse, Sync, Experiment): account-level identity, the PLG-critical events, product-to-CRM and product-to-marketing syncs, and experimentation infrastructure. Use for: PLG data setup, TASE framework, PLG analytics, data-driven PLG, PLG instrumentation, sync product data to CRM, PLG dashboards, data maturity assessment, analytics tool selection for PLG. For a full tracking plan, event naming, or a tracking audit, use the event-tracking plugin."
---

# PLG Data Setup

Find which data gaps block PLG work, and design what's missing. This skill does not write tracking code, and it is not a tracking-plan tool.

**Tracking plans live elsewhere.** For event names, properties, naming conventions, a full tracking plan, an audit of existing tracking, or platform-specific payloads, use the `event-tracking` plugin (`/event-tracking:event-definition` to design events, `/event-tracking:tracking-plan-review` to audit existing tracking). It starts from analytics use cases and matches the team's existing naming. If it isn't installed, still design events "decision first": every event must answer a question someone will act on.

## 1. Assess gaps with TASE

For each dimension, list what is **missing** and the **PLG decision or skill it blocks**. Don't give maturity scores.

- **Track:** Can you follow a person from anonymous visitor to signup to paid? Does every event carry an `account_id` (essential for B2B)? Are the PLG-critical events below tracked? Is there firmographic and UTM enrichment?
- **Analyse:** Is activation defined (`activation-domain`)? Can you cut retention and conversion by signup cohort? Is there a revenue driver tree view (`plg-revenue-analysis`)? Does anyone look at these weekly?
- **Sync:** Can sales see account usage in the CRM? Can marketing trigger messages from product behaviour? Do CRM outcomes (won or lost) flow back to the warehouse, so PQL rules can be validated?
- **Experiment:** Are there feature flags? Is there assignment at the account level? Is there a way to analyze results and a log of past tests?

## 2. PLG-critical events

These are the events that PLG skills depend on. Check that they exist. Leave names and properties to the team's convention or to `event-tracking`.

- Identity: signup (with method and source), anonymous-to-known link, and account created (with company domain)
- Activation: the defined activation action, with time since signup
- Monetization intent: paywall or limit hit (which limit), pricing page viewed, trial started
- Collaboration: invite sent, invite accepted, integration added or removed
- Payment lifecycle: subscription created, upgraded, downgraded, seat added, cancelled (with reason), payment failed, payment recovered. Reconcile these against the billing system.
- Account properties: plan, MRR, user count, department count

## 3. Sync design

| Flow | Purpose | Freshness |
|---|---|---|
| Product → analytics | Funnels, cohorts, activation | Near real time |
| Product → CRM (aggregated by account) | PQA and PQL flags, usage context for sales | Real time for triggers; daily for the rest |
| Product → marketing automation | Behaviour-triggered email and in-app messages | Real time |
| Product → warehouse | Joins across sources, revenue reporting, scoring models | Hourly or streaming |
| CRM → warehouse | Deal outcomes to validate PQL rules | Daily |
| CRM → product | Show the account owner, or "contact sales" vs "upgrade" | Daily or on change |

For each missing flow, name the owner and the transform needed (for example, events rolled up into account-level scores).

## 4. Ongoing data quality

Check weekly: sudden swings in event volume, missing values on required properties, events that never resolve to a known user, gaps between payment events and billing, duplicate events, and free-text properties that should be fixed lists (or that leak PII).

## Tool choice (only if asked)

The must-haves for PLG are: user- and account-level behaviour tracking, cohort retention, funnels you can break down by property, export or API access for syncs, and a feature-flag or experiment integration. Choose based on what the team already uses and can run without a dedicated analytics engineer.

## Output

Lead with: "Biggest gap: [X]. It blocks [PLG activity]. Fix first: [action]." Then give the gap list by TASE dimension, the missing PLG-critical events, and the missing syncs, in that order. Keep it to about one page. Hand the event specs to `event-tracking`.
