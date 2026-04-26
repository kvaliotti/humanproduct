# Activation Interviews: 3-Pillar Guide

Qualitative research methodology for identifying the activation moment. Interviews complement quantitative methods (CSI, IV, RF) by revealing WHY certain events predict success.

---

## Target Participants

### Selection Criteria
- **Completed target action within 14 days:** They have activated (or done what you believe is activation)
- **Fits ICP:** Firmographics, role, and use case match your ideal customer
- **Primary decision-maker:** They chose to use the product (not forced by a manager)
- **Recent:** Signed up within the last 30-60 days (memory is fresh)

### Sample Size
- **Minimum:** 15 interviews
- **Ideal:** 20-25 interviews
- **Saturation signal:** When 3 consecutive interviews reveal no new themes, stop

### Recruitment
- In-product prompt: "Help us improve -- 20-min call, get [incentive]"
- Email outreach to users matching criteria
- Incentive: gift card, account credit, or extended trial (match your audience)

---

## Interview Structure

Each interview is 20-30 minutes. Three pillars, roughly equal time.

### Opening (2 minutes)
"Thank you for your time. I am researching how people experience [product] in their first days. There are no right or wrong answers -- I want to understand your personal experience. I will ask about what you were trying to accomplish, your experience with the product, and what matters to you in a tool like this."

---

### Pillar 1: Jobs to Be Done (7-10 minutes)

**Goal:** Understand the user's context, trigger, and desired outcome before they found your product.

#### Core Questions

1. **"What were you trying to accomplish when you first signed up for [product]?"**
   - Listen for: the job, the desired outcome, the success criteria
   - Follow up: "What would success look like for that?"

2. **"What were you using before [product]? Walk me through how that worked."**
   - Listen for: the existing solution, its limitations, the pain
   - Follow up: "What was most frustrating about that approach?"

3. **"What triggered the switch? Was there a specific moment or event?"**
   - Listen for: the trigger event, the tipping point, the catalyst
   - Follow up: "If that [event] had not happened, would you still be using the old approach?"

4. **"Walk me through the moment you decided to try [product]. Where were you? What were you doing?"**
   - Listen for: the context, the search process, the discovery channel
   - Follow up: "How did you find [product] specifically?"

5. **"Who else is involved in this task/workflow? Who benefits from the output?"**
   - Listen for: stakeholders, collaborators, audience for the output
   - Follow up: "Did anyone else influence your decision to try [product]?"

#### What to capture
- The job statement: "When I [situation], I want to [motivation], so I can [expected outcome]"
- The trigger event: what specific thing pushed them to act NOW
- The existing solution: what they hired before and why they fired it

---

### Pillar 2: Aha Moment (7-10 minutes)

**Goal:** Identify the specific moment the user felt the product was valuable. This is the activation event.

#### Core Questions

1. **"When did you first feel the product was valuable? Walk me through that moment."**
   - Listen for: the specific action, the specific outcome, the emotion
   - Follow up: "What happened right before that? What happened right after?"

2. **"What specifically happened that made you think 'this is it'?"**
   - Listen for: the product event, the output, the comparison to old way
   - Follow up: "Can you show me / describe what you saw on screen?"

3. **"Was there a moment you thought 'this is better than what I was doing before'?"**
   - Listen for: the comparison point, the delta, the specific improvement
   - Follow up: "How much better? Can you quantify it?"

4. **"How long after signing up did this moment happen? Hours? Days?"**
   - Listen for: time-to-value estimate
   - Follow up: "What did you do between signing up and that moment?"

5. **"Were there any moments where you almost gave up? What kept you going?"**
   - Listen for: friction points, barriers, what pulled them through
   - Follow up: "What would have happened if [barrier] had been worse?"

#### What to capture
- The aha event: the specific product action/screen/outcome
- The aha emotion: what they felt (relief, excitement, surprise, satisfaction)
- Time-to-aha: approximate hours/days from signup
- Barriers overcome: what almost prevented them from reaching aha

