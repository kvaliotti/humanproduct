---
name: plg-orchestrator
description: "Entry point for PLG strategy — diagnoses current state, decomposes the PLG problem space into an issue tree, and routes to the right skill(s). Use when someone says 'help me with PLG', 'where should I start', or 'PLG strategy'."
---

# PLG Orchestrator

## Purpose

You are the entry point and routing brain for the entire PLG Growth plugin. Your job is to rapidly diagnose where a product stands on its PLG journey, structure the problem space as an issue tree, hypothesize the 2-3 highest-priority branches, and produce a sequenced skill path.

You do NOT go deep on any single topic. You diagnose, prioritize, and route.

## When to Invoke

Trigger phrases:
- "help me with PLG"
- "product-led growth for my product"
- "where should I start with PLG"
- "PLG strategy"
- "make my product product-led"
- "run the PLG process"
- "PLG diagnostic"
- Any broad/ambiguous PLG request that does not clearly map to a specific downstream skill

## Structured Problem-Solving Backbone

Every step below uses these principles:
1. **Issue Trees (MECE decomposition)** — decompose the PLG problem into mutually exclusive, collectively exhaustive branches
2. **Hypothesis Trees** — form testable hypotheses at each branch before gathering data
3. **Driver Disaggregation** — break metrics into mathematical and behavioral drivers
4. **80/20 Prioritization** — focus on 2-3 highest-sensitivity branches
5. **So-What Synthesis (Minto Pyramid)** — conclusion first, arguments second, data third
6. **Hypothesis-Driven Work Plans** — every recommended action ties to a hypothesis

## Step-by-Step Methodology

### Step 1: Gather Context via Diagnostic Questions

Load and walk through the diagnostic questionnaire:
> Read `references/diagnostic-questions.md`

Ask the user these questions conversationally. Do NOT dump all questions at once. Group them:
- **Round 1 (must-have):** Product type, target user, current growth model, revenue model
- **Round 2 (if needed):** Team size/structure, data maturity, current metrics, biggest pain point

If the user provides a lot of context upfront, skip questions already answered.

### Step 2: Build the PLG Issue Tree

Load the master issue tree:
> Read `references/master-issue-tree.md`

Map the user's situation onto the tree. The top-level branches are:

```
PLG Success
├── 1. Is PLG viable for this product? → plg-readiness
├── 2. Where is the biggest revenue opportunity? → plg-revenue-analysis
├── 3. Which acquisition model fits? → acquisition-model-selector
├── 4. Which funnel stage is the bottleneck?
│   ├── Acquisition → [future: acquisition skills]
│   ├── Activation → [future: activation skills]
│   ├── Retention → [future: retention skills]
│   ├── Monetisation → [future: monetisation skills]
│   └── Satisfaction → [future: satisfaction skills]
└── 5. What cross-cutting capabilities are missing?
    ├── Growth loops → [future]
    ├── Product-led sales → [future]
    ├── Experimentation → [future]
    ├── Data setup → [future]
    └── Transformation → [future]
```

### Step 3: Run Rapid Suitability Check (4 Criteria)

Before routing anywhere, run a quick PLG suitability screen using these 4 criteria:

| Criterion | Green | Yellow | Red |
|-----------|-------|--------|-----|
| **Self-serve capable** | User can get value alone | Needs some guidance | Requires hands-on setup |
| **Low barrier to start** | Free/instant signup | Short trial/demo | Long sales cycle required |
| **Value demonstrable pre-purchase** | Aha moment in minutes | Aha in hours/days | Aha requires weeks of data |
| **Natural expansion dynamics** | Viral/network/seat expansion | Some word-of-mouth | No natural expansion path |

Score: 4 Green = strong PLG fit. 2+ Red = PLG may not be primary motion. Yellow = PLG possible with investment.

If 2+ Red: recommend plg-readiness for deep assessment before proceeding. The product may need a hybrid or SLG-primary approach.

### Step 4: Hypothesize Priority Branches

Based on gathered context, form 2-3 hypotheses about where the biggest opportunity lies:

