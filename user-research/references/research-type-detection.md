# Research Type Detection

Shared signal list used by all six skills in this plugin to classify a piece of research as **Behavioral**, **General**, or **Mixed**. Every skill (build and evaluate) must use this same list so classification doesn't drift between the brief, the guide, the analysis, and their evaluations.

## The Rule: Trust the Field, Don't Re-Derive It

Research Type is decided **once**, by whichever skill first touches the research (usually `build-research-brief`), and then carried forward as a `Research Type: Behavioral | General | Mixed` line in every downstream artifact.

- **Producing skills** (`build-research-brief`, `build-research-guide`, `analyze-research`) detect the type using the signals below, then **write** `Research Type: [Behavioral / General / Mixed]` into the artifact they output. If an upstream artifact (brief, guide) already states a Research Type, inherit it — don't re-derive it — unless the new input clearly contradicts it (in which case, flag the conflict to the user before proceeding).
- **Consuming skills** (`evaluate-research-brief`, `evaluate-research-guide`, `review-research-analysis`) **read** the `Research Type:` field from the artifact being evaluated first. Only fall back to re-detecting from the signals below if the field is genuinely absent (e.g., a pasted brief with no header, or an artifact from before this convention existed).

This prevents the same research from being classified as "Behavioral" at brief stage and silently re-classified as "General" at analysis stage — which would apply the wrong methodology and reference files partway through the pipeline.

If you do have to re-detect (field absent), state which classification you landed on and why, then write the field into the artifact you produce so the next skill in the chain doesn't have to re-derive it either.

---

## Behavioral Research

The research centers on **getting users to do (or stop doing) a specific action**. Signals:

- Adoption, activation, onboarding completion
- Engagement, retention, habit formation, feature usage
- Behavior change framing ("users aren't doing X", "how to get users to Y")
- Churn framed as behavior ("users stop logging in after week 2")
- Conversion actions (signup → first value, trial → paid)
- A target behavior is specified, or COM-B / B=MAP decomposition is present (or clearly should be)
- Interview/analysis data centers on behavioral episodes: "I tried to do X but then Y happened"

**Action:** Use the behavioral reference file for this skill as the primary methodology (still borrow general elements for logistics, participants, and conversational tactics — see each skill's own instructions).

## General Research

The research centers on **understanding users, validating problems, or informing decisions** — not on changing one specific action. Signals:

- Discovery / exploration ("what do users need?", "is this a real problem?")
- Market validation, willingness to pay, competitive understanding
- Feature prioritization, product-market fit assessment
- Customer segmentation, persona building
- "Why are users churning?" framed as understanding, not behavior change
- Evaluative research (testing prototypes, concepts, usability)

**Action:** Use the general reference file for this skill as the primary methodology. Borrow behavioral elements (target behavior specification, COM-B or B=MAP decomposition) when the research touches on user actions, but keep them secondary.

## Mixed

Some research touches both. Example: "We want to understand why users churn and design interventions to retain them." The understanding part is general; the intervention design is behavioral.

**Action:** Use both reference files. Lead with whichever matches the primary intent. Flag the dual nature to the user/reader, and keep general and behavioral findings clearly separated in the output rather than blended.

---

## Writing the Field

Producing skills should render the field exactly as:

```
Research Type: Behavioral
```
(or `General`, or `Mixed`) — using this exact label so downstream skills can find it with a simple text search, regardless of whether it's a top-line metadata field or embedded in a "Date / Owner / Research Type" header block.

## Reading the Field

Consuming skills should look for a line matching `Research Type:` (case-insensitive, wherever it appears in the artifact's header/metadata) before running any detection signals. If found, state it in your own output as "Research type detected: [X] (inherited from artifact)." If absent, run the signals above, state "Research type detected: [X] (re-derived — no Research Type field found in source artifact)," and write the field into whatever artifact you produce.
