---
name: audience-segment-research
description: Build a deep, segmented understanding of the audience, users, buyers, customers, and — for B2B — the full stakeholder map for a product, category, or industry. Integrates conflicting signals rather than resolving them prematurely, and preserves singleton insights alongside patterns. Use this skill when the user asks to "understand the audience", "map the users", "segment the customers", "build a customer profile", "identify the ICP", "map the stakeholders", "who's the champion vs. the economic buyer", "do audience research", "analyze who cares about this", "build segment profiles", or provides an industry/category/product and wants a strategic view of who buys, uses, influences, and blocks. Consumes a handoff from industry-process-map when available, or bootstraps its own framing. Output is one markdown doc with primary segmentation, per-segment profiles, stakeholder map, a tension log for contradictions held, a singletons/outliers section, a glossary, and a YAML handoff for downstream skills.
---

# Audience & Segment Research

## Promise

Given an anchor (product, category, or industry), produce **one markdown artifact** that captures who is in the audience, how they cluster into segments, and how they buy and use — deep enough to inform positioning, pricing, and roadmap, without collapsing complexity.

The artifact contains:

1. **Framing & sources** — inherited from `industry-process-map` handoff when available, otherwise bootstrapped.
2. **Primary segmentation** — one chosen lens (or a two-lens hybrid), with rejected lenses in an appendix.
3. **Segment profiles** — one per segment, behavioral and specific.
4. **Stakeholder map** — buyer / user / champion / approver / blocker / gatekeeper / renewer (B2B), or buyer / influencer / user (B2C).
5. **Cross-segment synthesis** — shared vs. divergent jobs, segment adjacency, cannibalization risks.
6. **Tension log** — contradictions held, classified, visible.
7. **Outliers & singletons** — unique signals retained as evidence of nascent sub-segments or edge cases.
8. **Glossary, evidence-quality notes, open questions for willingness-to-pay.**
9. **YAML handoff** — structured data for the next skill in the plugin.

The output is read by a CPO-level audience. Write for a reader who will make allocation decisions on it.

## Operating principles

Six principles define this skill. When in doubt, return to them.

### 1. Behavior beats stated preference

What people *did* — bought, referred, paid full, churned, hacked around — beats what they *said* in a survey. Every segment claim is tagged as behavioral or stated; behavioral is weighted higher. A segment defined by "companies that value X" is a vibe; defined by "companies that already paid for Y integration and renewed twice" is real.

Rule of thumb: if a claim cannot be traced to an observable action, label it stated and lower its weight.

### 2. Start from the ecstatic (Dunford Ch. 3)

When real customers exist, shortlist the ones who love the product — bought fast, paid full, referred, resisted discounting — and find patterns among them only. Muddy patterns come from surveying the middle. Signal comes from the edges.

When customers don't exist yet, keep the net wide: hypothesize multiple candidate segments, flag each as speculative, and frame the output as calibration for research — not conclusion. Premature segmentation pre-PMF is worse than no segmentation.

### 3. Segment by "who cares a lot AND is identifiable" (Dunford Ch. 9)

A real segment passes two tests:

| Test | Pass | Fail |
|---|---|---|
| **Identifiability** | Can you build a prospect list? "Banks with PCI-DSS obligations and 500+ employees" | "Companies that value happy people" |
| **Care intensity** | Is there a specific, unmet, important need common to members? | Need is as common here as in the general market |

Pure demographics ("men 18–30", "SMBs 50-200") are rejected as **primary** segmentation. They may appear as descriptors inside a segment — never as the defining criterion.

### 4. Integrate tensions — do not resolve them prematurely

When two credible sources disagree about a segment, both stay. Every tension is classified, not silenced:

| Class | Meaning | Action |
|---|---|---|
| **Subsegment split** | Two real sub-types inside the segment | Split into sub-segments |
| **Context-dependent** | Same buyer, different situations | Add a context qualifier |
| **Stated vs. revealed** | Survey vs. behavior | Tag each; behavior outweighs |
| **Temporal shift** | Segment has changed over time | Note the direction and date |
| **Unresolved** | Genuinely unclear | Hold explicitly as an open question |

Tensions live in a dedicated log in the output — not hidden inside prose. Holding a tension visible is more useful than resolving it wrongly. See `references/tensions-and-singletons.md`.

### 5. Preserve singletons and outliers

Patterns appear in 3+ data points; singletons in 1–2. Singletons are **not noise**. They often foreshadow an emerging sub-segment, reveal an edge case that breaks the product, or expose a misclassified observation that unravels a category error.

