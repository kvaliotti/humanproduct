# Growth Team Structuring (shared)

How to organize a growth team for PLG execution. Used by both `plg-revenue-analysis` (Step: Team Structuring — organizing around revenue levers) and `plg-transformation` (Org Structure dimension — team design). The right structure depends on team size, PLG maturity, and where the biggest revenue opportunity sits.

---

## Foundational Principle

Every growth team needs three things:
1. **Dedicated owner** — a PM who owns the outcome, not a committee
2. **Self-sufficient team** — PM + design + engineering + data, not dependent on other teams for daily execution
3. **Clear priorities** — connected to a specific branch of the revenue driver tree, not "do growth"

Without all three, growth work gets deprioritized, delayed, or scattered.

---

## Small Team (< 5 Growth/Product People)

### Model A: Single Highest-Sensitivity Factor

**When to use:** One lever dominates the sensitivity analysis (>50% of the total opportunity).

**How it works:**
1. Build or load the revenue driver tree
2. Run sensitivity analysis: for each metric, "if this improves by 10%, what is the MRR impact?"
3. Find the ONE metric with the highest sensitivity
4. Dedicate all PM + engineering capacity to it, in 6–12 week sprints (1–2 experiments/week)
5. Rotate to the next lever only when: (a) the metric hits target, (b) diminishing returns, or (c) new data changes priority. Re-evaluate quarterly.

**Example:**
```
Revenue Driver Tree Sensitivity Analysis:
- Signups +10% → MRR +3%
- Activation rate +10% → MRR +8%   ← HIGHEST SENSITIVITY
- Conversion rate +10% → MRR +6%
- ARPA +10% → MRR +5%
- Churn rate -10% → MRR +4%

Decision: All growth capacity focused on activation rate.
```

**Structure:** 1 Growth lead (owns the metric) + 1–2 Engineers + 1 Designer/PM; shared data/analytics support.

**Pros:** maximum focus and depth, team becomes expert, clear ownership, easy to show impact.
**Cons:** ignores other branches; sensitivity can shift once the lever is optimized; risk of over-optimizing one metric.
**Best for:** clear bottleneck, early PLG stage, small team that cannot spread thin.

### Model B: Cross-Prioritize Low-Hanging Fruit / Cross-Lever Sprint

**When to use:** the biggest opportunity is not yet clear, OR two levers are close in priority and share dependencies (e.g., activation and paid conversion both need onboarding changes).

**How it works:**
1. For each branch of the revenue tree, identify the easiest wins (high impact, low effort)
2. Rank all opportunities across branches by ICE score
3. Work the top 3–5 regardless of branch; re-prioritize monthly
4. For two dependent levers, alternate focus every 2–3 weeks, or split the team (2 on lever A, 2 on lever B) if parallelizable

**Caution:** do not split a small team across more than 2 levers — context-switching kills velocity.

**Pros:** captures quick wins across the funnel, good for exploration, demonstrates impact fast (org buy-in).
**Cons:** scattered focus, no deep expertise, hard to attribute impact, risk of local optimization.
**Best for:** very early PLG stage. Use for one quarter to explore, then switch to Model A.

### Recommendation for Small Teams

**Default to Model A** unless you have no data on the bottleneck (use Model B for one quarter to explore) or the company needs quick wins to justify further PLG investment (use Model B to show breadth). Then switch to Model A once you have conviction.

### Small Team Anti-Patterns
- Working all levers at once (nothing moves)
- No dedicated metric owner (accountability gap)
- Building features instead of testing hypotheses
- Changing focus every week based on the latest fire

---

## Medium Team (5–15 Growth/Product People)

### Model C: Revenue-Type Pods

**When to use:** multiple MRR components (New, Retained, Expansion) are all significant priorities.

```
Growth Lead (cross-pod coordination)
├── New MRR Pod (3-5)      — Metrics: traffic, signup conv, activation, paid conv
├── Retention Pod (3-5)    — Metrics: churn rate, engagement depth, NPS
└── Expansion Pod (3-5)    — Metrics: NRR, seat expansion, upgrade rate
```
**Pros:** clear ownership, focused metrics, career paths. **Cons:** handoff friction, potential local optimization.

### Model D: Metrics-Cluster Teams (AARMS Journey)

**When to use:** funnel stages are more natural boundaries than revenue components; good for pure self-serve with a linear journey.

```
Growth Lead
├── Acquisition Team   — Traffic, signups, CAC        — landing pages, channels, signup flow
├── Activation Team    — Activation rate, TTV          — onboarding, aha moment, first value
└── Monetization Team  — Paid conversion, ARPU, NRR    — paywall, pricing, upgrade flow, retention
```
**Pros:** user-journey aligned, clear handoff points, easy to spot the biggest drop-off. **Cons:** can miss cross-funnel interactions; monetisation depends on upstream teams.

---

## Large Team (15+ Growth/Product People)

### Model E: Full Revenue-Lever Organization
```
VP Growth
├── Acquisition (5-8)         — organic/SEO, paid, viral/referral sub-teams
├── Activation & Onboarding   — new user onboarding, feature adoption
├── Monetization             — self-serve conversion, pricing & packaging, PQL-to-sales handoff
├── Retention                — engagement & stickiness, churn prevention, reactivation
├── Expansion                — seat growth, usage growth, upgrade/upsell
└── Growth Platform          — experimentation infra, data & analytics, growth tooling
```

### Model F: Lever + Horizontal Capabilities (10+ PMs, hybrid)

