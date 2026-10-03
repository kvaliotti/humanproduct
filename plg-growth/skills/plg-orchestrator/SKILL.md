---
name: plg-orchestrator
description: "Entry point for product-led growth work. Diagnoses where a product stands and routes to the right plg-growth skill. Use when someone says 'help me with PLG', 'product-led growth for my product', 'where should I start with PLG', 'PLG strategy', 'PLG diagnostic', 'make my product product-led', or asks any broad PLG question that doesn't clearly map to one skill."
---

# PLG Orchestrator

Diagnose fast, pick the one or two places that matter, and route. Don't go deep on any topic yourself. Follow `${CLAUDE_PLUGIN_ROOT}/references/problem-solving-backbone.md`.

## 1. Get context

Ask only what the user hasn't told you, a few questions at a time:

- What the product does, for whom, and whether the user is also the buyer.
- How customers arrive and buy today: sales, marketing, self-serve signup, free tier or trial.
- Revenue model and rough scale (order of magnitude is enough).
- The one metric they'd fix if they could, and what they've already tried.

Ask about team, data maturity and funnel numbers only if the answer would change the route.

## 2. Check fit in one pass

Four questions: can a user get value alone, start without a sales step, see core value before paying, and pull in more users or usage without sales? Say yes, partly or no to each. Two or more "no" answers mean PLG is likely a secondary motion. Route to `plg-readiness` before anything else.

Signs PLG should be secondary: the buyer is always a committee, value only appears after weeks of implementation or org-wide rollout, or procurement is mandatory.

## 3. Route

| What you see | Route to |
|---|---|
| Unsure PLG fits, or pre-PMF | `plg-readiness` |
| No free entry point yet, or debating freemium vs trial | `acquisition-model-selector` |
| Has PLG, doesn't know which lever matters most | `plg-revenue-analysis` |
| Not enough of the right users arrive | `acquisition-domain` |
| Users sign up but don't reach first value | `activation-domain` |
| Users reach value but don't come back | `retention-domain` |
| Users stay but don't pay or expand | `monetisation-domain` |
| NPS/CSAT, advocacy, or PMF-survey questions | `satisfaction-domain` |
| Wants self-reinforcing growth (viral, content, paid loops) | `growth-loops` |
| Needs PQLs, sales-assist triggers, land-and-expand | `product-led-sales` |
| Needs to design or prioritise experiments | `plg-experimentation` |
| Can't measure the funnel | `plg-data-setup` |
| Org, incentives or team structure block PLG | `plg-transformation` |

By stage: pre-PMF usually starts at readiness; early with PMF at model selection or revenue analysis; growth stage at the funnel bottleneck; mature companies adding PLG at readiness plus transformation. If the user can't give activation rate, free-to-paid conversion, retention curves or CAC by channel, that gap is itself a finding. Put `plg-data-setup` early.

## 4. Output

Keep it under half a page:

```
## PLG diagnosis
**Start here:** [skill] — [one sentence why]
**Fit:** [strong / possible with work / secondary motion] — [the deciding reason]
**Hypotheses (max 3):** We believe [X] is the constraint because [evidence]. → [skill]
**Unknowns:** [missing data that would change the route]
**Next action:** [one concrete step]
```

Then ask: "Shall we start with [skill]?" When handing off, pass what you learned, the hypothesis being tested, and what success looks like.

## Rules

- If the user asks about everything at once, pick one branch.
- If they want to skip diagnosis, still run step 2. Most PLG failures skip fit.
- If they're already deep in PLG, skip step 2 and go to the bottleneck.
