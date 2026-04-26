# Churn Levers: Diagnosis and Intervention

Churn splits into two fundamentally different categories: voluntary (user chose to leave) and involuntary (user left due to payment/technical failure). Each requires different diagnosis and different tactics.

---

## Voluntary Churn

Users who consciously decided to leave. This is the harder churn to fix because it reflects a product or value gap.

### Category 1: Dissatisfied

**Definition:** User had a bad experience and chose to leave.

**Diagnostic Signals:**
- Low NPS or CSAT scores from churned users
- Support tickets that escalated or were unresolved
- Feature requests that went unanswered
- Complaints about specific UX issues, bugs, or performance

**Sub-Categories:**

#### UX Issues
- Confusing navigation, inconsistent design, poor mobile experience
- Users who complain about "hard to use" or "took too long"
- **Tactics:** UX audit, usability testing, design system cleanup, task completion time benchmarking

#### Bugs and Stability
- Crashes, data loss, errors, slow performance
- Users who complain about "unreliable" or "lost my work"
- **Tactics:** Stability sprints, error monitoring, performance budgets, data backup/recovery

#### Missing Features
- Users who need a capability the product does not offer
- Often expressed as "I need X to make this work for my use case"
- **Tactics:** Feature gap analysis vs. competitive set, prioritization by churn volume, build vs. integrate decision

#### Poor Support
- Slow response times, unhelpful answers, no resolution
- Users who complain about "could not get help" or "gave up"
- **Tactics:** Response time SLAs, support quality scoring, self-serve help improvement, escalation paths

### Category 2: Do Not Need Anymore

**Definition:** User's need ended. They are not dissatisfied -- the job is done.

**Diagnostic Signals:**
- User completed a project or achieved a goal
- Usage gradually declined to zero without complaints
- No support tickets, no negative feedback
- Often seasonal or project-based products

**Sub-Categories:**

#### Use Case Ended
- Project completed, event over, campaign finished
- **Tactics:** Help users find the NEXT use case, expand to adjacent jobs, build recurring value

#### Seasonal
- Product is relevant only at certain times (tax season, hiring season, budget season)
- **Tactics:** Accept natural cycles, focus on reactivation at start of next cycle, expand to adjacent seasons

#### Project-Based
- Product was needed for a specific initiative, not ongoing work
- **Tactics:** Build habit-forming features for ongoing value, create recurring workflows, shift from project to process

### Category 3: Competitor

**Definition:** User found a better alternative.

**Diagnostic Signals:**
- Exit survey mentions specific competitor
- User asks about features that competitors have
- Market reports show competitor gaining share
- Price comparison requests

**Sub-Categories:**

#### Better Product
- Competitor has features, UX, or performance the user values more
- **Tactics:** Competitive intelligence program, feature parity assessment, differentiation strategy (do not chase every competitor feature)

#### Better Price
- Competitor offers similar value at lower cost
- **Tactics:** Value-based pricing review, packaging optimization, free tier/trial adjustment, demonstrate total cost of ownership (not just license price)

#### Better Experience
- Competitor is easier to use, faster to implement, better supported
- **Tactics:** UX benchmarking against competitors, implementation speed improvement, support quality investment

### Category 4: Price

**Definition:** User believes the perceived value is less than the cost.

**Diagnostic Signals:**
- Downgrade requests before cancellation
- "Too expensive" in exit survey or cancellation reason
- Users on highest plans churning more than lower plans
- Price sensitivity in expansion conversations

**Tactics:**
- **Value demonstration:** Show ROI in-product ("You saved X hours / $Y this month")
- **Packaging redesign:** Ensure each tier has clear, differentiated value
- **Usage-based pricing:** Align cost with value received
- **Downgrade path:** Offer a lower tier instead of cancellation ("Keep basic features for $X/month")
- **Win-back pricing:** Temporary discount to retain at-risk users (use sparingly)

---

## Involuntary Churn

Users who did not choose to leave. Their payment failed, their card expired, or a technical issue prevented renewal. This is often 20-40% of total churn in SaaS and is the easiest to fix.

### Category 1: Payment Failure

**Sub-Categories:**

#### Card Expiry
- Most common cause of involuntary churn
- Card expires, payment fails, account gets suspended/cancelled
- **Tactics:**
  - Pre-expiry notifications: Email 30, 14, and 7 days before card expiry
  - In-app banner when card is within 30 days of expiry
  - Self-serve card update (single-click from notification)
  - Auto-update through payment processor (Stripe can update some expired cards automatically)

#### Insufficient Funds
- Payment attempted but declined due to lack of funds
- **Tactics:**
  - Smart retry: retry the charge at different times/days (often succeeds on payday cycles)
  - Retry schedule: Day 1, Day 3, Day 5, Day 7 (4 attempts over a week)
  - Notify user after first failure with easy update path
  - Downgrade to free tier instead of cancellation (if applicable)

