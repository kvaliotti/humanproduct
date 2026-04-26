# General Research Analysis Reference

Synthesized from The Mom Test (Fitzpatrick), Deploy Empathy (Hansen), and Just Enough Research (Hall). Use this reference when the research goal is understanding users, validating problems, or informing decisions — any study where the primary output is insight rather than behavioral diagnosis.

---

## Table of Contents
1. Data Classification (Mom Test)
2. Customer Journey Mapping (Deploy Empathy)
3. Pain and Frequency Matrix (Deploy Empathy)
4. Decision Process Timeline (Deploy Empathy)
5. Affinity Diagramming (Just Enough Research)
6. Cross-Interview Pattern Recognition
7. Earlyvangelist Identification (Mom Test)
8. Commitment Quality Assessment (Mom Test)
9. Output Models
10. Anti-Patterns

---

## 1. Data Classification (Mom Test)

The first pass through any data: separate signal from noise.

### Good Data (keep and act on)

| Type | Definition | Example |
|------|-----------|---------|
| **Facts** | Concrete, specific things about what they do and why | "We spend £120k/year on agency fees for this" / "Last time this happened was Tuesday — I spent 3 hours fixing it" |
| **Commitments** | Something they gave up of value (time, reputation, money) | Agreed to intro you to their boss / Pre-ordered / Set up a trial with their team |
| **Advancement** | Moved to the next step in your real-world funnel | Scheduled demo with decision-maker / Signed letter of intent |

### Bad Data (discard or flag)

| Type | How to spot it | Example |
|------|---------------|---------|
| **Compliments** | Positive-sounding statements with no commitment | "That's cool, I love it" / "Sounds great, keep me in the loop" |
| **Fluff** | Generic claims, future promises, hypothetical maybes | "I would definitely buy that" / "I usually deal with it by…" |
| **Unanchored ideas** | Feature requests without understood motivation | "You should add Excel sync" (without knowing why) |

**Key test:** Did the person give up anything of value (time, reputation, money), or did they just say something nice? If they only said nice things, you have no data.

### Ambiguous Data (needs follow-up)

| Signal | What to do |
|--------|-----------|
| Strong emotion without context | Flag — dig into why in next conversation |
| Feature request you didn't explore | Go back and ask "Why?" or find another person in the same segment |
| Lukewarm response | Treat as reliable negative. Don't "up your game" to convince them |

---

## 2. Customer Journey Mapping (Deploy Empathy)

### Step 1: Extract the Process

From each transcript, pull out every step the person described. Diagram as sequential flow — include branches and loops.

For each step, capture:

| Step | Functional | Emotional | Social | Tools Used | Time | Money | Frequency |
|------|-----------|-----------|--------|-----------|------|-------|-----------|
| [action] | [literal task, data, manual steps] | [hopes, frustrations, relief] | [other people involved] | [tools/software] | [duration] | [cost] | [how often] |

### Step 2: Answer the 7 Core Questions

For each interview, extract answers to:

1. **What are they trying to do overall?** — The goal behind the goal. Not "upload files" but "build a job listing platform where companies can upload logos."
2. **What are all the steps?** — The full process map.
3. **Where are they now?** — Current state in the process.
4. **Where does your product fit?** — Which step(s) does it replace or improve?
5. **Where do they spend a lot of time or money?** — Pain signals.
6. **How often do they experience this?** — Frequency determines billing model and willingness to pay.
7. **What have they already tried?** — Previous solutions, including manual/homemade ones. This tells you your real competitive alternatives.

### Step 3: Map the Three Dimensions

For each significant step, identify:

| Dimension | What to look for | Example quotes |
|-----------|-----------------|----------------|
| **Functional** | The literal task, tools, data, time, money, manual steps | "I have to enter it all myself because I can only get a PDF printout" |
| **Emotional** | Hopes, frustrations, uncertainties, relief, elation | "I was at my wits' end" / "Free always comes with caveats" |
| **Social** | Other people involved — team, managers, legal, external vendors | "A friend said, 'Hey, why don't you just try this thing?'" / "I had to chase down someone in another department" |

**Key insight:** The same goal can have entirely different processes depending on context. A person might use a pod machine during a rushed weekday morning (emotional: stressed; social: alone; functional: speed) and a pour-over on weekends with guests (emotional: relaxed; social: entertaining; functional: quality). Context determines everything.

---

## 3. Pain and Frequency Matrix (Deploy Empathy)

### The Framework

