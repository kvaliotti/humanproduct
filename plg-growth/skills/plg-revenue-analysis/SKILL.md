---
name: plg-revenue-analysis
description: "Decompose revenue into a driver tree for any revenue model, run sensitivity analysis, and size the 2–3 levers worth working on. Use when someone asks 'which lever should I focus on', 'where are my biggest growth opportunities', 'revenue driver tree', 'revenue decomposition', 'MRR analysis', 'growth levers', 'unit economics', 'LTV analysis', 'CAC analysis', or 'PLG revenue analysis'."
---

# PLG Revenue Analysis

Find the lever that moves revenue most for a realistic effort, and say how much it's worth. Follow `${CLAUDE_PLUGIN_ROOT}/references/problem-solving-backbone.md`.

## Default: quick answer

If the user gives a few numbers and asks which lever to pull, build the tree in your head, run the sensitivity, and answer: the lever, the dollar impact, and the assumption it rests on. Offer the full brief only if they want it.

## 1. Build the tree for their model

| Model | Top-level arithmetic |
|---|---|
| SaaS / subscription | Net new MRR = new + expansion + reactivation − churn − contraction; new MRR = traffic × signup rate × activation rate × paid conversion × ARPA |
| Transactional | Revenue = visitors × conversion × AOV × purchase frequency |
| Marketplace | Revenue = GMV × take rate; GMV depends on both supply and demand, and on match quality |
| Usage-based | Revenue = paying users × usage per user × effective price per unit (model volume discounts explicitly) |
| Ad-supported | Revenue = DAU × sessions × impressions per session × fill rate × CPM / 1000 |
| Hybrid | Recurring base + transactional top-up + expansion |
| Freemium + enterprise | Two parallel trees. Free users feed both self-serve conversion and the PQL pipeline for sales. Model both. |

Decomposition rules:

- Keep splitting until each leaf is something the team can act on ("signup form conversion", not "revenue").
- Label each split as arithmetic (direct) or behavioural (indirect). Size only the direct ones.
- Include business levers (pricing, packaging, channels) as well as product levers.
- Split churn into voluntary and involuntary. Involuntary churn (failed payments, expired cards) is often fixable with dunning and retries, without any product change.
- Don't skip a branch because there's no data. Unknown drivers are often the biggest ones.

## 2. Fill in data

For each leaf: current value, trend over 3–6 months, and how reliable the number is (measured, estimated, unknown). Compare to the user's own history first. Use an outside benchmark only if the user has one with a named source. Otherwise mark the gap and make measuring it a next step. Never fill a gap with a generic industry number.

## 3. Sensitivity and sizing

Hold every driver constant, move one by a realistic amount, and recompute revenue. Rank by impact, then adjust for effort: a lever you can move this quarter beats a bigger one that takes two years. Pick 2–3.

Example: new MRR = 500,000 visitors × 5% × 30% × 8% × $50 = $30,000. Activation 30% → 36% adds $6,000/month.

Combined projections assume drivers are independent. They rarely are, so treat a combined number as the upside case, not a commitment.

For each priority lever, write: "If [metric] moves from [current] to [target], monthly revenue changes by [$X] ([Y]%). We believe [action] will do it because [evidence]."

Unit economics on request: LTV = ARPA × gross margin ÷ monthly churn (prefer cohort LTV curves by segment); CAC payback in months = CAC ÷ (ARPA × gross margin). Compute CAC by channel, not just blended. Judge both against the company's own history and plan, not against generic thresholds.

## 4. Output

```
## Revenue analysis
**Focus on:** [lever] — worth [$X/month] if [current → target]
**Tree:** [compact tree or table, leaves marked direct/indirect, unknowns flagged]
**Sensitivity:** | Driver | Current | Realistic target | Revenue impact | Effort |
**Priority levers (2–3):** sizing statement + hypothesis + first action + which plg-growth skill
**Data gaps:** [what to instrument]
```

If they ask how to organise the team around these levers, use `${CLAUDE_PLUGIN_ROOT}/references/team-structuring.md`.

## Next skills

Route each priority lever to its funnel skill: `acquisition-domain`, `activation-domain`, `retention-domain`, `monetisation-domain`. Can't measure the tree → `plg-data-setup`. PLG fit not yet established → `plg-readiness`.
