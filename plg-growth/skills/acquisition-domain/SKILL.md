---
name: acquisition-domain
description: "Analyse and plan product-led acquisition: which channels bring the right users, product-driven SEO, sidecar tools, piggybacking on other platforms, signup quality, channel mix, and CAC by channel. Use when someone says 'improve acquisition', 'how to get more signups', 'product-led acquisition', 'acquisition strategy', 'channel strategy', 'channel mix', 'product-driven SEO', 'sidecar product', 'piggybacking', 'top-of-funnel conversion', or 'reduce CAC'. For designing viral or referral loops and k-factor math, use growth-loops."
---

# Acquisition Domain

Get more of the right users into the product through the product itself, not just paid spend. Follow `${CLAUDE_PLUGIN_ROOT}/references/problem-solving-backbone.md`.

Scope: channels, product-led acquisition strategies, and signup quality. Not here: viral/referral loop design and k-factor math (`growth-loops`), freemium vs trial (`acquisition-model-selector`), and page-level signup-form optimisation (the `cro-engine` plugin).

## Default: quick answer

Answer narrow questions directly. Run the full analysis below only when the user asks for an acquisition analysis or plan.

## The analysis

**1. Quality before volume.** Break signups down by channel and compare each channel's activation rate, early retention, and revenue, not just signup count. High signups with low activation means the wrong audience or a broken promise. Fix that before optimising signup conversion. A channel that brings most of the signups but little of the revenue is a channel-market misfit.

**2. Product-led strategies.** For each strategy, judge structural fit first. If the product doesn't have the prerequisite, skip it; no investment fixes structural misfit. Most PLG companies run 2–3 of these at once.

| Strategy | Prerequisite | Watch |
|---|---|---|
| **Exposure** (product outputs carry the brand to non-users, e.g. scheduling links, shared videos, "made with" forms) | Outputs are shared outside the account, and the viewer has a one-click path to try it | Hand loop design to `growth-loops` |
| **Product-driven SEO** (indexable user content, template pages, free tool pages) | The product naturally produces unique public content at volume | Thin or duplicate pages; indexed pages vs pages created; slow ramp |
| **Piggybacking** (listings in other platforms' marketplaces, embeds, "powered by", API partnerships) | A platform whose users overlap your ICP, plus a reason to install | Platform dependency and policy risk |
| **Sidecar tool** (a small free tool for a problem only your ICP has) | A narrow ICP pain solvable in seconds without signup, whose output points at the problem your core product solves | Generic tools attract the wrong audience; measure sidecar users' activation, not just usage |

**3. Promise and first experience.** Users who arrive with the right expectations activate faster. Check that the landing page promise matches what the product delivers in session one, that ad copy and landing page match, and that a user arriving from a use-case page or a referral sees that context after signup. Onboarding questions are worth asking only if each answer changes what the user sees. Keep it to 2–4, make them skippable, and watch the skip rate.

**4. Channel economics.** CAC by channel (product-led channels near zero), payback by channel, and which channels reach the ICP at scale. If attribution doesn't exist, building it is the first work item.

## Output

```
## Acquisition analysis
**Biggest opportunity:** [one sentence]
**Hypotheses (max 3):** [hypothesis] — evidence — how to test
**Strategy fit:** [which product-led strategies fit, which to skip, and why]
**Gaps:** [missing data]
**Next step:** [one action]
```

For a work plan, use `${CLAUDE_PLUGIN_ROOT}/references/work-plan-template.md`. Acquisition plans should make channel economics (CAC, payback) known or an explicit item.

## Rules

- Don't default to paid before assessing exposure, SEO, piggybacking and sidecars.
- Don't copy a strategy because it worked for Slack or Canva. Check the prerequisite.
- Don't optimise signup conversion before you know traffic quality.

## Next skills

Signups fine, activation weak → `activation-domain`. Right users arrive but leave → `retention-domain`. Need acquisition in revenue terms → `plg-revenue-analysis`.