```
         HIGH PAIN
            |
   [Gold]   |   [Prime Target]
   Low freq |   High freq
   High pain|   High pain
            |
  ----------+----------
            |
   [Ignore] |   [Painkiller]
   Low freq |   High freq
   Low pain |   Low pain
            |
         LOW PAIN
  LOW FREQ         HIGH FREQ
```

### Pain Indicators

- Time consumed (minutes? hours? days? weeks?)
- Money spent (on tools, manual labor, error consequences)
- Number of steps involved
- Number of people involved
- Cost of getting it wrong
- Manual/homemade solutions (spreadsheets, copy-paste, paper)
- Multiple tools stitched together
- Emotional language ("frustrating," "at my wits' end," "Band-Aids")

### Frequency Indicators

- How often does this happen? (Daily? Weekly? Monthly? Annually? Once?)
- One-time setup or recurring task?
- Does the underlying need recur even if setup is one-time?

### Quadrant Implications

| Quadrant | Implication | Example |
|----------|------------|---------|
| **High pain + High frequency** | Highest willingness to pay. Prime product opportunity. | Weekly podcast transcription — manual = 1.5 hrs/episode |
| **High pain + Low frequency** | Can still command high prices due to stakes. | Buying a house — rare but extremely expensive to get wrong |
| **Low pain + High frequency** | "Painkiller" products. Smaller individual value but high volume. | Scheduling a meeting — annoying, not agonizing |
| **Low pain + Low frequency** | Not worth building for. | — |

### Pricing Signals from Pain/Frequency

Extract for each problem:
1. What they currently pay (money) for tools at each step
2. What they currently pay (time) for each step
3. How often they pay that (frequency → billing model)
4. What happens if they don't solve it (stakes → price ceiling)

**Don't ask "What would you pay?"** Add up what they already pay in time and money across the steps your product would replace. That's the floor for willingness to pay.

**Billing model follows frequency:**
- Annual task → annual billing
- Daily task → monthly subscription or usage-based
- One-time task → one-time purchase (but explore whether underlying need recurs)

---

## 4. Decision Process Timeline (Deploy Empathy)

Use for switch interviews — mapping how customers moved from status quo to a new solution.

| Stage | What to extract | Example |
|-------|----------------|---------|
| 1. Status quo | What they were using; why it was "good enough" | "We were using Firebase Storage because it was right next to Firestore" |
| 2. First thought | When they first realized it might not work | "We started the migration and things just didn't work" |
| 3. Passive looking | Heard about alternatives but didn't act | "I first heard about it but our current solution worked" |
| 4. Active looking | Decided to find something new | "Almost immediately I wanted to use something else" |
| 5. Deciding | Evaluated options, involved others | "I mentioned it to everyone... I was like, 'I'm going to give this a try'" |
| 6. Consuming | First use experience | "I think I had it working in five minutes... I was elated" |
| 7. Satisfaction | Whether it delivered on the hope | "It's up and working. And it's beautiful." |

### Four Forces

- **Push:** What pushed them away from the old solution? (External pressure)
- **Pull:** What attracted them to the new solution? (Internal desire)
- **Anxiety:** What made them hesitant to switch? (Fear of the new)
- **Inertia:** What kept them with the old solution? (Comfort of the known)

---

## 5. Affinity Diagramming (Just Enough Research)

### The Process

1. **Extract observations** — write down anything interesting as individual data points
   - Direct quotes (verbatim language)
   - Objective descriptions of what the user did or said
   - Stated or implicit goals
   - Vocabulary, especially where it differs from internal language
   - Unanticipated needs

2. **Code each observation** to its source participant (traceability)

3. **Group observations** — place on a conceptual whiteboard, start grouping. Patterns emerge quickly.

4. **Name each pattern** and identify the user need it represents
   - Example cluster → pattern "Needs reminders for organized activities":
     - "I see signs around town for events that look interesting, but I never remember before it's too late."
     - "The week rushes by and then I wake up on Saturday morning with no good ideas."

5. **Rearrange and refine** — move observations between groups, merge or split. Iterate until the best groupings emerge.
   - Group by: user type, task type, importance for product success
   - Best groupings are based on emergent patterns, not pre-imposed categories

6. **Extract design mandates** — from each pattern group, identify the actionable principle
   - Example: "When announcing a new exhibit, offer the ability to sign up for a reminder"
   - Example: "Allow members digital access to all services"

### What to Look For in the Data

