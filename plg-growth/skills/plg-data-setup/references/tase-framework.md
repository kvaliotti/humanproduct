# TASE Framework

The TASE framework organizes PLG data infrastructure into four dimensions: Track, Analyse, Sync, Experiment. Each dimension must be in place for data-driven PLG execution. Gaps in any dimension create blind spots that degrade decision quality.

---

## T: TRACK

What to capture from the product, users, and external sources. Tracking is the foundation -- without clean event data, analysis, sync, and experimentation are impossible.

### Event Categories

#### Identity Events
Events that establish and resolve user identity across the journey.

| Event | Trigger | Required Properties | Purpose |
|-------|---------|-------------------|---------|
| `user_signed_up` | User completes signup | `signup_method`, `referral_source`, `utm_source`, `utm_medium`, `utm_campaign`, `plan_type` | Acquisition attribution |
| `user_logged_in` | User authenticates | `login_method`, `days_since_last_login` | Engagement tracking |
| `user_identified` | Anonymous user links to account | `anonymous_id`, `user_id` | Identity resolution |
| `account_created` | New organization/workspace created | `account_name`, `creator_user_id`, `company_domain` | Account-level tracking |

#### Activation Events
Events that define and measure progress toward activation. These are product-specific -- the exact events depend on what "activated" means for this product.

| Event | Trigger | Required Properties | Purpose |
|-------|---------|-------------------|---------|
| `onboarding_step_completed` | User completes an onboarding step | `step_name`, `step_number`, `total_steps`, `time_spent` | Onboarding funnel |
| `onboarding_completed` | User finishes full onboarding | `total_time`, `steps_skipped` | Onboarding completion rate |
| `activation_action_completed` | User performs the key activation action | `action_name`, `time_since_signup` | Activation rate + TTV |
| `first_value_moment` | User experiences the core value for the first time | `value_type`, `time_since_signup` | Time-to-value |

**Defining activation events:** The activation action is the behavior most correlated with long-term retention. Common examples:
- Slack: sent 2,000 messages as a team
- Dropbox: saved one file in Dropbox folder
- HubSpot: used 5 features within 60 days
- Zoom: hosted first meeting with 3+ participants

To find your activation action: correlate early behaviors (first 7-14 days) with D30/D60 retention. The action with the strongest correlation is your activation metric.

#### Feature Events
Events that track feature discovery and depth of usage.

| Event | Trigger | Required Properties | Purpose |
|-------|---------|-------------------|---------|
| `feature_used` | User interacts with a specific feature | `feature_name`, `feature_category`, `usage_depth` (view/interact/complete), `is_first_use` | Feature adoption + breadth |
| `feature_discovered` | User sees a feature for the first time | `feature_name`, `discovery_method` (organic/prompted/search) | Feature discovery tracking |

**Usage depth levels:**
- `viewed`: User saw the feature (page load, modal open)
- `interacted`: User took an action within the feature (clicked, typed, configured)
- `completed`: User achieved the feature's intended outcome (report generated, project created, message sent)

#### Engagement Events
Session and activity-level events for measuring engagement patterns.

| Event | Trigger | Required Properties | Purpose |
|-------|---------|-------------------|---------|
| `session_started` | User begins a new session | `session_id`, `referral_source`, `platform`, `device_type` | Session analytics |
| `session_ended` | Session timeout or explicit logout | `session_id`, `session_duration`, `pages_viewed`, `actions_taken` | Engagement depth |
| `page_viewed` | User loads a page/screen | `page_name`, `page_category`, `referrer` | Navigation patterns |

#### Payment Events
All monetization-related events. Critical for revenue driver tree analysis.

