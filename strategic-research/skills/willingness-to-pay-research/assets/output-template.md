# Willingness-to-Pay Research — {anchor_or_industry}

## Framing & sources

| Field | Value |
|---|---|
| **Anchor** | {anchor, or "none"} |
| **Industry** | {short industry name} |
| **B2B / B2C** | {b2b / b2c / hybrid} |
| **Lifecycle stage** | {pre-PMF / early-PMF / scaling / mature} |
| **End-user persona (upstream)** | {from audience-segment-research, or "bootstrapped"} |
| **Scope boundary** | {one-sentence scope note} |
| **Upstream handoffs consumed** | industry-process-map: {Y/N}; audience-segment-research: {Y/N} |
| **Generated** | {date} |

### Research source mix

| Tier | Source type | Count | Notes |
|---|---|---|---|
| 1 | Case studies with disclosed ACV / deal size | {n} | |
| 2 | Churn and expansion posts, SaaS cohort writeups | {n} | |
| 3 | Reviews with price commentary | {n} | |
| 4 | Competitor pricing pages (category anchors) | {n} | |
| 5 | Practitioner forums (Reddit, HN, niche) | {n} | |
| 6 | Job descriptions with budget / tool mentions | {n} | |
| 7 | Vendor marketing (glossary only) | {n} | |

### Evidence base summary

| Metric | Value |
|---|---|
| Total observations in scratch table | {n} |
| Behavioral : stated ratio | {ratio, e.g., 2:1} |
| Distinct primary sources | {n} |
| Disconfirming searches performed | {n} |
| Overall confidence in WTP model | {0-100}% |

## Three-layer value model per segment

{Repeat the full segment block for each segment.}

---

### Segment {N} — {Name}

**One-liner:** {one-sentence description of the segment (inherited from handoff)}

**Segment identifier (inherited):**
- Behavioral: {observable action 1}; {observable action 2}
- Firmographic: {descriptor 1}; {descriptor 2}

---

#### Layer A — What they pay for

**Leader outcomes** (drive ≥80% of WTP)

| # | Outcome (ODI form) | L/F/K | Kano | Kano migration horizon | Bain elements activated | Opportunity score | Evidence | Confidence |
|---|---|---|---|---|---|---|---|---|
| L1 | {"Reduce time-to-X when Y"} | Leader | Performance | n/a | Functional (saves time), Emotional (reduces anxiety) | 14/20 | {src: ..., behavioral} | 75% |
| L2 | ... | | | | | | | |

**Filler outcomes** (neutral WTP — keep for tier differentiation)

| Outcome | Reasoning |
|---|---|
| ... | ... |

**Killer outcomes** (reduce WTP if present — remove or quarantine)

| Outcome | Severity | Reasoning |
|---|---|---|
| ... | {low/med/high} | ... |

---

#### Layer B — Why they pay

**Next-best alternative:** {specific, named — e.g., "$3,500/mo Publicis retainer" or "manual spreadsheet + 2 analyst hires"}

| Alt limitation | Why they'd switch |
|---|---|
| {limitation} | {driver} |

**EVC math:**

| Value component | Amount | Reasoning |
|---|---|---|
| Time saved | ${n}/yr | {hours/week × loaded rate × horizon} |
| Revenue uplift | ${n}/yr | {lift × attribution × horizon} |
| Cost avoided | ${n}/yr | {probability × impact} |
| Risk reduction | {qualitative} | {reasoning} |
| **Total EVC** | **${n}/yr** | |
| Share captured assumption | {25-60}% | {reasoning} |

**Pain intensity:** {1-10}
**Urgency trigger:** {event that flips tolerating-pain into actively-looking}
**Emotional stakes:** {short statement}
**Social stakes:** {short statement}
**Mom Test tag:** {behavioral / stated / mixed} — {explanation}

---

#### Layer C — How they know it's working (proof signals)

For each Leader in Layer A, the proof signal:

