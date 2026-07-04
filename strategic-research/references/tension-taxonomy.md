# Tension Taxonomy (shared)

Single source of truth for how the strategic-research skills classify **tensions** — cases where two or more credible pieces of evidence disagree. Every skill that keeps a tension log points here instead of restating the taxonomy. Referenced as `${CLAUDE_PLUGIN_ROOT}/references/tension-taxonomy.md`.

## The rule

When two credible sources disagree, **both survive**. A tension is never silently resolved, averaged, or deleted — it is classified and held visible in the output's tension log. Holding a tension visible beats resolving it wrongly.

## The five base classes

Used by `audience-segment-research` and `willingness-to-pay-research` (their handoff `class:` enum is exactly these five values).

| Class | Diagnostic question | Action |
|---|---|---|
| **subsegment-split** | Are the two signals about two different sub-types inside what I'm calling one segment? | Split into sub-segments |
| **context-dependent** | Is this the same buyer acting differently in different situations? | Keep as one; add a context qualifier to each claim |
| **stated-vs-revealed** | Is one source a survey/opinion and the other observed behavior? | Tag both; weight behavior heavier; note the divergence |
| **temporal** | Has the segment changed over time? | Note the shift, its direction, and approximate date |
| **unresolved** | Is there genuinely not enough evidence to classify? | Hold as an open question; promote to research |

## Competitor-evaluation variant (six classes)

`competitor-evaluation` compares **claimed** vs. **revealed** positioning, so it adds one class and renames one. Its enum is: `claimed-vs-revealed | subsegment-split | context-dependent | stated-vs-behavioral | temporal | unresolved`.

- **claimed-vs-revealed** — the vendor's stated positioning contradicts what buyer behavior reveals. Often the most exploitable insight in the analysis. Record the gap; do not restate the homepage as fact.
- **stated-vs-behavioral** — same meaning as `stated-vs-revealed` above, named for the competitive context.

## Tension log format

Every tension is recorded in the output's tension log (never buried in prose):

```
Tension #T-NN
  Scope:   <segment name | competitor | "cross-segment">
  Claim A: <statement> — [src: ..., behavioral|stated]
  Claim B: <contradicting statement> — [src: ..., behavioral|stated]
  Class:   <one of the classes above>
  Resolution: <the integration — e.g., "Both true: A for sub-segment X, B for sub-segment Y">
  Confidence in resolution: <0-100%>
```

## Anti-patterns

| Anti-pattern | Why wrong | Fix |
|---|---|---|
| Silently picking the "better" source | Loses information; hides judgment | Keep both; classify explicitly |
| Averaging two claims into a middle position | Produces a fiction true of neither | Hold both; note which is which |
| Discarding the "weaker" source | The weaker source is often the singleton signal | Downweight, don't delete |
| Treating all tensions as noise | Some tensions are the most informative data points | Classify before dismissing |
| Resolving without evidence | Premature closure | Use `unresolved` and promote to open questions |

## Worked example

**Tension #T-03** — Segment: Solo indie mobile developers
- **Claim A:** "Extremely price-sensitive; most bail above $20/month" — [src: Reddit r/indiedev poll Aug 2024, stated]
- **Claim B:** "A subset pays $199/month for the pro tier within 7 days of signup" — [src: vendor cohort data 2025-Q1, behavioral]
- **Class:** subsegment-split
- **Resolution:** The $20 ceiling applies to hobbyist-leaning solos (~80%); the $199 cohort is revenue-positive indies with 1+ profitable app (~20%). Two sub-segments, not one — split and profile separately.
- **Confidence:** 75% — needs 3+ more data points per sub-cohort.

Both claims survive; the segment is split; behavioral data gets the higher weight.
