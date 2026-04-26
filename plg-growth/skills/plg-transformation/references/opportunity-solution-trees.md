# Opportunity Solution Trees (OST)

OST is the operating system for PLG teams. It connects business outcomes to user opportunities to solutions to validation, ensuring teams work on the right problems with evidence.

---

## Structure

```
OUTCOME (measurable metric the team owns)
├── OPPORTUNITY (user need / problem from research)
│   ├── SOLUTION (idea addressing the opportunity)
│   │   └── VALIDATION (test confirming solution works)
│   ├── SOLUTION
��   │   └── VALIDATION
│   └── SOLUTION
│       └── VALIDATION
├── OPPORTUNITY
│   ├── SOLUTION
│   │   └── VALIDATION
│   └── SOLUTION
│       └── VALIDATION
└── OPPORTUNITY
    └── SOLUTION
        └── VALIDATION
```

Each level answers a different question:
- **Outcome:** What metric are we trying to move?
- **Opportunity:** What user problem, if solved, would move the metric?
- **Solution:** What product change could solve this problem?
- **Validation:** How do we know the solution works?

---

## Outcome Definition

The outcome is a measurable metric the team can directly influence through product changes.

### Good Outcome Criteria

| Criterion | Test | Good Example | Bad Example |
|-----------|------|-------------|-------------|
| Measurable | Can you track it with a number? | "Activation rate for SMB" | "Make onboarding better" |
| Directly influenceable | Can the team move this by changing the product? | "D7 retention for new signups" | "Total ARR" (depends on sales, marketing, pricing, etc.) |
| Specific enough | Is it clear what segment and metric? | "Free-to-paid conversion for teams >5 users" | "Improve monetization" |
| Time-bounded | Is there a target timeline? | "Increase from 25% to 35% this quarter" | "Improve activation rate" (no target, no timeline) |
| Connected to business | Does it trace to the revenue driver tree? | "Activation rate (impacts New MRR branch)" | "Increase NPS" (weak connection to revenue) |

### Decomposition Test

If the outcome is too broad, decompose it:

```
BAD: "Increase revenue"
  → Depends on: acquisition, activation, retention, monetization, expansion, churn
  → Team cannot influence all of these
  → Decompose to a specific branch

GOOD: "Increase activation rate for SMB segment (1-50 employees) from 25% to 35%"
  → Team can influence this through product changes
  → Clear metric, segment, baseline, target
  → Connected to New MRR branch of revenue tree
```

### Outcome Setting Process

1. Start from the revenue driver tree
2. Run sensitivity analysis: which metric, if improved by 10%, drives the most MRR impact?
3. Assign the highest-sensitivity metric to the team with the best capability to move it
4. Set a specific, measurable target (baseline + target + timeline)
5. Confirm with the team: "Can you move this by changing the product?" If no, decompose further.

---

## Distributed Opportunity Identification

Opportunities come from multiple sources. Each role contributes a different lens. No single role has a complete view.

### Analyst Contributions

**What they bring:** Data patterns, quantitative insights, correlation analysis

**Example opportunity findings:**
- "Users who connect an integration within 48 hours retain 2.3x better than those who don't"
- "There's a 40% drop-off between step 3 and step 4 of onboarding"
- "Users from the marketing channel have 50% lower activation than organic users"
- "Accounts with 3+ active users have 4x lower churn"

**How to surface:** Weekly data review, cohort analysis, funnel analysis, feature correlation

### Researcher Contributions

**What they bring:** Qualitative insights, user motivations, unmet needs, mental models

**Example opportunity findings:**
- "Users don't know that the collaboration feature exists -- they're using email to share instead"
- "New users feel overwhelmed by the dashboard -- they don't know where to start"
- "SMB users want to try premium features before committing, but the paywall blocks exploration"
- "Users' mental model of 'projects' doesn't match how our product structures work"

**How to surface:** User interviews, usability tests, support ticket analysis, in-app surveys

### Designer Contributions

**What they bring:** UX friction identification, interaction patterns, design heuristics

**Example opportunity findings:**
- "The signup form has 3 unnecessary steps that could be deferred to post-signup"
- "The empty state for new users provides no guidance -- just a blank canvas"
- "The upgrade CTA is buried in settings -- users who want to pay can't find it"
- "Mobile experience is broken for the core action -- 60% of signups are mobile"

**How to surface:** UX audits, heuristic evaluation, session recordings, analytics-driven design review

### PM Synthesis

**What they do:** Prioritize opportunities by impact on the outcome

For each opportunity, assess:
- **Size:** How many users are affected?
- **Impact:** If solved, how much would the outcome metric move?
- **Evidence strength:** Data (strong), research (medium), heuristic (weaker)
- **Dependency:** Does solving this unlock other opportunities?

Rank opportunities and focus on the top 2-3 per quarter.

---

## 3-Part Validation

Do not skip validation levels. Each level answers a different question.

### Level 1: Solution Fit (No Engineering)

**Question:** Does this solution solve the opportunity?

**Methods:**
- Paper prototypes or wireframes tested with 5-8 users
- Interactive Figma prototype with task completion testing
- Concept testing: describe the solution, ask users to rate value/willingness to use
- Landing page / fake door: measure interest before building

**Exit criteria:** 4 out of 5 users can complete the task / express clear intent to use

**Cost:** 3-5 days of design + research time, zero engineering

**What it prevents:** Building something users don't want or can't use

### Level 2: Reach/Impact Analysis

**Question:** If this solution works, how many users would it affect, and what's the expected metric lift?