**Leader L1 — {outcome}**

| Field | Value |
|---|---|
| Primary mode | Experiential / Quantitative / Social / Temporal |
| Secondary modes | {mode, mode} |
| Specific signal (buyer voice) | "{quoted phrasing}" |
| Detection latency | {minutes / hours / days / weeks} |
| Perceiver | Self / Team / Boss / Customer / Partner |
| Measurement friction | None / Low / Medium / High |
| Inverse risk signal | {what "failing silently" looks like} |
| UX / product implication | {where to design the signal into the product} |
| Evidence | {src, behavioral/stated/hypothesis} |
| Confidence | {0-100}% |

**Strength scorecard (1-5 each):**

| Lever | Score | Reasoning |
|---|---|---|
| Vividness | {n} | |
| Speed | {n} | |
| Travelability | {n} | |
| Defensibility | {n} | |
| **Total** | **{sum}/20** | |

{Repeat for each Leader.}

---

#### WTP band hypothesis

| Field | Value |
|---|---|
| **Band** | ${low}–${high} {per unit} |
| **Unit** | {per month per seat / per month flat / per use / per outcome / one-time} |
| **Reference anchor** | {named alternative} |
| **Reasoning** | {one paragraph: how EVC math × share captured lands at this band} |
| **Behavioral evidence count** | {n} |
| **Stated evidence count** | {n} |
| **Disconfirming question** | {the one research question that would most change this band} |
| **Confidence** | {0-100}% |

---

#### Per-segment research plan

| Field | Value |
|---|---|
| Primary method | {Van Westendorp / Gabor-Granger / Conjoint / BYO / MaxDiff / Mom-Test interview / Live price experiment / Feature removal} |
| Secondary method | {method or "none"} |
| Sample target | {n} |
| Key questions | {question 1}; {question 2} |
| Stimuli / attributes | {brief design note} |

**Draft interview / survey prompt:** {one paragraph of specific wording ready to run}

---

#### Tensions held — this segment

**T-{NN}:** {short title}
- **Claim A:** {statement} — [src: ..., behavioral/stated]
- **Claim B:** {contradicting statement} — [src: ..., behavioral/stated]
- **Class:** {subsegment-split / context-dependent / stated-vs-revealed / temporal / unresolved}
- **Resolution:** {integration statement}
- **Confidence:** {0-100}%

#### Outlier signals — this segment

**S-{NN}:** {observation}
- **Source:** {citation}
- **Hypothesis:** {why it might matter}
- **Promotes to pattern when:** {evidence threshold}

---

{End of segment block. Repeat for each segment.}

## Cross-segment synthesis

### Shared vs. divergent Leaders

| Dimension | Shared across all segments | Divergent (segment-specific) |
|---|---|---|
| Leader outcomes | ... | ... |
| Bain elements stacked | ... | ... |
| Next-best alternatives | ... | ... |
| Urgency triggers | ... | ... |

### WTP variance

| From / to | Ratio |
|---|---|
| Highest-WTP segment top vs. lowest-WTP segment bottom | {n.n}× |

{One paragraph interpreting variance — does the segmentation hold? What does the variance imply for packaging?}

### Killer inventory (packaging implications)

| Outcome | Killer for | Leader for | Packaging implication |
|---|---|---|---|
| {outcome} | {seg id} | {seg id} | {separate SKU / remove / quarantine} |

### Kano migration watchlist

| Feature / outcome | Currently | Expected to become | Horizon (months) | Notes |
|---|---|---|---|---|
| {name} | Delighter | Must-have | {n} | |

## Consolidated proof-of-value signals matrix

Across all segments and all Leader outcomes — the product-design brief.

