# NPS, CSAT, CES, and PMF Survey Methodology

Comprehensive reference for the four satisfaction measurement methods used in PLG growth analysis.

---

## 1. Net Promoter Score (NPS)

### Overview
Relationship-level satisfaction metric. Measures overall loyalty and likelihood to recommend. Best for tracking long-term sentiment trends and segmenting users by advocacy level.

### Question Wording

**Standard question:**
> "On a scale of 0 to 10, how likely are you to recommend [Product Name] to a friend or colleague?"

**Follow-up (required):**
> "What is the primary reason for your score?"

The follow-up is where the real insight lives. Never skip it.

### Scoring

| Score | Category | Meaning |
|-------|----------|---------|
| 9-10 | **Promoter** | Loyal enthusiasts who will fuel growth through referrals |
| 7-8 | **Passive** | Satisfied but unenthusiastic. Vulnerable to competitors. |
| 0-6 | **Detractor** | Unhappy users who can damage brand through negative word-of-mouth |

### Calculation

```
NPS = (% Promoters) - (% Detractors)
```

Range: -100 to +100

**Benchmarks (B2B SaaS):**
- Below 0: Serious problem
- 0-20: Room for improvement
- 20-40: Good (median range)
- 40-60: Excellent
- 60+: World-class

### Touchpoints for Collection

**In-app survey (primary):**
- Trigger: After user has been active for 30+ days (avoid asking too early)
- Placement: Subtle slide-in or modal, not blocking workflow
- Frequency: No more than once per quarter per user
- Targeting: Only active users (do not survey churned users via in-app)

**Email survey (supplementary):**
- Trigger: Quarterly cadence or at lifecycle milestones
- Benefit: Can reach inactive users and get churn-risk signals
- Response rate: Typically 10-25% (lower than in-app)
- Timing: Mid-week, mid-morning for B2B

**Post-interaction (transactional NPS):**
- Trigger: After support interaction, after onboarding, after major feature use
- Note: This is really closer to CSAT — label it appropriately
- Benefit: Ties satisfaction to specific experiences

### Cadence

- **Relationship NPS:** Quarterly. Consistent cadence enables trending.
- **Transactional NPS:** Real-time, after the interaction.
- **Rolling NPS:** Survey a random 25% of users each month. Provides monthly NPS with quarterly full-base coverage.

### Segmentation (Essential)

Never report a single NPS number. Always segment by:

| Segment | Why |
|---------|-----|
| Plan/tier | Free users vs paid users have different expectations |
| Tenure | New users vs 1-year users score differently |
| Company size | SMB vs Enterprise have different satisfaction drivers |
| Feature usage | Power users vs light users |
| Role | Admin vs end-user vs buyer |
| Acquisition channel | Different channels attract different expectations |

### Action Framework

**For Detractors (0-6):**
1. Alert: Notify CS/support within 24 hours
2. Respond: Personal outreach acknowledging feedback
3. Resolve: Address the specific issue raised
4. Re-survey: Follow up in 30 days to measure recovery
5. Analyze: Cluster themes across all Detractors

**For Passives (7-8):**
1. Analyze: What separates them from Promoters? (feature usage, onboarding quality, engagement depth)
2. Nudge: Help them discover value they are missing
3. Convert: Small improvements can tip Passives to Promoters

**For Promoters (9-10):**
1. Verify: Do they actually refer? (check referral data)
2. Activate: Give them tools to refer (referral program, share features, review prompts)
3. Amplify: Ask for testimonials, case studies, reviews
4. Protect: Monitor for score drops — a declining Promoter is a churn risk

---

## 2. Customer Satisfaction Score (CSAT)

### Overview
Transactional and feature-level satisfaction metric. Measures satisfaction with a specific interaction, feature, or experience. Best for identifying specific product areas that need improvement.

### Question Wording

**Standard question:**
> "How satisfied are you with [specific experience/feature]?"

**Scale options:**
- 1-5 scale: Very Dissatisfied / Dissatisfied / Neutral / Satisfied / Very Satisfied
- 1-7 scale: Adds "Slightly Dissatisfied" and "Slightly Satisfied" for more granularity

**Follow-up:**
> "What could we improve?"

### Calculation

```
CSAT = (Number of satisfied responses / Total responses) x 100
```

"Satisfied" = top 2 box on a 5-point scale (Satisfied + Very Satisfied) or top 3 box on a 7-point scale.

**Benchmarks:**
- Below 60%: Poor
- 60-75%: Needs improvement
- 75-85%: Good
- 85%+: Excellent

### When to Use

**After support interaction:**
> "How satisfied were you with the support you received?"
- Timing: Immediately after ticket resolution
- Measures: Support quality, not product quality

**After feature use:**
> "How satisfied are you with [Feature Name]?"
- Timing: After meaningful engagement with the feature (not first click)
- Measures: Feature quality, usability, value delivery

**After onboarding:**
> "How satisfied are you with your onboarding experience?"
- Timing: After onboarding completion (or 7 days after signup)
- Measures: First experience quality, time-to-value

**After key milestones:**
> "How satisfied are you with [Product] for [use case]?"
- Timing: After first project completed, first report generated, first collaboration, etc.
- Measures: Value delivery for the specific use case

### Segmentation

Segment CSAT the same way as NPS, plus:
- By specific feature or workflow
- By interaction type (support, onboarding, billing)
- By task complexity (simple vs complex workflows)

### Analysis Approach

1. Rank features/interactions by CSAT score
2. Identify the bottom 3 (lowest satisfaction)
3. For each, examine the open-ended feedback
4. Classify root causes using COM-B (Capability, Opportunity, Motivation)
5. Prioritize by: (a) number of users affected, (b) correlation with retention

