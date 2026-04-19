# Proof-of-Value Signals

The third question this skill answers — **how does the customer know the value they're paying for is actually present in the product, and to what degree?** — is not addressed by any single prior framework. This file is the skill's original contribution. It must be applied to every Leader outcome.

## Why this matters

Customers pay for **perceived** value, not value-in-fact (Monetizing Innovation Ch. 11). A product can deliver real value and still lose the sale — or churn a renewal — if the value is invisible. Conversely, a product can deliver modest real value and charge a premium if the value is vividly perceivable. The gap between the two is where monetization lives or dies.

Further, proof signals drive four downstream decisions:

| Downstream decision | How proof signals inform it |
|---|---|
| **Pricing** | Higher WTP where proof is vivid and fast; discount where proof is slow or invisible |
| **Product UX** | Where to design metric displays, celebration moments, team-visibility affordances |
| **Onboarding** | Time-to-first-signal is the single most important onboarding KPI for WTP protection |
| **Sales & marketing** | Testimonial capture ("I knew it was worth it when...") and objection defence |
| **Renewal / expansion** | Signals that trigger the upgrade moment or predict churn |

## The four signal modes

Every proof signal falls in one of four modes. Most Leaders have a primary mode and one or two secondary modes.

### Mode 1 — Experiential (felt / sensory / workflow moment)

A physical or workflow-level felt difference. The buyer notices a new pattern in their own behavior, a new feeling, a new absence of friction.

Telltale phrasing: "I noticed I...", "I stopped doing X", "the screen felt different", "I didn't have to", "it just clicked".

| Strength | Weakness |
|---|---|
| Emotionally sticky — high renewal correlation | Subjective; hard to share with a buyer who didn't personally use |
| Fast (can fire in first session) | Easy to habituate to; decays as novelty |
| Doesn't require instrumentation | Invisible to executive buyers removed from daily use |

**Design implication:** surface the *absence* of friction vividly at the moment it's avoided. (Example: a toast notification "saved you 4 Alt-tabs" after a workflow completes.)

### Mode 2 — Quantitative (metric moved)

A number the buyer can check — in a dashboard, report, invoice, timer, or external system. The value shows up as a measurable change.

Telltale phrasing: "time-to-X dropped from Y to Z", "we saved N hours", "close rate went from X% to Y%", "cost per lead dropped".

| Strength | Weakness |
|---|---|
| Defensible in budget meetings | Requires instrumentation pre- and post- |
| Travels across stakeholders | Attribution is contested ("was it really the tool?") |
| Supports ROI narratives | Slow signals if metric is lagging |

**Design implication:** build the metric dashboard into the product, and pre-populate the baseline during onboarding. If the buyer cannot see the metric without leaving the product, the signal weakens substantially.

### Mode 3 — Social (external validation)

A teammate, boss, peer, customer, or partner confirms the value — explicitly or behaviorally. The buyer's social graph becomes a proof carrier.

Telltale phrasing: "my boss stopped asking", "my team started using it too", "the client noticed the deck was better", "a peer asked how I did it".

| Strength | Weakness |
|---|---|
| High status payoff — amplifies Bain social layer | Slow (requires multiple interactions) |
| Drives word-of-mouth and organic expansion | Dependent on social context; some roles are isolated |
| Often the strongest renewal driver in team/enterprise | Buyer's peers may not be on the product |

**Design implication:** make the buyer's team-visible output better (cleaner output, shareable artifacts, observable-by-others behavior change). Slack/Teams/email integration is often the delivery mechanism for social signals.

### Mode 4 — Temporal (pattern over time)

A frequency, streak, or trend the buyer notices retrospectively. Value becomes a habit or a rhythm.

Telltale phrasing: "by week 3 I was using it daily", "I haven't opened the spreadsheet in a month", "every Monday morning now", "I forgot what it was like before".

| Strength | Weakness |
|---|---|
| Very high switching cost once established | Slow to fire (weeks, not minutes) |
| Correlates with renewal and expansion | Buyers who churn before the pattern forms never perceive it |
| Robust against single-session setbacks | Invisible to the sales process and exec sponsor |

**Design implication:** surface streaks, weekly recaps, anniversary moments. Make the temporal pattern legible to the buyer *and* to their boss.

## The detection fields (per Leader outcome)

