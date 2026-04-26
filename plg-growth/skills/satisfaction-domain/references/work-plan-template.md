# Satisfaction Work Plan Template

## Work Plan Types

Choose the type based on user situation:

| Situation | Type | Structure |
|-----------|------|-----------|
| No satisfaction measurement in place | **OST** | Build measurement infrastructure |
| Has data, needs to improve scores | **Experiment Backlog** | Prioritized improvements |
| Needs qualitative understanding of drivers | **Research Plan** | Deep-dive discovery |

---

## Type 1: OST (Objectives, Strategies, Tactics)

Use when the user needs strategic direction for satisfaction improvement.

### Template

```
## Satisfaction Work Plan: OST

### Objective
[Specific, measurable goal]
Example: "Increase NPS from 25 to 40 within 2 quarters by reducing Detractor rate from 22% to 12%"

### Strategy 1: [Strategy Name]
Hypothesis: "We believe [strategy] will improve [metric] because [reasoning]"

Tactics:
1. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]
2. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]
3. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]

### Strategy 2: [Strategy Name]
Hypothesis: "We believe [strategy] will improve [metric] because [reasoning]"

Tactics:
1. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]
2. [Tactic] -- Owner: [who] -- Timeline: [when] -- Metric: [what to measure]

### Key Unknowns
- [What we need to learn before committing]

### Success Criteria
- [How we will know the objective is met]
- [Leading indicators to track weekly/monthly]
```

### Satisfaction-Specific OST Examples

**Objective:** Increase NPS from 25 to 40 within 2 quarters

**Strategy 1: Reduce Detractor rate through friction elimination**
- Hypothesis: "We believe fixing the top 3 highest-effort workflows will reduce Detractor rate by 8 percentage points because 60% of Detractor comments reference usability frustration"
- Tactic 1: Deploy CES measurement on top 10 workflows (Week 1-2)
- Tactic 2: Redesign highest-CES workflow — export process (Weeks 3-6)
- Tactic 3: Redesign second-highest-CES workflow — team invitation (Weeks 7-10)
- Tactic 4: Redesign third-highest-CES workflow — integration setup (Weeks 11-14)

**Strategy 2: Activate Promoters as growth lever**
- Hypothesis: "We believe giving Promoters referral tools will increase referral rate from 3% to 8% because Promoters score high but have no easy way to share"
- Tactic 1: Implement referral mechanism (share link, invite credits) (Weeks 1-4)
- Tactic 2: Trigger referral prompt to users who scored 9-10 (Week 5)
- Tactic 3: Measure referral conversion and attribute to NPS (Week 6-12)

**Strategy 3: Build closed-loop feedback system**
- Hypothesis: "We believe responding to every Detractor within 48 hours will recover 20% of Detractors to Passive or higher because acknowledged users are 2x more likely to stay"
- Tactic 1: Set up Detractor alert → CS routing (Week 1)
- Tactic 2: Create Detractor response playbook (Week 2)
- Tactic 3: Launch recovery program, track re-survey at 30 days (Week 3+)

---

## Type 2: Experiment Backlog

Use when the user has satisfaction data and needs to test specific improvements.

### Template

```
## Satisfaction Experiment Backlog

### Experiment 1: [Name]
- Branch: [Which issue tree branch this tests]
- Hypothesis: "We believe [change] will [outcome] because [reasoning]"
- Metric: [Primary satisfaction metric + downstream business metric]
- Success criteria: [Threshold, e.g., "CES improvement from 3.8 to 5.0"]
- Audience: [Who is affected]
- Duration: [Test duration]
- Effort: [S/M/L]
- Expected impact: [Satisfaction change → estimated retention/revenue impact]
```

### Satisfaction-Specific Experiment Examples

**Experiment: Onboarding Redesign**
- Branch: Root Cause > Opportunity > Onboarding Quality
- Hypothesis: "We believe a guided onboarding flow will increase post-onboarding CSAT from 68% to 82% because new users report confusion in their first session"
- Metric: Post-onboarding CSAT + 30-day activation rate
- Success criteria: CSAT > 78%, activation rate improvement > 5%
- Audience: New signups, 500 per variant
- Duration: 4 weeks
- Effort: M
- Expected impact: +14% CSAT → estimated +5% retention at 90 days

