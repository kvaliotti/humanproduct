---
name: plan-research
description: Plan a user research study and write its interview guide in one file. Pins down the decision the research informs, the riskiest assumptions, who to talk to, and interview questions about past behaviour (Mom Test style). Use when the user says "plan my research", "research brief", "interview guide", "discussion guide", "what should I ask users", "I want to interview customers", or needs to scope discovery, validation, or behaviour research before fieldwork.
argument-hint: "[what you want to learn, or the product decision you're facing]"
---

# Plan Research

## Orchestration

1. If the user hasn't said what decision the research informs or who they want to learn from, ask with AskUserQuestion. Ask at most 3 questions, then state any remaining assumptions and proceed.
2. Write `research/plan-<topic>.md`.
3. Finish with the file path and the 3 riskiest assumptions. Mention `/user-research:analyze-interviews` for after fieldwork.

## Plan

Produce these sections in this order:

1. **Decision:** what the team will do differently depending on the answer. One or two sentences.
2. **Riskiest assumptions:** 3 to 5 beliefs that would sink the plan if wrong, most dangerous first.
3. **Research questions:** at most 5, each tied to an assumption by number. These are what *we* want to learn, not what we ask.
4. **Target behaviour** (only if the study is about why people do or don't do something): "After [situation], [who] will [observable action]." List the likely barriers as don't know / can't / don't want.
5. **Who to talk to:** screening criteria defined by what people have done recently, not demographics or opinions. 5 to 8 people per segment. Where to find them.
6. **Interview guide:**
   - Opener: one line on why we're talking, with no pitch.
   - 8 to 12 questions, grouped under the research question they serve, ordered from broad context to specific episodes.
   - Under each question, 1 or 2 probes ("What happened next?", "What did that cost you?", "What did you try instead?").
   - Close: "Who else should I talk to?" and "Can I follow up?"
7. **Done when:** what we need to have heard, and from how many people, to answer each research question.

Rules:
- Ask about the past, not the future: "Tell me about the last time you…", never "Would you…" or "Do you think…".
- Don't mention our idea or product until the last few minutes, if at all.
- Every question must be able to change the decision. Cut the ones that can't.
- Include at least one question whose honest answer the team might not want to hear.
- No leading questions and no two questions in one sentence.
- If something can be learned from desk research or analytics, list it under **Before fieldwork** instead of asking it in an interview.
