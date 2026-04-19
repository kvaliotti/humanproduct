# Positioning Reconstruction — Claimed vs. Revealed

Source: April Dunford, *Obviously Awesome* (5+1 framework, 2019); cross-checked with *The Mom Test* (Rob Fitzpatrick) for buyer-signal weighting.

This reference governs the Phase 5 work where every shortlisted competitor is reconstructed twice: once as **claimed** (what the company says about itself) and once as **revealed** (what buyers say and do). The gap between the two is often the most actionable insight in the whole evaluation.

## Why two reconstructions

A vendor's claimed positioning is propaganda — accurate or not, it is *what they want to be compared against*. Buyers compare them against something else, often involving alternatives the vendor doesn't acknowledge. Acting on the claimed map mis-allocates effort: building features that don't matter, contesting messaging that doesn't move purchases, fighting the wrong competitors.

Revealed positioning is what the buyer's behavior implies. It is built from: who they actually shortlisted, what triggered consideration, which alternative they switched from or to, and what value they cite when they renew or churn. Behavioral evidence beats stated evidence by 3×; pattern evidence beats single-source by 2×.

The output of this reference is a side-by-side reconstruction with explicit gap notes.

## The Dunford 5+1 Framework — claimed positioning

Reconstruct each competitor's claimed positioning across these six fields:

### 1. Competitive alternatives
**The set the vendor positions itself against.** Sources: comparison pages ("X vs Y"), homepage hero, sales decks, customer-story framing. If the vendor names alternatives explicitly, capture them verbatim. If they don't, infer from what they're *not* claiming to be (a SaaS tool that never says "spreadsheet" probably knows spreadsheets are the real alternative and is hiding from the comparison).

### 2. Unique attributes
**Features, capabilities, or relationships the alternatives don't have.** Pull from product pages, feature lists, and what the homepage emphasizes. Be specific — "fastest" is not an attribute; "sub-50ms p95 latency on the API" is.

### 3. Value (and proof)
**The benefit the unique attributes deliver, plus proof.** What can the buyer do/save/avoid because of the unique attributes? Look at pricing-page benefits, customer-story headlines, ROI calculators. Note proof types: testimonials, case-study numbers, third-party benchmarks, free trials.

### 4. Best-fit customers (target market)
**Who the product is explicitly for.** Sources: ICP language on the homepage, customer logo strip, "for [persona]" headers, signup forms with role/industry pickers, sales-page personas. If the product targets multiple segments, capture them all and note priority order from emphasis.

### 5. Market category
**The frame they ask buyers to compare them inside.** Sources: tagline, meta description, G2 category placement, analyst reports they cite. If the category is contested or new, the vendor often invents a name (e.g., "Customer Data Platform" before the category existed). Capture the invented name and the older category they're displacing.

### +1. Trends (optional, when relevant)
**Macro shifts they invoke as wind in their sails.** Sources: keynote talks, blog content, investor narrative. Use to understand the story they tell about *why now*. Skip if not load-bearing.

## Sources for claimed positioning — ranked

| Tier | Source | Why it matters |
|---|---|---|
| 1 | Homepage hero (above-the-fold copy) | The single message they bet on |
| 2 | First 30 seconds of a recorded demo or pitch | What they pitch when given 30 seconds |
| 3 | Comparison / "vs." pages | The fights they choose to pick |
| 4 | Pricing-page benefits and tiers | Where economic positioning leaks through |
| 5 | Customer-story headlines (not bodies) | The outcomes they want associated |
| 6 | Recent earnings calls or investor decks | Strategic framing for capital, often differs from buyer framing |
| 7 | Analyst reports the vendor cites | Externalized self-positioning |

Capture verbatim quotes for each Dunford field. Inference is fine but flag it as inference.

## Reconstructing Revealed Positioning

Revealed positioning is a different map. Reconstruct against the same six fields, but using buyer-side sources only.

### Sources for revealed positioning — ranked by signal

| Tier | Source | What it reveals | Behavioral / Pattern / Stated |
|---|---|---|---|
| 1 | Reviews on G2, Capterra, TrustRadius — "considered alternatives" sections | Real shortlists | Behavioral |
| 2 | Reviews — "switched from" / "switched to" | Substitution patterns | Behavioral |
| 3 | Reddit, Hacker News, niche Discord — "what do you use for [job]" | Non-SaaS and workaround alternatives | Behavioral / Pattern |
| 4 | Won/lost-deal notes from sales (if accessible) | Last-mile decision drivers | Behavioral |
| 5 | NPS verbatims and churn-survey verbatims | Why they stay vs. leave | Pattern |
| 6 | Sales-engagement transcripts or Gong call snippets | What buyers say in their own words | Behavioral |
| 7 | Customer-story bodies (not headlines) | Buyer-verbatim quotes scattered in marketing assets | Stated, but partially revealed |
| 8 | Job descriptions for buyer roles citing tools | Stack signal — what's in the buyer's actual environment | Behavioral |
| 9 | LinkedIn skill endorsements clustered by role | Tools associated with the role | Pattern |
| 10 | Twitter/LinkedIn posts where buyers describe a workflow | Casual, unfiltered behavior | Behavioral |

Mom Test discipline: **what the buyer did beats what the buyer said they would do.** Reviews are partly stated, but "considered alternatives" is behavioral because the buyer is reporting the actual shortlist they ran.

