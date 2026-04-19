# Handoff Schema — Competitor Evaluation → Synthesis Skill

The YAML handoff block is the contract with the downstream synthesis skill (#5 in the pipeline). Its job is to make every Phase 1–10 finding machine-parseable so the synthesis skill does not re-derive them.

## Schema rules

1. **YAML must be valid** — parseable by a standard YAML 1.2 parser. Use spaces (2 per level), no tabs.
2. **All required fields present.** Optional fields may be omitted but must be empty rather than missing if a previous skill expected them.
3. **Confidence on every claim.** Every per-competitor verdict, every Power call, every white-space hypothesis carries a `confidence: <0–100>` field.
4. **Evidence tier on non-trivial claims.** `evidence_tier: behavioral | pattern | stated`.
5. **Inherited identifiers preserved.** Segment IDs from `audience-segment-research`, matrix cell IDs from `industry-process-map`, and WTP band IDs from `willingness-to-pay-research` are referenced by their original IDs — never renamed.
6. **No prose inside YAML values that exceeds 160 chars.** Push longer text into the markdown body and reference it.

## Required top-level fields

```yaml
version: 1
skill: competitor-evaluation
anchor:
  name: <string>
  industry: <string>
  generated_at: <YYYY-MM-DD>
inherited_from:
  industry_process_map: <true|false>
  audience_segment_research: <true|false>
  willingness_to_pay_research: <true|false>
matrix_ref:
  framing: <string — inherited from skill #1, e.g., "Process step × Channel">
  cells: [<list of cell IDs from skill #1>]
segments_ref: [<list of segment IDs from skill #2>]
wtp_bands_ref: [<list of band IDs from skill #3>]
```

## Required per-competitor block

For each shortlisted competitor, one block:

```yaml
competitors:
  - id: <kebab-case slug, stable across runs>
    name: <string>
    class: direct | indirect | adjacent | substitute | non-consumption
    confidence: <0–100>
    evidence_tier: behavioral | pattern | stated
    one_line: <string ≤ 160 chars, buyer words>
    coverage:
      primary_cells: [<matrix cell IDs>]
      secondary_cells: [<matrix cell IDs>]
      partial_cells: [<matrix cell IDs>]
    overlap_with_anchor: <0.0–1.0 — share of anchor's primary cells covered>
    positioning:
      claimed:
        alternatives: [<list>]
        unique_attributes: [<list>]
        category: <string>
      revealed:
        alternatives: [<list>]
        unique_attributes: [<list>]
        category: <string>
      gap_severity: low | medium | high
    segment_affinity:
      - segment_id: <string from skill #2>
        grade: strong | fit | weak | antagonistic
        reason: <string ≤ 160 chars>
        anchor_position: winning | losing | absent | tied
    pricing:
      model: per-seat | usage | tiered | sales-led | freemium | other
      bands: [<string — e.g., "$15–$30/user/mo">]
      confidence: <0–100>
    entry_motion: self-serve | plg | sales-led | hybrid | channel
    winning_factors:
      - factor: <string>
        evidence_tier: behavioral | pattern | stated
        segments_decisive_in: [<segment IDs>]
    losing_factors:
      - factor: <string>
        evidence_tier: behavioral | pattern | stated
    seven_powers:
      scale_economies: { verdict: confirmed|partial|operational_lead|asserted_only|na, confidence: <0–100>, mechanism: <string ≤160> }
      network_economies: { verdict: ..., confidence: ..., mechanism: ... }
      counter_positioning: { verdict: ..., confidence: ..., mechanism: ... }
      switching_costs: { verdict: ..., confidence: ..., mechanism: ... }
      branding: { verdict: ..., confidence: ..., mechanism: ... }
      cornered_resource: { verdict: ..., confidence: ..., mechanism: ... }
      process_power: { verdict: ..., confidence: ..., mechanism: ... }
    unfair_advantage_call: <string ≤ 160 chars — names the 1–2 confirmed Powers, or "operational lead only">
    lfk_lens:
      leaders_covered: [<string from skill #3>]
      fillers_covered: [<string from skill #3>]
      killers_triggered: [<string from skill #3>]
    tensions:
      - id: <string>
        kind: claimed_vs_revealed | subsegment_split | context_dependent | stated_vs_behavioral | temporal | unresolved
        note: <string ≤ 160 chars>
    outliers: [<list of one-line singletons>]
    overall_confidence: <0–100>
    evidence_rollup:
      behavioral_count: <int>
      pattern_count: <int>
      stated_count: <int>
```

## Required cross-cuts

```yaml
strategic_groups:
  - id: <kebab-case>
    name: <string>
    members: [<competitor IDs>]
    defining_moves: [<list of strings ≤ 160 chars each>]
    convergence_factors: [<list of factor names>]

winning_factors_ledger:
  - factor: <string>
    competitors_winning: [<competitor IDs>]
    evidence_weight: <0.0–1.0>
    decisive_in_segments: [<segment IDs>]
    anchor_position: own | weak | absent

seven_powers_grid:
  category_rules: [<list of Powers held by 3+ competitors>]
  power_concentrations:
    - competitor_id: <string>
      powers_confirmed: [<list of Powers>]
  power_gaps: [<list of Powers nobody holds>]

strategy_canvases:
  - group_id: <string from strategic_groups>
    factors:
      - name: <string>
        anchor_definition: <string ≤ 160 chars>
        scores:
          - competitor_id: <string>
            score: <0–5>
            evidence: <string ≤ 160 chars>
    four_actions:
      eliminate: [<factor + rationale strings>]
      reduce: [<factor + rationale strings>]
      raise: [<factor + rationale strings>]
      create: [<factor + rationale strings>]
    convergence_zones: [<factor names>]
    white_spots: [<factor names>]

white_space_hypotheses:
  - id: <kebab-case>
    description: <string ≤ 200 chars>
    segment_id: <string from skill #2>
    evidence: <string ≤ 200 chars>
    confidence: <0–100>

threat_ranking:
  - rank: <1|2|3>
    competitor_id: <string>
    mechanism: power | winning_factor | segment_capture | disruption_path
    detail: <string ≤ 160 chars>

non_consumption_posture: shrinking | holding | growing
non_consumption_evidence: <string ≤ 200 chars>

tensions_global:
  - id: <string>
    kind: <see per-competitor tensions>
    note: <string ≤ 200 chars>

singletons:
  - note: <string ≤ 200 chars>
    source: <string ≤ 100 chars>

open_questions:
  - question: <string>
    blocks: <which downstream decision it blocks>
```

## Validation checklist

Before writing the markdown artifact, validate the handoff:

- [ ] `version`, `skill`, `anchor`, and `inherited_from` present at top level
- [ ] Every shortlisted competitor has a complete block (no required field omitted)
- [ ] Every competitor has all 7 Powers entries (use `na` for not applicable, never omit)
- [ ] Every Power verdict has a `mechanism` string (even `na`'d ones — explain why N/A)
- [ ] Every per-segment affinity entry references a `segment_id` that exists in `segments_ref`
- [ ] Every winning-factor decisive-segment reference exists in `segments_ref`
- [ ] Every white-space hypothesis names a `segment_id` and carries a confidence number
- [ ] Threat ranking has exactly 3 entries
- [ ] `non_consumption_posture` is one of the three allowed values
- [ ] All confidences are integers in 0–100 (not decimals, not strings)
- [ ] All evidence tiers are one of `behavioral`, `pattern`, `stated` (lowercase)
- [ ] No prose value exceeds the stated character limits

If any check fails, fix the YAML before writing the artifact. The synthesis skill will reject malformed handoffs.

## Worked mini-example

```yaml
version: 1
skill: competitor-evaluation
anchor:
  name: SplitMetrics
  industry: Mobile ad optimization
  generated_at: 2026-04-19
inherited_from:
  industry_process_map: true
  audience_segment_research: true
  willingness_to_pay_research: true
matrix_ref:
  framing: Process step × Channel
  cells: [creative-test-aso, creative-test-paid, bidding-paid, attribution-paid]
segments_ref: [s1-indie, s2-midmarket-ua, s3-agency, s4-enterprise]
wtp_bands_ref: [b1-low, b2-mid, b3-high]
competitors:
  - id: motion-app
    name: Motion
    class: indirect
    confidence: 78
    evidence_tier: behavioral
    one_line: Auto-scheduler that absorbs the creative-iteration cadence
    coverage:
      primary_cells: [creative-test-aso]
      secondary_cells: []
      partial_cells: [creative-test-paid]
    overlap_with_anchor: 0.25
    positioning:
      claimed:
        alternatives: [Manual planning, Reclaim]
        unique_attributes: [AI re-planning]
        category: AI calendar
      revealed:
        alternatives: [Notion, A spreadsheet]
        unique_attributes: [Re-plans without prompting]
        category: Calendar that owns the day
      gap_severity: medium
    segment_affinity:
      - segment_id: s1-indie
        grade: strong
        reason: 5-star reviews cluster on solo PMs
        anchor_position: losing
    pricing:
      model: per-seat
      bands: [$19/user/mo]
      confidence: 90
    entry_motion: plg
    winning_factors:
      - factor: Re-plans automatically when a meeting moves
        evidence_tier: behavioral
        segments_decisive_in: [s1-indie]
    losing_factors:
      - factor: No org admin view
        evidence_tier: pattern
    seven_powers:
      scale_economies: { verdict: na, confidence: 85, mechanism: No volume cost curve evident }
      network_economies: { verdict: na, confidence: 90, mechanism: Single-player utility }
      counter_positioning: { verdict: asserted_only, confidence: 50, mechanism: No documented incumbent P&L conflict }
      switching_costs: { verdict: operational_lead, confidence: 70, mechanism: Calendar embedding moderate; not structural }
      branding: { verdict: asserted_only, confidence: 55, mechanism: NPS strong; no price premium evidence }
      cornered_resource: { verdict: na, confidence: 90, mechanism: No exclusive data or talent }
      process_power: { verdict: na, confidence: 90, mechanism: 4-year-old company }
    unfair_advantage_call: Operational lead only — fast product iteration, no confirmed Powers
    lfk_lens:
      leaders_covered: [auto-replanning]
      fillers_covered: [calendar-sync]
      killers_triggered: [no-admin-view]
    tensions:
      - id: motion-t1
        kind: claimed_vs_revealed
        note: Claims "AI calendar" category; buyers describe as "scheduler that just works"
    outliers: [One review cites use as a CRM-replacement — single instance, flagged]
    overall_confidence: 75
    evidence_rollup:
      behavioral_count: 12
      pattern_count: 8
      stated_count: 4
strategic_groups:
  - id: g1-ai-schedulers
    name: AI schedulers
    members: [motion-app]
    defining_moves: [PLG, calendar-as-system-of-record, single-player utility]
    convergence_factors: [calendar-sync, auto-replanning]
threat_ranking:
  - rank: 1
    competitor_id: motion-app
    mechanism: segment_capture
    detail: Owns s1-indie via PLG; could expand into s2 if admin view ships
non_consumption_posture: holding
non_consumption_evidence: 41% of s1 forum threads describe "I just wing it" with no SaaS in stack
open_questions:
  - question: Does Motion's PLG motion convert into mid-market admins?
    blocks: GTM allocation between s1 and s2
```

This block compresses 12+ pages of analysis into ~120 lines of structured contract. The synthesis skill consumes it directly.
