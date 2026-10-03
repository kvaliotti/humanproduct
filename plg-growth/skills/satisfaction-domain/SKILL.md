---
name: satisfaction-domain
description: "Use user satisfaction as a PLG growth lever: NPS, CSAT, CES, and the PMF survey. Use for: NPS analysis, promoters and detractors, detractor analysis, customer satisfaction, CSAT, customer effort score, CES, PMF survey, Sean Ellis test, how disappointed would you be, feedback loops, satisfaction strategy, PLG satisfaction plan."
---

# Satisfaction Domain

Help a PM measure satisfaction, tie it to retention, expansion, and referral, and fix what drives detractors. A score on its own means nothing. It matters only if it predicts something the business cares about.

## Default: answer the question

Most requests are narrow ("how should I run NPS?", "what does our PMF score mean?"). Answer directly in a few paragraphs, using the rules below only where they help. End with one line offering the full analysis. Run it only when asked or when a short answer would mislead.

## Full analysis (on request)

1. **Coverage:** which of NPS, CSAT, CES, PMF survey they collect, how often, whether it is segmented, whether anyone follows up.
2. **Link to outcomes:** compare retention, expansion, and actual referrals by satisfaction group in their own data.
3. **Root causes:** cluster detractor comments, low-CSAT areas, and high-effort tasks; classify each (below).
4. **Pick the fixes** with the largest downstream effect on retention, expansion, or referral.

Output, one page at most:
- **Bottom line:** the single biggest satisfaction-driven growth opportunity, in one sentence.
- **Snapshot:** scores by segment and trend, not one number.
- **Satisfaction → outcome:** what the data shows, or "not yet measured".
- **Top 3 hypotheses:** hypothesis, evidence, how to test.
- **What we don't know** and **next step** (one concrete action).

## Which measure for what

- **NPS** — relationship loyalty. Always ask the follow-up "what is the main reason for your score?"; that is where the insight is.
- **CSAT** — one interaction or feature (after support, onboarding, a milestone).
- **CES** — effort on a specific task. Use it on core and onboarding workflows to find friction.
- **PMF survey** (Sean Ellis) — "How would you feel if you could no longer use the product?" Ellis's bar is 40% "very disappointed". Survey only users who have used the core workflow recently. The segment with the highest "very disappointed" share is your best ICP; their "main benefit" answers are your messaging; their "how can we improve" answers are your roadmap.

Survey rules: never report one blended score; segment by plan, tenure, company size, role, usage, and channel. Don't survey users before they have had a real chance to get value. Set a per-user cooldown across all surveys. Ask at natural pauses, not mid-task. Keep each survey to the core question plus one follow-up.

## Root causes → owner

| Cause | Question | Fix belongs to |
|---|---|---|
| **Capability** | Can users do what they need? (missing feature, bugs, speed) | Engineering: build or fix |
| **Opportunity** | Does the context help them succeed? (onboarding, docs, discoverability) | Design, content, CS |
| **Motivation** | Do they want to engage? (unclear value, lost trust) | Product and marketing: show value |

Low CSAT on a feature is often a discoverability problem, not a product problem. Classify before building.

## Close the loop

- **Detractors:** reach out quickly, fix the issue, re-survey later, cluster the themes.
- **Passives:** find what separates them from promoters (usage, onboarding path); they are the swing group.
- **Promoters:** check they actually refer before building a referral programme on them; then give them easy ways to share, review, and act as references. Watch for "false promoters" — high score, low engagement.
- Tell users what changed because of their feedback.

## Don't

- Collect scores nobody acts on.
- Assume promoters refer.
- Ignore passives and work only the extremes.
- Over-survey; it kills response rates.

## Route elsewhere

Pricing is a top detractor theme → `monetisation-domain`. Satisfaction gaps show up as churn → `retention-domain`. Promoters could power referral loops → `growth-loops` or `acquisition-domain`. Promoters as expansion targets → `product-led-sales`. Broader diagnosis → `plg-orchestrator`.
