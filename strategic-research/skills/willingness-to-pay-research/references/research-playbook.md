# Research Playbook — WTP-specific

Purpose: ground the WTP model in real prices paid, real churn and expansion, and real value-realization language. Eight to fifteen targeted searches beats twenty shallow ones. The goal is **behavioral evidence of what buyers actually paid for**, not what vendors claim they charge.

## Source priority

| Tier | Source type | Why | Watch-outs |
|---|---|---|---|
| 1 | Case studies with disclosed ACV / deal size / contract value | Behavioral evidence at real prices | Selection bias toward happy customers; useful for ecstatic filter not base rate |
| 2 | Public churn and expansion posts, SaaS cohort writeups | Shows what they paid, then kept paying or stopped | Retention is often driven by switching cost, not WTP — tag explicitly |
| 3 | G2 / Capterra / TrustRadius reviews with price commentary | Value-realization language; "worth it at $X" / "overpriced" | Filter out 1-line reviews; look for verified-user tags and specific dollar mentions |
| 4 | Competitor pricing pages (WaybackMachine for trajectory) | Category anchors; what buyers have been trained to expect | Public list price ≠ realized price; discounting is invisible here |
| 5 | Reddit / Hacker News / niche Discord surfaced on the web | Price complaints, substitutes, DIY workarounds | Watch for vendor shill threads; prefer posts with multiple voices |
| 6 | Job descriptions with tool stack or budget mention | Reveals routine spend and buyer authority | Aspirational JDs overshoot reality |
| 7 | Vendor marketing, sponsored content, analyst reports | Glossary, claimed value | Treat claimed ROI with strong suspicion; demand independent confirmation |

Spend the bulk of budget on Tiers 1–3. Tier 7 is terminology only.

## Search query patterns

Replace `[anchor]` with the anchor product, `[category]` with the industry category, `[role]` with the buyer persona, `[alt]` with the named next-best alternative.

### Discovering what buyers actually pay

```
[anchor] pricing "we pay" OR "we spend" OR "our ACV"
[anchor] contract value
[anchor] case study OR ROI OR payback
site:g2.com [anchor] "per user" OR "per seat" OR "per month"
[category] "annual contract" OR "average deal size"
[anchor] enterprise deal
[anchor] vs [alt] price comparison
```

### Discovering what they pay for (Leaders vs. Fillers vs. Killers)

```
[anchor] "what I love" OR "best feature" OR "killer feature"
[anchor] "we bought it because"
[anchor] "only reason we use"
[anchor] "don't need" OR "never use" OR "turned off"
[anchor] "wish they would remove" OR "too complicated"
[anchor] "deal breaker" OR "non-starter"
[role] must-have features [category]
```

### Discovering why they pay (drivers and EVC math)

```
[anchor] ROI case study
[anchor] saves hours OR "X hours per week"
[anchor] replaced [alt] cost
[role] time spent on [task]
[category] loaded cost OR "cost of"
before [anchor] we used to OR "we used to pay"
```

### Discovering proof-of-value signals

```
[anchor] "I knew it was worth it when"
[anchor] "the moment I realized"
[anchor] "first time I"
[anchor] success metric OR KPI moved
[anchor] "in my dashboard" OR "in the report"
[anchor] "my boss" OR "my team" OR "my client" noticed
```

### Discovering churn and non-value

```
[anchor] "we switched from" OR "we left"
[anchor] "not worth it" OR "canceled"
[anchor] "stopped paying" OR "downgraded"
[anchor] "didn't deliver"
why stopped using [anchor]
[category] disappointed OR overpromised
```

### Discovering WTP variance by segment

```
[anchor] small team OR SMB pricing
[anchor] enterprise pricing OR negotiated deal
[role] [anchor] budget
[role1] vs [role2] [category] spend
"too expensive for" [anchor] OR "out of reach"
```

### Discovering disconfirming evidence

Deliberately look for the opposite of the forming hypothesis. If counter-evidence returns nothing after three angles, the pattern is strong; if after one lazy angle, the search is incomplete.

```
[anchor] overpriced
[anchor] not worth
[dominant Leader] actually doesn't matter
"we pay for [anchor] but rarely use"
[anchor] free alternative
[category] DIY is fine
```

## The scratch table

Every observation during research is logged in a running scratch table. Keep it in the working file; it becomes the audit trail for every WTP claim.

| # | Observation | Kind | Source | URL / citation | Segment | Behavioral / stated | Confidence 0–100 | Tension with? |

`Kind` is one of: **value** (what they pay for), **price** (what they pay), **driver** (why they pay), **signal** (how they detect value), **anti-value** (Killer or dissatisfier).

Every claim in the final output must be traceable to a row here.

## Budget

- **8–15 searches.** Stop when new sources stop changing the emerging WTP model.
- **2–4 deep fetches** for case-study pages, review threads with price detail, or long-form practitioner posts.
- **Hard stop at 20 sources.** Beyond this, you're confirming, not discovering.

## Pre-PMF adjustment

If the anchor has no paying customers yet, research shifts to:

- Adjacent-product prices and expansion patterns (who pays what for the next-best alternative)
- Practitioner willingness-to-experiment (free trial conversion rates in adjacent categories)
- Cost of the pain being tolerated today (what they lose by doing nothing)
- Explicit hypothesis framing with confidence < 50% on all WTP bands
- Heavier weight on the Mom-Test interview methodology — primary research replaces missing behavioral signals

## Internal data when available

If the user provides internal pricing data, it outranks public research. Prioritization:

1. **Won-deal ACVs by segment** — pure behavioral evidence
2. **Lost-deal reasons when price was cited** — elasticity signals
3. **Expansion revenue by customer** — revealed willingness to pay more
4. **Discounting history** — how much price is actually realized vs. listed
5. **Support tickets about pricing** — friction points
6. **NPS comments mentioning value or price** — value-realization language
7. **Survey responses on WTP** — lowest weight; look only for divergence from behavior

## Anti-patterns

| Anti-pattern | Why wrong | Fix |
|---|---|---|
| Quoting vendor list price as the WTP | List ≠ realized; discount is invisible | Triangulate with reviews, case studies, deal registries |
| Using competitor pricing as WTP proxy | Category has trained buyers, but the anchor may have a different WTP fingerprint | Use competitor prices as reference anchors only |
| Accepting "I'd pay $X" survey answers | Stated preference is notoriously inflated | Demand behavioral confirmation |
| Averaging across segments | Obscures 5–10× variance | Preserve per-segment bands |
| Stopping when the first WTP estimate emerges | First estimate is usually the obvious one | Push for 2+ contrasting estimates per segment, then select |
| Forgetting the reference alternative | Absolute WTP is meaningless | Name the alternative on every claim |

## Meta-note

WTP research here is not about producing certainty. It is about producing enough structured evidence that a CPO can decide which research bets to fund next — and which pricing directions to explore with quantitative validation (Van Westendorp, conjoint, price experiments). Confidence marks (0–100%) on every band beat false-certain single numbers.
