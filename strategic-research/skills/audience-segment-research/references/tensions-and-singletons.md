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

### How tensions are classified and logged

Every tension is classified into one of five classes (subsegment-split, context-dependent, stated-vs-revealed, temporal, unresolved) and recorded in the output's tension log. The full taxonomy — the diagnostic question and action per class, the tension-log format, the anti-patterns to avoid, and a worked example — lives in the shared reference `${CLAUDE_PLUGIN_ROOT}/references/tension-taxonomy.md`. Use it directly; this skill adds no extra tension classes. The handoff `class:` enum in `references/handoff-schema.md` must stay exactly those five values.

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
