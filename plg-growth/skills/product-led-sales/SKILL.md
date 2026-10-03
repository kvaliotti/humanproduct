---
name: product-led-sales
description: "Design a Product-Led Sales (PLS) motion: PQA and PQL definitions, a sales pipeline driven by product signals, sales touchpoints tied to product milestones, and land-and-expand playbooks. Use for: product-led sales, PLS, PQA, PQL, product-qualified, when to add sales, sales in PLG, lead scoring from product usage, bottom-up sales, sales-assist, land and expand, enterprise expansion, product signals for sales."
---

# Product-Led Sales

PLS is sales driven by product data. The buyer already uses the product. Sales should add revenue that self-serve would not capture, never take over deals that would have closed on their own.

**Quick answers.** If the question is narrow ("what's a PQL?", "when should we add sales?"), answer it directly.

## 1. Readiness gate

Ask four questions. If the answer to the first or second is no, the user is **not ready**. Make fixing it the first action (route to `plg-data-setup`).

1. Can you map users to accounts (companies) and see usage by account?
2. Can sales see that usage in the CRM?
3. Is there a gap between what accounts pay through self-serve and what they could be worth (more seats, more teams, a need for SSO or compliance)?
4. Is the company willing to have sales and self-serve coexist, with incentives that reward expansion?

## 2. Define PQAs and PQLs

- **PQA (product-qualified account):** the account is ready. Signals: number of active users, number of departments or roles, growth week over week, attempts to use premium features, integrations, and firmographic fit.
- **PQL (product-qualified lead):** the person to contact. Signals: pricing or plan-comparison views, hitting usage limits, inviting others or exploring admin tools, SSO or security questions, and an admin role.
- Use both: the PQA picks the account, and the PQL picks the champion inside it.

How to build the score:
1. Start with two or three plain rules. Example: "5+ active users across 2+ teams" for a PQA, and "hit a limit or viewed pricing twice" for a PQL. Have sales review each flag by hand.
2. Check the rules against accounts that bought in the past 12 months. Keep the signals those accounts showed first. Set the threshold where the conversion rate jumps.
3. Add weights only once you have outcome data. Add ML only once you have enough conversions to train on.
4. Flagged accounts must convert well above your base rate. Measure that rate, and tighten the rules if they don't. Subtract for negative signals (falling usage, support complaints). Re-score continuously. Sales must log whether each flag was real.

## 3. Tie sales touches to product milestones

| Milestone | Who acts |
|---|---|
| Signup, first team onboarded (land) | No one from sales. Let self-serve work |
| Spread to other departments | Light touch: help the champion with templates and an internal pitch |
| Usage limit hit, admin or enterprise features explored | SDR, while the signal is fresh |
| SSO or security review requested, many teams active | AE plus a solutions engineer. Build the business case with the champion and send security docs before they are asked for |
| Renewal coming up | CSM, with a usage review and an expansion proposal |

Every message must cite the account's real usage. Good: "Your team of 12 hit the project limit last week." Bad: "Would you like a demo?"

## 4. Protect self-serve

- Set a minimum account size below which sales does not engage.
- Upgrades with no documented sales touch count as self-serve revenue. Separate "assisted" from "originated" deals.
- Weight sales and CSM pay toward expansion, not only new logos.

## Output

Lead with the answer: ready or not, and the single first action. Then give:
1. PQA and PQL rules (signals and thresholds) and how to validate them
2. The milestone → touch map for this product
3. Self-serve protection rules
4. Three hypotheses, each with how to test it
5. What we don't know: the data you need and don't have yet

Keep it to about one page. Offer outreach templates, pipeline stage metrics, or a comp plan only if asked.

## Don't

- Cold outreach with no product context.
- Add sales before you can identify PQAs from data.
- Go around the champion to reach the buyer. Give the champion the business case and ROI data instead.
- Quote target conversion rates, team sizes, or comp splits as benchmarks. Use the user's own pipeline data.

Route to `monetisation-domain` for enterprise packaging, `growth-loops` for sales loops, and `plg-orchestrator` for a broader diagnosis.