| Data Type | Definition | Example |
|-----------|-----------|---------|
| **Goals** | What participants want to accomplish | "I want my kids to keep learning outside school" |
| **Priorities** | What matters most | Safety > cost > convenience |
| **Tasks** | Actions toward goals | Searching online for weekend activities |
| **Motivators** | Situations/events that trigger tasks | Seeing a banner ad on the drive home |
| **Barriers** | Things preventing goal achievement | Forgetting about events by the weekend |
| **Habits** | Regular behaviors | Checking Facebook over morning coffee |
| **Relationships** | People involved | Partner who co-decides weekend plans |
| **Tools** | Objects used | iPhone, shared family laptop |
| **Environment** | Context affecting desire/ability | Interrupted by children, limited quiet time |

---

## 6. Cross-Interview Pattern Recognition

### Convergence Signals
- Same steps described by multiple people
- Same tools mentioned repeatedly
- Same frustrations in the same language
- Same discovery channels

### Divergence Signals (not a bad thing)
- Wildly different processes → scope too broad → narrow and do another round of 5
- Different terminology for the same thing → language opportunity
- Different contexts for the same goal → potential for multiple segments or pricing tiers

### Pattern Recognition Matrix

| Signal | Person A | Person B | Person C | Person D | Pattern? |
|--------|----------|----------|----------|----------|----------|
| Problem X exists | ✓ | ✓ | ✗ | ✓ | Strong (3/4) |
| Problem X is top 3 priority | ✓ | ✗ | — | ✓ | Moderate (2/3) |
| Currently paying to solve | ✓ | ✗ | — | ✗ | Weak (1/3) |
| Actively searched for solutions | ✓ | ✓ | — | ✗ | Moderate (2/3) |
| Would make intro/commit time | ✓ | ✗ | — | ✓ | Moderate (2/3) |

### What Consistency Tells You

- **Consistent problem + workaround + willingness to pay:** Push for commitments.
- **Consistent problem + no one paying/searching:** Vitamins, not painkillers.
- **Inconsistent everything:** Segment too broad. Slice further.
- **Consistent rejection/apathy:** Problem isn't real or wrong people. Pivot.

### Feature Request Handling

When a customer requests a feature, extract:
- The scenario where they'd use it
- The last time they needed to do [that thing]
- What they currently use for it
- How much they pay / how long it takes
- How often they need it

Filter through: Is this **valuable** (for them), **usable** (by them), **viable** (for our business), **feasible** (for us to build)?

---

## 7. Earlyvangelist Identification (Mom Test)

Look for people who show all four signs:

1. They **have** the problem
2. They **know** they have the problem
3. They have the **budget** to solve it
4. They've already **cobbled together** their own makeshift solution

These people will commit before it's rational. They're your first customers. Flag them, keep them close, prioritize their needs.

**Emotional intensity is the signal.** There's a significant difference between "Yeah, that's a problem" and "THAT IS THE WORST PART OF MY LIFE AND I WILL PAY YOU RIGHT NOW TO FIX IT."

---

## 8. Commitment Quality Assessment (Mom Test)

Rank every positive signal:

| Level | Signal | Reliability |
|-------|--------|-------------|
| **0 — Nothing** | Compliment ("Love it!") | Worthless |
| **1 — Words** | "I would definitely buy that" | Unreliable — future promise |
| **2 — Time** | Agreed to next meeting, sat for wireframe feedback | Low-moderate |
| **3 — Reputation** | Intro to boss, intro to peers, public endorsement | Moderate-high |
| **4 — Money** | Letter of intent, pre-order, deposit | High |
| **5 — Combined** | Paid trial with their whole team | Very high |

**Rule:** The more they give up, the more seriously you can take their words. If nobody has given up anything of value, you have zero validated customers — regardless of how many said they loved it.

---

## 9. Output Models

Choose based on project needs and data richness:

| Model | When to use | Source |
|-------|------------|--------|
| **Process diagram** | Understanding end-to-end flow; identifying where product fits | Deploy Empathy |
| **Pain/frequency matrix** | Prioritizing problems; pricing signals | Deploy Empathy |
| **Decision timeline** | Understanding switching behavior; acquisition insights | Deploy Empathy |
| **Quote bank by theme** | Marketing copy, landing pages, testimonials, internal alignment | All three |
| **Steps × dimensions table** | Detailed comparison across interviews | Deploy Empathy |
| **Journey map with F/S/E layers** | Comprehensive view for team alignment | Deploy Empathy |
| **Affinity diagram** | Distilling patterns from many data points; collaborative team analysis | Just Enough Research |
| **Personas** | Fictional archetypes from data patterns; design targets | Just Enough Research |
| **Mental models** | How users think something works; gap analysis | Just Enough Research |
| **Task analysis / workflow** | Breaking tasks into discrete steps; identifying interruption/resume points | Just Enough Research |
| **Scenarios** | Stories of persona interaction from user's perspective | Just Enough Research |
| **Pattern recognition matrix** | Assessing signal strength across participants | Mom Test |
| **Belief update table** | Tracking how hypotheses changed | Mom Test |