| Event | Trigger | Required Properties | Purpose |
|-------|---------|-------------------|---------|
| `subscription_created` | User starts a paid subscription | `plan_name`, `plan_price`, `billing_interval`, `trial_used`, `payment_method` | New MRR |
| `plan_upgraded` | User moves to a higher plan | `old_plan`, `new_plan`, `old_price`, `new_price`, `upgrade_trigger` | Expansion MRR |
| `plan_downgraded` | User moves to a lower plan | `old_plan`, `new_plan`, `old_price`, `new_price`, `downgrade_reason` | Contraction MRR |
| `subscription_cancelled` | User cancels subscription | `plan_name`, `cancel_reason`, `tenure_days`, `mrr_lost` | Churned MRR |
| `payment_failed` | Payment attempt fails | `failure_reason`, `plan_name`, `retry_count` | Involuntary churn |
| `payment_recovered` | Failed payment subsequently succeeds | `recovery_method`, `days_to_recover`, `plan_name` | Recovery rate |
| `seat_added` | Additional user added to paid plan | `new_seat_count`, `incremental_mrr` | Seat expansion |
| `addon_purchased` | User buys an add-on | `addon_name`, `addon_price` | Add-on expansion |

#### Account Events
Team and collaboration events for understanding account-level behavior.

| Event | Trigger | Required Properties | Purpose |
|-------|---------|-------------------|---------|
| `user_invited` | Existing user invites a new user | `inviter_user_id`, `invitee_email`, `invite_method`, `role_assigned` | Viral growth + expansion |
| `invite_accepted` | Invited user joins | `inviter_user_id`, `invitee_user_id`, `time_to_accept` | Invite conversion |
| `role_changed` | User's role/permission changes | `old_role`, `new_role`, `changed_by` | Account maturity |
| `team_created` | New team/group within account | `team_name`, `creator_user_id`, `initial_member_count` | Account expansion |
| `integration_added` | External tool connected | `integration_name`, `integration_category` | Stickiness + depth |
| `integration_removed` | External tool disconnected | `integration_name`, `reason` | Churn risk signal |

#### Enrichment Data
External data appended to user/account records for segmentation and scoring.

| Data Type | Source | Properties | Purpose |
|-----------|--------|-----------|---------|
| Firmographic | Clearbit, ZoomInfo, Apollo | `company_size`, `industry`, `revenue_range`, `funding_stage`, `tech_stack` | Segmentation + ICP scoring |
| UTM parameters | URL parsing | `utm_source`, `utm_medium`, `utm_campaign`, `utm_term`, `utm_content` | Channel attribution |
| Referral source | Product / URL | `referrer_url`, `referral_code`, `referral_user_id` | Viral attribution |
| Geographic | IP geolocation | `country`, `region`, `city`, `timezone` | Geo segmentation |

### Properties

#### User Properties (set once, update as they change)
| Property | Type | Example | Purpose |
|----------|------|---------|---------|
| `user_id` | String | "usr_abc123" | Unique identifier |
| `email` | String | "user@company.com" | Communication + identity |
| `role` | String | "admin" / "member" / "viewer" | Segmentation |
| `signup_date` | DateTime | "2026-01-15T10:30:00Z" | Cohort analysis |
| `activation_date` | DateTime | "2026-01-17T14:00:00Z" | Activation timing |
| `plan` | String | "free" / "pro" / "enterprise" | Plan segmentation |
| `last_active` | DateTime | "2026-04-25T09:00:00Z" | Engagement recency |

#### Account Properties (set once, update as they change)
| Property | Type | Example | Purpose |
|----------|------|---------|---------|
| `account_id` | String | "acc_xyz789" | Unique identifier |
| `company_name` | String | "Acme Corp" | Display + CRM sync |
| `company_size` | String | "51-200" | ICP segmentation |
| `industry` | String | "SaaS" | Vertical segmentation |
| `plan` | String | "team_pro" | Account plan |
| `mrr` | Number | 499.00 | Revenue tracking |
| `user_count` | Integer | 12 | Usage + expansion signal |
| `department_count` | Integer | 3 | Account depth |
| `created_date` | DateTime | "2025-11-01T00:00:00Z" | Account tenure |

