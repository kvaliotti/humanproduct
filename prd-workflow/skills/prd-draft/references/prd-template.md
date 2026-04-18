# PRD Template

Use this exact structure when drafting PRDs. Fill every section. If information is unavailable, mark with `[INFERRED — please validate]` or `[TBD]`.

---

```markdown
# [Feature/Product Name] — PRD

## Problem

### What is the problem we are solving?

[1-3 sentences. Define the problem: user problem, business problem, or system problem. Be specific about who has the problem and the impact.]

### What opportunity do we have to solve the problem?

[1. How are we going to address the problem?
2. What evidence (data, user research, logic) suggests it will solve the problem?]

## Success measurement

Target metric hypothesis: [target metric's name] will [increase/decrease] from [current level] to [expected new level] because [Product experience name] will [explanation of why the experience will change the metric].

Secondary metrics & guardrails:
1. [secondary metric name] will [increase/decrease] because [product experience name] will [explanation]
2. Guardrail: [guardrail metric name] — must not [degrade/exceed threshold]
3. …add as many as needed

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

### Out of Scope / Constraints

1. [What you are NOT addressing]
2. [Technical or timeline constraints]
3. …

## FAQ

Q: [Question a reasonable engineer/designer would ask]
A: [Best available answer]

Q: …
A: …
```
