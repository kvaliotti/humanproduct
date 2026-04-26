# Decision-Driver Research Methodology

## Overview

Decision-driver research discovers and ranks the factors that drive customer purchase decisions, then maps those drivers to PLG mechanics. This methodology ensures your free/trial experience proves what customers actually care about — not what you assume they care about.

This was originally a standalone positioning skill (plg-positioning) but is merged into plg-readiness because PLG viability depends on whether top decision drivers can be demonstrated through self-serve product experience.

---

## Step 1: Define the Decision

Before researching drivers, precisely define what decision you are studying.

### 1a. ICP Definition
- **Who is the target user?** (Role, seniority, department, company size)
- **Who is the target buyer?** (Same as user? Manager? Procurement?)
- **What is their current situation?** (Using a competitor? Doing it manually? Not addressing the problem?)

### 1b. Decision Question
Frame the exact decision being made:
- "Should I adopt [product category] at all?" (New category adoption)
- "Should I switch from [competitor/manual process] to [your product]?" (Switching decision)
- "Should I upgrade from free to paid?" (Monetization decision)
- "Should I expand usage to my team?" (Expansion decision)

Each decision type has different drivers. Be specific about which you are researching.

### 1c. Role to Interview
- For adoption decisions: interview recent adopters (last 3-6 months)
- For switching decisions: interview recent switchers AND those who evaluated but did not switch
- For monetization decisions: interview recent converters AND active free users who have not converted
- For expansion decisions: interview team admins and champions

---

## Step 2: Discover Drivers (Interview-Based)

### Interview Guide — Wide Discovery Format

**Goal:** Identify the full range of decision drivers without leading the interviewee.

**Interview structure (30-45 minutes):**

#### Opening (5 min)
"I am researching how people in your role make decisions about [category]. I want to understand your experience, not test any hypotheses."

#### Trigger & Context (10 min)
1. "What triggered you to start looking for a solution like [category]?"
2. "What was your first research action? Where did you go first?"
3. "Who else was involved in the evaluation or decision?"
4. "What were the stakes? What would happen if you chose wrong?"

#### Evaluation Process (15 min)
5. "What criteria mattered most when comparing options?"
6. "How did you evaluate whether a product met each criterion?"
7. "What surprised you during the evaluation? Anything you didn't expect to care about?"
8. "Were there any deal-breakers — things that would have eliminated an option immediately?"
9. "How did you narrow from a long list to a short list?"

#### Decision (10 min)
10. "Why did you ultimately select [product they chose]?"
11. "What was the second-best option? Why didn't you choose it?"
12. "What was the closest call — which criterion almost tipped the decision the other way?"
13. "If you had to justify the decision to your boss in one sentence, what would you say?"

#### Closing (5 min)
14. "Is there anything about your decision process I didn't ask about that mattered?"

### Synthesizing Interview Data

After 8-12 interviews, extract:
1. **Raw driver list:** Every criterion, concern, or factor mentioned
2. **Frequency count:** How many interviewees mentioned each driver
3. **Intensity signals:** Which drivers were described with emotion, emphasis, or stories
4. **Deal-breaker list:** Which drivers were pass/fail (not graded)
5. **Surprise drivers:** Factors that emerged that you didn't anticipate

Group raw drivers into categories (MECE). Typical categories:
- Functional capability (does it DO what I need?)
- Ease of use / learning curve
- Time to value / speed of implementation
- Price / total cost of ownership
- Trust / security / reliability
- Integration with existing tools
- Team/collaboration features
- Support and documentation
- Brand / market presence / social proof
- Future roadmap / company viability

---

## Step 3: Rank Drivers (Survey-Based)

### Likert Rating
For each driver identified in Step 2, ask survey respondents:

"How important is [driver] in your decision to [adopt/switch/upgrade]?"
- 1 = Not at all important
- 2 = Slightly important
- 3 = Somewhat important
- 4 = Moderately important
- 5 = Important
- 6 = Very important
- 7 = Extremely important