Every segment profile carries an **Outlier signals** section. Singletons record: the observation, the source, and a hypothesis about why it might matter. A dedicated global section collects singletons that don't fit any segment yet.

A pattern-only map is a lossy compression of reality. We trade a little neatness for a lot of signal.

### 6. Map the full buying unit, not just the user (B2B)

For B2B, user ≠ buyer ≠ budget holder ≠ blocker. A segmented audience map that only profiles the end-user misses the people who approve, veto, pay, implement, and decide renewal. Every B2B segment profile includes the stakeholder map for that segment — user, champion, economic buyer, approver, blocker, renewer.

For B2C: the triad is usually user / influencer / purchaser. These collapse into one person for many categories but diverge for gift-buyers, parents, household budget holders, and accessibility buyers.

## Workflow

Execute in order. Phases feed forward.

### Phase 1 — Intake & calibration

Consume input in this order of preference:

1. **YAML handoff from `industry-process-map`** — parse it. Inherit `framing.anchor`, `framing.industry`, `framing.end_user_persona`, `framing.scope_boundary`, `process_tree`, `substitutes`, and `open_questions`. The open questions from step 1 become priority research directions here.
2. **User-provided context** — anchor, industry, known customers, existing segments, internal data (interview notes, CRM tags, support tickets).
3. **Bootstrap** — if neither is available, ask 2–3 clarifying questions with `AskUserQuestion`.

Resolve these variables before research:

| Variable | What it is | Example |
|---|---|---|
| **Anchor** | Reference product/company (optional) | "SplitMetrics" |
| **Industry / domain** | The space | "Mobile ad optimization" |
| **B2B or B2C** | Determines stakeholder map style | "B2B (SMB to enterprise)" |
| **Lifecycle stage** | Pre-PMF, early PMF, scale — changes segmentation posture | "Early PMF" |
| **Known customers** | Customers whose behavior can anchor the ecstatic filter | "15 paying; 3 case studies" |
| **Scope boundary** | How wide to go | "Paid acquisition managers at consumer apps, excluding publisher-side" |

When to ask vs. assume: **ask** if B2B/B2C is ambiguous or lifecycle stage is unknown — both change the method. **Assume** otherwise and state assumptions explicitly. Cap at 3 questions.

### Phase 2 — Research

Goal: practitioner language, real behavior, conflicting views, outliers — not a synthesis of vendor marketing.

Read `references/research-playbook.md` at the start of this phase for query patterns and source-mix guidance.

Source priority (high to low signal):

1. **Behavioral artefacts** — case studies, public churn stories, cohort analyses, public deal registries, retention posts, LinkedIn tenure data
2. **Practitioner-authored content** — forum threads (Reddit, Hacker News, niche Discords surfaced on the web), Substack/Medium posts written by actual operators
3. **Detailed reviews** — G2/Capterra/TrustRadius with specific workflow descriptions; filter out one-line reviews
4. **Job descriptions** — reveals what buyer orgs actually want done; maps buyer titles to responsibilities
5. **Vendor content** — use only for glossary and claimed ICP; treat with suspicion

Budget: 8–15 searches. Stop when new sources stop changing the emerging segmentation.

Capture into a scratch table — every observation carries source and evidence type:

| Observation | Source | Segment hypothesis | Behavioral or stated | Confidence |

This table is the raw material for both pattern-finding and singleton-preservation. Keep it in the working file; do not discard.

### Phase 3 — Surface candidate segmentation lenses

Generate **3–5 candidate lenses** internally. Do not show the user yet.

Read `references/segmentation-lenses.md` before generating. The catalog covers:

