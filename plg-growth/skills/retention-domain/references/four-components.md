# Four Components of Retention

Retention is not one thing. It is four interconnected components. Diagnosing which component is broken determines the intervention strategy.

---

## Component 1: Activation (Leading Indicator)

**Definition:** The user reaches the first moment of value. This is the gateway to all retention.

**Connection:** This component is fully covered by `activation-domain`. If activation is the weak link, route there.

**Why it is a retention component:**
- Users who do not activate almost never retain (< 5% retention for non-activated users is typical)
- Activation rate is the single strongest predictor of retention at 30/60/90 days
- Improving activation has the highest leverage on retention because it is the earliest intervention point

**Key Metrics:**
- Activation rate (% of signups who reach activation event within time window)
- Time-to-value (median time from signup to activation)
- Activation rate by cohort (trending up or down?)

**When Activation is the Problem:**
- Retention curve drops sharply in the first 7 days
- Vast majority of churn happens before users reach the aha moment
- Activated users show healthy retention but the activation funnel is leaky

**Intervention:** Route to `activation-domain` for deep analysis and work planning.

---

## Component 2: Adoption (Breadth)

**Definition:** The breadth of product features a user engages with. Adoption measures how much of the product's surface area a user has explored and incorporated into their workflow.

**Why it matters for retention:**
- Users who adopt more features have higher switching costs (more invested in the product)
- Broader adoption = more use cases served = more reasons to stay
- Single-feature users are fragile: if that feature disappoints, they leave
- Multi-feature users tolerate individual feature issues because overall value is high

**Key Metrics:**
- Features used per user (average and distribution)
- Feature adoption rate per feature (% of users who used it at least once)
- Core feature set: which features do retained users consistently use?
- Feature adoption sequence: what order do users typically adopt features in?

### Feature Adoption Heatmap

Build a heatmap:
- Rows: product features (grouped by category)
- Columns: user segments (or retained vs. churned)
- Cell value: % who used the feature regularly (not just once)

**What to look for:**
- **Core features (high adoption, high retention correlation):** These are table stakes. Ensure every user adopts them.
- **Hidden gems (low adoption, high retention correlation):** Users who find them stay, but most do not find them. Discoverability problem.
- **Shiny objects (high adoption, low retention correlation):** Popular but do not drive retention. Do not over-invest.
- **Dead weight (low adoption, low retention correlation):** Consider deprecating or redesigning.

### Adoption Barriers and Tactics

**Discoverability:**
- Users do not know the feature exists
- Tactics: feature announcements, contextual tips, onboarding checklist expansion, "Did you know?" prompts
- Measure: feature page views vs. feature usage (high views, low usage = different problem)

**Usability:**
- Users find the feature but cannot use it effectively
- Tactics: UX simplification, inline guidance, better defaults, tutorials
- Measure: feature start rate vs. feature completion rate

**Perceived Value:**
- Users can use the feature but do not see why they should
- Tactics: use case examples, success stories, value messaging, integration with core workflow
- Measure: feature trial rate vs. feature repeat rate

**Feature Announcement Best Practices:**
- In-app changelog or "What's New" section
- Contextual announcement (show the feature tip when the user is in a related area)
- Email announcement for major features (segment by relevance)
- Do NOT announce every small change. Save announcements for meaningful additions.

---

## Component 3: Engagement (Depth)

**Definition:** The depth and intensity of product usage. While adoption measures breadth (how many features), engagement measures depth (how often, how intensely, how recently).

**Why it matters for retention:**
- Frequency creates habit (habit = automatic retention)
- Intensity creates value (deep sessions = more value extracted)
- Recency predicts churn (users who have not engaged recently are at risk)
- Engaged users expand, refer, and advocate

**Key Metrics:**

| Metric | Definition | Healthy PLG SaaS |
|--------|-----------|------------------|
| DAU/MAU ratio | Daily active / Monthly active | > 20% casual, > 40% sticky |
| WAU/MAU ratio | Weekly active / Monthly active | > 50% |
| Sessions per week | Average sessions per active user | 3-5 for daily-use products |
| Actions per session | Meaningful actions per session | 5-15 |
| Session duration | Average time in product | Depends on product type |
| Recency | Days since last session | < 7 for weekly products |

### Engagement Scoring

Build a composite engagement score:

```
Engagement Score = (0.4 * Frequency) + (0.3 * Recency) + (0.3 * Intensity)

Where:
- Frequency = min(sessions_this_week / target_sessions, 1.0)
- Recency = max(0, 1 - days_since_last / dormancy_threshold)
- Intensity = min(actions_per_session / target_actions, 1.0)
```