| Leader outcome | Segment | Primary mode | Signal strength (4-20) | UX placement | Inverse risk |
|---|---|---|---|---|---|
| ... | S1 | Experiential | 13 | Inline calendar nudge at meeting start | Brief too shallow → manual prep resumes |
| ... | S2 | Quantitative | 17 | Dashboard with pre/post metric on landing | Metric plateaus → renewal risk |
| ... | ... | ... | ... | ... | ... |

One paragraph on signal-mode patterns: does the audience cluster on one mode, or do segments require different proof designs?

## WTP research plan — consolidated

Prioritized roll-up of the per-segment plans.

| Priority | Segment | Method | Sample | Why it matters |
|---|---|---|---|---|
| P1 | S{N} | {method} | {n} | {one line} |
| P2 | ... | ... | ... | ... |

Budget and sequencing notes: {one paragraph on what to run first, what depends on what}.

## Tension log — cross-segment

Tensions that span multiple segments or the overall WTP model.

| # | Tension | Class | Resolution | Confidence |
|---|---|---|---|---|
| T-{N} | {A vs. B} | {class} | {integration} | {0-100}% |

## Outliers & singletons — global

Observations that don't fit any current segment but are preserved as nascent WTP patterns.

**S-{NN}:** {observation}
- **Source:** {citation}
- **Hypothesis:** {why it might signal a new WTP pattern, sub-segment, or edge case}
- **Promotes to pattern when:** {evidence threshold}

{Repeat.}

If zero singletons were found after deliberate counter-evidence search: *"No global singletons observed after targeted counter-evidence search across N sources. Noted for re-check in 6 months."*

## Glossary

| Term | Definition |
|---|---|
| {term} | {plain-language definition} |

Include only terms that are opaque to an outsider but everyday language for the buyer persona.

## Evidence quality notes

| Metric | Value |
|---|---|
| Total observations | {n} |
| Behavioral ratio | {%} behavioral, {%} stated |
| Distinct primary sources | {n} |
| Disconfirming searches | {n} |
| Overall confidence | {0-100}% |

**Known gaps:**
- {gap 1 — e.g., "No case studies with disclosed ACV for S3; WTP band for that segment is hypothesis-only"}
- {gap 2}

## Open questions for pricing / packaging / positioning / GTM

Prioritized list. Each question has a "why it matters" and a suggested method.

1. **[P1] {Question}** — Why: {reason}. Method: {method from wtp-research-methods.md}.
2. **[P1] {Question}** — Why: {reason}. Method: {method}.
3. **[P2] {Question}** — Why: {reason}. Method: {method}.

## Appendix — rejected value framings

{2-3 framings that lost. Evidence the choice was made with alternatives in view.}

### Rejected framing A — {name, e.g., "feature-price conjoint without behavioral layer"}
- Why considered: {one line}
- Why rejected: {one line}

### Rejected framing B — {name, e.g., "purely EVC-driven band without Bain emotional stacking"}
- Why considered: {one line}
- Why rejected: {one line}

## Handoff block