### How to fill each Dunford field on the revealed map

**1. Competitive alternatives (revealed).** From "considered alternatives" lists in reviews + forum substitute discussion. List the top 5–8 alternatives mentioned, ordered by frequency. Tag each with the segment that mentioned it most.

**2. Unique attributes (revealed).** What buyers cite when asked why they chose this competitor over the alternatives. Strip marketing words. Cluster around 3–5 attributes. Look for surprising attributes the vendor doesn't emphasize ("their support team actually answers", "the API is the only one that works at our scale").

**3. Value (revealed).** What buyers say they got — outcomes, not features. Look for verbatim "before/after" framing: "before X, we used to spend 4 hours per week on Y; now it's 20 minutes". Cluster on the 2–3 most-cited values.

**4. Best-fit customers (revealed).** Who actually loves it (5-star reviews) vs. who churns (1–2-star reviews and churn-destination evidence). Often the revealed ICP is narrower than the claimed ICP. Note segment-level affinity.

**5. Market category (revealed).** What buyers call it in their own words. Often differs from the vendor's invented category. Capture the verbatim category words from forum and review evidence.

**+1. Trends (revealed).** What buyers say is changing in their world that drove them to look. Optional — only fill if the trend is referenced in 3+ buyer sources.

## The Gap Note

For each competitor, write a 3–5 line **gap note** comparing claimed vs. revealed across the six fields:

```
Gap note for [Competitor]:
- Claimed alternatives: [vendor's named set]
- Revealed alternatives: [buyer's actual set]
- Largest delta: [specific divergence — e.g., "buyers compare them with internal scripts and Excel; vendor never names spreadsheets"]
- Implication for the anchor: [one line — e.g., "their real fight is replacing manual workflows, not displacing other SaaS"]
- Confidence: [%]
```

The gap note is the unit of insight that the strategy canvas (Phase 9) and synthesis (Phase 10) will lean on. A weak gap note signals weak research — return to Phase 2.

## Common reconstruction failures

| Failure | Symptom | Counter |
|---|---|---|
| **Restating the homepage as revealed positioning** | Both columns say roughly the same thing | Force two distinct sources — one vendor, one buyer-side. If they truly match, write "no gap detected — verify" |
| **Single-source revealed positioning** | All revealed evidence is from G2 reviews | Add at least one non-review source: forum, job description, churn note |
| **Treating "we have feature X" as a unique attribute** | Unique-attribute column reads like a product changelog | Require buyer evidence that the attribute is *uniquely* attributed to this vendor in shortlists |
| **Ignoring non-consumption** | The revealed-alternatives list contains only SaaS competitors | Force at least one non-SaaS revealed alternative (Excel, an EA, doing nothing); if none exists, the segment may not be the right anchor |
| **Over-confident gap claims** | Gap note declares a sharp divergence with thin evidence | Express confidence as a number; if under 60%, frame the gap as a hypothesis with a research path |

## Mom Test cross-checks for revealed positioning

Apply these filters to anything sourced from buyer interviews, surveys, or customer success notes (where the buyer was asked, not observed):

| Buyer signal | Treat as | Why |
|---|---|---|
| "I would pay for that" | **Suspect** — discount heavily | Future commitment without consideration is cheap |
| "I love it" | **Suspect** — ask what they actually do | Affection without behavior is cheap |
| "I switched from X because of Y" | **Trust** — behavioral | Past behavior with named comparison |
| "I would switch from X because of Y" | **Suspect** — discount heavily | Future intention rarely converts |
| "I use it every day for Z" | **Trust** — behavioral with named use | Frequency claim with specifics |
| "It's the best in the category" | **Suspect** — narrative, not data | Compliment without comparison |
| "I tried X, Y, Z, and chose this" | **Trust** — behavioral with shortlist | Past consideration set + decision |

When in doubt, downgrade stated evidence to "stated" and flag the need for behavioral confirmation.

## Output format for the positioning section

For each competitor, produce two parallel 5+1 tables:

```markdown
#### Claimed positioning ([Competitor])

| Field | Content | Source |
|---|---|---|
| Competitive alternatives | [verbatim or inferred] | [URL / page] |
| Unique attributes | [list] | [URL / page] |
| Value | [list with proof] | [URL / page] |
| Best-fit customers | [ICP language] | [URL / page] |
| Market category | [the frame they ask for] | [URL / page] |
| Trends | [optional] | [URL / page] |

#### Revealed positioning ([Competitor])

| Field | Content | Source tier | Behavioral / Pattern / Stated |
|---|---|---|---|
| Competitive alternatives | [buyer-named set, ordered by frequency] | [tier] | [type] |
| Unique attributes | [buyer-cited differentiators] | [tier] | [type] |
| Value | [buyer-described outcomes with verbatim] | [tier] | [type] |
| Best-fit customers | [revealed ICP from 5-star vs. churn] | [tier] | [type] |
| Market category | [verbatim buyer category language] | [tier] | [type] |
| Trends | [if mentioned in 3+ sources] | [tier] | [type] |

#### Gap note
- Largest claim/reveal delta: [specific]
- Implication for the anchor: [one line]
- Confidence: [%]
```

This is the structure the Phase 5 deep profile expects. Skipping the side-by-side and writing only "positioning" is a critical failure — the synthesis skill cannot allocate against it.
