# YAML Handoff Schema

The YAML block at the end of the output is the contract between this skill and downstream skills in the strategic-research plugin (willingness-to-pay, positioning, GTM).

Downstream skills parse the block. Break the schema, break the pipeline.

## Schema

```yaml
# audience-segment-research handoff
version: 1
generated_at: <ISO-8601 date>

# Inherited from industry-process-map when available; otherwise bootstrapped
framing:
  anchor: <product/company name, or null>
  industry: <short industry name>
  b2b_or_b2c: <b2b | b2c | hybrid>
  lifecycle_stage: <pre-pmf | early-pmf | scaling | mature>
  end_user_persona: <persona from upstream, if any>
  scope_boundary: <one-sentence scope note>
  upstream_handoff_consumed: <true | false>

# The chosen segmentation lens (one or a two-lens hybrid)
segmentation:
  primary_lens: <e.g., "workflow-shape">
  secondary_lens: <lens name, or null if single-lens>
  rationale: <one-paragraph why this lens won>
  scores:
    identifiability: <1-5>
    care_intensity: <1-5>
    behavioral_grounding: <1-5>
    downstream_actionability: <1-5>

# Each segment gets a full structured profile
segments:
  - id: <short slug, e.g., "S1-high-volume-agencies">
    name: <human-readable name>
    one_line: <one-sentence description>
    identifier:
      behavioral: [<observable action 1>, <observable action 2>]
      firmographic: [<descriptor 1>, <descriptor 2>]
    prevalence_estimate: <percent of addressable audience>
    prevalence_confidence: <0-100>

    who_they_are: <short paragraph — role, context, scale>
    what_they_do: <observed workflow — verbs>
    jobs:
      - <JTBD statement>
    pains_unmet_needs:
      - pain: <description>
        source: <citation>
        evidence_type: <behavioral | stated>
    current_alternatives:
      - <alternative 1, e.g., "Spreadsheet">
      - <alternative 2, e.g., "Agency X">
    buying_triggers:
      - <trigger 1>

    stakeholders:
      # For B2B; for B2C use user/purchaser/influencer only
      user: <title + 1-line description>
      champion: <title + role in deal>
      economic_buyer: <title>
      approvers: [<role 1>, <role 2>]
      blocker: <role most likely to kill the deal>
      renewer: <role>
      implementer: <role or null>

    tensions:
      # Tensions specific to this segment (cross-segment tensions go in `tensions:` at root)
      - id: <T-NN>
        claim_a: <statement>
        claim_b: <contradicting statement>
        class: <subsegment-split | context-dependent | stated-vs-revealed | temporal | unresolved>
        resolution: <integration statement>
        resolution_confidence: <0-100>

    outlier_signals:
      - id: <S-NN>
        observation: <the unusual thing>
        source: <citation>
        hypothesis: <why it might matter>
        promotes_to_pattern_when: <what additional evidence would confirm>

    confidence: <0-100 this segment is real>
    evidence_rollup:
      behavioral_observations: <count>
      stated_observations: <count>

# Tensions that span multiple segments or the overall audience
cross_segment_tensions:
  - id: <T-NN>
    scope: <e.g., "all segments" or "S1 and S2">
    claim_a: <statement>
    claim_b: <statement>
    class: <one of the five classes>
    resolution: <integration statement>
    resolution_confidence: <0-100>

# Singletons that don't fit any current segment — nascent patterns
global_outliers:
  - id: <S-NN>
    observation: <the unusual thing>
    source: <citation>
    hypothesis: <why it might matter — possibly new segment>
    promotes_to_pattern_when: <what additional evidence would confirm>

# Cross-segment synthesis
cross_segment:
  shared_jobs: [<job common to 2+ segments>]
  shared_pains: [<pain common to 2+ segments>]
  divergent_jobs:
    - job: <statement>
      specific_to_segments: [<segment id 1>, <segment id 2>]
  adjacency:
    # Which segments can be served by one product together
    compatible_pairs: [[<seg1>, <seg2>]]
    # Which segments would perceive each other as competitors if bundled
    cannibalization_risks: [[<seg1>, <seg2>]]

glossary:
  - term: <term>
    definition: <user-facing definition>

evidence_quality:
  total_observations: <count>
  behavioral_ratio: <0.0-1.0>
  primary_sources_distinct: <count>
  overall_confidence: <0-100>
  known_gaps: [<gap 1>, <gap 2>]

open_questions:
  # Priority research directions for skill #3 (willingness-to-pay)
  # and any unresolved tensions
  - question: <question>
    why_it_matters: <short reason>
    suggested_method: <interview | survey | analytics query | price test | observation>

rejected_lenses:
  - lens: <name>
    score_total: <sum of 4 criteria>
    why_rejected: <one-line reason>
```

## Validation checklist

Before finalizing:

- [ ] `segmentation.primary_lens` is NOT a pure demographic/firmographic cut.
- [ ] Every segment has at least one behavioral identifier.
- [ ] Every B2B segment has a named `blocker`.
- [ ] Every segment with pain claims has at least one `evidence_type: behavioral` pain.
- [ ] Every tension is classified.
- [ ] `global_outliers` has at least 1 entry OR a note in `evidence_quality.known_gaps` that none were found.
- [ ] `rejected_lenses` has 2–3 entries.
- [ ] `open_questions` has at least 3 items. This is runway for skill #3.
- [ ] `evidence_rollup.behavioral_observations` > 0 for every segment (no segment built entirely on stated preference).

## Why this schema matters

Downstream skills need:

- **Willingness-to-pay (skill #3):** segment-level price sensitivity, stakeholder authority to spend, trigger-to-buy (predicts urgency premium)
- **Positioning:** competitive alternatives per segment, value themes per segment, champion language
- **GTM motion:** blocker per segment, buying unit composition, ecstatic-customer signal intensity

Changing the schema breaks parsing. Bump `version` and document breaking changes.
