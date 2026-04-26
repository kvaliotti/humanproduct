# Behavioral Experiment Ideation (B=MAT Framework)

Use BJ Fogg's Behavior Model to systematically generate experiment ideas. The core principle: **Behavior = Motivation x Ability x Trigger.** All three must be present for the behavior to occur. If you do not know which component is the bottleneck, you are guessing. B=MAT turns experiment ideation from brainstorming into diagnosis.

---

## Step 1: Define the Target Behavior Precisely

Vague behaviors produce vague experiments. Be surgical.

**Format:**
> "User completes [specific action] within [timeframe] of [trigger event]."

**Good examples:**
- "User creates their first project within 3 days of signup"
- "Free user invites a second team member within 7 days of activation"
- "Trial user connects at least one integration within the first session"
- "Monthly active user upgrades to paid within 14 days of hitting the usage limit"

**Bad examples:**
- "Users engage more" (not specific)
- "Improve retention" (not a behavior -- it is an outcome of many behaviors)
- "Users like the product" (not observable)

### Behavior-Metric Connection
Map the target behavior to a metric and a revenue tree branch:

| Target Behavior | Metric | Revenue Tree Branch |
|----------------|--------|-------------------|
| Complete signup | Signup completion rate | New MRR > Signups |
| Reach activation | Activation rate | New MRR > Activation |
| Return on day 7 | D7 retention | Retained MRR > Retention rate |
| Invite a teammate | Invite rate | Expansion MRR > Seats |
| Upgrade to paid | Free-to-paid conversion | New MRR > Conversion rate |
| Add a second use case | Feature breadth | Retained MRR > Engagement depth |

---

## Step 2: Diagnose the Bottleneck

For the target behavior, systematically check each B=MAT component. Use data first, then qualitative evidence, then informed judgment.

### MOTIVATION Check

**Question:** Do users WANT to do this?

**Diagnostic signals of LOW motivation:**

| Signal | Data Source | What It Tells You |
|--------|-----------|------------------|
| Users start the action but abandon midway | Funnel analytics | They tried but decided it was not worth it |
| Users skip optional steps consistently | Product analytics | The perceived value is not high enough to invest effort |
| Low return rate after first session | Retention data | The first experience did not create enough pull to come back |
| Users complete onboarding but never do the key action | Activation funnel | They understand HOW but do not see WHY |
| Survey responses: "I don't see the value" | User research | Direct motivation signal |
| High signup rate but low activation | Funnel comparison | Interest exists (signed up) but value is unclear (did not activate) |

**Experiment playbook for MOTIVATION bottleneck:**

1. **Show value preview before effort**
   - Experiment: Show a "here's what you'll get" preview before asking users to complete setup
   - Hypothesis: "Showing the end-state reduces perceived risk of investing time"
   - Example: Canva shows template gallery before asking you to create; Notion shows use-case demos

2. **Add social proof at the decision point**
   - Experiment: Show "X teams completed this step" or testimonials from similar users at the moment of hesitation
   - Hypothesis: "Social proof reduces uncertainty about whether this action is worth it"
   - Example: "87% of teams like yours complete this step in under 5 minutes"

3. **Gamification / progress indicators**
   - Experiment: Add a progress bar, checklist, or achievement system to the target behavior
   - Hypothesis: "Progress visibility creates completion motivation through the endowed progress effect"
   - Example: LinkedIn profile completeness bar; Duolingo streaks

4. **Loss aversion framing**
   - Experiment: Frame the CTA in terms of what the user loses by NOT acting
   - Hypothesis: "Loss framing is 2x more motivating than gain framing (Kahneman & Tversky)"
   - Example: "Your trial expires in 3 days -- save your work" vs "Upgrade to keep building"

5. **Personalized outcomes**
   - Experiment: Show the user what THEY specifically will get, based on their profile or usage
   - Hypothesis: "Personalized value propositions are more motivating than generic ones"
   - Example: "Based on your usage, upgrading would save your team 12 hours/week"

