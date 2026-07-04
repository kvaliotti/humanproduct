---
name: competitive-alternatives
description: >
  Deep dive into mapping competitive alternatives, isolating unique attributes, and translating
  them to value themes — the foundational analysis steps of product positioning. Use when the
  user says "map competitive alternatives", "what would customers use instead", "who do we
  compete with", "find our differentiators", "what makes us unique", "competitive analysis
  for positioning", "list our alternatives", "map attributes to value", or wants to understand
  their true competitive landscape from the customer's perspective. Can run standalone or as
  a sub-step of the full positioning workshop.
---

# Competitive Alternatives Deep Dive

This skill covers Steps 4-6 of the positioning framework — the analytical core where most positioning goes wrong. Run these steps with rigor; they are the foundation everything else builds on.

## Prerequisites

Before starting, establish:
1. **Who are the best-fit customers?** (From Step 1 or ask now)
2. **Is the user willing to set aside their existing assumptions about competitors?** (Baggage check)

If the user hasn't identified best-fit customers, run a quick version: "Describe 3-5 of your happiest customers — the ones who bought fast, love the product, and refer others."

## Step 4: List True Competitive Alternatives

### The Core Question

"What would your best customers use or do if your product didn't exist?"

This is NOT "who are your competitors?" It's what customers would ACTUALLY do. The distinction matters — `references/elicitation-guide.md` has the research behind this (the database-company example where asking about "problems" produced narrow answers but asking about "alternatives" revealed the true market frame).

### Guided Elicitation

Run the full 4-round sequence from `references/elicitation-guide.md`:
1. **Open-ended** — "If our product didn't exist tomorrow, what would your best customers do instead?"
2. **Category prompts** — general-purpose tools, manual/human processes, status quo, cobbled combinations, internal builds
3. **Validation** — is this observed customer behavior or the user's inference?
4. **Ranking** — most to least common, grouped into clusters

`references/elicitation-guide.md` also has a full alternative-types table with B2B and consumer examples for each category.

### Anti-Pattern Detection

Watch for the failure modes and scripted responses in `references/elicitation-guide.md` — most commonly: only listing VC-funded startups, projecting expert landscape knowledge onto customers, listing aspirational competitors (Salesforce) instead of real ones, and forgetting "do nothing" as the default alternative.

### Output

Produce a ranked, grouped list:
```
Group A (most common): [what + why it's common]
Group B: [what + why]
Group C: [what + why]
```

Aim for 2-5 groups. If more than 5, the best-fit customer definition is probably too broad.

## Step 5: Isolate Unique Attributes

### The Question

"For each alternative group: what do you have that they don't?"

### Systematic Exploration

Don't let the user stop at product features. Work through all 6 categories in `references/attribute-categories.md` — technical features, delivery model, business model, expertise & experience, partnerships & ecosystem, and team composition — using its probe questions and concrete examples for each.

### Quality Checks

For each attribute, apply:
1. **Provability test:** "How would you prove this to a skeptic? Data, demo, customer quote?" — If opinion only, flag it.
2. **Uniqueness test:** "Does ANY alternative also have this?" — If yes, it's not a differentiator.
3. **Consideration test:** "Would this matter in a purchase decision, or only after they're already a customer?" — Focus on consideration attributes; see `references/attribute-categories.md` for the full consideration-vs-retention distinction with examples.

### Negative-as-Positive Check

Ask: "What about your product might some people see as a downside?" Then explore whether that's actually a feature for best-fit customers.

Example: "Requires professional services to install" = negative for self-serve buyers, but a FEATURE for enterprises wanting high-touch customization.

### Output

A list of 8-15 unique attributes, each with:
- What it is (factual description)
- Which alternative group it's unique relative to
- How it's provable

## Step 6: Map Attributes to Value Themes

### The "So What?" Chain

For each attribute, run the chain twice:
```
Attribute → "So what?" → Benefit → "So what?" → Value (customer goal)
```

**Example:**
- Attribute: "Patented fuzzy logic query algorithm"
- Benefit: "Sub-second response times on complex queries"
- Value: "Reps answer customer questions while they're on the phone instead of calling back → decreased support time, increased satisfaction"

### Clustering Method

1. Map every attribute to its value endpoint
2. Group values that serve the same customer goal
3. Name each cluster as a theme (from the customer's perspective)
4. Target: 1-4 themes

**Example clustering:**
- "Works on any mobile device" + "Works without internet" + "Offline sync" → Theme: **"Works everywhere your team works"**
- "One-click reports" + "Real-time dashboards" + "Scheduled email digests" → Theme: **"Decisions backed by current data"**

### Proof Assignment

For each theme, identify proof:
- Customer quote or case study
- Measurable outcome (time saved, revenue increased, costs reduced)
- Third-party validation (analyst report, review, award)
- Demo-able capability

Themes without proof get flagged as hypotheses. They stay on the canvas but are marked as unproven.

### Output

A value themes table:

| Theme | Attributes | Benefit | Customer Goal | Proof |
|-------|-----------|---------|---------------|-------|
| ... | ... | ... | ... | ... |

Plus a YAML handoff block for downstream skills:

```yaml
competitive_alternatives:
  groups: [...]
unique_attributes: [...]
value_themes: [...]
```

## Style Rules

- This is where most positioning falls apart. Be rigorous, not friendly.
- Challenge every attribute that smells like opinion. "Easy to use" → "Prove it. What specifically is easier?"
- Don't accept "we're better" as differentiation. Better HOW, measured BY WHAT?
- If the user can't identify unique attributes, the positioning problem might be a product problem. Say so.