- Workflow-shape
- Maturity / sophistication (Schwartz's 5 awareness levels; DIY vs. outsourced vs. automated)
- Use-case / JTBD
- Org context (stage, size, regulatory, ecosystem)
- Stakeholder archetype (role and authority)
- Trigger-to-buy
- Switch-from (competitive alternative)
- Hybrid two-lens matrices

Reject pure demographics as a primary lens. Describe with demographics, never define with them.

### Phase 4 — Score and select the primary lens

Score each candidate 1–5 on:

| Criterion | Bad (1) | Good (5) |
|---|---|---|
| **Identifiability** | Can't build a list from this lens | Clean, mechanical list-build |
| **Care intensity** | All members care equally | Specific, unmet, important need common to members |
| **Behavioral grounding** | Keys on what people say | Keys on what people do |
| **Downstream actionability** | WTP / positioning skills can't use it | Segments have clear price sensitivity and messaging implications |

Pick the winner. Record a one-paragraph rationale for why this lens beat the alternatives. A **two-lens hybrid** (e.g., workflow-shape × sophistication) is acceptable when one lens alone under-specifies — never more than two.

Save the losers for the appendix with scores and rejection reasons.

### Phase 5 — Build segment profiles

For each segment produced by the chosen lens, write a profile using `assets/output-template.md`.

Profile fields (full structure in the template):

| Field | Purpose |
|---|---|
| Identifier | Behavioral + firmographic descriptors that let you spot one |
| Prevalence estimate | Rough % of addressable audience, with confidence |
| Who they are | Role, context, scale |
| What they do | Observed workflow, not imagined |
| Jobs / desired outcomes | The transformation they want |
| Pains & unmet needs | Specific, with source |
| Current alternatives | Including non-consumption, DIY, agency |
| Buying triggers | Events that push them into buying |
| Stakeholder map (this segment) | Who decides, champions, blocks |
| Tensions held | Contradictions about this segment, classified |
| Outlier signals | 1–2 data-point insights worth preserving |
| Confidence | 0–100% this segment is real |
| Evidence roll-up | Count of behavioral vs. stated observations |

Profiles are at least 250 words. Shorter = the segment isn't real, or research is too thin. Go back to Phase 2.

### Phase 6 — Cross-segment synthesis

Half a page. Two cross-cuts:

1. **Shared vs. divergent** — jobs and pains common across segments (universal) vs. unique to one or two (differentiating).
2. **Segment adjacency** — which segments can a single product serve together vs. which require different products. Call out cannibalization risks (one segment perceives another as a competitor).

The job of this section is to make the *relationships between segments* legible.

### Phase 7 — Assemble the output

Use `assets/output-template.md`. Full structure:

1. Framing & sources
2. Segmentation decision (chosen lens + rationale)
3. Segment profiles
4. Stakeholder map (B2B or B2C)
5. Cross-segment synthesis
6. Tension log
7. Outliers & singletons (global)
8. Glossary
9. Evidence quality notes
10. Open questions for willingness-to-pay
11. Appendix — rejected segmentation lenses
12. YAML handoff block

Write to `/sessions/wonderful-quirky-ptolemy/mnt/tempSkills/audience-segment-research-[slug].md` where `[slug]` is a kebab-case tag of the anchor or industry (e.g., `splitmetrics-apple-ads`).

The YAML handoff block is non-negotiable. Schema in `references/handoff-schema.md`.

### Phase 8 — Share

Link the file with a `computer://` link. Short message: title, chosen lens in one sentence, link. Don't restate content in chat.

## Quality audit — mandatory before Phase 7

Run these checks explicitly. Fix any failure before writing the final artifact.

- [ ] Does every segment pass the identifiability test (prospect list buildable)?
- [ ] Is every major claim traceable to a source in the scratch table?
- [ ] Does every profile separate behavioral from stated observations?
- [ ] Is every tension classified (subsegment-split / context-dependent / stated-vs-revealed / temporal / unresolved)?
- [ ] Do singletons appear somewhere — per-segment and/or in the global outliers section?
- [ ] For B2B: does every segment's stakeholder map include a plausible blocker?
- [ ] Is any segment a pure demographic cut? (If yes, redefine using behavior.)
- [ ] Does the YAML handoff validate against `references/handoff-schema.md`?

If any check fails, loop back to the relevant phase.

## Writing style

- **No preamble.** Start with the framing table.
- **Tables and structured profiles over prose.** Prose only where nuance requires it.
- **Specific names, not categories.** "A 12-person performance-marketing team at a FinTech with 6+ countries" beats "mid-market marketing teams".
- **Source tags on non-obvious claims.** Inline `[src: G2 review 2024-09]` or `[src: r/PPC thread]`.
- **Confidence marks as percentages.** No hedge words ("somewhat", "arguably").
- **Honest gaps.** "Thin evidence — 2 data points, 1 behavioral" beats dressing it up.
- **Verbs for segment labels** where possible. "Outsource-and-oversee paid acquisition buyers" beats "Agency-reliant marketers".

## When this skill is the wrong tool

| User wants | Use |
|---|---|
| Map the space (processes, workflow) | `industry-process-map` (skill #1) |
| Willingness-to-pay / pricing sensitivity | Skill #3 (downstream in this plugin) |
| Competitive teardown of named vendors | `product-management:competitive-brief` |
| Synthesize a pile of interviews you already have | `product-management:synthesize-research` |
| Positioning canvas | `pm-sage:position-product` (feed it this skill's output) |

This skill maps **who**. Stay in lane.