### Persona Components (if building personas)

| Element | Source |
|---------|--------|
| Photo | Real, relatable person (Creative Commons) — not stock |
| Name | Fits demographics, easy to remember |
| Demographics | From actual interviewees — realistic without stereotyping |
| Role | Matches an actual interviewee who is a target user type |
| Quote | Actual quote from interviews embodying core belief |
| Goals | 3-4 key goals from research |
| Behaviors & habits | Specific, habitual patterns |
| Skills | Technical expertise — don't assume |
| Environment | Hardware, software, internet, context of use |
| Relationships | People who influence their product interaction |

**Persona count:** As few as possible while representing all relevant behavior patterns.

**Validation test:** "Does this address Dana's concerns about privacy?" — when you ask these instead of "Does this make my boss happy?", personas are working.

### Handling Outliers

An outlier = a participant whose behaviors and attributes would rule them out as a target user, despite passing the screener.

- Note the outlier and circumstances for future recruiting improvement
- Set data aside — don't accommodate their needs just because you talked to them

---

## 10. Anti-Patterns in General Research Analysis

| Anti-Pattern | What it looks like | Fix |
|-------------|-------------------|-----|
| **Acting on one interview** | Strategic conclusions from a single participant | Wait for 5. Exception: typos and broken links. |
| **Confusing requests with decisions** | Feature requests treated as product decisions | Customers know what's valuable and usable. Only you know what's viable and feasible. |
| **Over-indexing on negatives** | Cancellation feedback feels more urgent than it is | Loss aversion bias. Balance with happy customer insights. |
| **Skipping emotional/social dimensions** | Only functional analysis | Missing why people actually switch (or don't). Emotional pull and social proof often more decisive than feature comparison. |
| **Asking "What should we build?"** | Expecting data to hand you a solution | Data tells you the problem and severity. The solution is your job. |
| **Not sharing with the team** | Insights stay in one person's head | Insights that stay in one head don't change decisions. Share transcripts, quotes, themes broadly. |
| **All compliments, no commitments** | Pitched instead of asked | Redo with Mom Test questions. |
| **"Everyone loves it" but no commitment** | Zombie leads | Words without sacrifice are worthless. Push for time, reputation, or money. |
| **20 conversations, 20 different problems** | Segment too broad | Slice before more conversations. |
| **Unexpected answers changed nothing** | Ignoring disconfirming data | If data contradicts beliefs and nothing changes, you're not doing research — you're seeking validation. |

---

## Team Analysis Process (Stripe Model)

If the user has a team, recommend this structured review:

1. **Pull together** everyone's notes from interviews
2. **Hold a review session** — everyone reads transcripts and notes
3. **Extract themes** with specific quotes. No actions yet — just themes.
4. **Sit on the themes** — give time to think (don't rush to solutions)
5. **Schedule a second session** — brainstorm actions and recommendations
6. **Share** themes and proposed actions with leadership

**Key principle (Hall):** "People who have a hand in collecting insights will look for opportunities to apply them." Include engineering, design, product, marketing in analysis — not just researchers.

---

## Warning Signs in Your Data

| Warning sign | What it means |
|-------------|---------------|
| All notes are compliments | Pitched instead of asked. Redo with Mom Test questions. |
| Everyone "loves it" but no commitments | Zombie leads, not customers |
| 20 conversations, 20 different problems | Segment too broad. Slice first. |
| Unexpected answers but nothing changed | Ignoring data that contradicts beliefs |
| No notes | Can't analyze what you didn't capture. Start over. |
| Haven't reviewed with team | Creating a learning bottleneck |
| "The meeting went well" without specifics | Counting compliments as data |

---

## Rules of Thumb

- "There's more reliable information in a 'meh' than a 'Wow!'" — Mom Test
- "Compliments are the fool's gold of customer learning: shiny, distracting, and entirely worthless." — Mom Test
- "The world's most deadly fluff is: 'I would definitely buy that.'" — Mom Test
- "Allow sufficient time for analysis. After doing the research, it's tempting to just forge ahead to solutions." — Hall
- "The act of creating an affinity diagram will allow you to distill the patterns and useful insights from the many individual quotes and data points." — Hall
- "Keep having conversations until you stop hearing new stuff." — Mom Test
- Cardinal rule: Never make business decisions after a single interview. Wait for 5 minimum. — Hansen
