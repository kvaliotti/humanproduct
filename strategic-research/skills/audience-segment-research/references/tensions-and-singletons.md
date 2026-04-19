# Tensions and Singletons

Two of this skill's six principles demand explicit machinery: **integrate tensions, don't resolve them** and **preserve singletons, don't average them away**. This file is that machinery.

## Why this matters

A clean segment map is always partially a lie. Real audiences contain:

- **Genuine contradictions** — two things can be true at once
- **Context-dependent behavior** — the same person acts differently in different situations
- **Stated-vs-revealed gaps** — what people say and what they do diverge
- **Singletons that foreshadow tomorrow's segment** — the first few signals of a pattern that hasn't formed yet

A skill that smooths these over produces a map that *feels* clean but misleads downstream decisions. A skill that captures them produces a map that is harder to read but truer.

The user's explicit ask: **"If the skill finds conflicting or polar information about the segment, it shouldn't discard it, and instead it should integrate it or highlight that two things can be true at once."** And: **"We want uniqueness to be retained as much to supplement the patterns found."**

This file operationalizes both.

---

## Part 1 — Tensions

### What counts as a tension

A tension is any case where two or more credible pieces of evidence about a segment disagree.

Examples:
- Review site says "small teams love this"; Reddit thread says "you need a dedicated ops person for it to work"
- Case study says "deployed in 2 weeks"; practitioner blog says "took us 4 months"
- Vendor positions as "for agencies"; ecstatic customer list is 70% in-house teams

### Tension classification taxonomy

Every tension gets classified into one of five types. Each type has a different action.

| Class | Diagnostic question | Action |
|---|---|---|
| **Subsegment split** | Are the two signals actually about two different sub-types within what I'm calling one segment? | Split the segment into two sub-segments |
| **Context-dependent** | Is this the same buyer acting differently in different situations? | Keep as one segment; add context qualifiers to each claim |
| **Stated vs. revealed** | Is one source a survey and the other behavior? | Tag both; weight behavior heavier; note the divergence |
| **Temporal shift** | Has the segment changed over time? | Note the shift, direction, and approximate date |
| **Unresolved** | Do I genuinely not have enough evidence to classify? | Hold as an open question for research/interviews |

### The tension log format

Every tension is recorded in the output's Tension Log section:

```
Tension #T-NN
  Segment: <segment name or "cross-segment">
  Claim A: <statement> — [src: ..., behavioral|stated]
  Claim B: <contradicting statement> — [src: ..., behavioral|stated]
  Class: <subsegment-split | context-dependent | stated-vs-revealed | temporal | unresolved>
  Resolution: <the integration — e.g., "Both true: A for sub-segment X, B for sub-segment Y">
  Confidence in resolution: <0-100%>
```

### Anti-patterns when handling tensions

| Anti-pattern | Why wrong | Fix |
|---|---|---|
| Silently picking the "better" source | Loses information; hides judgment | Keep both; classify explicitly |
| Averaging the two claims into a middle position | Produces a fiction true of neither | Hold both; note which is which |
| Discarding the "weaker" source | Weaker source is often the singleton signal | Downweight, don't delete |
| Treating all tensions as research noise | Some tensions are the most informative data points | Classify before dismissing |
| Resolving without evidence | Premature closure | Use "unresolved" and promote to open questions |

### Worked example

**Tension #T-03**
- **Segment:** Solo indie mobile developers
- **Claim A:** "They're extremely price-sensitive; most bail above $20/month" [src: Reddit r/indiedev poll Aug 2024, stated]
- **Claim B:** "A subset pays $199/month for the pro tier within 7 days of signup" [src: vendor cohort data 2025-Q1, behavioral]
- **Class:** Subsegment split
- **Resolution:** The $20 ceiling applies to hobbyist-leaning solos (≈80%). The $199 cohort is revenue-positive indies with 1+ profitable app (≈20%). These are two sub-segments, not one — split and profile separately.
- **Confidence:** 75% — needs validation from 3+ more data points in each sub-cohort.

Note the output: **both claims survive**, the segment is split, and the behavioral data gets the higher weight.

---

## Part 2 — Singletons and outliers

### What counts as a singleton

A singleton is an observation appearing in **only 1–2 data points** that might — on further evidence — become a pattern. Typical forms:

- A detail mentioned in one review that contradicts the standard use case
- A case study customer doing something weird that the rest don't
- A forum comment describing a workaround no one else mentions
- A support ticket hinting at a use case nobody is building for

Singletons are **not**:
- Random noise (missing data, typos, user error)
- Irrelevant detail (background context that doesn't affect the segment claim)
- Stated preference without behavior

A singleton needs to be **interesting** — it should invite a question: *why does this person behave this way, and what if more like them exist?*

### Preservation format

Each singleton is recorded with:

```
Singleton #S-NN
  Scope: <per-segment: segment name | global: no current segment>
  Observation: <the unusual thing>
  Source: <person/company if known, or "anonymous: [source type]">
  Hypothesis: <why this might matter — new sub-segment, edge case, misclassification, precursor, red herring>
  What would promote this to a pattern: <what additional evidence would confirm>
```

### Where singletons live

- **Per-segment** — each segment profile has an "Outlier signals" subsection for singletons within its scope
- **Global** — a dedicated section for singletons that don't fit any segment yet; these are the most valuable (they often reveal a missing segment)

### Anti-patterns when handling singletons

| Anti-pattern | Why wrong | Fix |
|---|---|---|
| Dropping anything below a threshold of N occurrences | Discards the first signal of every new pattern | Keep with explicit N=1 or N=2 tag |
| Merging singletons into existing segments for neatness | Hides a possible new segment | Flag before merging; merge only if fit is strong |
| Using singletons as equal evidence to patterns | Overweights anecdote | Keep but tag with explicit singleton marker |
| Ignoring singletons because the pattern-finding story is tidy | Tidiness is the enemy here | The untidy map is the accurate one |

### Worked example

**Singleton #S-07**
- **Scope:** Global (no segment fit yet)
- **Observation:** A 3-person accounting firm uses the product exclusively for reconciling crypto transactions, treating it as a forensic tool rather than its intended bookkeeping purpose.
- **Source:** G2 review by "Anna T., Staff Accountant", 2025-01
- **Hypothesis:** Possible emerging sub-segment of crypto-native small accounting firms — if 2–3 more similar observations show up, this becomes a sub-segment candidate.
- **What would promote this to a pattern:** 2+ additional reviews or case studies of crypto-forensics use by non-exchange, non-audit firms.

---

## Part 3 — The integration move

The output is clean **not** because tensions and singletons are hidden — it's clean because they are **structured**.

A reader should be able to:

1. Read the primary segmentation confidently
2. Read each segment profile confidently
3. Read the tension log and see exactly what's contested
4. Read the singletons and see exactly what's nascent

This is better than a false-clean map where tensions and singletons were quietly deleted.

## Checklist for Phase 7

- [ ] Every major segment claim lists its evidence count (behavioral / stated)
- [ ] Every tension has a class
- [ ] Every tension has a resolution statement (even if "unresolved")
- [ ] Every segment profile has an Outlier signals subsection (even if empty, mark as "none observed")
- [ ] The global Outliers & Singletons section has at least 1 entry OR a note that none were found after deliberate search
- [ ] No singleton is silently dropped; no tension is silently averaged