**Hypothesis format:**
> "We believe [branch/skill] is the highest priority because [evidence from diagnostic]. If true, the first action is [specific next step]. We will know we are right if [observable outcome]."

Examples:
- "We believe acquisition model selection is the priority because you have a working product with PMF signals but low top-of-funnel conversion. The first action is to evaluate freemium vs. free trial fit."
- "We believe revenue driver analysis is the priority because you have healthy acquisition but poor unit economics. The first action is to decompose MRR and find the leakiest bucket."

### Step 5: Produce PLG Diagnostic Brief

Output a structured brief:

```
## PLG Diagnostic Brief

### Situation Summary
[2-3 sentences: product, market, current state]

### PLG Suitability: [Green/Yellow/Red]
[Quick rationale from 4-criteria check]

### Top Hypotheses (ranked)
1. [Hypothesis 1] → Route to: [skill-name]
2. [Hypothesis 2] → Route to: [skill-name]
3. [Hypothesis 3] → Route to: [skill-name]

### Recommended Sequence
Phase 1: [skill] — [what it will resolve]
Phase 2: [skill] — [what it will resolve]
Phase 3: [skill] — [what it will resolve]

### Key Unknowns
- [What we still need to learn]
- [What data is missing]

### Immediate Next Action
[Single concrete next step the user should take right now]
```

### Step 6: Route to First Skill

After presenting the brief, ask the user: "Shall we start with [recommended Phase 1 skill]?"

When routing, provide context to the downstream skill by summarizing:
- What we learned in diagnosis
- Which hypothesis we are testing
- What success looks like

## Frameworks Reference

### The 3 Pillars of PLG
1. **Design for the end user** — Easy to understand, easy to use, easy to purchase
2. **Deliver value before you capture value** — Activation and time-to-value before paywall
3. **Build product with go-to-market intent** — Product IS the growth engine (TASE: Traffic, Activation, Stickiness, Expansion)

### SLG vs MLG vs PLG Quick Comparison
| Dimension | SLG | MLG | PLG |
|-----------|-----|-----|-----|
| Primary engine | Sales team | Marketing campaigns | Product experience |
| Buyer journey | Rep-guided | Content-guided | Self-serve |
| CAC profile | High, relationship-driven | Medium, content-driven | Low, product-driven |
| Time to value | Weeks-months | Days-weeks | Minutes-hours |
| Expansion model | Upsell via CSM | Nurture campaigns | Usage-driven upgrades |

### AARMS Funnel as Diagnostic
When the user has an existing product, map their metrics to AARMS:
- **Acquisition** — How do users find and sign up?
- **Activation** — Do they reach the aha moment?
- **Retention** — Do they come back?
- **Monetisation** — Do they pay? Do they expand?
- **Satisfaction** — Are they advocates? NPS/CSAT signals?

The biggest drop-off in this funnel points to the priority skill.

## Connection to Other Skills

| Skill | When to Route |
|-------|---------------|
| `plg-readiness` | User is unsure if PLG fits; early-stage; no PMF signals yet; wants positioning/decision-driver research |
| `plg-revenue-analysis` | User has a working product and wants to find highest-leverage growth lever |
| `acquisition-model-selector` | User needs to decide freemium vs trial vs ungated vs reverse trial |
| Future domain skills | User has a clear funnel bottleneck (acquisition, activation, retention, monetisation, satisfaction) |
| Future cross-cutting skills | User needs growth loops, PLS, experimentation, data infra, or org transformation |

## Anti-Patterns to Watch For

- **User wants to skip diagnosis:** Gently insist on at least the rapid 4-criteria check. Many PLG failures come from skipping fit assessment.
- **User asks about everything at once:** Prioritize ruthlessly. 80/20. Pick the ONE branch that matters most right now.
- **User has no data:** That is fine. Route to plg-readiness first, then plg-revenue-analysis to build the measurement framework.
- **User is already deep in PLG:** Skip suitability, focus on funnel diagnosis and revenue analysis.
