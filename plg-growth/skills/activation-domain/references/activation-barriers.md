# Activation Barriers: Diagnosis and Tactical Playbook

Three categories of barriers that prevent users from reaching the activation moment. Every barrier maps to specific onboarding steps and has specific tactical responses.

---

## Category 1: Don't Know

**Definition:** Users do not understand what to do next, why they should do it, or what the product even does for them.

### Diagnostic Signals
- **High signup-to-nothing rate:** Users sign up and take zero meaningful actions
- **Tooltip/tour skip rate > 50%:** Users dismiss guidance before reading it
- **Help article searches in first session:** Users go to docs before trying the product
- **Repeated navigation to homepage:** Users return to the starting point without progressing
- **Low click-through on onboarding steps:** Users see the checklist but do not engage

### Root Causes
- Misaligned expectations from acquisition (website promised X, product feels like Y)
- Unclear product UI (users do not know where to start)
- No visible path to value (empty state does not guide)
- Too many options on first screen (cognitive overload)
- Jargon or domain-specific language that new users do not understand

### Tactical Playbook

#### Welcome Tour / Product Walkthrough
- Show 3-5 key screens/features in a guided tour
- Each step explains WHAT + WHY (not just where to click)
- Allow skip but track skip rate
- Best practice: trigger on first login, not every login
- Tool examples: Appcues, Pendo, Userflow, custom

#### Contextual Tooltips
- Triggered when user hovers or arrives at a feature for the first time
- One sentence: what this does and why it matters
- Disappears after first interaction (do not nag)
- Progressive: introduce features as user advances, not all at once

#### Video Walkthroughs
- 60-90 second "getting started" video on the dashboard
- Use case-specific videos if personalization data is available
- Embedded in product, not linked to YouTube (reduces drop-off)
- Show the product, not talking heads

#### Onboarding Checklist
- 3-5 items that lead to activation
- Each item is a clear action ("Create your first project," not "Get started")
- Progress indicator (2 of 5 complete)
- Persistent but dismissible
- Reward on completion (confetti, badge, or unlock)

#### Email Drip Education
- Day 0: Welcome + single CTA to do first key action
- Day 1: Tips for the specific use case (if personalization data exists)
- Day 3: "Did you try [feature]?" with quick link
- Day 7: Social proof + success story from similar user
- Day 14: "Need help?" with link to support/community
- Each email has ONE CTA, not five

#### Website-Product Expectation Alignment
- Audit: does the homepage value prop match the first-session experience?
- If the website says "collaboration," the first screen should invite teammates
- If the website says "reports," the first screen should show a sample report
- Misalignment is a root cause, not a product problem -- fix the website OR the first session

---

## Category 2: Can't

**Definition:** Users understand what to do and want to do it, but something blocks them. Friction, complexity, or missing capabilities prevent progress.

### Diagnostic Signals
- **Drop-off at specific steps:** Clear, consistent abandonment at a particular onboarding step
- **Support tickets about "how to":** Users are trying but need help at specific points
- **Long TTV (time-to-value):** Users who eventually activate take days/weeks when it should take hours
- **Repeated attempts:** Users try the same action multiple times (suggests unclear feedback)
- **Integration/setup failures:** Users try to connect tools or import data and fail

### Root Causes
- Too many required setup steps before any value
- Complex configuration that requires technical knowledge
- Missing integrations with user's existing tools
- Poor error handling (users fail but do not know why)
- Mobile experience broken for critical steps
- Browser/device compatibility issues

### Tactical Playbook

#### Remove Non-Essential First-Session Steps
- Audit every required step before activation
- For each step ask: "Can we defer this until AFTER the user gets value?"
- Example: Do not require email verification before first action
- Example: Do not require team invite before solo exploration
- Example: Do not require full profile setup before using core feature
- Goal: minimum viable onboarding to reach aha moment

#### Progressive Disclosure
- Show only what is needed for the current step
- Hide advanced settings behind "Advanced" toggles
- Introduce features as they become relevant, not all at signup
- Settings that have safe defaults should be pre-set, not asked

#### Smart Defaults
- Pre-fill every field you can infer (timezone, language, company from email domain)
- Set reasonable defaults for all settings (users can change later)
- Pre-create a sample project/workspace so the user is not staring at an empty state
- Use industry/role data from onboarding questions to set defaults

#### Templates and Quick Starts
- Offer 3-5 templates matching common use cases
- "Start from template" should be more prominent than "Start from scratch"
- Templates should be populated with sample data (not empty)
- Template selection can BE the first meaningful action

