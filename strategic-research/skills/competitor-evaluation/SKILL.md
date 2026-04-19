---
name: competitor-evaluation
description: Build an evidence-based map of the competitive set for a product, category, or industry — classified (direct / indirect / adjacent / substitute / non-consumption), placed on the industry matrix, profiled by positioning, segment affinity, winning factors, and structural advantages (7 Powers), and compressed into Blue Ocean strategy canvases. Integrates Blue Ocean Strategy, 7 Powers (Helmer), Obviously Awesome (Dunford), Christensen, and The Mom Test. Consumes handoffs from industry-process-map, audience-segment-research, and willingness-to-pay-research. Use when the user asks to "evaluate competitors", "map the competitive landscape", "who else plays here", "what are competitors' unfair advantages", "build a strategy canvas", "do Blue Ocean analysis", "who wins what and why", or "find the white space". Output: one markdown artifact with classified competitive set, matrix coverage, per-competitor profiles, segment affinity, winning-factors ledger, 7 Powers grid, strategy canvases, and YAML handoff.
---

# Competitor Evaluation

## Promise

Given an anchor (product, category, or industry) — ideally with upstream handoffs from `industry-process-map`, `audience-segment-research`, and `willingness-to-pay-research` — produce **one markdown artifact** that answers seven questions in order:

1. **Who is actually competing?** — the full substitution set classified as direct, indirect, adjacent, substitute, and non-consumption, built from buyer behavior rather than vendor self-declarations.
2. **Where do they play on the industry matrix?** — each competitor placed onto the cells of the matrix inherited from skill #1, with coverage overlap made explicit.
3. **How are they positioned?** — positioning statement, category claim, and competitive alternatives named (Dunford 5+1), reconstructed from their own messaging, behavior, and buyer-side evidence — not taken at face value.
4. **Which segments do they appeal to?** — segment-by-segment affinity matrix against the segments inherited from skill #2, graded by evidence (wins, references, ICP language, review cohort).
5. **Why do they win (or lose) where they do?** — winning-factors ledger per competitor: what buyers cite, what behavior reveals, and what the competitor itself optimizes for.
6. **What "unfair" advantages do they actually have?** — each competitor run through the 7 Powers test (Helmer). Advantages that fail the persistence-and-hardness test are downgraded to operational lead, not moat.
7. **What does the strategic picture compress to?** — one or more Blue Ocean strategy canvases (value curves on the factors of competition) showing strategic groups, convergence, and white space.

