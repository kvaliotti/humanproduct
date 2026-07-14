# Value-Oriented Splitting Patterns

Use these only after clarifying the intended outcome. Do not split a vague feature request into smaller vague feature requests.

| Pattern | Use when | First slice | Guardrail |
|---|---|---|---|
| **Start with outputs** | Inputs/integrations/legacy migration create a large dependency chain | Produce one useful output from temporary/manual inputs | Output must enable real work, not just prove plumbing |
| **Skeleton on crutches** | Full architecture blocks early value | Realistic UI/workflow backed by temporary/manual/simple internals | Avoid throwaway theatre; preserve learning about actual use |
| **Narrow the segment** | “Everyone needs the whole system” | One territory, role, proficiency level, workflow, or context | Segment must be real and reachable |
| **Examples of usefulness** | Large technical change seems indivisible | One concrete use case where only part of the technical change is needed | Pick usefulness first, then technical scope |
| **Split by capacity** | Scale drives most complexity | Limited users, data, file size, concurrency, catalogue, or session length | Later capacity growth should be evolutionary, not a rewrite |
| **Dummy then dynamic** | Reference data/integration access blocks delivery | Hard-coded, manually entered, or local reference data | Mark temporary behaviour and bound acceptable exceptions |
| **Simplify outputs** | Multiple formats/channels/downstream systems expand scope | Simplest usable format or one channel | Must still support the user’s decision/action |
| **Learning then earning** | Unknown feasibility, standard, vendor, or migration risk dominates | Time-boxed investigation with a decision and evidence | No open-ended research; separate implementation story follows |
| **Extract basic utility** | Full usability/automation is too large or deadline-driven | Manual, single-item, repetitive, or less convenient path that completes the critical task | Utility must be real; explicitly plan whether convenience is still needed |
| **Hamburger** | Team is stuck in horizontal technical slicing | Map workflow steps × options and select a thin end-to-end route | Keep workflow high level; avoid one layer per story |

## Selection order

Prefer the split that:

1. tests the riskiest assumption;
2. reaches a real user fastest;
3. produces an observable outcome;
4. minimises irreversible architecture;
5. leaves plausible follow-up slices rather than forcing a rewrite.

## Anti-patterns

- Backend story → API story → frontend story.
- “Phase 1” that no user can access or benefit from.
- Smaller acceptance-criteria bundles with the same untested assumption.
- Splitting by screens when the user still cannot complete a task.
- Treating research as endless analysis rather than a time-boxed decision.
