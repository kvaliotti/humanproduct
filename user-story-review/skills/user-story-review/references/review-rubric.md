# Review Rubric

A lookup, not a script. Consult the gate a story is failing; do not walk every gate aloud, and never transcribe this file into the output. A story does not need every field written on the card — it needs enough shared context to support the relevant conversation.

## The causal chain the gates test

Three different links, routinely collapsed into one:

1. the product changes an observable capability or rule *(the team controls this)*;
2. a user behaves differently *(the team influences this)*;
3. that behaviour contributes to an organisational outcome *(the team contributes to this)*.

Collapsing the chain is what produces feature requests, fake benefits, and promises the team cannot keep. Most findings below are a symptom of a collapse somewhere in it.

## Gate A — Strategic connection

**Pass:** links to one milestone objective and a priority impact · fits the product's current stage and chosen segment · organisational value is explicit or traceable through a short causal chain.

**Fail:** pet feature with a retrofitted "so that" · optimises a local activity with no plausible link to the objective · PRD mixes unrelated segments or impacts in one milestone · detailed story list with no hierarchy, journey, or impact structure.

**Ask:** Which objective would be less likely without this? · Which user behaviour must change for the business outcome to move? · Why now rather than someday?

## Gate B — User and outcome

**Pass:** actor is a meaningful segment, role, or stakeholder · outcome is an observable change in behaviour or capability · "how much?" has a threshold, range, frequency, or qualitative boundary where useful · current pain/workaround is understood.

**Fail:** feature noun masquerading as a need ("dashboard", "export", "AI assistant") · circular value ("so I can use the feature") · generic actor that gives no design guidance ("user", "admin", "system") · claimed value cannot be observed after delivery.

**Ask:** Who behaves differently after this ships? · What do they start, stop, do faster, do more accurately, or do with less effort? · What is the minimum change worth achieving?

Segments matter only when they change the need or the solution. Reject generic actors — but do not manufacture decorative personas either. The segment must explain different behaviour, context, constraints, or value. Replacing "user" with "team lead" and stopping there is not a fix.

## Gate C — System change and control

**Pass:** observable "currently" vs "after" system behaviour is clear · states product/business-rule change, not implementation internals · deliverable is in the team's zone of control · desired outcome is in its sphere of influence · external dependencies and owners are visible.

**Fail:** the need is actually a technical task · team is asked to guarantee an external outcome it can only influence ("so my audience doubles") · specifies architecture while user-visible behaviour stays vague · no one can say what demonstration would prove the change exists.

**Ask:** What observable system output or rule differs from today? · What can this team act on without another group? · What would the end-of-iteration demo show?

## Gate D — Evidence, assumptions, and learning

**Pass:** important assumptions are named · story is a survivable experiment — affordable if wrong, informative either way · learning work has a time box, a decision, and an expected output · post-release evidence and a real-user check are planned.

**Fail:** large investment resting on untested desirability, usability, feasibility, viability, or adoption assumptions · "research story" with no time budget or decision it informs · success inferred from shipping rather than user behaviour · metrics that only capture the expected behaviour and cannot reveal surprises.

**Ask:** What must be true for this to create value? · What is the cheapest credible way to disprove it? · What decision follows from the result? · How will we observe real use after release?

The smallest story is not automatically the best story. Prefer the slice that cheaply tests a material assumption and stays affordable if it fails.

## Gate E — Slice and delivery

**Pass:** end-to-end, demonstrable, useful to at least one meaningful segment · small because scope or risk was reduced, not because value was stripped out · releasable, testable, or usable independently · global constraints still satisfied.

**Fail:** horizontal technical slice (database, API, frontend, migration step) · walking skeleton with no user utility · all-or-nothing across every segment, format, capacity, and edge case · combines learning and full implementation · "MVP" that still needs complete architecture before any feedback · big-bang irreversible redesign where an opt-in parallel rollout would derisk it.

**Ask:** Who can get value first? · What output can exist before all inputs/integrations are complete? · What is the simplest usable output? · Which capacity, format, or segment can be deferred?

## Gate F — Story-set and PRD quality

**Pass:** visible hierarchy from goal → actors/segments → impacts/journey → deliverables · detail increases only as work approaches delivery · a story map or equivalent exposes gaps and end-to-end workflow · cross-cutting concerns defined once per milestone · fixed dates and major risk-reduction points explicit · delivered stories not treated as permanent spec.

**Fail:** flat backlog of hundreds of equally detailed items · stories spanning unrelated segments in one milestone · security, performance, accessibility, or consistency as repetitive fake stories · historic tickets as the only source of current product behaviour · numeric story points offered as evidence of value or certainty · a real external deadline (regulation, contract, season) left implicit.

**Ask:** What higher-level impact or journey step owns this story? · Which global constraints apply to all of them? · Which fixed dates alter sequencing? · Where is current behaviour documented after delivery?

## Severity

- **Blocker** — objective/actor/outcome is false or absent; not actionable; a critical assumption or dependency is hidden.
- **Major** — likely to cause wrong scope, wrong solution, failed learning, or non-valuable technical slicing.
- **Moderate** — avoidable ambiguity or delivery risk, resolvable in normal refinement.
- **Minor** — wording or consistency. Usually not worth reporting.

Blockers and Majors are what compete for the three systemic slots. Never roll severities into a single quality score — the pattern of failure matters more than the arithmetic, and a score hides which kind of failure it is.