#### Standard Event Properties (on every event)
| Property | Type | Purpose |
|----------|------|---------|
| `timestamp` | DateTime | When the event occurred |
| `user_id` | String | Who triggered it |
| `account_id` | String | Which account |
| `session_id` | String | Which session |
| `platform` | String | web / ios / android / api |

---

## A: ANALYSE

What dashboards, reports, and analyses to build on top of tracked data.

### Dashboard per AARMS Stage

#### Acquisition Dashboard
| Metric | Definition | Visualization | Cadence |
|--------|-----------|---------------|---------|
| Visitors | Unique visitors to marketing site + product | Line chart, daily/weekly | Daily |
| Signups | New user_signed_up events | Line chart + stacked by channel | Daily |
| Signup rate | Signups / Visitors | Line chart with trend | Weekly |
| CAC | Total acquisition spend / New customers | Bar chart by channel | Monthly |
| Channel attribution | Signups by utm_source/medium | Stacked bar + table | Weekly |

#### Activation Dashboard
| Metric | Definition | Visualization | Cadence |
|--------|-----------|---------------|---------|
| Activation rate | Users reaching activation action / Signups (cohorted) | Line chart by cohort | Weekly |
| Time-to-value (TTV) | Median time from signup to activation_action_completed | Distribution histogram | Weekly |
| Onboarding completion | Users completing onboarding / Signups | Funnel visualization | Weekly |
| Onboarding drop-off | Per-step completion rate | Step funnel with drop-off % | Weekly |
| Setup completion | Users completing key setup steps | Checklist heatmap | Weekly |

#### Retention Dashboard
| Metric | Definition | Visualization | Cadence |
|--------|-----------|---------------|---------|
| D1/D7/D30/D90 retention | % of cohort active on day N | Retention curve by cohort | Weekly |
| Feature adoption heatmap | % of users using each feature | Heatmap (features x cohort) | Monthly |
| Engagement score | Composite: frequency x breadth x depth | Distribution + trend | Weekly |
| Churn rate | Accounts cancelling / Total active accounts | Line chart + decomposition | Monthly |
| Resurrection rate | Churned users returning / Total churned | Line chart | Monthly |

#### Monetisation Dashboard
| Metric | Definition | Visualization | Cadence |
|--------|-----------|---------------|---------|
| Free-to-paid conversion | subscription_created / user_signed_up (cohorted) | Line chart by cohort | Weekly |
| ARPA | Total revenue / Total paying accounts | Line chart + by plan | Monthly |
| Expansion rate | Expansion MRR / Beginning MRR | Bar chart (upgrade + seats + addons) | Monthly |
| Contraction rate | Contraction MRR / Beginning MRR | Bar chart by reason | Monthly |
| LTV | ARPA / Churn rate (simplified) | Trend line | Quarterly |

#### Satisfaction Dashboard
| Metric | Definition | Visualization | Cadence |
|--------|-----------|---------------|---------|
| NPS | Net Promoter Score | Gauge + trend line | Quarterly |
| CSAT | Customer Satisfaction Score | Trend + by touchpoint | Monthly |
| CES | Customer Effort Score | Trend + by flow | Monthly |
| PMF score | % "very disappointed" if product gone | Trend line | Quarterly |

### Revenue Driver Tree Dashboard
One panel per MRR/revenue component with drill-down to sub-drivers:
```
Total MRR
├── New MRR = New customers x ARPA(new)
│   ├── Signups x Activation rate x Conversion rate x ARPA
├── Retained MRR = Retention rate x Existing MRR
├── Expansion MRR = Expansion rate x Existing MRR
│   ├── Seat expansion + Plan upgrades + Add-ons
├── Contraction MRR = Contraction rate x Existing MRR
├── Churned MRR = Churn rate x Existing MRR
│   ├── Voluntary churn + Involuntary churn
└── Reactivation MRR = Reactivation rate x Churned pool x ARPA
```