**Minimum sample:** 30 respondents for directional insights, 100+ for statistical significance.

### 5-Dimension Deep Dive (Top Drivers Only)

For the top 5-7 drivers (highest average rating), assess these 5 dimensions:

#### Dimension 1: Meaning
"When you say [driver] is important, what exactly do you mean by that?"
- Unpack the specific sub-attributes
- Identify what "good" looks like concretely
- Surface different interpretations across respondents

#### Dimension 2: Indicators
"What evidence or proof do you look for to assess [driver]?"
- What would they see in a product demo?
- What would they read in documentation?
- What would they test during a trial?
- What social proof matters? (Reviews, case studies, certifications)

#### Dimension 3: Measurement
"How do you evaluate whether a product delivers on [driver]?"
- Quantitative measures (speed benchmarks, uptime SLAs, feature checklists)
- Qualitative measures (feel of the UI, quality of support interaction)
- Comparative measures (side-by-side evaluation)

#### Dimension 4: Comparison
"How do you compare products on [driver]?"
- Direct comparison (feature matrix, side-by-side trial)
- Proxy comparison (reviews, recommendations, analyst reports)
- Experience comparison (trial both products)

#### Dimension 5: Credibility
"What makes a claim about [driver] believable?"
- First-party evidence (product demo, trial experience)
- Third-party evidence (analyst reports, independent reviews)
- Social proof (customer testimonials, community size)
- Guarantees (SLAs, money-back guarantees, certifications)

---

## Step 4: Statistical Synthesis

### Basic Statistics Per Driver

| Driver | Avg (1-7) | Median | Std Dev | Interpretation |
|--------|-----------|--------|---------|----------------|
| [Driver A] | 6.2 | 6 | 0.8 | High importance, consensus = table stakes |
| [Driver B] | 5.8 | 6 | 2.1 | High importance, high variance = segmentation signal |
| [Driver C] | 4.5 | 5 | 2.3 | Mid importance, high variance = different ICPs |
| [Driver D] | 3.2 | 3 | 0.9 | Low importance, consensus = not a differentiator |

### Interpretation Rules

**High Average + Low StdDev (< 1.0):**
- Universally important. This is table stakes.
- Must be competent here but unlikely to differentiate.
- In PLG: must be proven in free experience (it is expected).

**High Average + High StdDev (> 1.5):**
- Important but segment-dependent. Different groups value it differently.
- Potential differentiation opportunity for the right segment.
- In PLG: tailor free experience to your highest-value segment's interpretation.

**Mid Average + High StdDev:**
- Segmentation signal. Some people care a lot, others don't care at all.
- Likely maps to different ICPs or use cases.
- In PLG: consider segment-specific onboarding paths.

**Low Average + Low StdDev:**
- Not important to anyone. Do not invest here.
- In PLG: do not waste free experience on demonstrating this.

### Segmentation Analysis
If StdDev > 1.5 on any top driver, segment the data by:
- Company size (SMB vs. mid-market vs. enterprise)
- Role (IC vs. manager vs. exec)
- Use case (primary workflow they described)
- Current solution (specific competitor vs. manual process vs. nothing)

Look for clusters where the same driver is rated very differently. These are your segments.

---

## Step 5: Map Drivers to PLG Mechanics

This is the critical synthesis step that connects positioning research to PLG strategy.

### Driver-to-Experience Alignment Matrix

| Rank | Decision Driver | Can Free/Trial Experience Prove This? | How? | Gap? |
|------|----------------|--------------------------------------|------|------|
| 1 | [Top driver] | Yes / Partially / No | [specific mechanism] | [if gap, what to fix] |
| 2 | [Second driver] | Yes / Partially / No | [specific mechanism] | |
| 3 | [Third driver] | Yes / Partially / No | [specific mechanism] | |

### Key Questions

