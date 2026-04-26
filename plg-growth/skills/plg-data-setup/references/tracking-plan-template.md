# PLG Tracking Plan Template

A complete tracking plan for product-led growth. Use this as a starting template and customize for your product. Every event exists to support a specific decision or analysis.

---

## Naming Conventions

### Event Names
- **Format:** `snake_case`, `verb_noun` pattern
- **Examples:** `project_created`, `feature_used`, `plan_upgraded`, `user_invited`
- **Anti-patterns:** camelCase (`projectCreated`), spaces (`Project Created`), inconsistent verbs (`create_project` mixed with `project_created`)

### Property Names
- **Format:** `snake_case`, `noun` or `adjective_noun`
- **Examples:** `plan_name`, `user_role`, `session_duration`, `is_first_use`
- **Boolean properties:** prefix with `is_` or `has_` (e.g., `is_activated`, `has_integration`)

### Property Standards

**Required on ALL events (set automatically by SDK):**
| Property | Type | Description |
|----------|------|-------------|
| `timestamp` | DateTime | When the event occurred (ISO 8601) |
| `user_id` | String | Authenticated user identifier |
| `anonymous_id` | String | Pre-authentication identifier |
| `account_id` | String | Organization/workspace identifier |
| `session_id` | String | Current session identifier |
| `platform` | String | `web` / `ios` / `android` / `api` |
| `app_version` | String | Current product version |

---

## Starter Tracking Plan

### Acquisition Events

| Event Name | Category | Trigger | Properties | Destinations | Owner | AARMS Stage |
|-----------|----------|---------|-----------|-------------|-------|-------------|
| `page_viewed` | Acquisition | Marketing site page load | `page_name`, `page_url`, `referrer`, `utm_source`, `utm_medium`, `utm_campaign` | Analytics, Warehouse | Marketing | Acquisition |
| `signup_started` | Acquisition | User clicks signup CTA | `signup_source` (page or button), `referral_code` | Analytics, Warehouse | Growth | Acquisition |
| `user_signed_up` | Acquisition | User completes registration | `signup_method` (email/google/github/sso), `referral_source`, `utm_source`, `utm_medium`, `utm_campaign`, `plan_type` | Analytics, CRM, Marketing, Warehouse | Growth | Acquisition |
| `signup_abandoned` | Acquisition | User starts but does not complete signup (inferred) | `last_step_completed`, `time_on_form` | Analytics, Warehouse | Growth | Acquisition |

### Activation Events

| Event Name | Category | Trigger | Properties | Destinations | Owner | AARMS Stage |
|-----------|----------|---------|-----------|-------------|-------|-------------|
| `onboarding_started` | Activation | User enters onboarding flow | `onboarding_version`, `user_segment` | Analytics, Marketing, Warehouse | Product | Activation |
| `onboarding_step_completed` | Activation | User completes an onboarding step | `step_name`, `step_number`, `total_steps`, `time_on_step`, `skipped` | Analytics, Warehouse | Product | Activation |
| `onboarding_completed` | Activation | User finishes full onboarding | `total_time`, `steps_completed`, `steps_skipped`, `onboarding_version` | Analytics, Marketing, Warehouse | Product | Activation |
| `onboarding_abandoned` | Activation | User exits onboarding before completing (inferred) | `last_step`, `time_in_onboarding` | Analytics, Marketing, Warehouse | Product | Activation |
| `activation_achieved` | Activation | User performs the defined activation action | `activation_action`, `time_since_signup`, `session_count_to_activate` | Analytics, CRM, Marketing, Warehouse | Growth | Activation |
| `setup_step_completed` | Activation | User completes a setup/configuration step | `step_name` (e.g., `profile_completed`, `integration_connected`, `teammate_invited`), `time_since_signup` | Analytics, Warehouse | Product | Activation |

### Feature & Engagement Events

