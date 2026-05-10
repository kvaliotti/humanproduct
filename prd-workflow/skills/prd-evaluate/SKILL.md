---
name: prd-evaluate
description: >
  Evaluate a PRD or product document for missing use cases, edge cases, UI/UX gaps, and implicit
  assumptions that need to be explicit. Use this skill when the user says "evaluate my PRD",
  "review my spec", "find gaps in my product doc", "what am I missing", "check for edge cases",
  or wants a thorough quality review of a product requirements document. Also trigger when the user
  has just finished drafting a PRD (via prd-draft or otherwise) and wants it stress-tested before
  handing it to engineering. This skill catches the things that feel "obvious" but aren't written
  down — like adding the creator to a calendar invite in accepted status, or handling what happens
  when a user has zero items in a list.
user-invocable: true
argument-hint: "[path to PRD or product document]"
---

# PRD Evaluation Skill

Systematically find what's missing, implicit, or underspecified in a product document. The goal is to catch every gap that would cause an engineer to make assumptions, a designer to guess, or a QA engineer to file a bug.

## Philosophy

Product documents fail in predictable ways. The most dangerous gaps aren't the big missing features — they're the small, "obvious" behaviours that nobody writes down because they seem self-evident. Examples:

- "If a user creates a calendar invite, the creator should be added as an attendee in accepted status" — obvious to the PM, but an engineer might not add this
- "What happens when the list is empty?" — every list view needs an empty state
- "What if the user loses connectivity mid-flow?" — especially relevant for mobile
- "Who gets notified when X happens?" — notification logic is almost always underspecified

This skill exists to surface these gaps before they become bugs, delays, or design debt.

## Step 0: Launch a separate agent to avoid context pollution

A separate agent that doesn't have the session context, and, thus, is unpolluted, should be launched for evaluation. 

## Step 1: Ingest the PRD

Read the full document. Build a mental model of:

- The core user flows (happy paths)
- The actors involved (users, systems, admins, third parties)
- The state transitions (what changes when an action is taken)
- The data model implications (what gets created, read, updated, deleted)

## Step 2: Run the evaluation checklist

Work through each category below. For each category, identify specific gaps in the PRD. Do not generate generic advice — every finding must reference a specific part of the PRD and describe what's missing.

Read the detailed evaluation checklist from `references/evaluation-checklist.md`.

### Category summary (details in references):

1. **State & lifecycle gaps** — What happens at each state transition? What about creation defaults, deletion cascades, and undo?
2. **Empty, zero, and boundary states** — Empty lists, first-time use, maximum limits, zero quantities
3. **Multi-actor & permission gaps** — Who else is involved? What can each role see/do? Concurrent access?
4. **Error & failure handling** — Network failures, validation errors, timeouts, partial failures, retry behaviour
5. **Notification & communication gaps** — Who gets notified? When? Through what channel? Can they act on it?
6. **Temporal & scheduling gaps** — Time zones, recurring events, deadlines, expiration, scheduling conflicts
7. **UI/UX micro-interactions** — Loading states, confirmation dialogs, success feedback, progress indicators, back/cancel behaviour
8. **Data integrity & consistency** — What happens to related records? Orphaned data? Display when source is deleted?
9. **Onboarding & progressive disclosure** — First use experience, feature discovery, contextual help
10. **Accessibility & inclusivity** — Screen reader paths, keyboard navigation, colour contrast, responsive behaviour
11. **Performance & scale implications** — What happens with 10x data? Pagination? Lazy loading?
12. **Integration & system boundary gaps** — API contracts, webhook payloads, third-party failure modes

## Step 3: Classify and prioritize findings

For each finding, assign:

- **Severity**: Critical (will cause bugs/confusion) | Important (should address before dev) | Nice-to-have (improves completeness)
- **Category**: Which checklist category it falls under
- **Specific gap**: What exactly is missing or implicit
- **Suggested addition**: Draft the actual text/AC that should be added to the PRD

## Step 4: Present findings

Present findings grouped by severity, highest first. Format:

```
### Critical gaps

**[GAP-1] [Short title]**
- Section: [which PRD section this affects]
- Gap: [what's missing]
- Risk: [what goes wrong if this isn't addressed]
- Suggested addition: [draft the specific text, user story, or AC to add]

...
```

After presenting, ask:

> "Which gaps should I add to the PRD? Say **'add all'** to incorporate everything, or list specific gap numbers (e.g., 'add GAP-1, GAP-3, GAP-7'). After updating, I'll run **sit-beh analysis** to generate product-led mechanisms for each situation."

## Step 5: Update the PRD

For each accepted gap:
- Add new acceptance criteria to existing user stories where the gap is related
- Create new user stories for gaps that represent distinct functionality
- Update the FAQ with questions surfaced during evaluation
- Add empty/error/edge state specifications to the relevant user flows

Preserve the original PRD structure. Add content inline where it belongs — do not create a separate "gaps" appendix.

## Chaining

After updating the PRD:
1. Suggest running **sit-beh** for full behavioural analysis on the situations
2. The sit-beh analysis will generate product-led mechanisms that can further enrich the PRD