**Methods:**
- Segment analysis: how many users experience the opportunity? (Use analytics to size the affected population)
- Metric modeling: if X% of affected users change behavior, what's the outcome metric lift?
- Sensitivity calculation: is the expected lift worth the engineering investment?

**Exit criteria:** Expected lift justifies the engineering cost (apply ICE scoring)

**Cost:** 1-2 days of analyst time

**What it prevents:** Building a solution that works but affects too few users to matter

### Level 3: Progressive Experimentation

**Question:** Does the solution actually move the outcome metric in production?

**Methods:**
- MVP build: minimum version that tests the core hypothesis
- A/B test: randomized control trial with statistical rigor
- Staged rollout: 10% → 50% → 100% with metric monitoring at each stage

**Exit criteria:** Statistically significant improvement in primary metric, no guardrail degradation

**Cost:** 1-4 weeks of engineering + experiment duration

**What it prevents:** Shipping something that seemed good in research but doesn't move metrics in practice

### Validation Decision Tree

```
Opportunity identified
    |
    v
Is the solution obvious? (fixing a clear bug, removing an unnecessary step)
    |
    ├── YES → Skip to Level 3 (build and A/B test directly)
    |
    └── NO → Level 1 (prototype test)
            |
            v
        Did users value/use it?
            |
            ├── NO → Kill or redesign. Back to solution generation.
            |
            └── YES → Level 2 (reach/impact analysis)
                    |
                    v
                Is expected lift worth the investment?
                    |
                    ├── NO → Park. Work on higher-impact opportunities.
                    |
                    └── YES → Level 3 (build MVP, A/B test)
                            |
                            v
                        Stat-sig improvement?
                            |
                            ├── NO → Learn and iterate or abandon
                            |
                            └── YES → Ship to 100%
```

---

## Implementation Guide

### Getting Started (First 2 Weeks)

1. **Choose one team** to pilot OST. Pick the team with the strongest PM and most data access.
2. **Define the outcome** from the revenue driver tree. Be specific (metric + segment + baseline + target).
3. **Brainstorm opportunities** in a 90-minute session with PM + analyst + designer + researcher. Write each opportunity on a sticky note / card.
4. **Organize into a tree** on a visual board (Miro, FigJam, or physical whiteboard).
5. **Prioritize** the top 2-3 opportunities. Start generating solutions for the #1 opportunity.

### Operating Cadence

| Cadence | Activity | Duration | Participants |
|---------|----------|----------|-------------|
| Weekly | OST review: update opportunity priorities, review validation results, discuss learnings | 30 min | Full team (PM, design, eng, data) |
| Sprint-level | Prioritize solutions, plan validation work for the sprint | Part of sprint planning | PM + eng lead |
| Monthly | Outcome check: is the metric moving? Are we working on the right opportunities? | 30 min | Team + manager |
| Quarterly | Outcome setting: update metrics from revenue tree, refresh opportunity identification | 60-90 min | Team + leadership |

### Champion Role

Appoint one person (usually PM) as the OST champion:
- Maintains the visual board
- Facilitates the weekly review
- Ensures opportunities are evidence-based (not just opinions)
- Tracks validation results
- Reports progress to leadership

### Visual Board Layout

```
┌─────────────────────────────────────────────────────────────────┐
│ OUTCOME: Increase activation rate for SMB from 25% to 35%       │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  [Opportunity 1]      [Opportunity 2]      [Opportunity 3]       │
│  Users don't know     Onboarding takes     No value visible      │
│  where to start       too many steps       until day 3           │
│  ├─ Solution A        ├─ Solution D        ├─ Solution F         │
│  │  ✅ Validated      │  🔬 Testing        │  💡 Ideation        │
│  ├─ Solution B        └─ Solution E        └─ Solution G         │
│  │  ❌ Failed             🔬 Testing           💡 Ideation       │
│  └─ Solution C                                                   │
│     📊 Sizing                                                    │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Team Effectiveness: Want-Know-Feedback

### Want To (Motivation)

Teams need intrinsic motivation to do their best work on OST:
- **Autonomy:** Team chooses HOW to achieve the outcome (solutions, experiments, approaches). Leadership sets WHAT (the outcome), not how.
- **Visible impact:** Team can see their experiments move the metric. Celebrate wins publicly. Share learnings from failures.
- **Ownership:** The team OWNS the outcome. No external team can override their prioritization without discussion.

**Warning signs of low motivation:** Team treats OST as a checkbox, not a tool. Weekly reviews are skipped. PM fills in the tree alone.

### Know How (OST Structure)

Teams need to understand the methodology:
- **OST training:** 60-minute session explaining outcome definition, opportunity identification, solution validation
- **Templates:** Provide standard templates for each level (opportunity card, solution brief, experiment design)
- **Examples:** Show completed OSTs from other teams or industry examples
- **Coaching:** PM mentor or growth lead reviews the tree monthly, suggests improvements

**Warning signs of low capability:** Opportunities are really solutions in disguise ("opportunity: add a tutorial" -- that's a solution; the opportunity is "users don't know where to start"). Solutions skip validation. Outcomes are too vague.

### Get Feedback (Shared Loops)

Teams need fast feedback on whether their work is working:
- **Shared dashboards:** Outcome metric visible to the whole team, updated daily/weekly
- **Experiment results:** Reviewed together, not just by the PM. Full team discusses implications.
- **Retrospectives:** What did we learn this sprint? What should we try differently?
- **Cross-team sharing:** Teams share their OST and learnings with other teams quarterly

**Warning signs of missing feedback:** Team ships solutions but never checks if the metric moved. Experiment results are filed and forgotten. No retrospectives.