#### Bank Blocks
- Bank flags the transaction as suspicious or blocks recurring payments
- **Tactics:**
  - Clear billing descriptor (user recognizes the charge)
  - Provide user with bank-friendly transaction details
  - Alternative payment methods (PayPal, wire, ACH as backup)
  - Customer support playbook for helping users contact their bank

### Category 2: Dunning Management

Dunning is the systematic process of recovering failed payments. A good dunning process can recover 30-70% of failed payments.

**Best Practice Dunning Sequence:**

| Day | Action | Channel |
|-----|--------|---------|
| 0 | Payment fails. Retry immediately. | Automatic |
| 1 | Email: "Payment failed, update your card" + direct link | Email |
| 3 | Retry payment. Email if fails again. | Automatic + Email |
| 5 | In-app banner: "Your account is at risk" | In-app |
| 7 | Retry payment. Email with urgency. | Automatic + Email |
| 10 | Final email: "Account will be downgraded in 4 days" | Email |
| 14 | Downgrade to free tier (not full cancellation) | Automatic |
| 30 | If still no update: suspend account (preserve data) | Automatic |
| 90 | If still no update: archive account | Automatic |

**Key principles:**
- Never immediately cancel. Always retry and notify first.
- Downgrade to free tier before cancellation (preserves data and relationship)
- Preserve data for at least 90 days (users may come back)
- Make payment update a one-click action from every notification
- Track recovery rate at each step to optimize the sequence

### Category 3: Technical Issues

**Account Access:**
- Forgot password, locked out, SSO configuration changed
- **Tactics:** Magic link recovery, multiple auth methods, account recovery flow, proactive outreach if login attempts fail

**Integration Failures:**
- Connected integrations break, causing product to stop working
- **Tactics:** Integration health monitoring, automatic reconnection, user notification with fix instructions

**Organization Changes:**
- Company switches identity provider, changes domain, restructures
- **Tactics:** Account transfer flows, domain migration support, admin tools for organizational changes

---

## Churn Diagnostics

### Step 1: Measure the Split

Calculate voluntary vs. involuntary churn:
- Involuntary: any cancellation where last payment failed AND no explicit cancellation request
- Voluntary: explicit cancellation, downgrade request, or exit survey completed

**Typical split:** 60-80% voluntary, 20-40% involuntary for SaaS

### Step 2: Exit Survey (for Voluntary)

Implement a cancellation survey. Keep it short (1-2 questions):

**Question 1 (required, single-select):**
"What is the main reason you are cancelling?"
- [ ] Too expensive
- [ ] Missing features I need
- [ ] Too hard to use
- [ ] Found a better alternative
- [ ] No longer need it
- [ ] Not enough time to use it
- [ ] Other (free text)

**Question 2 (optional, free text):**
"Is there anything we could have done to keep you?"

### Step 3: Cohort Churn Analysis

| Dimension | What to Look For |
|-----------|------------------|
| By tenure | When does most churn happen? (Month 1? Month 6? Month 12?) |
| By plan | Do higher plans churn more or less? |
| By segment | Do specific ICP segments churn differently? |
| By channel | Do users from certain acquisition channels churn faster? |
| By activation | Did churned users ever activate? |
| By engagement | What was the engagement trajectory before churn? |

### Step 4: Pre-Churn Signals

Build a model of behaviors that predict churn 14-30 days before it happens:
- Declining login frequency (week over week)
- Declining session depth (fewer actions per session)
- Support ticket followed by silence
- Data export (user may be migrating)
- Removal of integrations
- Team member removal
- Downgrade inquiry

**Use signals to trigger proactive intervention** (human outreach, in-app prompt, value demonstration).

---

## Churn Reduction Priority Matrix

| Lever | Impact | Effort | Timeframe | Priority |
|-------|--------|--------|-----------|----------|
| Dunning optimization | High (recover 20-40% of involuntary) | Low | 1-2 weeks | P1 |
| Pre-expiry card notifications | Medium | Low | 1 week | P1 |
| Exit survey + analysis | Medium (enables targeting) | Low | 1 week | P1 |
| Smart payment retries | Medium | Low-Medium | 2-3 weeks | P1 |
| Pre-churn signal detection | High (enable proactive save) | Medium | 4-6 weeks | P2 |
| Downgrade path (instead of cancel) | Medium | Medium | 2-4 weeks | P2 |
| Feature gap closure | High (if top churn reason) | High | Quarter+ | P2 |
| UX improvement | Medium-High | Medium-High | Quarter+ | P2 |
| Competitive response | Variable | Variable | Quarter+ | P3 |
| Pricing restructure | Variable | Medium | 4-8 weeks | P3 |

**Start with involuntary churn.** It is always the highest ROI because it is technical, not behavioral. Then address the top voluntary churn reason from exit survey data.