---

## 3. Customer Effort Score (CES)

### Overview
Measures the effort required to complete a specific task. High effort correlates strongly with churn. Best for identifying friction points in the product experience.

### Question Wording

**Standard question:**
> "How easy was it to [complete specific task]?"

**Scale:** 1-7
- 1: Very Difficult
- 4: Neither Easy nor Difficult
- 7: Very Easy

**Alternative wording:**
> "[Product] made it easy to [task]." — Strongly Disagree to Strongly Agree

### Calculation

```
CES = Average score across responses
```

Or: % of respondents scoring 5-7 (easy)

**Benchmarks:**
- Below 4.0: High friction, needs immediate attention
- 4.0-5.0: Moderate friction, improvement opportunity
- 5.0-6.0: Good
- 6.0+: Excellent, low effort

### Best Use Cases

CES is most valuable for:
- **Onboarding tasks:** Setting up account, connecting integrations, inviting team
- **Core workflows:** The 3-5 tasks users do most frequently
- **Complex tasks:** Tasks that require multiple steps or learning
- **Support interactions:** How easy was it to get help?
- **Billing/upgrade tasks:** How easy was it to change plan?

### Implementation

1. Identify the 5-10 most important user tasks
2. Add CES survey trigger after task completion
3. Collect continuously (not batched quarterly)
4. Track CES trend per task over time
5. Correlate high-effort tasks with support tickets and churn

### Correlation with Retention

Research consistently shows:
- High-effort experiences are 4x more likely to drive disloyalty than low-effort experiences
- 96% of high-effort customers are disloyal vs 9% of low-effort customers
- Reducing effort has a stronger effect on loyalty than exceeding expectations

**Implication for PLG:** Reducing friction in key workflows may have a larger retention impact than adding new features. Measure effort, fix friction, re-measure.

---

## 4. Product-Market Fit (PMF) Survey

### Overview
The Sean Ellis test measures how essential your product has become to users. Run as an ongoing signal (not just once), it tracks whether you are maintaining and deepening PMF.

### Question Wording

**Core question:**
> "How would you feel if you could no longer use [Product Name]?"

**Response options:**
- Very disappointed
- Somewhat disappointed
- Not disappointed

**Follow-up questions:**

> "What type of people do you think would most benefit from [Product]?"
(Identifies your best-fit user segment in their words)

> "What is the main benefit you receive from [Product]?"
(Identifies your core value proposition in their words)

> "How can we improve [Product] for you?"
(Identifies gaps and opportunities)

### Interpretation

```
PMF Signal = % "Very Disappointed"
```

| % Very Disappointed | Interpretation |
|---------------------|---------------|
| Below 20% | Weak PMF — product is nice-to-have, not must-have |
| 20-30% | Emerging PMF — getting closer, focus on the "very disappointed" segment |
| 30-40% | Moderate PMF — strong with a segment, potential to broaden |
| 40%+ | Strong PMF — product is essential for a meaningful user base |

### Who to Survey

**Target: Power users and regular users only.**
- Users who have used the product at least 2x in the last 2 weeks
- Users who have completed core workflows
- Do NOT survey users who signed up yesterday (they have not experienced enough)

**Sample size:** Minimum 40 responses per segment for meaningful data.

### Cadence

- **Quarterly:** Run to track PMF over time
- **After major launches:** Run 2-4 weeks after a major feature release to measure impact
- **By segment:** Run separately for different user segments to identify where PMF is strongest

### Analysis Methodology

1. Calculate overall % "Very Disappointed"
2. Segment by user type, plan, company size, use case
3. Identify the segment with highest % "Very Disappointed" — this is your core PMF audience
4. Read the "main benefit" responses from the "Very Disappointed" group — this is your real value proposition
5. Read the "how can we improve" responses — these are your roadmap priorities
6. Compare across quarters — is PMF strengthening or weakening?

### Connecting PMF to Growth

- **PMF segment = ICP definition:** The segment with highest "Very Disappointed" rate is your ICP. Acquisition should target this segment.
- **PMF value prop = messaging:** The "main benefit" language from PMF respondents should appear in your marketing and pricing page.
- **PMF improvement areas = roadmap:** The "how to improve" responses from "Very Disappointed" users should drive product priorities. These users already love the product — make it even better for them.

---

## Survey Infrastructure Best Practices

### Technical Implementation
- Use in-app survey tools (Pendo, Hotjar, Survicate, Typeform, custom)
- Ensure surveys do not block user workflow (dismissible, non-modal preferred)
- Store responses linked to user profile for segmentation
- Integrate with product analytics for correlation analysis

### Preventing Survey Fatigue
- No user should receive more than 1 survey per month
- Implement a "survey cooldown" system (global, per-user suppression)
- Prioritize: NPS quarterly > CSAT at key moments > CES on critical tasks > PMF quarterly
- Rotate survey targeting (different users each cycle for NPS)

### Response Rate Optimization
- Keep surveys to 2-3 questions maximum (core question + 1 follow-up + optional comment)
- In-app surveys get 20-40% response rate (vs 10-25% for email)
- Trigger at natural pause points (after task completion, not mid-workflow)
- Show that feedback leads to action ("You asked, we built" communications)

### Closed-Loop System
1. **Collect:** Survey at the right touchpoint
2. **Route:** Detractors → CS for outreach; Themes → product for roadmap
3. **Act:** Fix the issue or build the feature
4. **Communicate:** Tell users what changed because of their feedback
5. **Re-measure:** Survey again to confirm improvement
