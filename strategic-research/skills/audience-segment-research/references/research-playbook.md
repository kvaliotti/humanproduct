# Research Playbook

Purpose: ground the segmentation in real behavior and practitioner language. Eight to fifteen targeted searches beats twenty shallow ones. Pull evidence from sources that reveal what buyers *did*, not just what vendors *claim*.

## Source priority

Rank from highest signal (top) to lowest (bottom). Spend most of the budget on top tiers.

| Tier | Source type | Why | Watch-outs |
|---|---|---|---|
| 1 | Case studies with metrics; public churn/retention posts; public deal announcements with ACV | Reveals behavior with evidence | Case studies are selection-biased toward happy customers — useful for ecstatic filter, not base rate |
| 2 | Practitioner-authored content — Reddit, HN, niche subreddits, Substack/Medium by operators | Unfiltered language, real workflows, substitutes, complaints | Watch for vendor shill accounts; prefer threads with multiple voices |
| 3 | Detailed reviews (G2, Capterra, TrustRadius, ProductHunt) with ≥3 sentences and specifics | Reveals actual use cases, trigger-to-buy, churn reasons | Skip 1-liner reviews and star-only; filter for verified-user tags |
| 4 | Job descriptions | Reveals what buyer orgs actually want done and who owns it | Aspirational JDs overshoot reality; triangulate with tenure data |
| 5 | LinkedIn role titles, role-change data | Reveals how buying roles evolve over time and by company size | Gated/limited — use as confirmation, not primary |
| 6 | Vendor websites, analyst reports, sponsored content | Glossary, claimed ICP, trend language | Treat claimed ICP with suspicion — it's marketing, not evidence |

## Search query patterns

Replace `[domain]` with the industry, `[role]` with the end-user persona, `[anchor]` with the anchor product.

### Discovering who actually buys

```
[anchor] case study
[anchor] customer review site:g2.com
[anchor] "we use" OR "we switched to" OR "we tried"
[anchor] pricing "we pay" OR "we spend"
[role] AMA Reddit
"typical customer" [domain]
who buys [anchor]
[domain] ideal customer profile
```

### Discovering the buying unit (B2B)

```
[anchor] vendor security review
[anchor] SOC2 OR GDPR OR "data processing agreement"
[anchor] procurement
[anchor] implementation
"we bought [anchor]" how long approval
who approves [domain] tools
```

### Discovering pain, triggers, and alternatives

```
[domain] frustrating OR "what I hate"
switched from [anchor] to
we stopped using [anchor]
"finally moved off" [anchor]
DIY [domain]
spreadsheet for [domain]
[role] pain points
[domain] without software
```

### Discovering segment signals (the ecstatic filter)

```
[anchor] best thing ever
[anchor] life-changing OR "game changer"
[anchor] worth it
[anchor] cheaper than
testimonial [anchor] specific
NPS [anchor]
```

### Discovering contradictions and edge cases

Deliberately look for the opposite of whatever pattern you're forming.

```
[anchor] not worth it
[anchor] overpriced OR "too expensive"
[anchor] doesn't work for
[anchor] wrong fit
[emerging segment] + [anchor] critical
```

If a search for counter-evidence returns nothing, it's either because the pattern is very strong or because the search was lazy. Try three angles before concluding.

## The scratch table

Every observation during research is logged in a running scratch table. Keep the table in the working file; it becomes the evidence base for claims.

| # | Observation | Source | URL / citation | Segment hypothesis | Behavioral or stated | Confidence 0-100 | Tension with? |
|---|---|---|---|---|---|---|---|
| 1 | ... | G2 review | link | S1 | behavioral | 70 | — |
| 2 | ... | Reddit thread | link | S2 | stated | 40 | #1 |

Every claim in the final output must be traceable to a row in this table. If a claim has no traceable source, either find one or delete the claim.

## Budget

- **8–15 searches.** Stop when new sources stop changing the emerging segmentation.
- **2–4 WebFetch calls** for case-study pages, review threads with depth, or practitioner blogs.
- **Hard stop at 20 sources.** Past this, you're confirming, not discovering.

## Pre-PMF adjustment

If the anchor has no real customers yet, research shifts:

- Skip case studies and churn posts (they don't exist)
- Lean heavily on adjacent-product reviews (who buys the alternative?)
- Lean on practitioner content about the problem, not any product
- Frame every segment as hypothesis with explicit confidence <50%
- Surface more candidate segments; narrow less aggressively

## Internal data when available

If the user provides internal data (interview notes, CRM exports, support tickets), it outranks public research. Treat it as primary evidence.

Prioritization for internal data:

1. **Interview transcripts** — what they said, with their words preserved
2. **CRM win/loss reasons** — behavioral data on why deals closed or died
3. **Support tickets by segment tag** — pain patterns
4. **Usage data** — actual behavior, the highest signal
5. **Survey responses** — lowest weight (stated preference); look for divergence from behavior

## Anti-patterns

| Anti-pattern | Why wrong | Fix |
|---|---|---|
| Listing vendors and calling it research | Vendors are evidence, not the map | Research buyers, not products |
| Taking the vendor's claimed ICP as given | That's marketing, not truth | Cross-check with case studies and reviews |
| Using AI-generated "typical customer" personas as input | Circular — they reflect training data, not current reality | Base personas on primary evidence |
| Mixing regions silently | Segments often differ by geography (EU vs. US vs. APAC) | Tag region on each observation |
| Fishing for validation | Confirmation bias | Actively search for counter-evidence each round |
| Stopping when the first pattern forms | First pattern is often the obvious one, not the most strategic | Push to 2–3 candidate segmentations before selecting |

## Meta-note

Research here is not about producing certainty — it's about producing *enough* structured evidence that a CPO can make allocation decisions with known-unknowns. Confidence marks (0–100%) on every claim beat false-certain paragraphs.
