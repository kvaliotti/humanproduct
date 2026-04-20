---
name: positioning-orchestrator
description: >
  Run the end-to-end product positioning pipeline: workshop → competitive alternatives deep
  dive → market frame selection → sales story. Use when the user says "full positioning
  process", "end-to-end positioning", "complete positioning workflow", "run the whole
  positioning pipeline", "do everything from scratch", or wants to go from zero to a complete
  positioning canvas plus sales story in one session. This is the entry point for users who
  want the comprehensive treatment.
---

# Positioning Orchestrator

Run the full positioning pipeline from start to finish. Each phase runs as a distinct skill invocation to keep reasoning clean between stages.

## Pipeline Overview

```
Phase 1: Positioning Workshop (Steps 1-3 pre-work + Steps 4-7 core analysis)
    ↓
Phase 2: Market Frame Selector (Step 8 — deep dive on market choice)
    ↓
Phase 3: Trend Layer (Step 9 — optional, skip if no natural fit)
    ↓
Phase 4: Capture & Pressure Test (Step 10 — canvas + narrative + tests)
    ↓
Phase 5: Sales Story Builder (Post-positioning — 7-stage narrative)
```

## How to Run

### Phase 1: Core Positioning Workshop

Use the `positioning-workshop` skill for Steps 1-7. This produces:
- Best-fit customer profile
- Competitive alternatives (grouped and ranked)
- Unique attributes
- Value themes with proof
- Target market characteristics

If the user wants a deeper exploration of competitive alternatives, invoke the `competitive-alternatives` skill for Steps 4-6 instead of the workshop's built-in version.

At the end of Phase 1, summarize what was established and confirm with the user before proceeding.

### Phase 2: Market Frame Selection

Use the `market-frame-selector` skill for Step 8. Feed it the outputs from Phase 1:
- Competitive alternatives
- Unique attributes and value themes
- Best-fit customer characteristics

This produces:
- Chosen market category with rationale
- Two rejected alternatives with reasoning
- Positioning style (Head to Head / Big Fish Small Pond / Create New Game)

### Phase 3: Trend Layer

Ask the user if there's a relevant trend. Apply the three-circle test:
1. Connects to product strengths?
2. Connects to market context?
3. Customers actually care about it?

If all three: include it. Otherwise: skip. "Better boring than baffling."

### Phase 4: Capture and Pressure Test

Assemble the full 5+1 positioning canvas. Write the positioning narrative and one-liner. Run the 9-question pressure test.

Deliverables:
1. Filled 5+1 positioning canvas
2. Positioning narrative paragraph
3. One-line elevator version
4. Stop/Start saying list (3 each)
5. Pressure test results with pass/fail for each

If any pressure tests fail, patch the specific component before proceeding.

### Phase 5: Sales Story

Use the `sales-story-builder` skill. Feed it the completed positioning canvas. This produces:
1. Full 7-stage sales story document
2. Story-on-a-page condensed version
3. Downstream cascade recommendations (messaging, roadmap, pricing, sales, CS)

## Output Format

At the end of the pipeline, deliver a single comprehensive document containing:

1. **5+1 Positioning Canvas** (one page)
2. **Positioning Narrative** (one paragraph)
3. **One-Line Elevator** (one sentence)
4. **Stop/Start Saying** (table)
5. **Pressure Test Results** (scored table)
6. **Sales Story** (full 7-stage arc)
7. **Story-on-a-Page** (condensed reference)
8. **Next Steps** (downstream cascade priorities)

Save as a markdown file in the user's workspace.

## Handoff Protocol

Between phases, pass structured data:

```yaml
phase_1_output:
  best_fit_customers: [...]
  competitive_alternatives:
    groups: [...]
  unique_attributes: [...]
  value_themes: [...]
  target_market: [...]

phase_2_output:
  market_category: "..."
  positioning_style: "..."
  rejected_options: [...]
  trend: "..." # or null

phase_4_output:
  canvas: {filled 5+1}
  narrative: "..."
  elevator: "..."
  pressure_test_results: [...]
```

## Session Management

The full pipeline takes 30-60 minutes of interactive work. At each phase boundary:
1. Summarize what was established
2. Confirm the user wants to proceed
3. Offer to save progress so far

If the user wants to stop mid-pipeline, save the current state and note which phase to resume from.

## Style Rules

- This is the premium, comprehensive experience. Don't rush.
- Each phase should feel like a distinct workshop session, not a form to fill.
- Challenge aggressively at every step — the orchestrator sets the tone for rigor.
- The final deliverable should be a document the user can hand to their team and say "this is our positioning."
