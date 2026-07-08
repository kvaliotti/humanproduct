# Lens: Control & Autonomy

**Distilled from:** *Making Sense of Behavior* (Powers / Perceptual Control Theory). This lens flips the frame the other three share. They ask "how do we get the user to *do* X?" PCT asks "what is the user trying to *control*, and does the product help them do it?" It is also the plugin's **anti-manipulation backbone** — the theory behind the ethics gate — so it doubles as the check that behavioural machinery serves the user rather than working against them.

## What this lens sees

Behaviour is not a response to stimuli or a fixed script. A person acts to keep some **perception** matching an internal **reference state** — to close the gap between *what is* and *what they want to be true*. Actions vary; the controlled outcome stays stable. So the design question is not "what action do we trigger" but:

> **What is the user trying to make true, can they perceive the gap, can they act to close it, and does the product help — without fighting the user's other goals?**

A product that "causes behaviour" against what the user is controlling will generate resistance, conflict, and churn even when every loop and nudge is technically well-built. This lens catches the failures the other three are structurally blind to.

## 1. The controlled variable & reference state  *(behaviour)*

- Can the team state **what perception the user is trying to control** here (what "right / done / safe / better" looks like *to the user*), not just what action the company wants?
- Is the behaviour framed as **reducing a gap the user cares about** — current state vs. desired state — rather than as an isolated action to elicit?
- Does the product identify what the user is **already controlling** before trying to change anything, and map the new behaviour onto an existing user goal rather than imposing a company goal?
- Does it let users set/confirm/personalize their reference state (what "good enough" means), rather than imposing milestones and moving goalposts without consent?
- Does it measure whether the user achieved the **intended outcome**, not whether they performed the exact expected action?

## 2. Perception & feedback  *(behaviour, engagement)*

Users can only control what they can perceive. Check the feedback on the variable that matters:

- Is the variable the user is trying to control made **visible/legible**, and is feedback given on *that* variable — not a proxy metric presented as if it were the user's goal?
- Can the user tell whether they're **closer to or farther from** the desired state, and when they've reached it? Is feedback frequent, accurate, and specific enough to *correct*, not just evaluate?
- Do labels, statuses, progress states, and "success" states mean to the user what the team thinks they mean? (Don't assume everyone reads a screen the same way.)
- Does the product avoid inferring motivation only from clicks/time/completion, and validate what users *believe* they're doing?

## 3. Disturbances  *(behaviour, adoption, engagement)*

A disturbance is anything that pushes the user's controlled outcome off target — interruptions, fatigue, ambiguity, fear, social/time pressure, competing priorities, a changed environment:

- Has the team identified the main disturbances that break the target behaviour, **from the user's point of view**, and does the product help keep the outcome stable despite them (fallbacks, recovery flows, pause without losing progress, resume from the state the user cares about)?
- Does the product distinguish "the user lacks intent" from "the user's control was **blocked**"? Measure *where users lose control*, not only where they drop off.
- Does the product avoid being a disturbance **itself** — notifications, prompts, or constraints that interrupt a *more important* user goal to serve a product metric?

## 4. Action variability & autonomy  *(engagement, adoption)*

- Does the product allow **different users (and the same user in different contexts) to reach the same outcome via different actions** — or does it over-script one "correct" path?
- Does it distinguish necessary steps from optional means, let experts bypass unnecessary low-level steps, and give novices scaffolding without locking them into it forever?
- Does it measure **stability of the controlled outcome under changing conditions**, rather than treating "same action repeated" as the only sign of habit/engagement? (Repeated outcomes often require *varied* actions.)
- Autonomy rises when users choose the means: does the product avoid confusing **compliance** with successful control?

## 5. Hierarchy of control & conflict  *(behaviour, engagement)*

Goals are layered — immediate actions serve sequences, which serve workflows, which serve principles and identity. Friction is often a **higher-level conflict**, not a usability bug:

- Does the product connect the immediate action to the user's higher-level goal, and avoid optimizing a low-level action **against** a higher-level user goal?
- Does it detect **goal conflict** — the user wants two incompatible things — and treat procrastination, hesitation, avoidance, and repeated failed attempts as *possible conflict signals* rather than laziness? Does it investigate **what the user protects by not acting**?
- When a user is stuck, does the product let them **"go up a level"** — reframe, change the situation, pause, renegotiate, choose a different path — instead of pushing harder on the same action?
- Does it fix conflict at the level where it's *caused*, not paper over the symptom with a low-level UI tweak?

## 6. Product–user conflict & incentives  *(behaviour, engagement)* — *the anti-manipulation core*

The line between helping a user control their world and controlling the user against their goals:

- Does the product avoid **coercion, guilt, threat, embarrassment, and artificial scarcity** as behavioural engines? Does it respect the user's control system — explaining why an ask matters, offering alternatives when it conflicts with another goal, negotiating rather than dictating?
- **Incentive test:** treat rewards as *value exchange*, not control levers. Would the user still want to act **without** the incentive? Does the reward require the user to be *deprived* first (artificial scarcity to manufacture control)? Would removing the reward collapse the behaviour — and if so, is that because the core behaviour lacks real user value?
- Does the product avoid creating **dependence** by restricting the user's alternative ways of meeting their need?
- Does it treat **resistance as diagnostic** (what is the user trying to control by resisting?) rather than as an objection to overcome by escalating pressure?

## 7. Engagement & adoption *through* control  *(engagement, adoption)*

- Does the user return because the product helps them **control something they care about** — not because of streak anxiety, manufactured error, or unresolved loops engineered to force a re-open?
- Does the product recognise the real disengagement causes: **error is zero** (goal achieved — sometimes healthy churn, not failure), **error is hopeless** (too hard), or **the product creates more error than it removes** (it's a net disturbance)? Is there a strategy for each — and does it avoid boosting "engagement" by *withholding* what the user needs?
- Does adoption mean the product **fits the user's existing control hierarchy** — reducing switching cost through visible control gains, not demanding unnecessary identity change or workflow disruption — and would the user feel a **real loss** if it disappeared (vs. being trapped by friction)?
- Would the user **endorse the product's engagement pattern on reflection**, fully understanding how it works? (If not, it's manipulation — route to the ethics gate.)

## Relationship to the ethics gate

This lens *scores* how well the current experience respects user control and autonomy. The separate **ethics-and-dark-patterns** reference is applied later by the orchestrator to the *recommendations*, to ensure the fixes this and the other lenses propose don't themselves cross into manipulation. Flag anything you'd want that gate to catch.

## Not your lens

Loop mechanics (trigger/reward/investment) → **behavioural-loop**. Decision-point ergonomics/biases → **cognitive-ease**. Whether the user gets more *capable* → **capability-results**. Note cross-lens observations in one line; don't score them here.