6. **Reduce perceived commitment**
   - Experiment: Make the action feel reversible or low-stakes
   - Hypothesis: "Reducing perceived risk increases willingness to try"
   - Example: "Try it free -- cancel anytime" vs "Subscribe now"

---

### ABILITY Check

**Question:** Can users do this EASILY?

**Diagnostic signals of LOW ability:**

| Signal | Data Source | What It Tells You |
|--------|-----------|------------------|
| Support tickets about how to do the action | Support data | Users want to but cannot figure out how |
| Drop-off at a specific step in the flow | Funnel analytics | That step is too hard or confusing |
| Long time-to-complete vs expected | Session analytics | Friction is slowing users down |
| High usage of help docs/tooltips at that point | Help analytics | Users are looking for guidance |
| Completion rate varies by user sophistication | Segment analysis | Less technical users struggle -- it is an ability issue |
| Users ask others for help (support, colleagues) | Support + session data | The task exceeds individual capability |

**Experiment playbook for ABILITY bottleneck:**

1. **Reduce steps**
   - Experiment: Remove steps that are not essential for reaching the target behavior
   - Hypothesis: "Every step removed increases completion by 5-15% (Fogg's simplicity factors)"
   - Example: Remove email verification before first use; skip optional profile fields

2. **Add templates / defaults**
   - Experiment: Pre-populate with smart defaults instead of requiring blank-slate creation
   - Hypothesis: "Starting from something is easier than starting from nothing"
   - Example: Notion templates; Airtable pre-built bases; Figma starter files

3. **Simplify the UI**
   - Experiment: Reduce cognitive load at the friction point (fewer options, clearer hierarchy, progressive disclosure)
   - Hypothesis: "Decision complexity is blocking action -- reducing choices enables completion"
   - Example: Hide advanced settings behind "Advanced" toggle; reduce pricing tiers from 5 to 3

4. **Add a wizard / guided flow**
   - Experiment: Replace an open-ended interface with a step-by-step wizard
   - Hypothesis: "Guided sequences reduce the cognitive cost of figuring out what to do next"
   - Example: Mailchimp campaign builder; HubSpot setup wizard

5. **Progressive disclosure**
   - Experiment: Show only what the user needs NOW, reveal complexity as they advance
   - Hypothesis: "Showing everything at once overwhelms; staged revelation matches user readiness"
   - Example: Show 3 features on day 1, reveal more as usage grows

6. **Inline help and contextual guidance**
   - Experiment: Add tooltips, inline hints, or contextual help at the exact friction point
   - Hypothesis: "Just-in-time guidance removes ability barriers without requiring users to search for help"
   - Example: Empty states with instructions; placeholder text showing expected format

7. **Reduce technical requirements**
   - Experiment: Offer a no-code or low-code alternative to a technical setup step
   - Hypothesis: "Technical complexity gates out users who would otherwise activate"
   - Example: One-click integration vs API key entry; CSV import vs API connection

---

### TRIGGER Check

**Question:** Are users PROMPTED at the right time?

**Diagnostic signals of MISSING triggers:**

| Signal | Data Source | What It Tells You |
|--------|-----------|------------------|
| Capable users who never start the action | Segment analysis | They can do it but are not prompted |
| Sporadic usage pattern (no rhythm) | Session analytics | No habitual trigger is formed |
| Users active in one area but unaware of the target feature | Feature adoption data | They need a nudge toward discovery |
| High re-engagement after manual outreach | Support/CS data | Users respond when prompted -- they just need the prompt |
| Users complete the action when shown by CS but not on their own | CS interaction data | The behavior is achievable; it just lacks initiation |

**Experiment playbook for TRIGGER bottleneck:**

1. **In-app notifications / nudges**
   - Experiment: Show a contextual prompt when the user is in the right state to act
   - Hypothesis: "A well-timed prompt converts latent ability and motivation into action"
   - Example: "You've created 3 projects -- invite a teammate to collaborate on them" (shown after 3rd project)