Vertical lever teams own metrics; horizontal capabilities serve all of them.
```
VP Growth
├── Lever Teams (vertical, own metrics):  Acquisition · Activation · Monetization · Retention
└── Horizontal Capabilities (serve all):  Data Science/Analytics · Experimentation Platform ·
                                          Growth Engineering (shared) · Growth Design (shared)
```
A common hybrid: Acquisition + Activation as journey teams, Engagement/Retention + Monetisation as revenue teams, plus a Platform team for experimentation, data, and feature flags.

---

## Team Composition Template

Each growth team needs these roles; scale engineering to the complexity of the team's scope.

| Role | Count | Responsibilities |
|------|-------|-----------------|
| PM | 1 | Owns strategy, prioritization, outcomes. Maintains OST. Designs experiments. |
| Designer | 1 | Growth design (UX + conversion optimization). Prototype testing. UI experiments. |
| Engineers | 2-4 | Full-stack. Frontend for UI experiments, backend for logic/data. Feature flag management. |
| Analyst | 1 | Funnel/cohort/experiment analysis, metric monitoring. Shared across 2 teams max. |
| Researcher | 0.5 (shared) | User interviews, usability testing, qualitative insight. Shared across 2-3 teams. |

**Minimum viable growth team: 5–6 people** (1 PM + 1 Designer + 2 Engineers + 1 Analyst) — the minimum to run experiments independently without depending on other teams.

### Dedicated Owner Model

Regardless of structure, every priority lever needs a dedicated owner across four hats (one person wears all four on a small team; distributed on a large one):

| Role | Responsibility |
|---|---|
| **Metric owner** | Accountable for the number. Reports weekly. Understands all sub-drivers. |
| **Hypothesis generator** | Maintains a backlog of hypotheses about what will move the metric. |
| **Experiment runner** | Designs and runs experiments to test hypotheses. |
| **Insight synthesizer** | Turns results into learnings and next hypotheses. |

### Reporting Structure

Growth teams should report to the **product org**, not marketing: growth needs product authority (ability to change the product), engineering follows the product org, and the PM career path lives in product. Marketing remains a partner for acquisition channels, content, and brand — but growth owns the in-product experience.

---

## Review Cadence

| Cadence | Activity |
|---|---|
| **Daily** | Check key metric dashboards (automated anomaly alerts) |
| **Weekly** | Growth review (30 min): metric check → experiments running/concluded/launching → blockers → decisions needed. Output: updated experiment tracker, blocker escalations. |
| **Bi-weekly** | Experiment review: analyze completed experiments, decide next |
| **Monthly** | Funnel review (60 min, + Product/Marketing/Sales/CS): full AARMS walkthrough → deep-dive on biggest drop-off → cross-team coordination → action items. Output: updated funnel dashboard, prioritized cross-team actions. |
| **Quarterly** | Strategy review (90 min, + Leadership/Finance): revenue driver tree review → goal progress → sensitivity re-analysis → next-quarter goals → team-structure assessment → resource decisions. Output: updated tree, next-quarter goals, structure decision. |

---

## Structuring Decision Framework

```
How many PMs do you have for growth?
    ├── 1 PM      → Model A: single sensitive factor (all capacity on the #1 revenue driver)
    ├── 2-4 PMs   → Is the biggest opportunity clear?
    │                 ├── YES → Model A: all PMs on one metric
    │                 └── NO  → Model B: each PM on a different AARMS stage, learn one quarter, then consolidate
    └── 5+ PMs    → Is your primary motion self-serve or sales-assisted?
                      ├── Self-serve      → Model D: by AARMS stage
                      └── Sales-assisted  → Model C: by revenue type (New/Retained/Expansion)
```

Supporting questions:

| Question | If Yes → | If No → |
|---|---|---|
| Is one lever >50% of the opportunity? | Single-lever focus (Model A/B) | Multi-lever structure (Model C-F) |
| Is team < 5 people? | Model A or B | Model C+ |
| Are revenue components fairly independent? | Revenue-type pods (Model C) | Metrics-cluster teams (Model D) |
| Does team need to share engineers/designers? | Lever + Horizontal (Model F) | Full lever org (Model E) |
| Is there a separate data/analytics team? | Embed analysts in pods | Include in Growth Platform |

---

## Common Anti-Patterns & Pitfalls

| Anti-Pattern | What It Looks Like | Why It Fails | Fix |
|-------------|-------------------|-------------|-----|
| Growth team in marketing | "Growth" means demand gen, ads, content | No product authority, cannot change the product | Move growth to product org |
| Growth as a side project | PM does growth 20% alongside feature work | Growth always loses to feature deadlines | Dedicated PM with protected capacity |
| Growth without data | Experiments run without analytics | Cannot measure impact or prioritize | Invest in data first (TASE: Track + Analyse) |
| Growth without engineering | PM designs experiments, no engineers to build | Queue behind feature teams, slow execution | Dedicate at least 2 engineers to growth |
| Too many metrics | Team owns 15 metrics across all AARMS stages | Scattered focus, no depth | Pick 1-2 metrics. Use OST for focus. |
| Growth vs Product tension | Optimizing short-term metrics at UX expense | Dark patterns, trust erosion, churn | Guardrail metrics on every experiment |
| No executive sponsor | Team exists with no leadership champion | Budget cut in next reorg | Get VP+ sponsor before forming the team |

Additional pitfalls to avoid:

1. **Org chart follows strategy, not the reverse.** Pick the levers first, then structure the team.
2. **Rotate, do not re-org.** When priorities shift, rotate people between focuses; re-orgs are expensive.
3. **Measure inputs, not just outputs.** Revenue is an output; experiments run, hypotheses tested, and learning velocity are inputs. Track both.
4. **Growth is cross-functional.** A "growth PM" without engineering capacity is just a person with opinions.
5. **Avoid "growth theater."** Don't A/B test button colors when the real problem is a broken value prop. Focus experiments on the priority levers from the revenue analysis.