#### Checklists with Inline Action
- Each checklist item links directly to the action (not to a docs page)
- If possible, complete the action inline (without navigation)
- Show estimated time: "This takes about 2 minutes"
- Allow items to be completed in any order

#### Human Touch at Friction Points
- Trigger chat/support when user is stuck at a specific step for > N minutes
- Offer a "book a call" option at high-friction steps (especially for enterprise)
- In-app chat with response time < 5 minutes during onboarding
- Concierge onboarding for high-value accounts (autodetect from email domain)

---

## Category 3: Don't Want

**Definition:** Users understand what to do and technically can do it, but are not motivated enough. The product feels cold, empty, or not worth the effort right now.

### Diagnostic Signals
- **Signup but no action:** Users create an account and never return
- **Low engagement with empty state:** Users see the empty dashboard and leave
- **"I will come back later" behavior:** Users browse features without committing to any action
- **Low onboarding completion despite low friction:** Steps are easy but users do not bother
- **High bounce rate from first-session product screens:** Users see the product and immediately leave

### Root Causes
- Cold start problem: empty product has no visible value
- No immediate win: first action requires too much investment before any payoff
- No social pull: solo experience when the product shines with a team
- Unclear ROI: user does not see how this tool saves time/money/effort
- Low urgency: the problem is real but not painful enough today

### Tactical Playbook

#### Templates and Sample Data
- Pre-populate with realistic sample data relevant to user's use case
- "See what a completed [project/report/dashboard] looks like"
- Make it interactive: user can modify the sample, not just view it
- One-click "Use this as my starting point"

#### Pre-Generated Experiences
- Create a "wow moment" before the user does any work
- Example: upload a URL and instantly generate an analysis
- Example: connect an account and immediately show insights from existing data
- Example: show "Here is what your team's workflow could look like" with pre-built demo

#### Quick Wins
- Design the first action to be completable in < 2 minutes
- First action should produce a visible, satisfying output
- Celebrate completion: animation, congratulations, next step suggestion
- The first win should relate to the user's stated JTBD (from onboarding questions)

#### Demo Content / Sandbox
- Interactive demo environment with pre-loaded data
- User can explore features without risk ("this is demo data -- your real workspace is separate")
- Reduce anxiety of "what if I break something"
- Show the product at its best before asking the user to invest effort

#### Collaborative Invites
- If the product is better with teammates, prompt invitation early
- Frame as value: "Invite a teammate to try this together" not "Invite your team"
- Show what collaboration looks like (preview of shared features)
- Social commitment: people who invite others are more likely to return

#### Urgency and Scarcity (use carefully)
- "Your trial includes X feature for 14 days"
- "Complete setup this week to get [bonus]"
- Do NOT use fake urgency. Real urgency only.

---

## Diagnostic Process

### Step 1: Identify the Primary Barrier

Look at the data to classify which category dominates:

| Data Point | Don't Know | Can't | Don't Want |
|-----------|------------|-------|------------|
| Signup to zero action | High | Low-Medium | High |
| Drop-off at specific step | Low | High | Low |
| Support tickets (how-to) | Medium | High | Low |
| Long TTV | Medium | High | Medium |
| Browse but no commit | Medium | Low | High |
| Empty state bounce | High | Low | High |

### Step 2: Map Barriers to Onboarding Steps

For each onboarding step in the funnel, classify the barrier type:

```
Step 1: Account creation → Usually no barrier (already signed up)
Step 2: Onboarding questions → Can't (too many questions) or Don't Want (feels like work)
Step 3: First action prompt → Don't Know (unclear what to do) or Don't Want (empty state)
Step 4: Configuration/setup → Can't (technical complexity) or Don't Know (unclear why needed)
Step 5: Core feature use → Can't (friction) or Don't Know (feature not obvious)
Step 6: Aha moment → Don't Want (not enough payoff) or Can't (blocked by prior step)
```

### Step 3: Prioritize by Drop-off Volume

Calculate the absolute number of users lost at each step. Fix the step that loses the most users first, regardless of barrier type. A 10% improvement at a step that 10,000 users reach is worth more than a 50% improvement at a step only 500 users reach.

### Step 4: Design Interventions

For each prioritized barrier:
1. Pick 1-2 tactics from the relevant playbook above
2. Hypothesize the expected impact
3. Design an experiment to test
4. Measure against activation rate and TTV

---

## Barrier Resolution Priority Matrix

| Impact on Activation Rate | Effort to Fix | Action |
|--------------------------|---------------|--------|
| High | Low | Do immediately (quick win) |
| High | High | Plan for next sprint/quarter |
| Low | Low | Batch with other small improvements |
| Low | High | Deprioritize or eliminate the step entirely |