```yaml
# willingness-to-pay-research handoff
version: 1
generated_at: {ISO-8601 date}

framing:
  anchor: {name or null}
  industry: {name}
  b2b_or_b2c: {b2b | b2c | hybrid}
  lifecycle_stage: {pre-pmf | early-pmf | scaling | mature}
  end_user_persona: {persona}
  scope_boundary: {sentence}
  upstream_handoffs_consumed:
    industry_process_map: {true | false}
    audience_segment_research: {true | false}

segments:
  - id: {slug}
    name: {name}
    value_layer:
      leader_outcomes:
        - outcome: {ODI statement}
          lfk_class: {leader | filler | killer}
          kano_class: {must-have | performance | delighter | indifferent | reverse}
          kano_migration_horizon_months: {number or null}
          bain_elements:
            functional: [{element}]
            emotional: [{element}]
            life_changing: [{element}]
            social_impact: [{element}]
          opportunity_score: {0-20}
          evidence_type: {behavioral | stated}
          source: {citation}
          confidence: {0-100}
      filler_outcomes:
        - outcome: {statement}
          reasoning: {short}
      killer_outcomes:
        - outcome: {statement}
          reasoning: {why}
          severity: {low | medium | high}
    drivers_layer:
      next_best_alternative:
        name: {name}
        price: {dollar cost}
        limitations: {why switch}
      evc_math:
        time_saved_usd_per_year: {number or null}
        revenue_uplift_usd_per_year: {number or null}
        cost_avoided_usd_per_year: {number or null}
        risk_reduction_notes: {qualitative}
        total_evc_usd_per_year: {number or null}
        share_captured_assumption: {0.0-1.0}
        reasoning: {paragraph}
      pain_intensity: {1-10}
      urgency_trigger: {event}
      emotional_stakes: {statement}
      social_stakes: {statement}
      mom_test_tag: {behavioral | stated}
    proof_signals:
      - leader_outcome_ref: {outcome text or id}
        primary_mode: {experiential | quantitative | social | temporal}
        secondary_modes: [{mode}]
        specific_signal: {buyer-voice description}
        detection_latency: {minutes | hours | days | weeks}
        perceiver: {self | team | boss | customer | partner}
        measurement_friction: {none | low | medium | high}
        inverse_risk_signal: {description}
        ux_implication: {where to design}
        strength_scores:
          vividness: {1-5}
          speed: {1-5}
          travelability: {1-5}
          defensibility: {1-5}
          total: {4-20}
        evidence_type: {behavioral | stated | hypothesis}
        source: {citation}
        confidence: {0-100}
    wtp_band:
      low_usd: {number}
      high_usd: {number}
      unit: {unit}
      reference_anchor: {name}
      reasoning: {paragraph}
      behavioral_evidence_count: {number}
      stated_evidence_count: {number}
      disconfirming_question: {question}
      confidence: {0-100}
    research_plan:
      primary_method: {method}
      secondary_method: {method or null}
      sample_target: {number}
      key_questions: [{question}]
      stimuli_or_attributes: {description}
    tensions:
      - id: T-{NN}
        claim_a: {statement}
        claim_b: {statement}
        class: {class}
        resolution: {integration}
        resolution_confidence: {0-100}
    outlier_signals:
      - id: S-{NN}
        observation: {statement}
        source: {citation}
        hypothesis: {why it matters}
        promotes_to_pattern_when: {threshold}

cross_segment:
  shared_leader_outcomes: [{outcome}]
  divergent_leader_outcomes:
    - outcome: {statement}
      specific_to_segments: [{seg id}]
  killer_inventory:
    - outcome: {statement}
      killer_for: [{seg id}]
      leader_for: [{seg id}]
      packaging_implication: {implication}
  wtp_variance_ratio: {number}
  kano_migration_watchlist:
    - feature: {name}
      currently: delighter
      expected_to_become: must-have
      horizon_months: {number}

proof_signals_matrix:
  - leader_outcome: {text}
    segment: {id}
    primary_mode: {mode}
    strength_total: {4-20}
    ux_placement: {description}

cross_segment_tensions:
  - id: T-{NN}
    scope: {scope}
    claim_a: {statement}
    claim_b: {statement}
    class: {class}
    resolution: {integration}
    resolution_confidence: {0-100}

global_outliers:
  - id: S-{NN}
    observation: {statement}
    source: {citation}
    hypothesis: {why it matters}
    promotes_to_pattern_when: {threshold}

glossary:
  - term: {term}
    definition: {definition}

evidence_quality:
  total_observations: {n}
  behavioral_ratio: {0.0-1.0}
  primary_sources_distinct: {n}
  overall_confidence: {0-100}
  disconfirming_searches_performed: {n}
  known_gaps: [{gap}]

open_questions:
  - question: {question}
    why_it_matters: {reason}
    suggested_method: {method}
    priority: {high | medium | low}

rejected_framings:
  - framing: {name}
    why_rejected: {reason}
```
