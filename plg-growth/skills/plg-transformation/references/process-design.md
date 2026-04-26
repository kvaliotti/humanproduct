# Freedom Within Frame: Process Design for PLG

Product processes are not manufacturing processes. Manufacturing standardizes for consistency. Product processes raise decision quality through transparency and shared context. The frame provides guardrails; freedom within the frame enables creativity and speed.

---

## Core Principle

> **The goal of a PLG process is not to standardize behavior. It is to raise the quality of decisions by making relevant information visible at the right moment.**

A good process makes the right thing easy and the wrong thing hard -- without slowing the team down.

---

## Know-Can-Want-Do Framework

For any process to be adopted, four conditions must be met. If any condition fails, the process will not stick. Diagnose which condition is failing before adding more process.

### KNOW: Do People Know the Process Exists and How It Works?

**Problem signs:**
- People say "I didn't know we had a process for this"
- New hires skip the process because nobody told them
- Process exists in a wiki page nobody reads

**Tactics:**

| Tactic | When to Use | Effort | Effectiveness |
|--------|-----------|--------|--------------|
| Periodic enablement sessions | Every quarter, not just once | Low | Medium -- refreshes awareness |
| Written playbook in team wiki | Always | Low | Low alone -- nobody reads wikis proactively |
| Process visible in tooling | When the process has a tool (e.g., experiment brief in Notion template) | Medium | High -- process surfaces where work happens |
| New hire onboarding step | Always | Low | High for new hires, does nothing for existing team |
| Process champion | For complex or new processes | Low-Medium | High -- human reminder and coach |

**Key insight:** One-time training does not work. Knowledge decays. Use periodic reminders and embed the process in the tools where work happens.

### CAN: Is the Process Simple Enough to Follow?

**Problem signs:**
- People know the process but say "it takes too long"
- People skip steps they consider unnecessary
- Process requires tools people don't have access to
- Process has more than 5 steps

**Tactics:**

| Tactic | When to Use | Effort | Effectiveness |
|--------|-----------|--------|--------------|
| Reduce steps | Always start here | Low | Very High -- every step removed doubles compliance |
| Automate steps | When a step is mechanical (e.g., sending notifications, creating tickets) | Medium-High | Very High -- removes friction entirely |
| Pre-fill templates | When process requires documentation | Low | High -- starting from blank is hard |
| Integrate into existing tools | When the process requires a separate tool | Medium | High -- reduces context switching |
| Make the right thing the easy thing | Design default | Varies | Very High -- defaults shape behavior |

**Key insight:** If you cannot explain the process in 3 sentences, it is too complex. Simplify until a new hire can follow it on day one.

### WANT: Do People Want to Follow the Process?

**Problem signs:**
- People know the process and can follow it, but choose not to
- Leadership skips the process ("too busy," "this one's urgent")
- Process is seen as bureaucracy rather than value-add

**Tactics:**

| Tactic | When to Use | Effort | Effectiveness |
|--------|-----------|--------|--------------|
| Show consequences of non-compliance | When people don't see the cost of skipping | Low | High -- make the damage visible |
| Broken windows principle | When process compliance is inconsistent | Low | High -- enforce small violations to prevent large ones |
| Peer accountability | When team culture supports it | Low | Medium-High -- social pressure works |
| Leadership modeling | Always -- this is a prerequisite | Low | Very High -- if leaders skip it, everyone skips it |
| Make impact visible | When process outcomes can be measured | Medium | High -- show that following the process leads to better results |

**Key insight:** Do NOT use rewards for following the process. Focus on consequences for skipping it. The "broken windows" principle applies: if small violations are tolerated, the process is dead. And critically: **leadership must follow the same processes.** If leaders skip the process, they signal it is optional for everyone.

### DO: Are There Mechanisms Ensuring the Process Happens?

**Problem signs:**
- Everything above works in theory, but compliance is still low
- People forget at the moment of action
- There is no checkpoint where non-compliance is caught

**Forcing Function Types:**

| Type | Description | Example | Strength |
|------|-----------|---------|----------|
| **Soft approval** | Approval is required but can be overridden with justification | "Submit experiment brief for review. If no response in 24h, proceed." | Medium -- creates a speed bump without blocking |
| **Hard approval** | Cannot proceed without approval | "Feature flag cannot be toggled to production without experiment brief approved by analyst." | Strong -- ensures compliance, but can slow down |
| **Follow-through** | Automated check after the action to verify compliance | "After experiment ends, automated reminder to complete results document within 3 days." | Medium -- catches missed steps |
| **Trigger** | Automated prompt at the right moment | "When a PM creates a feature flag, auto-create an experiment brief template linked to it." | Strong -- process starts automatically |
| **Automated enforcement** | System enforces the process with no human override | "Experiment results dashboard is locked until minimum duration reached." | Very Strong -- no compliance issue, but inflexible |