### Cohort Analysis
- **Weekly/monthly cohorts:** Group users by signup week/month
- **Retention by cohort:** Are newer cohorts retaining better?
- **Revenue by cohort:** Are newer cohorts monetizing faster?
- **Activation by cohort:** Is time-to-value improving?

---

## S: SYNC

How data flows between systems. The goal: every team has the data they need in the tool they use, without manual exports.

### Data Flow Architecture

```
Product (events + properties)
    |
    v
CDP / Event Router
    |
    ├──> Product Analytics
    ├──> CRM
    ├──> Marketing Automation
    ├──> Data Warehouse
    └──> Experimentation Platform
```

### Key Syncs

#### Product -> CRM (for PQA/PQL scoring)
- **What flows:** Account-level aggregated usage data (activation status, feature adoption, engagement score, team size, usage trend)
- **Why:** Sales needs to see which accounts are product-qualified without logging into analytics
- **Frequency:** Near-real-time for PQL triggers, daily for enrichment
- **Transform:** Raw events aggregated into account-level scores and statuses

#### Product -> Marketing (for behavioral triggers)
- **What flows:** User-level events and properties (signup, activation, feature usage, inactivity, upgrade eligibility)
- **Why:** Marketing automation sends the right message at the right time based on product behavior
- **Frequency:** Real-time for triggered messages (e.g., "user invited but invite not accepted after 48h")
- **Transform:** Events translated into trigger conditions and user segments

#### CRM -> Product (for sales context in-app)
- **What flows:** Account owner, deal stage, customer segment, renewal date, support tier
- **Why:** Product experience can adapt based on sales context (e.g., show "contact your account manager" for enterprise, "upgrade" for self-serve)
- **Frequency:** Daily batch or on-change webhook
- **Transform:** CRM fields mapped to product feature flags or display logic

#### Product -> Data Warehouse (for complex analysis)
- **What flows:** All events, all properties, all enrichment data
- **Why:** Analytics tools have limitations on joins, lookback windows, and custom calculations. Warehouse enables anything.
- **Frequency:** Near-real-time (streaming) or hourly batch
- **Transform:** Raw events into denormalized fact and dimension tables

---

## E: EXPERIMENT

Infrastructure and process for running rigorous experiments.

### Infrastructure Components

| Component | Purpose | Tool Examples |
|-----------|---------|--------------|
| Feature flag service | Toggle features on/off for segments | LaunchDarkly, Statsig, Unleash, PostHog |
| Experiment assignment | Randomly assign users to variants | Statsig, Optimizely, GrowthBook |
| Event tracking | Capture behavior in control and treatment | Amplitude, Mixpanel, Segment |
| Statistical analysis | Calculate significance, confidence intervals | Statsig (built-in), Jupyter/R, Eppo |
| Experiment registry | Document all experiments, hypotheses, results | Notion, Confluence, Statsig |

### Process Requirements

| Process | Purpose | Forcing Function |
|---------|---------|-----------------|
| Experiment brief | Ensure proper design before launch | Required document template (blocks launch without it) |
| Peer review | Catch design flaws | Required approval from analyst or PM peer |
| Duration enforcement | Prevent peeking and premature conclusions | Automated lock on results until minimum duration |
| Results documentation | Capture learnings for future experiments | Required template before experiment can be marked "complete" |
| Growth review | Share learnings across team | Weekly meeting with experiment results on agenda |

### Experiment Registry Template

| Field | Description |
|-------|------------|
| Experiment ID | Auto-generated unique ID |
| Name | Descriptive name |
| Owner | PM responsible |
| Hypothesis | Falsifiable statement |
| Primary metric | What we measure |
| Guardrail metrics | What must not degrade |
| Audience | Who is included/excluded |
| Start date | When the experiment launched |
| Planned end date | When to check results |
| Actual end date | When it was concluded |
| Status | Draft / Running / Concluded / Shipped / Killed |
| Result | Won / Lost / Inconclusive |
| Decision | Ship / Revert / Iterate |
| Learnings | What we learned |
| Follow-up | Next experiment or action |