---

### Pillar 3: Decision Criteria (7-10 minutes)

**Goal:** Understand what the user values, what would make them leave, and how they evaluate alternatives.

#### Core Questions

1. **"What would make you stop using [product]?"**
   - Listen for: deal-breakers, must-haves, non-negotiables
   - Follow up: "Has that ever almost happened?"

2. **"What would you compare us to? Not just direct competitors -- anything you might use instead."**
   - Listen for: the competitive set from the user's perspective (may differ from your assumptions)
   - Follow up: "What does [alternative] do better? What do we do better?"

3. **"What matters most to you in a tool like this? If you had to pick three things."**
   - Listen for: prioritized criteria, weighted preferences
   - Follow up: "If you could only pick one, which one?"

4. **"Would you recommend [product] to a colleague? What would you tell them?"**
   - Listen for: the pitch (this IS your positioning from the user's mouth)
   - Follow up: "Who specifically would you recommend it to? Who would you NOT recommend it to?"

5. **"If [product] disappeared tomorrow, what would you do?"**
   - Listen for: switching cost perception, dependency, alternatives
   - Follow up: "How painful would that be on a 1-10 scale?"

#### What to capture
- Decision criteria ranked by importance
- Competitive alternatives (from user perspective)
- The user's pitch (how they describe you to others)
- Switching cost perception

---

### Closing (2 minutes)
"Is there anything else about your experience that I did not ask about but should have?"
- This often surfaces the most important insight
- Thank them, confirm incentive delivery

---

## Analysis Framework

### After All Interviews

**1. Cluster by JTBD**
Group users by the job they hired the product for. Expect 3-5 distinct jobs.
- For each job cluster: what is the common trigger? Common old solution?
- Do different jobs have different aha moments?

**2. Map aha moments to product events**
For each aha moment described, map it to a specific product event in your analytics:
- "I felt it was valuable when I created my first report" → event: `report_created`
- "It clicked when I saw my team's comments" → event: `received_first_comment`
- The most common aha event across interviews is your activation metric hypothesis

**3. Extract decision criteria themes**
Rank criteria by frequency:
- How many users mentioned speed/ease?
- How many mentioned a specific feature?
- How many mentioned price?
- How many mentioned collaboration?

**4. Build the aha timeline**
For each user, plot: signup → [intermediate steps] → aha moment → current state
- What is the median number of steps to aha?
- What is the median time to aha?
- Are there common intermediate steps that always precede aha?

**5. Identify barrier themes**
From "almost gave up" responses:
- What barriers appear repeatedly?
- Map to the 3 barrier categories (Don't Know, Can't, Don't Want)

### Output: Activation Hypothesis

Combine findings into a testable hypothesis:

> "Users who [aha event from interviews] within [time window] are our activated users. The primary barriers are [barriers], and the primary motivation is [JTBD]. This hypothesis should be validated against quantitative CSI analysis."

---

## Interview Logistics

### Scheduling
- Calendly or similar with 25-minute slots
- Offer 3-4 time slots across different time zones
- Send reminder 1 hour before

### Recording
- Always ask permission to record
- Use Zoom/Meet with transcription
- Take notes during AND review transcript after

### Incentives by Audience
- SMB / individual users: $25-50 gift card
- Mid-market: $50-100 gift card or account credit
- Enterprise: often no incentive needed (they want to shape the product)
- Developers: swag, open source credits, or charitable donation

### Common Mistakes to Avoid
- **Leading questions:** "Did you love the dashboard?" → "How did you feel about the dashboard?"
- **Yes/no questions:** "Was it easy?" → "Walk me through the experience."
- **Hypothetical questions:** "Would you use feature X?" → "Tell me about the last time you needed to do X."
- **Not probing:** Accept the first answer. Always ask "Why?" or "Tell me more about that."
- **Selecting only happy users:** Include users who activated but have mixed feelings. Their barriers are most instructive.
