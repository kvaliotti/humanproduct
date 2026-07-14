# user-story-review

Reviews user stories in their PRD context and hands back **one page**: what will sink this milestone, a verdict per story, and rewrites for the worst offenders. Not a forty-question homework assignment.

## Install

```
/plugin marketplace add kvaliotti/humanproduct
/plugin install user-story-review@human-led
```

## Use

```
/user-story-review                     # auto-discovers the newest PRD-*.md
/user-story-review path/to/backlog.md
```

Or just ask: *"review the user stories in this PRD"*, *"are these stories ready?"*, *"is this story too big?"*

## What you get

```
Verdict: Needs revision — 2 of 9 stories ready
2 READY · 1 NEEDS CONVERSATION · 3 REFRAME · 1 SPLIT · 2 NOT A STORY

The 3 things that will sink this
1. Milestone mixes two segments  [US-3, US-4, US-7 are enterprise; objective says solo]
2. US-2/5/6 are horizontal layers, not slices  ["create database schema"]
3. No story says how the outcome gets checked with real users

Stories        → one row each: verdict · primary issue · next move
Rewrites       → the worst 3 only, and only where the PRD supplies the evidence

Ask for: splitting options · full question list · non-story work
```

Depth is available on request. It is never the default — a review you have to work through is not a review, it is a new task.

## What makes this reviewer different

- **Reads the whole PRD first.** A story can be locally reasonable and still wrong for the milestone, segment, or product stage.
- **Does not reward template compliance.** "As a user, I want a dashboard so that I can see my data" is syntactically perfect and says nothing.
- **Separates the causal chain** — observable system change (the team controls it) → user behaviour change (it influences it) → business impact (it contributes to it). Collapsing these is what produces fake benefits and promises the team cannot keep.
- **Names the work that should not be a user story.** Engineering, ops, research, and cross-cutting quality get tracked honestly instead of wrapped in "As a system, I want…".
- **Splits by value and learning, never by architecture.** Ten value-oriented slicing patterns; backend→API→frontend is called out as the task decomposition it is.
- **No quality score.** The pattern of failure matters more than the arithmetic, and a number hides which kind of failure it is.

## Verdicts

| | |
|---|---|
| **READY** | Enough basis for a productive conversation and delivery planning |
| **NEEDS CONVERSATION** | Plausible, but one material question is unresolved |
| **REFRAME** | Feature request, fake value, generic actor, or solution-as-need |
| **SPLIT / EXPERIMENT** | Valuable direction, too broad or assumption-heavy for one increment |
| **NOT A USER STORY** | Technical, operational, research, or cross-cutting work in a story wrapper |

## Pairs with

`prd-workflow`: `prd-draft` → `prd-evaluate` → `sit-beh` → **user-story-review**, as the last gate before engineering picks it up. Auto-discovers the `PRD-*.md` that pipeline writes.

## Source

Operationalises Gojko Adzic, David Evans, and Nikola Korac, *Fifty Quick Ideas to Improve Your User Stories* (Neuri Consulting LLP, 2014). Paraphrased and applied — the book's chapters are not reproduced.