| Event Name | Category | Trigger | Properties | Destinations | Owner | AARMS Stage |
|-----------|----------|---------|-----------|-------------|-------|-------------|
| `feature_used` | Engagement | User interacts with a specific feature | `feature_name`, `feature_category`, `usage_depth` (view/interact/complete), `is_first_use` | Analytics, Warehouse | Product | Retention |
| `session_started` | Engagement | New session begins | `session_id`, `referral_source`, `platform`, `device_type` | Analytics, Warehouse | Product | Retention |
| `session_ended` | Engagement | Session ends (timeout or logout) | `session_id`, `session_duration`, `pages_viewed`, `features_used_count` | Analytics, Warehouse | Product | Retention |
| `search_performed` | Engagement | User searches within product | `query`, `results_count`, `result_clicked` | Analytics, Warehouse | Product | Retention |
| `content_created` | Engagement | User creates primary content | `content_type`, `template_used`, `is_first_creation` | Analytics, Warehouse | Product | Retention |
| `content_shared` | Engagement | User shares content externally | `content_type`, `share_method` (link/email/embed), `recipient_count` | Analytics, Marketing, Warehouse | Growth | Retention |

### Collaboration & Account Events

| Event Name | Category | Trigger | Properties | Destinations | Owner | AARMS Stage |
|-----------|----------|---------|-----------|-------------|-------|-------------|
| `user_invited` | Account | User sends an invite | `invitee_email_domain`, `invite_method` (email/link/bulk), `role_assigned`, `team_name` | Analytics, CRM, Marketing, Warehouse | Growth | Retention |
| `invite_accepted` | Account | Invited user joins | `inviter_user_id`, `time_to_accept`, `invite_method` | Analytics, CRM, Warehouse | Growth | Retention |
| `team_created` | Account | New team/workspace created | `team_name`, `initial_member_count`, `creator_role` | Analytics, CRM, Warehouse | Product | Retention |
| `role_changed` | Account | User role/permission updated | `old_role`, `new_role`, `changed_by` | Analytics, Warehouse | Product | Retention |
| `integration_added` | Account | External tool connected | `integration_name`, `integration_category`, `setup_time` | Analytics, CRM, Warehouse | Product | Retention |
| `integration_removed` | Account | External tool disconnected | `integration_name`, `reason` | Analytics, CRM, Warehouse | Product | Retention |

### Monetisation Events

| Event Name | Category | Trigger | Properties | Destinations | Owner | AARMS Stage |
|-----------|----------|---------|-----------|-------------|-------|-------------|
| `paywall_viewed` | Monetisation | User encounters a paywall or upgrade prompt | `feature_blocked`, `plan_required`, `user_plan`, `trigger_context` | Analytics, Marketing, Warehouse | Growth | Monetisation |
| `pricing_page_viewed` | Monetisation | User views pricing page | `source_page`, `current_plan`, `view_duration` | Analytics, Warehouse | Growth | Monetisation |
| `trial_started` | Monetisation | User begins a free trial | `trial_plan`, `trial_duration_days`, `trigger` | Analytics, CRM, Marketing, Warehouse | Growth | Monetisation |
| `subscription_created` | Monetisation | User starts a paid subscription | `plan_name`, `plan_price`, `billing_interval`, `trial_used`, `payment_method`, `coupon_code` | Analytics, CRM, Marketing, Warehouse | Finance | Monetisation |
| `plan_upgraded` | Monetisation | User moves to higher plan | `old_plan`, `new_plan`, `old_price`, `new_price`, `upgrade_trigger` | Analytics, CRM, Warehouse | Finance | Monetisation |
| `plan_downgraded` | Monetisation | User moves to lower plan | `old_plan`, `new_plan`, `old_price`, `new_price`, `downgrade_reason` | Analytics, CRM, Warehouse | Finance | Monetisation |
| `seat_added` | Monetisation | Additional seat purchased | `new_seat_count`, `incremental_mrr` | Analytics, CRM, Warehouse | Finance | Monetisation |
| `addon_purchased` | Monetisation | Add-on feature purchased | `addon_name`, `addon_price`, `billing_interval` | Analytics, CRM, Warehouse | Finance | Monetisation |
| `subscription_cancelled` | Monetisation | User cancels subscription | `plan_name`, `cancel_reason`, `tenure_days`, `mrr_lost`, `feedback_provided` | Analytics, CRM, Marketing, Warehouse | Finance | Monetisation |
| `payment_failed` | Monetisation | Payment attempt fails | `failure_reason`, `plan_name`, `retry_count`, `is_first_failure` | Analytics, CRM, Marketing, Warehouse | Finance | Monetisation |
| `payment_recovered` | Monetisation | Failed payment recovered | `recovery_method` (retry/card_update/dunning_email), `days_to_recover` | Analytics, CRM, Warehouse | Finance | Monetisation |

