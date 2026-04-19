# YAML Handoff Schema — Willingness-to-Pay Research

The YAML block at the end of the output is the contract between this skill and downstream skills in the strategic-research plugin (pricing / packaging, positioning, GTM).

Downstream skills parse the block. Break the schema, break the pipeline.

## Schema

```yaml
# willingness-to-pay-research handoff
version: 1
generated_at: <ISO-8601 date>

# Inherited upstream from audience-segment-research when available
framing:
  anchor: <product/company name, or null>
  industry: <short industry name>
  b2b_or_b2c: <b2b | b2c | hybrid>
  lifecycle_stage: <pre-pmf | early-pmf | scaling | mature>
  end_user_persona: <persona from upstream>
  scope_boundary: <one-sentence scope note>
  upstream_handoffs_consumed:
    industry_process_map: <true | false>
    audience_segment_research: <true | false>

# Three-layer value model per segment
segments:
  - id: <segment slug, e.g., "S1-high-volume-agencies">
    name: <human-readable name>

    # Layer A — what they pay for
    value_layer:
      leader_outcomes:
        - outcome: <ODI-form statement>
          lfk_class: <leader | filler | killer>
          kano_class: <must-have | performance | delighter | indifferent | reverse>
          kano_migration_horizon_months: <number, or null if not applicable>
          bain_elements:
            functional: [<element 1>, <element 2>]
            emotional: [<element 1>]
            life_changing: [<element 1>]
            social_impact: [<element 1>]
          opportunity_score: <number 0-20, Ulwick: importance + max(0, importance - satisfaction)>
          evidence_type: <behavioral | stated>
          source: <citation>
          confidence: <0-100>
      filler_outcomes:
        - outcome: <statement>
          reasoning: <short>
      killer_outcomes:
        - outcome: <statement>
          reasoning: <why it destroys WTP>
          severity: <low | medium | high>

    # Layer B — why they pay
    drivers_layer:
      next_best_alternative:
        name: <specific alternative, e.g., "Publicis retainer">
        price: <annualized dollar cost>
        limitations: <why buyer considers switching>
      evc_math:
        time_saved_usd_per_year: <number or null>
        revenue_uplift_usd_per_year: <number or null>
        cost_avoided_usd_per_year: <number or null>
        risk_reduction_notes: <qualitative>
        total_evc_usd_per_year: <number or null>
        share_captured_assumption: <0.0-1.0>
        reasoning: <one paragraph>
      pain_intensity: <1-10>
      urgency_trigger: <event that drives purchase>
      emotional_stakes: <short statement>
      social_stakes: <short statement>
      mom_test_tag: <behavioral | stated>

    # Layer C — how they detect value (proof signals)
    proof_signals:
      - leader_outcome_ref: <outcome text or id>
        primary_mode: <experiential | quantitative | social | temporal>
        secondary_modes: [<mode 1>, <mode 2>]
        specific_signal: <buyer-voice description>
        detection_latency: <minutes | hours | days | weeks>
        perceiver: <self | team | boss | customer | partner>
        measurement_friction: <none | low | medium | high>
        inverse_risk_signal: <what 'failing silently' looks like>
        ux_implication: <where in the product to design the signal>
        strength_scores:
          vividness: <1-5>
          speed: <1-5>
          travelability: <1-5>
          defensibility: <1-5>
          total: <4-20>
        evidence_type: <behavioral | stated | hypothesis>
        source: <citation>
        confidence: <0-100>

    # WTP band hypothesis
    wtp_band:
      low_usd: <number>
      high_usd: <number>
      unit: <per month per seat | per month flat | per use | per outcome | one-time>
      reference_anchor: <named alternative>
      reasoning: <one paragraph>
      behavioral_evidence_count: <number>
      stated_evidence_count: <number>
      disconfirming_question: <the one research question that would most change this band>
      confidence: <0-100>

    # Per-segment research plan
    research_plan:
      primary_method: <van-westendorp | gabor-granger | conjoint | byo | maxdiff | mom-test | live-price-experiment | feature-removal>
      secondary_method: <method | null>
      sample_target: <number>
      key_questions: [<question 1>, <question 2>]
      stimuli_or_attributes: <brief description of the survey/interview design>

    # Segment-level tensions and singletons specific to WTP
    tensions:
      - id: <T-NN>
        claim_a: <statement>
        claim_b: <statement>
        class: <subsegment-split | context-dependent | stated-vs-revealed | temporal | unresolved>
        resolution: <integration>
        resolution_confidence: <0-100>
    outlier_signals:
      - id: <S-NN>
        observation: <unusual WTP data point>
        source: <citation>
        hypothesis: <why it might matter>
        promotes_to_pattern_when: <evidence threshold>

# Cross-segment synthesis
cross_segment:
  shared_leader_outcomes: [<outcome 1>]
  divergent_leader_outcomes:
    - outcome: <statement>
      specific_to_segments: [<segment id>]
  killer_inventory:
    - outcome: <statement>
      killer_for: [<segment id>]
      leader_for: [<segment id>]
      packaging_implication: <separate SKU | remove | quarantine>
  wtp_variance_ratio: <high_segment_high / low_segment_low, e.g., 8.0>
  kano_migration_watchlist:
    - feature: <name>
      currently: <delighter>
      expected_to_become: <must-have>
      horizon_months: <number>

# Consolidated proof-signals matrix
proof_signals_matrix:
  - leader_outcome: <text>
    segment: <id>
    primary_mode: <mode>
    strength_total: <4-20>
    ux_placement: <description>

# Tensions that span multiple segments
cross_segment_tensions:
  - id: <T-NN>
    scope: <all segments | segments X and Y>
    claim_a: <statement>
    claim_b: <statement>
    class: <class>
    resolution: <integration>
    resolution_confidence: <0-100>

# Singletons that don't fit any segment — nascent WTP patterns
global_outliers:
  - id: <S-NN>
    observation: <statement>
    source: <citation>
    hypothesis: <why it might signal a new WTP pattern>
    promotes_to_pattern_when: <evidence threshold>

glossary:
  - term: <term>
    definition: <plain-language definition>

evidence_quality:
  total_observations: <count>
  behavioral_ratio: <0.0-1.0>
  primary_sources_distinct: <count>
  overall_confidence: <0-100>
  disconfirming_searches_performed: <count>
  known_gaps: [<gap 1>, <gap 2>]

open_questions:
  # Priority research directions for pricing/packaging, positioning, and GTM skills
  - question: <question>
    why_it_matters: <reason>
    suggested_method: <method from wtp-research-methods.md>
    priority: <high | medium | low>

rejected_framings:
  - framing: <name, e.g., "per-seat monetization">
    why_rejected: <one line>
```

