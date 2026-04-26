# Behavioral Research Brief Evaluation Reference

Synthesized from COM-B (Michie et al.) and B=MAP / Tiny Habits (Fogg).

Use this reference when evaluating briefs where the research goal is to drive, change, or sustain a specific user behavior — adoption, activation, engagement, retention, habit formation, feature usage, onboarding completion, conversion actions.

---

## Section A: Behavioral Problem Definition

| # | Criterion | What to check | Severity |
|---|---|---|---|
| A1 | **Problem stated as behavior** | Is the problem expressed as something people do/don't do — not as an attitude, feeling, or business metric? "Users don't complete onboarding" = behavior. "Users don't like our product" = attitude. "Conversion is low" = metric. | **Fatal** — rewrite before proceeding |
| A2 | **Behavior is observable** | Could a third party, in principle, observe whether the behavior occurred? If it's purely internal (e.g., "users don't understand"), it's a COM-B component, not the target behavior itself. | **Fatal** |
| A3 | **Causal logic explicit** | Is the chain from behavior → user outcome → business outcome stated? If the behavior changed, would the business problem actually improve? | **High** |

**Stop rule:** If A1 or A2 fails, stop evaluation. Rewrite the problem statement first.

---

## Section B: Target Behavior Selection

| # | Criterion | What to check |
|---|---|---|
| B1 | **Candidate behaviors listed** | Were multiple candidate behaviors considered, or did the brief jump to one? A single candidate = intuitive, not analytical. |
| B2 | **Selection criteria applied** | Were Impact, Likelihood of change, Spillover, and Measurability scored? Are scores justified with evidence or reasoning? |
| B3 | **Highest-impact behavior selected** | Does the selected behavior have the highest weighted score, or was a lower-scoring one chosen without justification? |

**Red flag:** No selection rationale (B2 missing) means the brief may be investigating the wrong behavior entirely.

---

## Section C: Behavioral Specification

| # | Element | What to check | Severity |
|---|---|---|---|
| C1 | **Who** | Target population precise enough to recruit? "Users" = too broad. "New users on mobile who signed up in the last 14 days" = specific. | **High** |
| C2 | **What** | Concrete action, not vague category? "Complete onboarding" > "engage with the product." | **High** |
| C3 | **When** | Time window or trigger moment defined? "During first session" = specific. "Eventually" = not. | **High** |
| C4 | **Where** | Physical/digital context stated? Platform, device, environment. | **Medium** |
| C5 | **How often** | Target frequency or completion threshold stated? | **Medium** |
| C6 | **With whom** | Other actors identified, or confirmed behavior is solo? | **Low** |

### B=MAP "Crispy" Test
- Is the behavior written in recipe format: "After [CONTEXT], user will [SPECIFIC ACTION]"?
- Can you physically demonstrate this behavior in under 30 seconds?
- If not, it's too abstract — the research will be unfocused.

**Red flag:** Any element scoring FAIL means the research team won't know what behavior to investigate in the field.

---

## Section D: COM-B Coverage of Research Questions

This is the most critical section. A research brief that doesn't systematically cover all COM-B components will produce research with blind spots.

| # | COM-B Component | What to check |
|---|---|---|
| D1 | **Physical Capability** | Questions about whether users can physically execute the behavior (motor skills, stamina, accessibility)? If purely digital, explicitly ruled out with reasoning? |
| D2 | **Psychological Capability** | Questions about knowledge, cognitive skills, memory, attention, decision-making, self-regulation? This is the most commonly under-specified component. |
| D3 | **Physical Opportunity** | Questions about environmental enablers/barriers — feature discoverability, time availability, tools, prompts, cues? |
| D4 | **Social Opportunity** | Questions about social norms, peer behavior, social pressure, cultural context, organizational expectations? |
| D5 | **Reflective Motivation** | Questions about beliefs, intentions, plans, identity, self-efficacy, perceived consequences? |
| D6 | **Automatic Motivation** | Questions about emotions, habits, impulses, desires? This is the second most commonly missed component. |

### D7: Balance Check
Are research questions evenly distributed across COM-B, or do they cluster in one area (usually Psychological Capability or Reflective Motivation)?

| Distribution | Rating |
|---|---|
| All 6 components have 2+ questions each | Strong |
| 5 of 6 components covered, one light | Adequate |
| Cluster in 2-3 components, others token | Weak |
| Research questions don't map to COM-B at all | Fail |

**Most common failure mode:** Over-indexing on "what users think and know" while ignoring environment and habit.

---

## Section E: B=MAP Decomposition Quality

### Motivation Assessment

| Check | What to look for | Red flag |
|---|---|---|
| **PAC sources identified** | Brief names whether motivation is Person, Action, or Context | Only mentions "users are motivated" without specifying source |
| **Competing motivations mapped** | Identifies what pushes users toward *different* behaviors | Assumes single, uncontested motivation |
| **Conflicting motivations mapped** | Captures opposing drives toward the *same* behavior | Ignores ambivalence |
| **Motivation durability assessed** | Distinguishes enduring aspirations from Motivation Waves | Treats temporary spike as stable |
| **Mom Test applied** | Distinguishes observed behavior from stated intent | Relies on "users told us they want X" without behavioral evidence |
| **Motivation not assumed as primary bottleneck** | Doesn't jump to "users aren't motivated enough" | Motivation treated as first/only lever |

### Ability Assessment