### Satisfaction Events

| Event Name | Category | Trigger | Properties | Destinations | Owner | AARMS Stage |
|-----------|----------|---------|-----------|-------------|-------|-------------|
| `nps_survey_responded` | Satisfaction | User submits NPS survey | `score`, `comment`, `survey_trigger`, `user_tenure_days` | Analytics, CRM, Warehouse | Product | Satisfaction |
| `csat_survey_responded` | Satisfaction | User submits CSAT | `score`, `touchpoint`, `comment` | Analytics, CRM, Warehouse | Product | Satisfaction |
| `support_ticket_created` | Satisfaction | User contacts support | `ticket_category`, `priority`, `channel` (chat/email/phone) | Analytics, CRM, Warehouse | Support | Satisfaction |
| `feedback_submitted` | Satisfaction | User submits in-app feedback | `feedback_type` (bug/feature_request/complaint/praise), `feature_context`, `text` | Analytics, Warehouse | Product | Satisfaction |

---

## Implementation Checklist

### Phase 1: Foundation (Week 1-2)
- [ ] Choose and configure CDP / event router (Segment, RudderStack, etc.)
- [ ] Implement SDK in product (web, mobile, backend as needed)
- [ ] Set up identity resolution (`user_identified` event linking anonymous -> authenticated)
- [ ] Configure standard event properties (timestamp, user_id, account_id, session_id, platform)
- [ ] Implement `user_signed_up` event with all properties
- [ ] Validate: fire test events, confirm they arrive in all destinations

### Phase 2: Activation Tracking (Week 2-3)
- [ ] Define activation metric (correlate early behaviors with retention)
- [ ] Implement onboarding events (`onboarding_started`, `onboarding_step_completed`, `onboarding_completed`)
- [ ] Implement `activation_achieved` event
- [ ] Implement `setup_step_completed` events for key setup actions
- [ ] Validate: build activation funnel, confirm data accuracy

### Phase 3: Payment Events (Week 3-4)
- [ ] Implement all payment events (subscription, upgrade, downgrade, cancel, fail, recover)
- [ ] Validate: reconcile event data with billing system (Stripe, etc.)
- [ ] Set up payment event -> CRM sync

### Phase 4: Feature & Engagement (Week 4-5)
- [ ] Implement `feature_used` with feature_name taxonomy
- [ ] Implement session events
- [ ] Implement collaboration events (invite, team, integration)
- [ ] Validate: build feature adoption heatmap, confirm coverage

### Phase 5: Enrichment (Week 5-6)
- [ ] Configure enrichment provider (Clearbit, etc.)
- [ ] Append firmographic data to accounts
- [ ] Validate UTM parameter capture across all acquisition channels
- [ ] Validate referral source tracking

### Phase 6: Dashboards (Week 6-8)
- [ ] Build Acquisition dashboard
- [ ] Build Activation dashboard (funnel + TTV)
- [ ] Build Retention dashboard (cohort curves)
- [ ] Build Monetisation dashboard (conversion + MRR components)
- [ ] Build Revenue Driver Tree dashboard
- [ ] Set up weekly automated reports

### Phase 7: Experimentation (Week 8-10)
- [ ] Configure feature flag service
- [ ] Implement experiment assignment tracking
- [ ] Run first A/B test to validate infrastructure end-to-end
- [ ] Set up experiment registry (documentation template)

---

## Data Quality Checks

Run these checks weekly to catch tracking issues early:

| Check | What to Look For | Action if Failed |
|-------|-----------------|-----------------|
| Event volume anomaly | Sudden drop or spike (>30% change) in any event | Investigate: tracking code broken? Product change? Seasonal? |
| Null property rate | >5% null on required properties | Fix: SDK not capturing property, or backend not passing it |
| Identity resolution rate | >10% events with only anonymous_id | Fix: identify call not firing, or firing too late |
| Event-to-billing reconciliation | >2% discrepancy between event counts and billing system | Fix: payment events misconfigured or missing edge cases |
| Duplicate events | Same event + user + timestamp within 1 second | Fix: SDK firing multiple times, or retry logic creating duplicates |
| Property cardinality | Property with unexpectedly high unique values | Fix: free-text field that should be enum, or PII leaking |
