# Reverse Trial Model — Deep Dive

## Core Concept

A reverse trial gives new users full premium access from day one. After a set period (typically 14-30 days), they are gracefully downgraded to a free tier rather than locked out. Users keep using the product on the free tier but have experienced premium — creating a concrete, felt sense of what they are missing.

The key insight: users feel loss aversion more strongly than aspiration. "You had this and now it's gone" converts better than "imagine if you had this."

---

## How Reverse Trial Differs from Standard Trial

| Dimension | Standard Trial | Reverse Trial |
|---|---|---|
| End of trial | Locked out (must pay) | Downgraded to free tier |
| User experience at end | Frustration / loss of access | Mild friction / reduced capability |
| Conversion psychology | Fear of losing ALL access | Desire to regain PREMIUM access |
| Risk for user | High (lose everything if don't pay) | Low (still have free product) |
| Retention of non-converters | Lost forever (unless re-engaged) | Retained as free users (can convert later) |
| Data/work preservation | At risk | Always preserved |

---

## When to Use Reverse Trial

### Strong Signals for Reverse Trial

1. **Premium features clearly differentiate from free.** Users must FEEL the difference when downgraded.
2. **Free tier is viable standalone.** Users should not feel cheated by the free tier.
3. **Product value grows over time.** Users who stay on free will eventually want premium again.
4. **Low cost to serve free users.** Retaining non-converters must be affordable.
5. **Viral/network dynamics.** Free users contribute to growth (invitations, content, network).

### Weak Signals (Consider Other Models)

1. **No clear free/paid split.** If everything valuable is in one tier, downgrade has no meaningful impact.
2. **Premium value requires long-term use.** If premium features only show value after months, a 14-day trial won't demonstrate them.
3. **High cost to serve.** If free users are expensive (infrastructure), losing converters to free tier is costly.

---

## Flow Design

### Phase 1: Full Access (Day 1 - Day N)

```
Signup → Full Premium Access → Onboarding → Activation → Deep Feature Usage
```

**Design principles:**
- Onboard to ALL features, not just basic ones
- Highlight premium features explicitly ("This is a Premium feature — explore it during your trial")
- Track which premium features each user engages with
- Build workflows that incorporate premium features

**Premium feature tagging:**
Every premium feature should have a subtle, consistent visual indicator:
- Small badge or icon (star, diamond, "PRO")
- Not intrusive during trial, but creates awareness
- When downgraded, user remembers these markers

### Phase 2: Transition Communication (Day N-3 to Day N)

```
"Your premium trial ends in 3 days"
→ Show summary of premium features used
→ Show what will change (specific features they used)
→ Clear upgrade CTA
→ "Or continue on Free — your work is safe"
```

**Communication sequence:**
- Day N-3: "Your premium access ends in 3 days. Here's what you've used: [list]"
- Day N-1: "Tomorrow you'll move to Free. Upgrade to keep: [specific features they used most]"
- Day N: "You're now on Free. [Feature X, Feature Y] are no longer available. Upgrade anytime."
- Day N+3: "Missing [feature they used 10 times during trial]? Upgrade to get it back."
- Day N+7: "Reminder: [feature] is just an upgrade away."

### Phase 3: Graceful Downgrade (Day N+1)

```
Premium → Free Tier (data preserved, some features locked)
```

**Critical design principles:**

1. **NEVER delete or hide user data.** All work created during premium period must be visible.
2. **Lock, don't remove.** Premium features become visible-but-locked, not invisible.
3. **Show what they're missing.** When user encounters a locked feature, show what they had: "You used Advanced Analytics 14 times during your trial. Upgrade to continue."
4. **No degraded experience on free features.** Free features must work EXACTLY as well post-trial as during trial.

**Downgrade experience patterns:**

| Pattern | How It Works | Best For |
|---|---|---|
| **Feature lock** | Premium features show lock icon, click opens upgrade prompt | Feature-differentiated products |
| **Usage limit** | Premium usage limits kick in (e.g., 3 projects instead of unlimited) | Volume-limited products |
| **Read-only premium** | Premium content/reports visible but not editable | Content/analytics products |
| **Graceful degradation** | Premium features still work but with limitations (watermarks, reduced quality) | Creative tools |

### Phase 4: Ongoing Free User (Nurture to Convert)

```
Free usage → Natural upgrade moments → Conversion
```

**Ongoing triggers:**
- User attempts to use a premium feature they used during trial
- Usage approaches free tier limits
- Team grows (collaboration features are premium)
- Periodic "here's what you're missing" emails (monthly, not weekly)
- Product updates that add premium features

---

## Unified Onboarding vs. Split Onboarding

### Unified Onboarding (Recommended)

All users — regardless of eventual tier — go through the SAME onboarding that includes premium features.

**Pros:**
- Simpler to build and maintain
- All users experience the full product
- Premium features are demystified
- Stronger loss aversion when downgraded

**Implementation:**
- Single onboarding flow
- Premium features tagged but fully accessible
- Onboarding steps include premium-feature tasks
- Post-trial, onboarding adapts to show free-tier equivalent

### Split Onboarding (Rarely Recommended)

Different onboarding for trial vs. free users.

**When to consider:**
- Product is extremely complex and premium features confuse basic users
- Free and premium are essentially different products
- Regulatory/compliance requires different flows

**Usually avoid because:** It defeats the purpose of reverse trial (experiencing premium).

---

## Conversion Benchmarks

| Metric | Typical | Best-in-Class |
|---|---|---|
| Trial → Paid (during trial) | 5-10% | 15-25% |
| Trial → Paid (within 30 days of downgrade) | 5-10% | 10-15% |
| Trial → Paid (within 90 days of downgrade) | 3-5% | 5-10% |
| Total conversion (within 90 days) | 13-25% | 30-50% |
| Free-tier retention (30-day post-downgrade) | 40-60% | 60-80% |

**Key insight:** Reverse trial conversion happens in two waves:
1. **During trial** (urgency-driven, like standard trial)
2. **Post-downgrade** (loss-aversion-driven, unique to reverse trial)

The second wave is the bonus. It does not exist in standard trials.

---

## Design Patterns from Successful Products

### Pattern: Airtable
- 14-day pro trial for all signups
- Downgrade to free tier with record limits
- "Your base has X records. Free tier allows Y. Upgrade to keep all."

### Pattern: Notion
- Team trial with full features
- Downgrade to free tier with block limits
- "You've used X blocks. Free allows Y per member."

### Pattern: Miro
- Full-feature trial for team boards
- Downgrade to 3 editable boards
- "You have X boards. Convert to free to keep 3, or upgrade for unlimited."

---

## Reverse Trial Design Checklist

- [ ] Premium features are clearly tagged throughout the product
- [ ] Onboarding includes premium feature discovery
- [ ] Premium feature usage is tracked per user
- [ ] Transition emails are personalized (reference features THEY used)
- [ ] Downgrade preserves ALL user data and work
- [ ] Locked features are visible with clear upgrade path
- [ ] Free tier is genuinely useful (not a punitive downgrade)
- [ ] Post-downgrade nurture sequence is set up
- [ ] Upgrade is 1-click from any locked-feature prompt
- [ ] Analytics distinguish trial-period vs. post-downgrade conversion
