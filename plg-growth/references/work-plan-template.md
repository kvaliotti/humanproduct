# PLG Work Plan Template (shared)

This is the shared, domain-agnostic work-plan skeleton used by every AARMS domain skill (acquisition, activation, retention, monetisation, satisfaction). The calling skill supplies the **domain**: its issue-tree branches, its metrics, and its worked examples. For domain-specific sample plans and examples, read that skill's own `references/work-plan-examples.md` alongside this file.

Every work item is hypothesis-driven and ties to a branch of the domain's issue tree and a metric on the revenue/domain driver tree. No orphan tasks.

---

## Step 1 — Choose the plan format (situation → format)

| User situation | Plan format |
|----------------|-------------|
| Early stage, unclear direction, or wants strategic structure | **OST** (Objectives → Strategies → Tactics) |
| Has data, needs to test specific changes | **Experiment Backlog** (prioritized experiments) |
| Needs to learn before deciding (unknown drivers / willingness to pay / churn causes) | **Research Plan** (discovery activities) |

The exact mapping is tuned per domain — defer to the calling skill's Mode 3 table when it differs (e.g., activation maps "no metric defined" → Research Plan; satisfaction maps "no measurement in place" → OST).

---

## Step 2 — Universal work-item format

Regardless of format, every work item includes:

```
### [Short descriptive title]

**Issue Tree Branch:** [which branch of THIS domain's issue tree it addresses]
**Hypothesis:** "We believe [X] because [Y]"   (use the domain's hypothesis format if it has one)
**Work Type:** Research | Data Analysis | Strategy Decision | Experiment | Operations
**Priority:** P1 (high sensitivity) | P2 (moderate) | P3 (low)
**Connected Metric:** [which metric on the driver tree this moves]
**Success Criteria:** [target metric + guardrail metric]
**Timeline:** [duration, or target quarter]
**Dependencies:** [what must be true or done first]
**Risk:** [what could go wrong + mitigation]
```

---

## Step 3 — Priority assignment (by sensitivity, not ease)

Priority comes from sensitivity analysis on the driver tree:

- **P1 (High Sensitivity):** moving this lever ~10% has outsized impact on the outcome. Can start immediately (no unresolved dependencies).
- **P2 (Moderate Sensitivity):** meaningful impact but not the biggest lever; important for sustained growth.
- **P3 (Low Sensitivity):** good practice, low immediate impact; do once P1 and P2 are addressed.

Where a domain has an ordering rule (e.g., retention fixes the earliest broken component first: Activation > Engagement > Adoption > Resurrection), combine it with sensitivity.

---

## Step 4 — Work-type definitions

- **Research** — fill knowledge gaps with qualitative or secondary work (interviews, landscape/competitor teardown, intent mapping).
- **Data Analysis** — quantitatively test a hypothesis against existing data (funnels, cohorts, correlations, attribution).
- **Strategy Decision** — use evidence to make a directional choice.
- **Experiment** — test a specific change with a measurable outcome. Must specify hypothesis, metric, success criteria, audience + sample size, and duration for significance.
- **Operations** — enabling infrastructure and process (tracking/analytics, tooling, ownership/RACI).

---

## Step 5 — The three plan formats

### A) OST — Objectives, Strategies, Tactics

For strategic direction / early or discovery stage.

```
## Work Plan: OST

### Objective
[specific, measurable goal]

### Strategy N: [name]
Hypothesis: "We believe [strategy] will improve [metric] because [reasoning]"
Tactics:
1. [tactic] — Owner — Timeline — Metric
2. [tactic] — Owner — Timeline — Metric

### Key Unknowns
- [what to learn before committing]

### Success Criteria
- [how we know the objective is met + leading indicators to track]
```

### B) Experiment Backlog

For has-data situations.

```
## Experiment Backlog

### Experiment N: [name]
- Branch: [issue-tree branch tested]
- Hypothesis: "We believe [change] will [outcome] because [reasoning]"
- Metric: [primary metric + downstream business metric]
- Success criteria: [threshold]
- Audience: [who, sample size needed]
- Duration: [minimum for significance]
- Effort: [S/M/L]
- Risk: [what could go wrong]
- Expected impact: [$ or metric estimate if confirmed]

### Prioritization
| # | Experiment | Impact (H/M/L) | Effort (S/M/L) | Risk (H/M/L) | Priority |
```

### C) Research Plan

For needs-discovery situations.

```
## Research Plan

### Research Question
[what we need to learn]

### Study N: [method]
- Objective: [what this study answers]
- Method: [interviews / survey / observation / analysis / Van Westendorp / MaxDiff / etc.]
- Participants: [who, how many, how recruited]
- Timeline: [design, field, analysis]
- Deliverable: [what the output looks like]
- Decision it informs: [what strategy/tactic depends on this]

### Research Sequence
[which studies must happen first to inform later ones]

### Interim Decisions
[what can be decided now vs. what must wait]
```

---

## Step 6 — Work plan review checklist (generic)

Before finalizing, verify:

- [ ] Every item has a hypothesis (not just "improve X")
- [ ] Items are prioritized by sensitivity/impact, not ease
- [ ] Mix of work types (not all experiments, not all research)
- [ ] Dependencies are explicit (what blocks what)
- [ ] Success criteria are specific and measurable (target + guardrail)
- [ ] Timeline is realistic given team capacity
- [ ] Each item connects to a metric on the driver tree
- [ ] P1 items can start immediately (no unresolved dependencies)
- [ ] Measurement infrastructure is in place or is an explicit work item

Add the domain-specific checklist items and worked examples from the calling skill's `references/work-plan-examples.md`.