Segment users by score:
- **Power users (0.8-1.0):** Advocates, expansion candidates. Nurture and celebrate.
- **Active users (0.5-0.8):** Healthy. Maintain engagement, deepen adoption.
- **At-risk users (0.2-0.5):** Engagement declining. Intervene with triggers.
- **Dormant users (0-0.2):** Gone quiet. Route to resurrection.

### Engagement Improvement Levers

**Triggers and Notifications:**
- Email: weekly digest, activity summary, personalized recommendations
- Push/in-app: real-time alerts for collaborative activity, task reminders
- Integration triggers: Slack/Teams notifications for product events
- Timing: match triggers to natural use-case frequency (do not over-notify)

**Integrations:**
- Connect to tools the user already uses daily (Slack, email, calendar, CRM)
- Make the product present where the user already is
- Reduce the "open another app" friction

**Context Coverage:**
- Cover more of the user's workflow within the product
- Example: if users export data to analyze in Excel, build analysis features
- More context covered = more reasons to open the product = higher frequency

**Habit Formation:**
- Identify the natural use-case frequency (daily? weekly? monthly?)
- Design triggers that match natural frequency
- Build variable rewards (new insights, updated data, social interactions)
- Encourage investment (customization, data entry, network building)

---

## Component 4: Resurrection (Recovery)

**Definition:** Re-engaging users who have gone dormant. Resurrection is the safety net -- it cannot replace good activation, adoption, and engagement, but it recovers users who slipped through.

**Why it matters:**
- Dormant users are a large, often untapped pool
- Reactivating a dormant user costs less than acquiring a new one
- Dormant users already have context and (possibly) data in the product
- Even a 5-10% reactivation rate from a large dormant pool is meaningful

**Key Metrics:**
- Dormancy rate: % of once-active users who are now dormant
- Reactivation rate: % of dormant users who return to active
- Reactivation retention: % of reactivated users who stay active for 30+ days
- Cost per reactivation vs. cost per new acquisition

### Defining Dormancy

Dormancy threshold is product-specific:
- **Daily-use products (messaging, collaboration):** Dormant after 7-14 days of inactivity
- **Weekly-use products (project management, analytics):** Dormant after 21-30 days
- **Monthly-use products (invoicing, reporting):** Dormant after 45-60 days
- **Seasonal products:** Account for natural usage cycles before declaring dormancy

### Reactivation Tactics

**Email Sequences:**
- Trigger: user crosses dormancy threshold
- Email 1 (Day 0 of dormancy): "We miss you" + what is new since they left
- Email 2 (Day 7): Specific value reminder based on their use case
- Email 3 (Day 14): Social proof -- what similar users are achieving
- Email 4 (Day 21): Final nudge -- offer or incentive to return
- Stop after 4 emails. Do not spam dormant users indefinitely.

**Magic Links:**
- One-click return to the product (no password, no login friction)
- Deep-link to where they left off or to the most relevant feature
- Reduces the "I do not remember my password" barrier

**"What's New Since You Left":**
- Show a curated changelog of features added since their last session
- Personalized: highlight features relevant to their use case
- Creates FOMO and shows the product is improving

**"Where You Left Off":**
- Preserve user state: open projects, draft content, in-progress workflows
- On return, show exactly where they were
- Reduces the "I have to start over" feeling
- "You had 3 items in progress. Ready to continue?"

**Returning User Onboarding:**
- Not the same as new user onboarding
- Acknowledge they are returning ("Welcome back!")
- Brief tour of what changed (not a full re-onboarding)
- Immediately show their existing data/projects

### When Resurrection is the Problem (vs. Prevention)
- If most churn happens in month 1-2: fix activation and engagement first
- If churn is spread across months 3+: both prevention and resurrection needed
- If reactivated users churn again quickly: the product has a fundamental value problem
- Rule of thumb: invest 80% in prevention (components 1-3), 20% in resurrection

---

## How the Components Interact

```
Activation → Adoption → Engagement
    ↓           ↓          ↓
    └───────────┴──────────┘
                ↓
         Resurrection (catches failures from any component)
```

**The healthy path:** Activation → explores features (Adoption) → builds habit (Engagement) → retains long-term.

**Failure at Activation:** User never gets value → churns immediately. Resurrection unlikely to work (no value memory).

**Failure at Adoption:** User uses one feature → that feature alone cannot sustain engagement → engagement drops → churn. Resurrection possible if you can show them new features.

**Failure at Engagement:** User adopted features but does not have triggers to return → usage fades → churn. Resurrection most effective here (user knows the product, just needs a nudge).

**Diagnosis priority:** Always fix the earliest broken component first. Improving engagement is pointless if users are not activating. Improving resurrection is pointless if the core product does not retain.