| Check | What to look for | Red flag |
|---|---|---|
| **All 5 Ability Chain links evaluated** | Time, Money, Physical effort, Mental energy, Routine fit | Missing links (usually Routine fit) |
| **Weakest link identified** | Hypothesizes which factor is the bottleneck | Treats ability as single dimension ("it's hard") |
| **Discovery Question answered** | "What makes this behavior hard to do?" has a specific hypothesis | Generic "users find it difficult" |
| **Breakthrough Question explored** | Proposes how to make behavior easier: Skill up / Tools / Make tiny | No design direction |
| **Starter Step or Scaling Back considered** | Considers the tiniest version of the behavior | Only studies full-size behavior |
| **Compensatory relationship acknowledged** | Recognizes M and A trade off | Treats M and A as independent |

### Prompt Assessment

| Check | What to look for | Red flag |
|---|---|---|
| **Prompt type classified** | Person / Context / Action (Anchor) | Prompt not addressed at all |
| **Existing anchors identified** | Maps behaviors users already do that could serve as prompts | Assumes new prompt must be created from scratch |
| **Anchor matching criteria applied** | Location, Frequency, Theme/Purpose evaluated | Anchor is arbitrary |
| **Trailing Edge specified** | Precise end-moment of the anchor identified | Fuzzy anchor ("after lunch") |
| **No-prompt scenario considered** | Tests whether behavior simply isn't being prompted | Assumes users are prompted but choosing not to act |

---

## Section F: Research Design Alignment

| Check | What to look for | Red flag |
|---|---|---|
| **Troubleshooting order respected** | Research questions check Prompt first, then Ability, then Motivation last | Questions start with "why aren't users motivated?" |
| **Hypotheses are testable** | Each follows: "[BEHAVIOR] doesn't happen because [M/A/P component] is insufficient. We test by [method]." | Hypotheses are vague |
| **Segments defined by B=MAP profile** | Users grouped by their M/A/P configuration | Segments are purely demographic |
| **Action Line position hypothesized** | States whether users are above/below the line and why | No framework for interpreting findings |
| **Research questions map to M, A, P** | Every question tagged to a specific component | Questions are generic |
| **Aspiration→Behavior chain clear** | Path from user aspiration → outcome → specific behavior | Jumps to feature without connecting to aspiration |

---

## Section G: Methodological Soundness (Behavioral)

| # | Criterion | What to check |
|---|---|---|
| G1 | **Methods match COM-B components** | Are methods appropriate for the components they investigate? Surveys alone cannot reliably assess Automatic Motivation. |
| G2 | **Self-report triangulated** | If interviews/surveys are primary, is there a plan to triangulate with behavioral data (analytics, observation)? |
| G3 | **Competing behaviors identified** | Does the brief name what users currently do instead, and why (using COM-B)? |
| G4 | **No leading questions** | Do questions genuinely investigate barriers, or presuppose the answer? "Why don't users like feature X?" presupposes motivation problem. |

---

## Section H: Actionability

| # | Criterion | What to check |
|---|---|---|
| H1 | **Findings can map to intervention functions** | Can team translate findings into Education, Training, Persuasion, Environmental Restructuring, etc.? |
| H2 | **Success criteria defined** | "We'll know the brief is answered when we can fill in a COM-B diagnosis for the target behavior." |

---

## Common Behavioral Failure Patterns

| Pattern | Symptom | Fix |
|---|---|---|
| **Attitude masquerading as behavior** | Problem uses "think", "feel", "perceive", "like" | Rewrite as observable action |
| **COM-B tourism** | One question per component, all shallow | 2-3 questions per component, each probing different facet |
| **Motivation monopoly** | 80% of questions about beliefs and intentions | Add environment, habit, and capability questions |
| **Solution baked in** | Brief assumes the intervention ("test whether a tooltip helps") | Strip solution; investigate COM-B barrier first |
| **Who = everyone** | Target population is "our users" | Narrow to specific segment, journey stage, context |
| **Missing competing behaviors** | No analysis of what users do instead | Add competing behavior analysis with COM-B drivers |
| **The Motivation Trap** | Brief assumes primary question is "why aren't users motivated?" | Apply troubleshooting order: Prompt → Ability → Motivation |
| **The Aspiration Masquerade** | Target behavior is actually an aspiration/outcome | Apply "can you do it right now?" test |
| **The Monolithic User** | All users treated as having same B=MAP profile | Create B=MAP profile matrix by segment |
| **The Missing Prompt** | Motivation and ability discussed, but no trigger addressed | Add mandatory prompt section |
| **The Undifferentiated Difficulty** | Behavior is "hard" without specifying which Ability Chain link | Run Ability Chain assessment, identify weakest link |

---

## Scoring Dimensions (Behavioral)

| Dimension | Weight | What it measures |
|---|---|---|
| Problem Definition (A) | 15% | Behavior-stated, observable, causal logic |
| Target Behavior Selection (B) | 10% | Candidates listed, criteria applied, best selected |
| Behavioral Specification (C) | 15% | Who/What/When/Where/How often/With whom + crispy test |
| COM-B Coverage (D) | 20% | All 6 sub-components covered, balanced, no blind spots |
| B=MAP Decomposition (E) | 15% | Motivation PAC, Ability Chain, Prompt anchors |
| Research Design Alignment (F) | 15% | Troubleshooting order, testable hypotheses, B=MAP segmentation |
| Methods & Actionability (G+H) | 10% | Methods match components, self-report triangulated, intervention-mappable |
