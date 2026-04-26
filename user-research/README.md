# User Research Plugin

End-to-end user research workflow — from scoping to analysis to review. Each phase has a "build" skill and an "evaluate" skill, so every artifact gets stress-tested before moving to the next stage.

## Pipeline

```
Brief → Evaluate Brief → Guide → Evaluate Guide → Analyze → Review Analysis
  1          2              3          4              5           6
```

## Skills

| # | Skill | What it does |
|---|-------|-------------|
| 1 | **build-research-brief** | Build a structured research brief from a business problem. Guided or from inputs. |
| 2 | **evaluate-research-brief** | Score and stress-test a brief before fieldwork — fatal flaws, anti-patterns, Mom Test. |
| 3 | **build-research-guide** | Turn a brief into an interview guide with probes, dig triggers, and time allocations. |
| 4 | **evaluate-research-guide** | Score and stress-test a guide — question quality, structure, behavioral coverage. |
| 5 | **analyze-research** | Analyze transcripts/notes into coded findings, patterns, and recommendations. |
| 6 | **review-research-analysis** | Evaluate analysis quality — evidence backing, coding rigor, failure patterns. |

## Research Types

Every skill auto-detects the research type and loads the appropriate methodology:

- **General** — discovery, validation, evaluative, exploratory (The Mom Test, Deploy Empathy, Just Enough Research)
- **Behavioral** — adoption, engagement, retention, habit formation (COM-B, B=MAP / Fogg Behavior Design)
- **Mixed** — both frameworks applied, clearly separated

## Trigger Phrases

- "create a research brief", "plan my research", "I need to do user research"
- "evaluate my brief", "stress-test my research plan", "is my brief ready"
- "build an interview guide", "write a discussion guide", "prepare for fieldwork"
- "evaluate my guide", "check my interview questions", "is my guide ready"
- "analyze my interviews", "synthesize the research", "what did we learn"
- "review my analysis", "are my conclusions solid", "stress-test my findings"

## Setup

No external services or environment variables required. All skills work with local files.