Plus: cross-competitor synthesis (strategic groups, convergence risk, white-space hypotheses), tension log, glossary, rejected-framings appendix, and YAML handoff for the synthesis skill (#5) that follows.

This is an **analysis** skill. It does not make a build-vs-partner decision, does not write positioning, and does not write a roadmap. It produces the substrate those decisions stand on.

The output is read by a CPO-level audience. Write for a reader who will make allocation and bet-sizing decisions on it.

## Operating principles

Seven principles define this skill. They are the book-grounded spine — when in doubt, return to them.

### 1. Define competitors by the buyer's substitution set, not by vendor category (Dunford Ch. 4 + Christensen JTBD)

A competitor is anyone the buyer considers — or silently tolerates — instead of you. That includes:

| Class | What it is | Example (for an "AI Chief of Staff" app) |
|---|---|---|
| **Direct** | Same job, same approach, same buyer | Reclaim.ai, Motion, Mem |
| **Indirect** | Same job, different approach | A $2k/mo human EA; Notion + templates; ChatGPT + memory hacks |
| **Adjacent** | Overlapping job, different primary use | Fireflies (meeting notes), Superhuman (email), Things3 (tasks) |
| **Substitute / workaround** | Non-SaaS alternatives | A Moleskine + Pomodoro, a personal Notion page, tolerating the chaos |
| **Non-consumption** | Buyer does nothing | "I just wing it. I'll get to it when I get to it." |

Vendor-declared categories ("productivity software", "CRM") are propaganda — they describe what the vendor wants to be compared against, not what the buyer actually chose from. The competitive set is reconstructed from won/lost deals, churn destinations, review "considered alongside" mentions, and forum substitute-discussion. If non-consumption is ≥ 30% of the addressable opportunity (common in net-new categories), it is treated as a top-ranked competitor and gets its own profile.

### 2. A competitor set without indirect and non-consumption is a sales pitch, not a map (Christensen + Dunford)

The most dangerous competitor is usually not the one on the G2 grid. It is the spreadsheet, the agency, the habit, or the adjacent tool being repurposed. Missing those → overestimating WTP, underestimating onboarding friction, and mis-pricing against the wrong anchor.

Completeness test: for each segment inherited from skill #2, name at least one non-SaaS alternative. If you cannot, the research is thin — return to Phase 2.

### 3. Positioning is inferred from behavior, not from the homepage (Dunford + The Mom Test)

A vendor's claimed positioning is a hypothesis about how they'd like to be understood. Revealed positioning is what buyers actually think they are, which surfaces from:

| Signal | What it reveals |
|---|---|
| Review cohort (role, company size, industry) | Who actually buys |
| "Best for…" language in third-party reviews | Revealed segment affinity |
| Churn-to destinations | Where they under-deliver |
| Expansion patterns (which add-ons land, which don't) | Real value drivers |
| Sales-led vs. PLG entry motion | Buyer archetype |
| Which competitors their own docs acknowledge | Their felt threat set |

Every claimed positioning must be cross-checked against at least two behavioral signals. Where the two diverge, record the gap as a tension — it is often the most exploitable insight in the entire analysis.

### 4. Winning factors are revealed by wins, losses, and retention — not by feature checklists (Mom Test discipline)

A feature a competitor has is not a reason they win. A reason they win is what a buyer (a) chose them for, (b) refuses to churn from, or (c) expands on. The winning-factors ledger separates:

| Claim type | Weight | Example |
|---|---|---|
| **Behavioral** — why they actually won a deal or kept an account | High (3×) | "We went with them because their iOS SDK was the only one that worked with our legacy build pipeline." |
| **Revealed via pattern** — recurring theme in reviews / posts | Medium (2×) | 11 of 14 G2 reviews mention "fastest onboarding I've had" |
| **Stated** — competitor's claim or analyst claim | Low (1×) | "Market leader in mobile attribution" (vendor deck) |

A competitor that wins on features the buyers never mention is a competitor with a marketing problem; one that wins on factors the buyers always mention is a competitor with a moat hypothesis.

### 5. "Unfair" is a strong word — test each advantage against the 7 Powers (Helmer)

The word "advantage" is almost always overused. An advantage is **unfair** only when it is (a) material to economics and (b) structurally hard for incumbents to copy and for challengers to overcome. Helmer's 7 Powers is the right test:

| Power | What it is | Fails the test when |
|---|---|---|
| **Scale economies** | Unit cost declines with scale | Cost curve is flat, or category isn't scale-sensitive |
| **Network effects** | Value rises with users | Users don't interact or cross-side dynamics don't hold |
| **Counter-positioning** | New model incumbents can't copy without cannibalizing | Incumbents can copy without collateral damage |
| **Switching costs** | Buyers incur real cost to leave | Data exports trivially, integrations are thin |
| **Branding** | Premium from durable affective association | Brand is new, thin, or category-generic |
| **Cornered resource** | Privileged access (talent, IP, deal, data) | Access is rentable or replicable |
| **Process power** | Organizational capability built over time, hard to copy | "Just" a talented team; no embedded system |

Each claimed advantage is run through this grid and either confirmed as a Power, downgraded to **operational lead** (real but copyable with effort), or rejected as **asserted-only** (no evidence). Calling operational lead a moat is the single most common error in competitive analysis. Bias toward skepticism.

Full grid and tests in the operating-principles rationale below; the skill pushes hard against false positives.

### 6. Strategy canvases are lossy compressions — run one per strategic group, not one for everyone (Blue Ocean Strategy Ch. 2)

A single strategy canvas that plots every competitor on the same factors of competition hides the most important fact: different competitors compete on different factors. Blue Ocean canvases are most useful when drawn:

- **Per strategic group** — competitors clustering on similar value curves share a group; draw one canvas per group and stack them.
- **With the "right" factors** — chosen to reveal convergence, not flatter everyone. Factors are selected from buyer evidence (what they cite as decisive), not from a SWOT brainstorm.
- **With non-consumption on the canvas** — the Four Actions Framework (Eliminate / Reduce / Raise / Create) aimed at non-customers is where new value curves come from, not at incumbents.

Canvases that make every competitor look similar are well-drawn. Canvases that make one competitor look dramatically different are interesting but suspect — verify before celebrating.

### 7. Per-segment competitive picture, not a single frame (inherited from skill #2 + skill #3)

The competitive set is non-uniform across segments. Company A may dominate Segment 1 on switching costs while losing Segment 2 to a workaround. A single "competitive landscape" slide that averages across segments is a compression that loses the most actionable information.

When segments are inherited from skill #2, every competitor is evaluated per segment on: entry motion, winning factors, retention pattern, and WTP band versus the segment's band from skill #3. Aggregate views are generated from the per-segment picture, not the other way around.

## Workflow

Execute in order. Phases feed forward.

### Phase 1 — Intake & calibration

Consume input in this order of preference:

1. **YAML handoff from `willingness-to-pay-research`** — parse it. Inherit per-segment WTP bands, Leaders / Fillers / Killers, proof signals, and next-best-alternative anchors. The named alternatives in skill #3's EVC math are the **first concrete candidates** for the competitor set — they are, by definition, what buyers compared against.
2. **YAML handoff from `audience-segment-research`** — inherit segments, stakeholder maps, and current-alternatives per segment. Current alternatives are competitor candidates.
3. **YAML handoff from `industry-process-map`** — inherit process tree, matrix framing, and substitutes. The matrix is the board this skill plays on; every competitor will be placed onto it in Phase 4.
4. **User-provided context** — known competitors, internal win/loss data, battlecards, churn destinations, NPS competitor mentions.
5. **Bootstrap** — if none of the above exist, ask 2–3 clarifying questions with `AskUserQuestion`.

Resolve these variables before research:

| Variable | What it is | Example |
|---|---|---|
| **Anchor** | Reference product/company | "SplitMetrics" |
| **Industry / domain** | The space | "Mobile ad optimization" |
| **Matrix** | Inherited from skill #1 (rows × columns) | "Process step × Channel" |
| **Segments** | Inherited from skill #2 | S1, S2, S3 |
| **WTP bands by segment** | Inherited from skill #3 | $ per month per user per segment |
| **Scope of competitive map** | How wide to cast | "Include indirect + non-consumption; exclude creative-production-only tools" |
| **Depth goal** | Breadth (20 competitors shallow) vs. depth (6 competitors deep) | "Depth — 5-7 competitors in detail + a long tail list" |

When to ask vs. assume: **ask** if the user has internal win/loss data or battlecards (they are the highest-signal input), and if depth-vs-breadth is ambiguous. **Assume** otherwise and state assumptions explicitly. Cap at 3 questions.

### Phase 2 — Build the candidate competitive set (wide first, then cut)

Goal: an over-inclusive roster the skill will trim, not an under-inclusive one it will regret.

Sources (ranked by signal):

| Tier | Source | What it reveals |
|---|---|---|
| 1 | Named alternatives in skill #3's EVC math | Confirmed substitutes from buyer behavior |
| 2 | Current-alternatives per segment from skill #2 | Buyer-declared substitution set |
| 3 | Reviews on G2/Capterra/TrustRadius "alternatives" and "considered alongside" sections | Revealed substitution set |
| 4 | Subreddits / HN / niche Discord threads asking "what do you use for [job]" | Non-SaaS and workaround candidates |
| 5 | Job descriptions naming required-tool stack for the role | Budget-holder revealed set |
| 6 | Competitor homepage "alternatives to us" and comparison pages | Their own felt threat set |
| 7 | Analyst grids — Gartner, Forrester, G2 | Vendor-category consensus (low signal, high noise) |

Budget: 10–20 searches + 3–6 deep fetches. Stop when two consecutive searches produce no new candidates.

Tag each candidate at capture time:

| Candidate | First source | Category hypothesis (direct / indirect / adjacent / substitute / non-consumption) | Segments mentioned | Confidence it belongs on the final list |

Include non-consumption explicitly as a candidate. If no one on the shortlist represents "buyer does nothing", add it.

### Phase 3 — Classify and shortlist

From the over-inclusive roster, produce:

1. **A classified long-list table** — every candidate in a row with final direct/indirect/adjacent/substitute/non-consumption class, one-line rationale, and evidence anchor.
2. **A shortlist for deep profiling** — typically 4–8 competitors spanning at least two classes (never all direct). Shortlist criteria:
   - Named by buyers as a real alternative (not just a vendor-grid neighbor)
   - Materially covers the anchor's cells on the industry matrix
   - Represents a distinct strategic group, not a near-clone of another shortlist entry
   - Includes the highest-threat indirect + at least one non-consumption alternative
3. **A long-tail mention list** — competitors known but not deeply profiled, with a one-line reason each is excluded from deep profiling.

The shortlist is where the rest of the skill does its work. Overshooting shortlist size is the common failure mode — 5–6 deep profiles beat 15 shallow ones.

### Phase 4 — Map competitors onto the industry matrix

For each shortlisted competitor, flag which cells of the inherited matrix they cover. Output:

- A **coverage grid** — matrix rows × competitors, with coverage intensity (primary / secondary / partial / absent).
- An **overlap score per competitor vs. anchor** — share of anchor's primary cells the competitor covers.
- A **white-space flag** — cells where no shortlist competitor is primary. These are candidate positioning territories.

Coverage is graded on evidence: "primary" only if the competitor's own product explicitly covers the cell *and* buyer evidence confirms use. Aspirations and adjacent-mention don't qualify.

### Phase 5 — Per-competitor deep profile

For each shortlisted competitor, produce the profile using these fields. Per-competitor profile length: 400–700 words.

| Field | Content |
|---|---|
| **Identity** | Name, year founded, stage, headcount band, funding (if relevant), public-vs-private |
| **Class** | Direct / indirect / adjacent / substitute / non-consumption |
| **One-line description** | How a buyer would describe it in a sentence (buyer words, not vendor words) |
| **Coverage on the matrix** | Cells they play in, from Phase 4 |
| **Claimed positioning** | Their own positioning — competitive alternatives, unique attributes, value themes, target market, market category (Dunford 5+1) — reconstructed from homepage, pricing page, and first 20 seconds of their pitch |
| **Revealed positioning** | What buyers actually describe them as, sourced from reviews and forums; note the delta from claimed |
| **Target segments** | Which of the inherited segments they appeal to, with evidence |
| **Segment affinity grade** | For each inherited segment: Strong / Fit / Weak / Antagonistic, with a one-line reason |
| **Pricing model and bands** | Pricing approach (per-seat, per-usage, tiered, sales-led) and known price points, with sources |
| **Entry motion** | Self-serve / PLG / sales-led / hybrid / channel |
| **Winning factors (behavioral)** | What buyers cite as reasons they chose it, weighted by evidence tier |
| **Losing factors / anti-patterns** | What buyers cite as reasons to leave or not choose |
| **Claimed advantages** | What the competitor and its analysts claim as moats |
| **7 Powers diagnosis** | Per-power verdict: Confirmed / Partial / Operational lead / Asserted-only / N/A — with reasoning |
| **Unfair advantage call** | The 1–2 (at most) Powers the competitor actually has, or "none — operational lead only" |
| **Kano / LFK lens** | Which of skill #3's Leaders they cover strongly, which they ignore, which Killers they trigger |
| **Tensions held** | Contradictions between claimed and revealed signals, classified |
| **Outlier signals** | 1–2 singleton observations worth preserving |
| **Confidence** | 0–100% this profile is directionally right |
| **Evidence roll-up** | Count of behavioral / pattern / stated observations |

Use `references/seven-powers-grid.md` as the diagnostic guide for the 7 Powers section and `references/positioning-reconstruction.md` for the claimed vs. revealed work.

### Phase 6 — Segment affinity matrix

Build a **competitor × segment** matrix where each cell contains:

- Affinity grade (Strong / Fit / Weak / Antagonistic)
- Primary evidence (one-line)
- Revealed winning factor in that segment (if known)
- Anchor's current position in that cell (winning / losing / absent / tied)

The goal is to make segment-level competitive dynamics legible. Where the anchor is losing a segment, name the specific factor the winner covers better. Where the anchor is absent, decide whether the segment is a white space or an anti-segment.

### Phase 7 — Winning-factors ledger (cross-competitor)

Consolidate winning factors across competitors into a ranked ledger:

| Factor | Competitors this wins for | Evidence weight | Segments where it's decisive | Anchor's position (own / weak / absent) |

This view answers: which factors are category table stakes, which are differentiation levers, and which are contested territory. It is the direct input into the strategy canvas factor selection in Phase 9.

### Phase 8 — 7 Powers consolidated view

Roll up the per-competitor 7 Powers diagnoses into a single competitor × power grid. Column totals reveal which Powers are most commonly held in this category (often telling about the category's structural dynamics). Row totals per competitor reveal structural threat level.

Flag:
- **Power concentration** — a single competitor holding 3+ confirmed Powers (rare, significant; verify)
- **Category Power gravity** — if 3+ competitors hold the same Power, it is a category rule; the anchor needs either that Power or a counter-position against it
- **Power gaps** — Powers no one yet holds. Candidate white space for the anchor

### Phase 9 — Build strategy canvas(es)

Execute in order:

1. **Select factors of competition** — 6–10 factors drawn from the Phase 7 winning-factors ledger. Factors must be (a) things buyers actually trade off, (b) plottable on a 0–5 or 0–10 offer-intensity scale, (c) not redundant. Example factors for an AI Chief of Staff category: price, meeting-prep automation, cross-tool memory, latency, native mobile UX, admin visibility, privacy/data isolation, setup time. Avoid generic factors like "quality" or "innovation" — they are not plottable.
2. **Cluster competitors into strategic groups** — competitors with similar value curves go on the same canvas. Typical groups: incumbents, challengers, low-end disruptors, adjacents, non-consumption. Draw one canvas per group, plus one overlay canvas comparing the anchor against the dominant group.
3. **Plot each competitor on each factor** — 0–5 based on offer intensity, with one-sentence evidence per plotted point. Rigor here is everything; shallow plotting produces false "white space".
4. **Apply the Four Actions Framework** — for the anchor, identify:

   | Action | What it does |
   |---|---|
   | **Eliminate** | Factors the industry takes for granted that buyers don't actually value |
   | **Reduce** | Factors over-served relative to buyer needs (cost out) |
   | **Raise** | Factors under-served by the current industry standard |
   | **Create** | Factors the industry has never offered (often surfaced from non-consumption research) |

5. **Identify convergence zones and blue spots** — factors where value curves are converging (commodity risk) vs. factors where no curve is drawn at all (blue spot — candidate value innovation).

Use `references/strategy-canvas-factors.md` for factor-selection heuristics and common traps.

### Phase 10 — Cross-competitor synthesis

Half a page. Five cross-cuts:

1. **Strategic groups** — name the 2–4 groups and their defining shared moves.
2. **Convergence risk** — where the category is flattening; which factors are table-stakes-ing.
3. **White-space hypotheses** — cells on the matrix, segments, factor combinations, or Power gaps where no one is strong. Each hypothesis names the segment that would care and the evidence behind the gap.
4. **Threat ranking** — top 3 threats to the anchor, with the specific mechanism (Power, winning factor, segment capture, or disruption path from Christensen).
5. **Non-consumption posture** — is non-consumption shrinking (competitors are reaching the under-served), holding (no one has cracked it), or growing (a new behavior is emerging)? The answer shapes GTM fundamentally.

### Phase 11 — Assemble the output

Use `assets/output-template.md`. Full structure:

1. Framing & sources
2. Competitive set — classified long-list + shortlist rationale + long-tail mentions
3. Coverage grid on the industry matrix
4. Per-competitor deep profiles (repeat)
5. Segment affinity matrix
6. Winning-factors ledger
7. 7 Powers consolidated grid
8. Strategy canvas(es) — per strategic group + anchor overlay + Four Actions summary
9. Cross-competitor synthesis (groups, convergence, white space, threats, non-consumption)
10. Tension log
11. Outliers & singletons
12. Glossary (competitor and category terminology, buyer words only)
13. Evidence quality notes
14. Open questions for the synthesis skill
15. Appendix — rejected framings (alternative groupings, rejected canvases, over-claimed Powers)
16. YAML handoff block

Write to `/sessions/compassionate-amazing-ptolemy/mnt/tempSkills/competitor-evaluation-[slug].md` where `[slug]` is a kebab-case tag of the anchor or industry (e.g., `splitmetrics-apple-ads`).

The YAML handoff block is non-negotiable — it's the contract with the synthesis skill (#5). Schema in `references/handoff-schema.md`.

### Phase 12 — Share

Link the file with a `computer://` link. Short message: title, one-sentence top-line (e.g., "3 strategic groups, 1 confirmed-Powers competitor, non-consumption still dominant in S2"), link. Don't restate content in chat.

## Quality audit — mandatory before Phase 11

Run these checks explicitly. Fix any failure before writing the final artifact.

- [ ] Does the competitive set include at least one indirect, one substitute/workaround, and one non-consumption alternative?
- [ ] For each segment inherited from skill #2, is there at least one non-SaaS alternative named?
- [ ] Is every shortlisted competitor classified (direct / indirect / adjacent / substitute / non-consumption) with a one-line rationale?
- [ ] Does every per-competitor profile separate claimed from revealed positioning, with a gap note?
- [ ] Is every winning factor tagged behavioral / pattern / stated, and weighted accordingly?
- [ ] Has every claimed advantage been run through the 7 Powers grid and either confirmed, downgraded to operational lead, or rejected?
- [ ] Is the behavioral-to-stated ratio in the winning-factors ledger ≥ 1:2? (If heavier on stated, flag thin evidence.)
- [ ] Does each strategy canvas factor have an evidence-anchored 0–5 plot for every competitor on it?
- [ ] Is there at least one canvas per strategic group (not a single whole-category canvas)?
- [ ] Does the Four Actions Framework produce at least one "Create" candidate, drawn from non-consumption research?
- [ ] Does the segment affinity matrix show the anchor's position in every cell?
- [ ] Is every tension classified (claimed-vs-revealed / subsegment-split / context-dependent / stated-vs-behavioral / temporal / unresolved)?
- [ ] Are singletons preserved either per-profile or in a global outliers section?
- [ ] Does the YAML handoff validate against `references/handoff-schema.md`?
- [ ] Have "features they have" claims been rejected as winning factors unless tied to buyer behavior?

If any check fails, loop back to the relevant phase.

## Writing style

- **No preamble.** Start with the framing table.
- **Tables and structured profiles over prose.** Prose only where nuance requires it.
- **Specific alternatives, not categories.** "Motion (AI calendar), a $2.5k/mo EA, or a Notion dashboard" beats "planning tools, assistants, and knowledge bases".
- **Behavior-anchored claims.** "41 of 58 churn-to reviews name 'slow sync' as reason" beats "users complain about performance".
- **Source tags on non-obvious claims.** Inline `[src: G2 review 2025-03, behavioral]` or `[src: r/productivity 2024-11]`.
- **Confidence marks as percentages.** No hedge words ("somewhat", "arguably", "it could be said").
- **Honest gaps.** "Thin evidence — 2 data points, both stated" beats dressing it up.
- **Verbs in factor labels.** "Preps me for my next meeting in 30 seconds" beats "Meeting preparation quality".
- **Skeptical voice on Power claims.** Default to "operational lead" until the persistence-and-hardness test is passed.

## Common failure modes — reject before they ship

| Failure | Looks like | Counter |
|---|---|---|
| **The G2 grid trap** | Competitive set = the other logos on a Gartner MQ | Rebuild from buyer behavior: reviews' "considered alongside", won/lost data, forum substitute-talk |
| **Moat inflation** | Every competitor has 2+ confirmed Powers | Re-run the 7 Powers test with bias toward "operational lead"; require structural evidence |
| **Homepage-driven positioning** | Claimed positioning is restated as revealed | Add at least two behavioral cross-checks per competitor; note gaps explicitly |
| **Feature-list-as-winning-factor** | "They win because they have X feature" | Require behavioral evidence — a named buyer citing the factor as decisive — or demote the claim |
| **Canvas vanity** | One strategy canvas with every competitor, everyone looks different | Per-strategic-group canvases; verify convergence isn't hidden by lumping unlike competitors |
| **Non-consumption blindness** | Shortlist is all SaaS | Force a non-consumption profile; if nobody is "doing nothing", the segmentation is probably inherited from a mature category and needs a challenge |
| **Segment averaging** | One winning-factor ledger for "the market" | Roll up from per-segment grids; aggregate last, not first |
| **Churn-destination gaps** | No evidence of where buyers *leave to* | Run dedicated searches on "switched from [anchor] to" and "left [competitor] for" — these are the highest-signal substitution indicators |

## When this skill is the wrong tool

| User wants | Use |
|---|---|
| Map the space (processes, workflow) | `industry-process-map` (skill #1) |
| Segment the audience and map stakeholders | `audience-segment-research` (skill #2) |
| Willingness-to-pay / pricing sensitivity | `willingness-to-pay-research` (skill #3) |
| Final strategic synthesis and recommendations | Synthesis skill (skill #5, downstream) |
| A named-competitor battlecard for sales | `product-management:competitive-brief` |
| Positioning canvas and market category claim | `pm-sage:position-product` (feed it this skill's output) |
| Evaluate a specific product idea against this landscape | `pm-sage:evaluate-idea` |
| Write a PRD that differentiates against this landscape | `pm-sage:write-prd` (feed it the strategy canvas) |

This skill maps **who competes, where, how they win, what their advantages actually are, and where the white space sits**. It does not synthesize the strategic response. Stay in lane.
