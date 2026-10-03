---
name: monetisation-domain
description: "PLG pricing, packaging, and monetisation. Use for: pricing strategy, packaging optimization, tier structure, feature gating, pricing metric, seat-based vs usage-based pricing, freemium conversion, free-to-paid, upgrade triggers, ARPA improvement, expansion revenue, willingness to pay, Van Westendorp, MaxDiff, pricing research, monetisation analysis, PLG monetisation plan."
---

# Monetisation Domain

Help a PM decide what to charge for, how to charge, and how much, then find the few levers that lift conversion, ARPA, and expansion.

## Default: answer the question

Most requests are narrow ("seat-based or usage-based?", "how do I calculate ARPA?"). Answer directly in a few paragraphs, using the rules below only where they help. End with one line offering the full analysis. Run it only when asked or when a short answer would mislead.

## Full analysis (on request)

1. **Check the free experience first.** If free users never reach value, this is an activation problem dressed as a monetisation problem. Route to `activation-domain`.
2. **Pricing triangle.** Assess packaging, metric, and price together. A wrong metric can't be fixed with a better price.
3. **Decompose ARPA** with the formula that matches their pricing model (below). Find the component with the most headroom.
4. **Levers.** Pick the few conversion, expansion, or contraction levers that hit that component.

Output, one page at most:
- **Bottom line:** the single biggest monetisation opportunity, in one sentence.
- **Weakest side of the triangle** and why.
- **ARPA component with most headroom**, with the arithmetic shown.
- **Top 3 hypotheses:** hypothesis, evidence, how to test.
- **What we don't know** and **next step** (one concrete action).

If the user wants a work plan, turn the hypotheses into items: hypothesis, metric, guardrail (total conversion, churn), sample and duration, priority by revenue impact. If willingness to pay is unknown, start with research, not experiments.

## Pricing triangle

**Packaging (what you charge for).** Gate on value, not punishment. Limit the dimension that grows with the value a customer gets: seats if value grows with team size, usage if with volume, projects or history if with complexity or data. Don't gate basic export or charge to remove branding with nothing added; users feel punished.

| Feature question | If yes |
|---|---|
| Needed to reach the aha moment? | Free |
| Creates viral exposure? | Free (it markets for you) |
| Mainly serves teams or orgs? | Paid |
| Power-user depth? | Middle tier |
| Security, compliance, admin, SSO? | Top tier |

Add-ons work when only some customers on any tier need the feature, and it has standalone value.

**Metric (how you charge).** Test each candidate: "If the customer doubled this, would they say they got twice the value?" Then check: predictable bill, grows as the customer succeeds, meterable, explainable in one sentence, fits how competitors charge. PLG tensions: per-seat pricing taxes the collaboration that drives virality; usage pricing lowers the barrier to start but risks bill shock.

**Price (how much).** Price to customer value, not your cost. Anchor to the alternative they use today. Separate willingness-to-pay segments with tiers ("price fences"), not discounts. Treat annual billing as a fair trade for commitment, not a discount.

## ARPA by model

Pick the formula that matches the pricing metric. Don't force a seat lens on a usage- or outcome-priced product.

```
Seat-based:      ARPA = avg seats × price/seat + add-ons + overage
Usage-based:     ARPA = base/committed fee + avg units × price/unit + overage
Outcome-based:   ARPA = avg successful outcomes × price/outcome
Marketplace:     ARPA = take rate × GMV per account + fixed fees
Hybrid:          platform fee + any of the above
```

For each component show the current level and what a realistic change is worth in revenue.

## Levers

- **Conversion:** a clear pricing page (side-by-side plans, recommended plan highlighted, user language), few clicks from upgrade prompt to payment, payment methods the ICP uses (invoice/PO for enterprise), trial extension in exchange for finishing onboarding.
- **Upgrade and expansion triggers** — prompt at the moment of need: tries a gated feature, nears or hits a limit, hits the seat limit, invites a teammate, shares with an outside email, several users from one company domain on separate free accounts.
- **Contraction prevention:** watch paid vs. active seats; offer right-sizing before the customer asks (it builds trust); send admins a usage and value summary before renewal; offer pause or a smaller plan instead of cancel.
- **Price increases:** add value before raising price, give advance notice, apply to new customers first, grandfather existing ones for a period.

Opinionated default order when nothing else points the way: pricing page clarity, then upgrade prompts at limits, then annual billing, then seat-utilisation monitoring.

## Research

- **Upgrade decision interviews** first. Talk to recent upgraders, users who abandoned the upgrade flow, heavy free users who never upgraded, and recent downgraders. Ask what triggered the upgrade, what they compared the price to, what held them back. Use the answers to design any survey.
- **Van Westendorp** gives an acceptable price range. It is stated preference: use it as a direction, then confirm with real conversion data.
- **MaxDiff** ranks features or pricing metrics by forced trade-offs. Top-ranked features drive willingness to pay and belong in paid tiers. Bottom-ranked ones can go in free.

## Don't

- Set prices by gut feel or by copying a competitor without checking value.
- Obsess over price while the metric is wrong.
- Use one plan when segments clearly differ in value and willingness to pay.
- Optimise new-customer conversion and ignore expansion.
- Use fake urgency on the pricing page.

## Route elsewhere

Freemium vs. trial decision → `acquisition-model-selector`. Revenue model context → `plg-revenue-analysis`. Sales-assisted expansion → `product-led-sales`. Monetisation inside loops → `growth-loops`. Pricing drives detractors or churn → `satisfaction-domain` / `retention-domain`. Broader diagnosis → `plg-orchestrator`.
