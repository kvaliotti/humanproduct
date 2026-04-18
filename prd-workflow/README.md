# PRD Workflow Plugin

End-to-end product requirements pipeline that turns messy input into engineering-ready PRDs, then stress-tests them for completeness.

## What it does

This plugin provides a 6-step sequential workflow:

1. **Review** messy input (notes, ideas, Slack dumps, brainstorms)
2. **Draft** a structured PRD using a proven template
3. **Evaluate** the PRD for missing use cases, edge cases, UI/UX gaps
4. **Update** the PRD with accepted findings
5. **Analyse** situations using the Sit/Beh behavioural framework
6. **Update** the PRD with product-led mechanisms from the analysis

## Skills

### prd-draft
Transforms unstructured product thinking into a structured PRD. Extracts problem signals, solution signals, user situations, and constraints from whatever input format you provide.

**Trigger phrases:** "draft a PRD", "turn this into a product doc", "here's my rough idea", "write a spec"

### prd-evaluate
Systematically reviews a PRD across 12 evaluation categories to find missing use cases, implicit assumptions, edge cases, and UI/UX gaps. Each finding comes with a severity rating and suggested text to add.

**Trigger phrases:** "evaluate my PRD", "find gaps", "what am I missing", "review my spec"

### sit-beh
Situation/Behaviour framework that grounds product design in real-life moments instead of abstract personas. Identifies target behaviours, uncovers barriers (don't know / don't want / can't), and generates concrete product-led mechanisms.

**Trigger phrases:** "sit-beh analysis", "situation behaviour", "target behaviour", "behavioural barriers"

## Usage

### Full pipeline
Provide your messy input and ask to "draft a PRD". After the draft, say "evaluate" to run gap analysis, then "sit-beh" for behavioural analysis. Each step enriches the PRD.

### Individual skills
Each skill works independently. You can run prd-evaluate on any existing PRD, or do a sit-beh analysis on any product description.

## Output

- PRD saved as `PRD-[feature-name].md` in the working directory
- Sit/Beh framework saved in `.sitbeh/` directory for future reference