**Escalation ladder:** Start with soft forcing functions. Escalate to hard only if soft consistently fails. Start with triggers and follow-throughs before approvals.

---

## Process-as-Product

Treat every internal process like a product. The "users" are your team members. Apply the same rigor you would to a customer-facing feature.

### Discovery

Interview the process "users":
- What problem does this process solve for you? (Or does it create problems?)
- Walk me through the last time you followed this process. Where did you get stuck?
- What steps do you skip? Why?
- If you could redesign this process, what would you change?
- What information do you need at each step that you don't have?

### Design

Apply UX principles to the process:
- **Progressive disclosure:** Don't show all steps upfront. Reveal what's needed at each stage.
- **Smart defaults:** Pre-fill what you can. Templates with guidance, not blank forms.
- **Error prevention:** Design the process so common mistakes are impossible (e.g., required fields, validation).
- **Feedback:** Show progress. "Step 2 of 4" is more motivating than an endless form.

### Beta Test

Try with one team first:
- Run the process for one sprint/quarter with a single team
- Collect feedback weekly
- Iterate before rolling out broadly
- Do NOT mandate organization-wide on day one

### Measure

Track process health:
| Metric | What It Measures | Target |
|--------|-----------------|--------|
| Adoption rate | % of eligible actions that follow the process | > 80% |
| Time-to-complete | How long the process takes | Decreasing over time |
| Satisfaction | Team rating of the process (1-5) | > 3.5/5 |
| Error rate | % of process outputs with quality issues | < 10% |
| Skip rate | % of steps skipped | < 20% (identify which steps are skipped and why) |

### Iterate

Based on metrics and feedback:
- Remove steps that are consistently skipped (they're not valuable)
- Automate steps that are slow and mechanical
- Add guidance where errors are common
- Simplify language and reduce jargon

---

## Culture-Process Loop

Processes and culture are interdependent. You cannot have good processes without a supportive culture, and you cannot build culture without processes that reinforce desired behaviors.

### The Loop

```
Leadership behavior → Process design → Team behavior → Culture → Leadership behavior
```

1. **Leadership models the process:** If the VP of Product skips the experiment brief, PMs will too. Leaders go first.
2. **Process makes the behavior easy:** Well-designed processes make the desired behavior the path of least resistance.
3. **Repeated behavior becomes culture:** When teams consistently run experiments, review data, and share learnings, it becomes "how we do things."
4. **Culture reinforces the process:** When experimentation is cultural, new hires adopt the process naturally because "everyone does it."

### Breaking the Loop (When Culture is Anti-Process)

If the current culture resists process:
1. **Start small:** One process, one team. Do not attempt organization-wide change.
2. **Show, don't tell:** Run the process yourself. Produce visibly better results. Let others see the benefit.
3. **Find allies:** Identify 2-3 people who already value structure. They become your early adopters.
4. **Make it optional at first:** "Try this experiment brief template for your next test. See if it helps." Voluntary adoption is more durable than mandated compliance.
5. **Celebrate outcomes, not compliance:** "That experiment brief helped us catch a design flaw before launch" not "great job filling out the template."

---

## Common PLG Processes to Design

### Experiment Process

**Frame (non-negotiable):**
- Every experiment has a written hypothesis before launch
- Every experiment has guardrail metrics defined
- Results are documented within 1 week of conclusion
- Failed experiments are shared in growth review

**Freedom (flexible):**
- How the hypothesis is generated (data, research, intuition)
- Which tools are used for the experiment
- How long the experiment runs (within guidelines)
- How the results are communicated (Slack, doc, presentation)

### Feature Launch Process

**Frame:**
- Success metric defined before development starts
- Tracking events implemented before launch
- Launch/no-launch decision based on success metric at 30 days

**Freedom:**
- Feature design approach
- Engineering implementation
- Rollout strategy (staged, flag, big-bang)

### Pricing Change Process

**Frame:**
- Impact analysis (revenue model + customer segment analysis) before any pricing change
- Customer communication plan approved
- Grandfathering policy decided
- Monitoring dashboard for 90 days post-change

**Freedom:**
- Pricing model design
- Communication channels and timing
- Grandfathering duration and terms

### Goal Setting Process

**Frame:**
- Goals derived from revenue driver tree
- Every goal has a leading indicator the team can influence weekly
- Goals reviewed monthly, adjusted quarterly
- Goal miss analyzed (why, not who)

**Freedom:**
- Specific targets (team proposes, leadership approves)
- Strategies and tactics to achieve goals
- How the team organizes work to pursue the goal