**Experiment: Performance Optimization**
- Branch: Root Cause > Capability > Performance/Reliability
- Hypothesis: "We believe reducing dashboard load time from 4s to <1s will increase CES for reporting workflow from 4.1 to 5.5 because speed is the #1 Detractor complaint for this feature"
- Metric: CES for reporting workflow + feature retention (weekly usage)
- Success criteria: CES > 5.0
- Audience: All reporting feature users
- Duration: 2 weeks post-deployment
- Effort: L
- Expected impact: CES improvement → estimated -3% churn for power users

**Experiment: Detractor Recovery Outreach**
- Branch: Closing the Loop > Detractor Recovery
- Hypothesis: "We believe personal outreach to Detractors within 24 hours will recover 25% to Passive or higher because most Detractors want to be heard, not just surveyed"
- Metric: 30-day NPS re-survey score for contacted Detractors
- Success criteria: 25%+ move from Detractor (0-6) to Passive (7-8) or Promoter (9-10)
- Audience: All NPS Detractors (0-6 scores)
- Duration: 8 weeks (one NPS cycle)
- Effort: S (CS time, no engineering)
- Expected impact: Recovering 25% of Detractors = +5 NPS points

---

## Type 3: Research Plan

Use when the user needs qualitative understanding of satisfaction drivers before making decisions.

### Template

```
## Satisfaction Research Plan

### Research Question
[What do we need to learn?]

### Study 1: [Method]
- Objective: [What this study answers]
- Method: [Interviews / Observation / Survey / Analysis]
- Participants: [Who, how many, how recruited]
- Timeline: [Design, field, analysis]
- Deliverable: [What the output looks like]
- Decision it informs: [What strategy depends on this]
```

### Satisfaction-Specific Research Examples

**Research Question:** "Why are 22% of users Detractors and what would convert them?"

**Study 1: Detractor Deep-Dive Interviews**
- Objective: Understand root causes of dissatisfaction and identify recoverable Detractors
- Method: 30-minute semi-structured interviews
- Participants: 12 Detractors (0-6 NPS), recruited from latest NPS survey
- Segment: 4 from score 0-3, 4 from score 4-5, 4 from score 6
- Timeline: Recruit (1 week), Interview (2 weeks), Synthesize (1 week)
- Deliverable: Detractor theme taxonomy, recovery opportunity map, COM-B classification
- Decision it informs: Which root causes to address first

**Study 2: Passive Conversion Interviews**
- Objective: Understand what separates Passives from Promoters
- Method: 20-minute semi-structured interviews
- Participants: 8 Passives (7-8 NPS) + 8 Promoters (9-10 NPS) for comparison
- Timeline: Recruit (1 week), Interview (2 weeks), Synthesize (1 week)
- Deliverable: Gap analysis (Passive vs Promoter behaviors, needs, perceptions)
- Decision it informs: Where to invest for Passive → Promoter conversion

**Study 3: Effort Mapping Observation**
- Objective: Identify highest-friction product workflows through direct observation
- Method: Task-based usability observation (5 key tasks, think-aloud protocol)
- Participants: 10 users (mix of tenure and plan)
- Timeline: Design tasks (3 days), Sessions (2 weeks), Analysis (1 week)
- Deliverable: Effort score per task, friction point inventory, severity rating
- Decision it informs: Which workflows to redesign for CES improvement

**Research Sequence:** Study 1 first (identifies themes), then Studies 2 and 3 in parallel (deepens understanding of Passive gap and effort sources).

---

## Universal Work Item Format

Regardless of plan type, every work item should include:

```
### [Item Name]
- Issue tree branch: [Which branch this addresses]
- Hypothesis: "We believe [X] because [Y]"
- Action: [Specific, concrete action]
- Owner: [Person or team]
- Timeline: [Start and end date]
- Satisfaction metric: [NPS / CSAT / CES / PMF change expected]
- Business metric: [Retention / expansion / referral impact expected]
- Dependencies: [What must happen first]
- Risk: [What could go wrong and mitigation]
```
