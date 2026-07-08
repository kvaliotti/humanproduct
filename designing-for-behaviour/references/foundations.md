# Foundations: shared definitions and intake

Every lens-analyst and the orchestrator reads this file first. It exists so no lens re-derives the vocabulary or re-does the intake — that shared work happens **once, here**, and each lens spends its attention only on its distinctive contribution.

## The vocabulary

The plugin judges how well a product experience drives **behaviour**, and through behaviour, **adoption** and **engagement** — those three are the **scored dimensions**. **Activation** is defined below as well, but it's a *moment* you reason about inside behaviour and adoption, **not a fourth score**. Keep them distinct — they fail for different reasons and get fixed differently.

- **Behaviour** — the concrete steps, actions, and activities a user performs to reach a desired outcome/state. Always observable. "Feels motivated," "understands the value," "is aware of the feature" are *not* behaviours. "Creates a project," "invites a teammate," "returns the next morning and logs a metric" are behaviours.
- **Activation** — the first time a user extracts the core value of the product experience. Not signup, not setup, not a finished tutorial — the first real value moment.
- **Adoption (breadth)** — whether a user uses a product experience / feature at least once per period. Account-level adoption = how many of the core experiences a user actually uses. If there are 5 core experiences and a user uses 3, adoption is 60%. Aggregate adoption = average core experiences used per account. Higher adoption = broader lock-in.
- **Engagement (depth)** — the frequency/depth with which users perform a core experience. If a user runs experience A five times per period, engagement is 5. Some products define engagement as time spent, watch depth, units consumed per session, or scenarios completed per period. Depth, not breadth.

Every finding a lens produces must be tagged to one or more of **behaviour / adoption / engagement** so the orchestrator can roll scores up per dimension. A finding that can't be tagged to a dimension is probably not a finding.

## Anti-slop contract (read this before writing anything)

The single biggest failure mode of a tool like this is generic advice: "add onboarding," "reduce friction," "make it engaging," "use social proof." That output is worthless. Every observation and recommendation MUST be **anchored to the specific experience** under review:

- **Point at the artifact.** Name the exact screen, flow, step, empty state, notification, file, function, or PRD section. In codebase mode, cite `path/to/file.tsx:line` or the component/route. In PRD mode, quote the sentence. "The onboarding is weak" is slop. "After signup, `OnboardingWizard` (steps 1–4) collects company size, role, and 3 integrations before the user ever sees a populated dashboard — first value is gated behind ~90 seconds of setup" is a finding.
- **Quote the real thing.** Quote the actual button label, headline, error message, or empty-state copy. If you're inferring because you can't see it, say so explicitly ("assuming the CTA reads 'Get started'…").
- **Name the moment.** Behaviour happens at a specific point in time and context. Locate it: "at the end of the first session," "when a returning user opens the app with zero new data," "the third time they hit the paywall."
- **Prefer one sharp finding over five vague ones.** A lens that returns 15 hedged observations is less useful than one that returns the 4 that actually move behaviour, each concrete enough to act on.
- **Say when something is genuinely fine.** Not every experience needs every mechanism. Marking an item strong (or not-applicable) with a reason is a real result — it protects the product from being told to bolt on machinery it doesn't need.

## Intake: reconstruct the actual experience first

Before any scoring, build a shared picture of what you're actually reviewing. The orchestrator does this once and passes it to every lens. Do not skip it — a lens scoring an experience it hasn't reconstructed will hallucinate.

Establish and write down:

1. **The product experience under review** — which flow/feature/surface, and its boundaries. ("The trial-to-paid upgrade flow," not "the whole app.")
2. **The target behaviour(s)** — what the user is supposed to *do*, stated observably, with the situation and moment it should happen in.
3. **Its place in the product** — where it sits in the journey (acquisition / activation / core loop / expansion), and what precedes and follows it.
4. **Why it exists** — the user outcome it serves and the business outcome it drives. Keep these separate.
5. **The users it serves** — who, in what real context (time, energy, attention, device, prior tools/habits).
6. **Core user expectations** — what a reasonable user expects at each step.
7. **How behaviour/adoption/engagement are defined for THIS product** — instantiate the four definitions above concretely (what counts as activation here? what's the natural frequency of the core loop?).

### Mode A — existing product / codebase

Reconstruct the experience the user actually gets, from the code:

- Map the entry points and routes/screens for the flow in scope. Find the components, pages, or handlers that render each step.
- Trace the **first-run path**: signup → setup → first value. Note every gate (form, permission, config, verification, paywall) between the user and the first value moment. Count the steps and the decisions.
- Find the **triggers**: notifications, emails, lifecycle messages, in-app prompts, badges. What brings a user back, and what does each one point to?
- Find the **loops**: what a returning user sees, what state persists between sessions, what accumulates (data, history, progress, streaks, collections).
- Find the **empty states, error states, and edge cases** — zero-data dashboards, failed actions, the returning user with nothing new. These are where behaviour breaks.
- Read the **real copy** — button labels, headlines, empty-state text, error messages, tooltips. Copy is where craving, clarity, and framing live.
- Note what you **cannot** determine from code alone (actual analytics, real drop-off, what users feel) and flag it as an assumption rather than inventing it.

Search widely but report narrowly: it's fine to explore many files; only cite the ones that carry a finding.

### Mode B — idea / PRD / feature description

Reconstruct the *intended* experience from the document(s):

- Extract the intended flow step by step. Where the PRD is silent about a step, that silence is itself a finding (an undesigned moment where behaviour will happen anyway).
- Identify the target behaviour(s) the PRD assumes and check whether they're stated observably or hidden behind intent words ("users will engage more").
- Identify the moments the PRD hasn't designed: the trigger to return, the empty state, the second session, the lapse-and-recovery, the failure path.
- Distinguish what the PRD *asserts* users will do from what would actually make them do it. A PRD that says "users will invite teammates" without a trigger, an easy action, and a reason is describing a hope, not a mechanism.
- You are evaluating a design on paper, so frame findings as risks and gaps ("as specified, there is no cue that would bring a user back on day 2") rather than observed facts.
- **If there is no document — just an inline feature description** — treat the description text you were handed as the document; it is what you analyze. (The orchestrator embeds that text in your prompt so you always have something concrete.)

## What each lens is responsible for (and NOT)

The four lenses are carved so they don't score the same thing twice. If you find yourself evaluating something outside your lens, note it in one line for the orchestrator and move on — don't score it.

- **behavioural-loop** — the mechanics of the repeatable loop: is there a trigger, is the action easy enough to happen, is there a reward, does investment/tracking make the next cycle more likely. Owns habit formation and the core return loop.
- **cognitive-ease** — the moment-to-moment decision experience: at each choice point, is the desired action the fast, obvious, low-effort, low-risk one; framing, defaults, anchoring, memory of the experience.
- **capability-results** — whether the user actually gets better / achieves something they care about outside the product; the progress curve from novice to capable; whether engagement is meaningful or empty.
- **control-autonomy** — what the user is trying to control, whether the product helps them control it without creating conflict or dependence; the ethical/anti-manipulation backbone.

Shared concerns that every book repeated — the definitions above, scoring, ethics/dark-patterns, and the coherence/anti-bloat review — live in their own references and are handled once by the orchestrator, **not** re-scored by each lens.