For each Leader outcome in the value map, record these fields:

| Field | What to capture |
|---|---|
| **Primary signal mode** | Experiential / Quantitative / Social / Temporal |
| **Secondary signal modes** | Additional modes that reinforce |
| **Specific signal** | The buyer-voice description of what the signal looks like |
| **Detection latency** | Time from first use until signal reliably fires (minutes / hours / days / weeks) |
| **Perceiver** | Self / Team / Boss / Customer / Partner — who notices |
| **Measurement friction** | None / Low / Medium / High — how much effort to check |
| **Inverse risk signal** | What it looks like when value is NOT being delivered |
| **UX / product implication** | Where the signal must be designed into the product |
| **Evidence source** | Case study, review, interview, hypothesis |
| **Confidence** | 0–100% this signal is real |

## Signal strength — the four-lever scorecard

Score each Leader's proof signal on four levers (1–5 each):

| Lever | Bad (1) | Good (5) |
|---|---|---|
| **Vividness** | Invisible or abstract | Concrete, unmissable |
| **Speed** | Weeks to fire | Seconds to fire |
| **Travelability** | Felt by buyer only | Naturally shared with buyer's stakeholders |
| **Defensibility** | Contested attribution | Unambiguous, trackable to the product |

Total score 4–20.

- **16–20:** strong WTP protection; the buyer will happily renew and defend the spend internally.
- **11–15:** moderate; proof can be reinforced through UX work (dashboards, streaks, team affordances).
- **≤10:** invisible value; either redesign proof signals, or reduce the WTP hypothesis.

## Anti-patterns

| Anti-pattern | Why wrong | Fix |
|---|---|---|
| Claiming value without naming a signal | Value-in-fact without proof is unmonetizable | Force-name a signal per Leader |
| Relying only on experiential mode | Doesn't travel; loses enterprise sale | Add at least one social or quantitative mode for B2B |
| Signals with week-plus latency and no earlier proxy | Onboarding churn before proof | Design an interim signal that fires in session 1 |
| Treating inverse risk signals as optional | Churn is invisible until it happens | Always capture what "failing silently" looks like |
| Conflating feature-use metrics with value-realization signals | "They logged in 12 times" ≠ "they got the outcome" | Track the outcome, not the activity |

## Worked example — AI Chief of Staff (meeting-briefs Leader)

**Leader outcome:** "Walk into a 1:1 already prepped, without having spent 20+ minutes pre-reading context before it."

| Field | Value |
|---|---|
| **Primary signal** | Experiential — "I realized I hadn't opened Slack or last week's notes before the meeting started" |
| **Secondary signals** | Temporal — by week 2, the pre-meeting scramble is gone as a routine; Social — teammate notices better follow-through |
| **Detection latency** | First meeting (minutes) — experiential; week 2 — temporal |
| **Perceiver** | Self primarily; team observes downstream behavior shift |
| **Measurement friction** | None (automatic in workflow) |
| **Inverse risk** | Brief is shallow → buyer still preps manually → value unperceived → churn at renewal |
| **UX implication** | Surface the brief inline at the moment the meeting starts (calendar nudge, Slack DM 5 min before). Do NOT bury in a separate dashboard. |
| **Evidence** | Hypothesis (pre-PMF); validate with 10 Mom-Test interviews of target buyers who currently tolerate the pre-meeting scramble |
| **Confidence** | 55% — plausible direction, needs behavioral confirmation |

**Signal scorecard:**
- Vividness: 4 (very concrete once felt)
- Speed: 4 (first meeting)
- Travelability: 2 (mostly personal unless team observes behavior)
- Defensibility: 3 (easy to attribute if pattern breaks)
- **Total: 13 / 20** — moderate; strengthen travelability with shareable brief artifact or manager visibility feature.

## Cross-segment proof signal matrix

In the output, consolidate signals across all segments into one matrix:

| Leader outcome | Segment | Primary signal mode | Signal strength (4–20) | UX placement |
|---|---|---|---|---|
| ... | S1 | Experiential | 13 | Inline calendar nudge |
| ... | S2 | Quantitative | 17 | Dashboard with pre/post metric |
| ... | S3 | Social | 15 | Shared artifact surfaced to manager |

This matrix is the product-design brief for the UX team and the foundation for onboarding KPI design (time-to-first-signal).