2. **Email / push notification sequences**
   - Experiment: Send a behavioral email triggered by (or lack of) specific product actions
   - Hypothesis: "Out-of-product reminders bring back users who forgot, not users who rejected"
   - Example: Day 2 email: "Your project is waiting -- here's what to do next" (sent to users who signed up but did not activate)

3. **Contextual prompts based on usage patterns**
   - Experiment: Trigger prompts based on what the user just did, not on a fixed schedule
   - Hypothesis: "Context-aware triggers feel helpful; time-based triggers feel spammy"
   - Example: After exporting a report manually: "Automate this with scheduled exports"

4. **Team activity feeds / social triggers**
   - Experiment: Show what teammates are doing to create social triggers
   - Hypothesis: "Seeing teammate activity creates FOMO and mimetic desire"
   - Example: "Sarah shared a new dashboard" notification

5. **Calendar / scheduling integration**
   - Experiment: Tie product actions to calendar events
   - Hypothesis: "Calendar-based triggers create reliable habit loops"
   - Example: "Your weekly review is tomorrow -- here's your dashboard summary"

6. **Habit-forming trigger design**
   - Experiment: Create a recurring trigger tied to an existing user habit
   - Hypothesis: "Piggybacking on existing habits has higher trigger success than creating new ones"
   - Example: Monday morning Slack summary; end-of-day digest email

---

## Step 3: Design Experiment Addressing the Specific Bottleneck

For each bottleneck identified, pick the 1-2 most promising experiments from the playbook above. For each:

### Experiment Card

```
TARGET BEHAVIOR: [precise behavior statement]
BOTTLENECK: [Motivation / Ability / Trigger]
EVIDENCE: [What data/observations identified this bottleneck]

EXPERIMENT: [Name]
HYPOTHESIS: "We believe that [change] will cause [effect] for [audience] because [B=MAT rationale]."
CHANGE: [Specific change description]
PRIMARY METRIC: [Metric + current baseline]
EXPECTED LIFT: [X% based on rationale]
CONFIDENCE: [High/Medium/Low + why]
EFFORT: [S/M/L]
REVENUE TREE CONNECTION: [Which branch and sub-driver]
```

---

## Step 4: Predict Interaction Effects

B=MAT components interact. Fixing one bottleneck may reveal another.

### Common Interaction Patterns

| If You Fix... | You May Discover... | What to Do |
|--------------|-------------------|------------|
| Ability (made it easier) | Motivation was also low (users CAN but still don't) | Run motivation experiment next |
| Trigger (added prompts) | Ability is too low (users get prompted but struggle) | The trigger creates frustration, not action -- fix ability first |
| Motivation (showed value) | Ability blocks them from realizing value | Motivation experiments fall flat if users cannot act on desire |
| Trigger + Motivation | Overload -- too many nudges + too much persuasion feels manipulative | Balance: prompt, don't push |

### Recommended Sequencing

**Default order:** Ability > Trigger > Motivation

1. **Ability first:** Remove friction. This has the highest ROI and lowest risk. Users who already want to act will immediately benefit.
2. **Trigger second:** Once the path is easy, make sure users are prompted. This unlocks users who are willing and able but forgetful.
3. **Motivation last:** Motivation is hardest to influence and most variable across segments. Only invest here after ability and trigger are optimized.

**Exception:** If data clearly shows motivation is the bottleneck (users can do it, are prompted, but choose not to), address motivation directly.

---

## Key Principle

> **If you do not know the bottleneck, you are guessing. B=MAT turns experiment ideation from brainstorming into diagnosis.**

The worst thing a PM can do is brainstorm "cool experiment ideas" without diagnosing the bottleneck. You end up testing triggers when ability is the problem, or testing motivation when users are not even prompted. B=MAT ensures every experiment addresses the actual constraint.
