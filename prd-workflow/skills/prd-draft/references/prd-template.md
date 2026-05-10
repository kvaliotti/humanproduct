# PRD Template

Use this exact structure when drafting PRDs. Fill every section. If information is unavailable, mark with `[INFERRED — please validate]` or `[TBD]`.

---

```markdown
# [Feature/Product Name] — PRD

## Problem

### What is the problem we are solving?

[1-3 sentences. Define the problem: user problem, business problem, or system problem. Be specific about who has the problem and the impact.]

### What segment of the audience are we targeting?

Define the target segment: 
1. What types of companies & roles will benefit from this problem being solved?
2. What types of companies & roles will NOT benefit from this problem being solved?

If you have the data, provide an estimate of the target segment's size. 

### What opportunity do we have to solve the problem?

1. What happens if we solve the problem for the target segment?
2. What makes solving the problem important for the target segment?

### User success

1. What would change for the user after they use this product experience?
2. How could a user measure the impact of having or using this product experience?
3. What’s the end consequence of having this solution? What will change for the user? 

### Business success measurement

1. How will we measure success? After launching this product initiative, how will we know whether building it was successful for our business?
2. Why are we building this? Why not something else? 
3. If the product initiative is targeted at moving a specific metric, use the template below:

**Target metric hypothesis:** [target metric’s name] will [increase/decrease] from [current level] to [expected new level] because [Product experience name] will [explanation of why the experience will change the metric].

**Secondary metrics & guardrails:**

1. if secondary metric: [provide secondary metric’s name here] will [increase/decrease] because [product experience name] will [explanation of why the experience will change the metric].
2. if guardrail metric: [provide guardrail metric’s name]

> If no metrics are available yet, write: "To be defined after solution validation."

## Solution

### Real-world situations to address (sit-beh)

Define real-world situations this product experience addresses:

1. [activation moment: during/after/within/...] + a [type of person / person that ...] + wants to [desire: Verb + specific goal/outcomes/avoided negative] + [within / taking no more than / with / added / while / ... + precise limitation and its context]

2. …add each distinct situation

**Example:**
> After learning their child's play in 3 days overlaps with the upcoming visit, an initial ADHD patient wants to see any available provider within the same day except 2-4 PM, before it's less than 24h left and they need to pay a $50 rescheduling fee.

### User flows & diagrams

[Add Mermaid diagram for flows with >3 steps or branching logic. Use numbered list for simple linear flows.]

### Key features

US-1. **[Story name]**
As a [ROLE], I want to [ACTION], So that I can [ACHIEVE_GOAL]

Acceptance criteria:
1. AC-1: [specific, testable criterion]
2. AC-2: [specific, testable criterion]

US-2. **[Story name]**
…

### High level technical architecture
Provide key technical architecture decisions that stay high-level and inform the subsequent step of software design doc / implementation plan creation. 

### Out of Scope / Constraints

1. [What you are NOT addressing]
2. [Technical or timeline constraints]
3. …

### Event tracking
If the app has event tracking, outline key events we'll need to pass to the event tracking system. 
Use existing naming convention. If no naming convention exists, default to "Area - Subarea (if relevant) - Verb in paste tense and modifiers". 
Provide event properties and their values. Format as a table. 

## FAQ

Q: [Question a reasonable engineer/designer would ask]
A: [Best available answer]

Q: …
A: …
```