## Validation checklist

Before finalizing:

- [ ] Every segment has at least one Leader outcome with an EVC math entry (or explicit "not calculable" note).
- [ ] Every Leader outcome has at least one proof signal with all strength-score fields populated.
- [ ] Every WTP band has a named reference anchor (not "status quo" generic).
- [ ] Every WTP band has `behavioral_evidence_count` and `stated_evidence_count` populated; behavioral > 0 preferred.
- [ ] `mom_test_tag` is populated per segment drivers block.
- [ ] `kano_migration_horizon_months` is populated for every delighter.
- [ ] `killer_inventory` exists (even if empty, explicitly so).
- [ ] `wtp_variance_ratio` is computed and ≥ 2.0 (or flagged as segmentation concern).
- [ ] `disconfirming_searches_performed` ≥ 2.
- [ ] `open_questions` has at least 3 items, each with a suggested method.
- [ ] `rejected_framings` has 2–3 entries.

## Why this schema matters

Downstream skills need:

- **Pricing / packaging:** WTP bands per segment, tier design inputs (G/B/B), killer inventory (what to exclude), monetization-metric hints from the drivers layer.
- **Positioning (Dunford):** value themes per segment = the Leader outcomes × Bain layers stacked; competitive alternatives = next-best alternatives named.
- **GTM motion:** proof signals dictate onboarding KPIs (time-to-first-signal), UX design placement, and renewal-triggering moments.
- **Product roadmap:** Kano migration watchlist tells PMs which delighters to harvest soon before they decay; Killer inventory tells them what to remove.

Changing the schema breaks parsing. Bump `version` and document breaking changes.
