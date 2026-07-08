# Coherence & Anti-Bloat Review

This is the step that makes the plugin worth using. Four lenses each generate recommendations. If you simply concatenate them, you get a product with streaks *and* badges *and* a tour *and* three nudges *and* a progress bar *and* a goal-setting wizard *and* five lifecycle emails — each individually defensible, collectively an unusable, overloaded mess where the core value is buried under machinery. **A checklist tool without this step actively makes products worse.**

The goal is the opposite: **a strong core product experience with behavioural mechanisms embedded so seamlessly they read as part of the product, not bolted-on mini-experiences.** The best mechanism is usually invisible — a property of the thing the user already does, not a new thing to do.

Run this pass over the *combined* recommendation set from all four lenses, before writing the report.

## The mindset

The lenses were asked "what would make this stronger?" — an *additive* question. Your job here is the *editorial* one: **what is the smallest set of changes that most improves behaviour, adoption, and engagement while keeping the experience coherent and light?** You are protecting the user from the sum of all good advice.

Two failure modes to hold in tension:
- **Under-designed** — the real gaps the lenses found go unaddressed. (Don't over-correct into cutting everything.)
- **Over-designed / bloated** — every gap gets its own new widget, surface, notification, or flow, and the product collapses under its own engagement machinery. This is the more common and more dangerous failure, and the one nobody else checks for.

## Step 1 — Consolidate & de-duplicate

The lenses are carved to minimise overlap, but their *recommendations* still cluster on shared moments (the empty state, the first session, the return trigger, the paywall). Merge recommendations that touch the same moment or propose the same change into one, keeping the sharpest framing. Note which lenses converged — **agreement across lenses is a strong priority signal** (if three lenses independently point at the day-2 empty state, fix that first).

## Step 2 — Detect conflicts & tensions

Find recommendations that undercut each other, and resolve them explicitly rather than shipping both:

- **Direct contradictions** — "cut onboarding to one step" vs. "add a goal-setting step so the reference state is set." Decide which wins, or find the synthesis (set the goal *as* the first value action, not a separate step).
- **Shared-budget collisions** — "add a return notification" (loop) vs. "notifications are noise; cut them" (cognitive-ease/control). More prompts, more salience, more surfaces all draw from the same finite attention budget.
- **Cross-purpose framing** — a loss-aversion or scarcity nudge (cognitive-ease) that the control-autonomy lens would call manipulation. When mechanism-lenses and the autonomy lens disagree, autonomy and the ethics gate win.

## Step 3 — Enforce a complexity budget

The experience has a finite budget of user attention, memory, and willpower (Badass's cognitive-resource economy; Hooked's "one dominant path, don't scatter attention"; Kahneman's effort economy). **Every mechanism you add spends it.** Make the budget explicit:

- **Count the mechanisms** the product already has *and* the ones being proposed (each distinct nudge, badge, streak, tour, banner, modal, notification type, progress indicator, gamification element counts as one).
- **Calibrate the budget to the archetype and natural frequency.** A daily consumer app can carry more loop machinery than a quarterly B2B tool used under time pressure; a focused developer tool should carry almost none. If a mechanism is N/A for this archetype (per the scoring rubric's N/A discipline), it does not go in the report as a recommendation, full stop.
- **A tight budget forces prioritisation.** If ten mechanisms are proposed and the budget is three, the other seven aren't "later" — they're evidence you haven't found the *root* fix (see Step 5).

## Step 4 — Prefer embedding over adding (the "one core experience" test)

For each surviving recommendation, ask: **does this strengthen the single dominant path, or add a parallel mini-experience?** Push every mechanism toward becoming a *property of the core action* rather than a new surface:

- Instead of a streak page + badge system + reminder emails → make accumulated progress **visible inside the thing the user already opens**.
- Instead of a separate onboarding tour → make the **first real action** the thing that teaches, with the product's defaults doing the explaining.
- Instead of a new "achievements" surface → let the **artifact the user built** be the reward and the social proof.
- Instead of a re-engagement email campaign → **load the next trigger from the user's own investment** (a scheduled item, a pending result) so the return reason is intrinsic.

If a recommendation can only exist as a new screen/flow/notification, it must clear a higher bar than one that folds into an existing moment. Bolted-on mechanisms are the texture of a bloated product.

## Step 5 — Find the root fix (collapse the pile)

Many recommendations are **symptoms of one upstream cause**. Fixing the cause makes a dozen downstream mechanisms unnecessary — this is how you shrink the pile without losing value:

- If **first value is too slow**, half the "retention nudge" recommendations evaporate once you fix it — users who feel value come back on their own.
- If the **target behaviour is wrong or too big**, no amount of triggers/rewards/framing will save it; redefining it deletes most of the other recs.
- If the product is a **net disturbance** (control lens), adding engagement mechanics makes it worse, not better.

Always ask: *is there one change that dissolves several of these recommendations?* Lead with it.

## Step 6 — The subtraction pass

The highest-leverage move is often **removal**, not addition. Explicitly look for existing mechanisms to cut:

- Machinery that fights the core (a gamification layer that distracts from the actual value; notifications that train users to ignore them).
- Redundant mechanisms doing the same job (three different progress indicators).
- Anything the lenses flagged as empty engagement, dark pattern, or product-created disturbance.

A recommendation to *remove* something is a first-class output, not a footnote.

## Step 7 — Prioritise & sequence

Apply 80/20: identify the **few moves that unlock the most behaviour/adoption/engagement**, and sequence them by leverage and dependency:

- **Prerequisites first** — some fixes only pay off after an upstream one lands (fix first-value before optimising the return loop).
- **One coherent increment at a time** — recommend shipping in a sequence the team can actually absorb, not a 20-item pile dumped at once. Bloat happens when everything ships together.
- Mark each surviving move with the dimension(s) it improves and a rough effort/leverage read.

## Output of this pass

Feed the report three explicit buckets:

1. **Core moves (do these, in this order)** — the small set of integrated, sequenced changes that most improve behaviour/adoption/engagement. Each says *what* changes, *which existing surface it folds into* (or why it must be new), which dimension it lifts, and which lens findings it resolves.
2. **Fold-ins** — mechanisms embedded into existing surfaces rather than added as new ones, with the specific host surface named.
3. **Deliberately NOT adding (and why)** — recommendations that were cut or deferred: redundant, over-budget, N/A for the archetype, conflicting, manipulative, or dissolved by a root fix. **This list is a feature, not an omission** — it's the evidence the plugin protected the product from bloat, and it's often the most valuable part of the report for the user.

Close with a one-paragraph **coherence rationale**: how the surviving set holds together as one experience, what the dominant path is, and what you deliberately kept the product from becoming.