1. **Does activation prove the #1 driver?**
   - If YES: PLG has natural conversion power. The aha moment IS the top decision driver.
   - If NO: Critical misalignment. Either redesign activation to demonstrate #1 driver, or accept that PLG will underperform on conversion.

2. **Which drivers require TIME to demonstrate?**
   - Drivers like "reliability" or "long-term ROI" cannot be proven in a 14-day trial.
   - Mitigation: social proof, case studies, SLAs, data from other users.

3. **Which drivers require TEAM adoption to demonstrate?**
   - Drivers like "collaboration" or "team productivity" need multiple users.
   - Mitigation: team trial, invite flows, shared workspaces.

4. **Which drivers are better proven by sales than product?**
   - Drivers like "vendor stability" or "enterprise support" may need human reassurance.
   - These are signals for sales-assist model, not pure self-serve.

---

## JTBD Integration

Map decision drivers to Jobs-to-Be-Done for richer insight:

**Job statement format:** "When [situation], I want to [motivation], so I can [outcome]."

For each top driver, identify the underlying job:
- Driver: "Easy to use" → Job: "When I'm under time pressure, I want a tool I can use without training, so I can deliver results immediately."
- Driver: "Integrations" → Job: "When I have data in multiple systems, I want everything connected, so I don't waste time on manual data transfer."

The job behind the driver tells you HOW to design the free experience.

---

## Competitive Positioning Gap Analysis

### Driver Performance Matrix

| Driver | Your Product (1-10) | Competitor A (1-10) | Competitor B (1-10) | Gap |
|--------|---------------------|--------------------|--------------------|-----|
| [Driver 1] | | | | |
| [Driver 2] | | | | |
| [Driver 3] | | | | |

**Positioning opportunities:**
- Drivers where you score highest = lead with these in messaging and free experience
- Drivers where you score lowest but importance is high = fix or de-emphasize
- Drivers where no one scores well = potential new category positioning

### New Category Positioning

If research reveals a driver that is highly important but no current solution addresses well, consider creating a new category:
1. Name the unmet need as a category
2. Define the evaluation criteria (yours)
3. Position competitors as solving the old problem
4. Position yourself as solving the real problem

---

## Positioning-to-PLG Alignment Checklist

Use this checklist to verify alignment:

- [ ] Top 3 decision drivers are identified and ranked
- [ ] Each top driver has been unpacked across 5 dimensions (Meaning, Indicators, Measurement, Comparison, Credibility)
- [ ] Activation / aha moment demonstrates at least the #1 driver
- [ ] Free experience allows evaluation of top 3 drivers
- [ ] Drivers that require time/team are addressed through social proof or trial design
- [ ] Messaging on landing page leads with top decision drivers (not features)
- [ ] Upgrade triggers align with moments where paid features serve top drivers
- [ ] Competitive differentiation is visible in the free experience (not just paid)

---

## Output Template

```
### Decision-Driver Research Summary

**Decision studied:** [What decision, for whom]
**Sample:** [N interviews, M survey respondents]

**Top Decision Drivers (Ranked):**
1. [Driver] — Avg: X.X, StdDev: X.X — [Interpretation]
2. [Driver] — Avg: X.X, StdDev: X.X — [Interpretation]
3. [Driver] — Avg: X.X, StdDev: X.X — [Interpretation]
4. [Driver] — Avg: X.X, StdDev: X.X — [Interpretation]
5. [Driver] — Avg: X.X, StdDev: X.X — [Interpretation]

**PLG Alignment:**
- #1 driver provable in free experience: [Yes/No — how]
- Top 3 drivers addressable in self-serve: [Yes/Partially/No]
- Critical gap: [if any]

**Segmentation Signals:**
- [Segment A values X differently because...]
- [Segment B values Y differently because...]

**Positioning Recommendation:**
[2-3 sentences on how to position based on driver research]

**PLG Design Implications:**
- Activation should demonstrate: [driver]
- Free experience should include: [capability]
- Upgrade trigger should align with: [driver/limit]
```
