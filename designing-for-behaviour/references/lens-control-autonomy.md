# Lens: Control & Autonomy

**Source:** *Making Sense of Behavior* (William T. Powers, Perceptual Control Theory). This lens flips the frame the other three share. They ask "how do we get the user to do X?" This one asks **"what is the user trying to make true, can they see the gap, can they close it, and does the product help without fighting their other goals?"**

People act to keep a perception matching what they want to be true. Actions vary; the controlled outcome stays stable. A product that pushes behaviour against what the user is controlling creates resistance and churn even when every loop and nudge is well built. This lens catches failures the other three can't see, and it is the anti-manipulation backbone behind the ethics gate.

## 1. What the user controls *(behaviour)*

- Can the team say what the user is trying to make true here (what "done / safe / better" looks like **to the user**), not just what action the company wants?
- Is the new behaviour mapped onto a goal the user already has, rather than a company goal imposed on them?
- Can users set or confirm what "good enough" means, rather than having goalposts moved for them?
- Does the product measure whether the user reached the outcome, not whether they performed the expected action?

## 2. Feedback on the right variable *(behaviour, engagement)*

Users can only control what they can perceive.

- Is the variable the user cares about made visible, with feedback on **that**, not a proxy metric dressed up as their goal?
- Can the user tell whether they are closer or farther, and when they've arrived?
- Do statuses and "success" states mean to users what the team thinks they mean?

## 3. Disturbances *(behaviour, adoption, engagement)*

Anything that pushes the outcome off target: interruptions, fatigue, ambiguity, fear, time pressure, competing priorities.

- Are the main disturbances identified from the user's side, and does the product keep the outcome stable despite them (fallbacks, pause without losing progress)?
- Does it tell "the user lacks intent" apart from "the user's control was blocked"? Measure where users lose control, not only where they drop off.
- **Is the product itself a disturbance?** Notifications, prompts, or constraints that interrupt a more important user goal to serve a product metric.

## 4. Many paths to the same outcome *(engagement, adoption)*

- Can different users, or the same user in different contexts, reach the outcome by different routes? Or is one "correct" path over-scripted?
- Can experts skip unnecessary steps, and can novices drop the scaffolding once they've outgrown it?
- Does the team confuse compliance (same action repeated) with control (stable outcome)?

## 5. Goal conflict *(behaviour, engagement)*

Friction is often a higher-level conflict, not a usability bug.

- Is the immediate action tied to the user's higher-level goal, never optimised against it?
- Are procrastination, hesitation, and repeated failed attempts treated as possible conflict signals, not laziness? What is the user protecting by not acting?
- When stuck, can the user "go up a level" (reframe, pause, choose a different path) instead of being pushed harder on the same action?
- Is conflict fixed where it is caused, not patched with a UI tweak?

## 6. Product–user conflict and incentives *(behaviour, engagement)*

- **Incentive test:** would the user still act without the reward? Does the reward require deprivation first? If removing it collapses the behaviour, the core behaviour may lack real value.
- Does the product create dependence by cutting off the user's other ways of meeting the need?
- Is resistance treated as information, not an objection to overpower?
- Check existing mechanics against the dark-pattern list in `${CLAUDE_PLUGIN_ROOT}/references/ethics-and-dark-patterns.md` and flag matches by name.

## 7. Why users return or leave *(engagement, adoption)*

- Do users return because the product helps them control something they care about, not because of streak anxiety or engineered unresolved loops?
- Which disengagement is it? **Goal reached** (sometimes healthy churn), **goal hopeless** (too hard), or **the product creates more trouble than it removes** (a net disturbance). Each needs a different response; none is fixed by withholding what the user needs.
- Does the product fit the user's existing goals and workflow, and would they feel a real loss if it disappeared, rather than feeling trapped?
