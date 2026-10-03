# Human-Led Product Claude Plugins

A Claude Code plugin marketplace for product work — turning messy input into engineering-ready specs, researching markets and users, pulling voice-of-customer out of sales calls, and reviewing, optimising, or building design systems, and reviewing your writing, all grounded in real user behaviour.

## Plugins at a glance

| Category | Plugin | What it does |
|---|---|---|
| Define what to build | [prd-workflow](#prd-workflow) | Draft a PRD from messy input, find its gaps, ground it in real user situations |
|  | [user-story-review](#user-story-review) | One-page triage of a PRD's user stories |
| Research users and markets | [strategic-research](#strategic-research) | Market research ending in a one-page recommendation |
|  | [user-research](#user-research) | Plan interviews, analyze each participant, synthesize answers |
|  | [sales-call-analysis](#sales-call-analysis) | Pains, objections, and decision criteria from sales calls, with quotes |
| Position and grow | [pmm-define-and-review-positioning](#pmm-define-and-review-positioning) | Define or audit positioning (5+1 framework) and build the sales story |
|  | [plg-growth](#plg-growth) | Product-led growth diagnosis across the AARMS funnel |
|  | [cro-engine](#cro-engine) | Conversion review of pages, signup, paywalls, onboarding, and forms |
|  | [event-tracking](#event-tracking) | Analytics tracking plans: use cases, event specs, and audits |
| Design | [design-system-master](#design-system-master) | Review, optimise, or create a design system as a DESIGN.md |
|  | [designing-for-behaviour](#designing-for-behaviour) | How well a product drives behaviour and engagement, with fixes |
| Write | [writing-review](#writing-review) | Five parallel reviewers find defects in a draft; one merged review |

## Install

In Claude Code:

```
/plugin marketplace add kvaliotti/humanproduct
```

Then install the plugins you want:

```
/plugin install prd-workflow@human-led
/plugin install user-story-review@human-led
/plugin install strategic-research@human-led
/plugin install user-research@human-led
/plugin install sales-call-analysis@human-led
/plugin install pmm-define-and-review-positioning@human-led
/plugin install plg-growth@human-led
/plugin install cro-engine@human-led
/plugin install event-tracking@human-led
/plugin install design-system-master@human-led
/plugin install designing-for-behaviour@human-led
/plugin install writing-review@human-led
```

## Define what to build

Turn messy input into a spec, then check its stories before engineering starts.

### prd-workflow

End-to-end PRD pipeline: draft from messy input, evaluate for gaps, then run Situation/Behaviour analysis to ground the spec in real user moments.

Three skills:
- **prd-draft** — structured PRD from unstructured input
- **prd-evaluate** — gap analysis across 12 categories
- **sit-beh** — situation/behaviour framework with product-led mechanisms

To build what the PRD describes, pair it with [superpowers](https://github.com/obra/superpowers) (brainstorming → plan → subagent-driven implementation).

See [prd-workflow/README.md](./prd-workflow/README.md) for details.

### user-story-review

Reviews the user stories in a PRD or backlog and hands back **one page**: the few things that will sink the milestone, a verdict per story, and rewrites for the worst offenders. Depth on request — a review you have to work through is not a review, it's a new task.

One skill (`user-story-review`), backed by a six-gate rubric and ten value-oriented splitting patterns.

It reads the whole PRD before judging any story, doesn't reward template compliance, separates the causal chain (system change the team *controls* → behaviour change it *influences* → business impact it *contributes to*), names the work that shouldn't be a user story at all, and refuses to emit a quality score. Grounded in *Fifty Quick Ideas to Improve Your User Stories*.

```
/user-story-review              # auto-discovers the newest PRD-*.md
```

Pairs with `prd-workflow` as the last gate before engineering. See [user-story-review/README.md](./user-story-review/README.md) for details.

## Research users and markets

Markets, interviews, and sales calls, with every finding sourced or quoted.

### strategic-research

Research a market and get a recommendation you can read in five minutes. Five steps, each a short markdown file with sourced facts, plain words, and a list of what we still don't know.

Run the whole pipeline with `/strategic-research <product, category, or industry>` (resume with `--from=N`), or call any step on its own:

1. **industry-process-map** — the steps people go through and how each gets done today
2. **audience-segment-research** — segments, how to spot them, who to go after first
3. **willingness-to-pay-research** — what they pay today and a price range to test, with the arithmetic shown
4. **competitor-evaluation** — who else solves it, why people pick or leave them, the gaps
5. **strategic-synthesis-report** — one page: where to play, how to win, risks, next steps

See [strategic-research/README.md](./strategic-research/README.md) for details.

### user-research

Plan interviews, analyze each participant, then roll everyone up into answers. Every finding carries verbatim quotes and a count of who said it.

Three skills:
- **plan-research** — the decision the research informs, riskiest assumptions, who to talk to, and an interview guide that asks about past behaviour
- **analyze-interviews** — one Opus sub-agent per participant: what they actually did, pains, goals, barriers, each with quotes
- **synthesize-research** — answers to the research questions, assumptions marked confirmed / killed / open, and theme → finding tables

See [user-research/README.md](./user-research/README.md) for details.

### sales-call-analysis

Turn sales call transcripts into pains, outcomes, objections and decision criteria, each with verbatim quotes, plus what it would take to convert each prospect and which hooks would land with them. Then roll all clients up into cross-client tables.

Two skills:
- **analyze-sales-call** — one Opus sub-agent per client, with each client's transcripts merged into one analysis
- **aggregate-call-analyses** — category → item tables for pains, outcomes, objections and decision criteria, with companies, quotes and counts

See [sales-call-analysis/README.md](./sales-call-analysis/README.md) for details.

## Position and grow

Positioning, product-led growth, conversion, and the tracking to measure it.

### pmm-define-and-review-positioning

Product positioning toolkit grounded in the 5+1 positioning framework. Define positioning through a guided workshop, audit existing positioning, or go deep on specific steps.

Six skills:
- **positioning-workshop** — full guided 10-step positioning process
- **positioning-review** — audit and stress-test existing positioning
- **competitive-alternatives** — deep dive into alternatives, attributes, and value themes
- **market-frame-selector** — choose between Head to Head / Big Fish Small Pond / Create a New Game
- **sales-story-builder** — 7-stage sales narrative from completed positioning
- **positioning-orchestrator** — end-to-end pipeline running all skills in sequence

See [pmm-define-and-review-positioning/README.md](./pmm-define-and-review-positioning/README.md) for details.

### plg-growth

Product-led growth help for PMs. Each skill answers the question you asked in a few paragraphs, and runs the full analysis (about one page) only when you ask for it. No benchmark appears unless it has a source.

Fourteen short skills, with `plg-orchestrator` as the entry point that routes to the rest:
- **Fit and levers:** `plg-readiness` (is PLG right here?), `plg-revenue-analysis` (which revenue lever matters most)
- **Acquisition:** `acquisition-model-selector` (freemium, trial, reverse trial, ungated, demo), `acquisition-domain`
- **Funnel stages:** `activation-domain`, `retention-domain`, `monetisation-domain`, `satisfaction-domain`
- **Cross-cutting:** `growth-loops`, `product-led-sales`, `plg-experimentation`, `plg-data-setup` (hands tracking plans to `event-tracking`), `plg-transformation`

See [plg-growth/README.md](./plg-growth/README.md) for details.

### cro-engine

A conversion-rate-optimization reviewer for landing pages, pricing, signup, onboarding, paywalls, popups, and forms. One skill (`cro-engine`) returns the biggest leak and the top few fixes, each tied to a concrete element (quoted copy, a named field or step), why it hurts, and a test to run. No scores, no borrowed benchmarks.

### event-tracking

Define what to track, name it, and review what you already track. Every event traces back to a question someone will act on, and existing naming conventions are detected and matched, not replaced.

Three skills:
- **analytics-use-cases** — stakeholder questions, analysis types, and dashboards, before any event is named
- **event-definition** — event specs (names, properties, firing conditions, user properties, PII), with an optional final step that formats them for Amplitude, Mixpanel, PostHog, Segment, or GA4
- **tracking-plan-review** — audit existing tracking; leads with the top fixes, then measured ratios per check

See [event-tracking/README.md](./event-tracking/README.md) for details.

## Design

Design systems and behavioural design.

### design-system-master

Your design-system master — review an existing design system, optimise one (including retrofitting it into a product codebase), or build one from scratch as a lintable `DESIGN.md`. Grounded in a corpus of 74 real-world design systems (minimal dev-tools → dense financial/enterprise → expressive consumer/automotive), with a complexity-calibration gate so it never naively simplifies complexity a domain legitimately needs (dual-coded green/red, dual font stacks, multi-surface theming, semantic ramps).

An orchestrator plus three skills:
- **design-system-master** — entry point / router: diagnoses whether you need review, optimize, or create, and what input you have
- **review-design-system** — accessibility gate (real WCAG contrast math) and complexity-fit gate, then the top fixes and a Keep list; about one page, no scores
- **optimize-design-system** — consolidate tokens, fill gaps, fix contrast, and/or roll the system into a codebase (CSS variables / Tailwind / Style Dictionary), protecting the signature
- **create-design-system** — build a complete `DESIGN.md` from scratch, sized to the product's archetype

Run the router with `/design-system-master`, or call any skill standalone. See [design-system-master/README.md](./design-system-master/README.md) for details.

### designing-for-behaviour

A behavioural-design reviewer — point it at a codebase or at an idea/PRD and it answers: how well does this drive behaviour, adoption, and engagement, where are the gaps, and what integrated set of fixes strengthens one coherent core experience rather than bloating it.

An orchestrator skill driving four read-only analyst agents in parallel:
- **behavioural-loop-analyst** — trigger → action → reward → investment (Atomic Habits, Tiny Habits, Hooked)
- **cognitive-ease-analyst** — System 1/2, friction, framing, defaults, peak-end (Thinking, Fast and Slow)
- **capability-results-analyst** — does the user get more capable and get results they care about (Badass)
- **control-autonomy-analyst** — what the user is trying to control, plus the anti-manipulation backbone (Perceptual Control Theory)

Six books collapse into four de-duplicated lenses, then an **anti-bloat coherence review** turns four lenses' worth of additive suggestions into the smallest integrated set — with an explicit "deliberately NOT adding" list. Two-page report, no score. Run with `/designing-for-behaviour`.

## Write

Review drafts before they ship.

### writing-review

Review a draft the way a linter reviews code: find defects, don't rewrite. Five narrow reviewers (reader, structure, argument, evidence, prose) run in parallel without seeing each other's work. Every finding is an exact quote, the problem it causes, and the smallest fix; then they're merged into one ranked review.

One skill (`review-writing`) and one agent. The prose reviewer checks a short list of Zinsser-style clutter rules and AI-writing tells, and the review's own text follows them.

```
/writing-review:review-writing draft.md                    # all five reviewers
/writing-review:review-writing draft.md --only argument,evidence
```

See [writing-review/README.md](./writing-review/README.md) for details.

## Author

Konstantin Valiotti — [PM blog on Substack](https://kvaliotti.substack.com)
