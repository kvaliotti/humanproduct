# Expert Panel Review

A design system fails differently for different people. A rubric score can look fine while the system is
quietly hostile to an engineer, illegible to a low-vision user, or off-brand to an art director. The
**expert panel** is an adversarial gate: five specialists each review the system through one lens, each
can raise a **blocking objection**, and the panel only "passes" a system (or a proposed change) when
every lens is satisfied or its objection is consciously accepted with a reason.

**How to run it.** For a normal review, role-play all five inline — one short pass each, in the voice of
the specialist, ending in a verdict. For a large or high-stakes system, dispatch the five as parallel
subagents (one `Task` each, given the `DESIGN.md` + the rubric) and synthesize their verdicts; this keeps
each lens independent and uncolored by the others. Either way, **every panelist must name at least one
concrete thing to fix or explicitly say "nothing blocking, here's the one thing I'd watch."** Vague
approval is not a verdict.

---

## The five lenses

### 1. The Art Director (brand & visual voice)
*Cares about:* does the system have a **point of view**, and is it held consistently?
- Is there a single distinctive signature move (Stripe's gradient mesh, Binance's yellow voltage, IBM's
  thin-300 display + square chrome), and does it appear everywhere it should?
- Is the accent rationed so it still lands, or diluted into decoration?
- Do color + type + shape + space add up to *one* voice, or a mood-board of borrowed parts?
- **Blocks when:** the system is generic/voiceless, or the signature is applied on some surfaces and
  abandoned on others. **Watches for:** an "optimize" pass that sands off the very thing that made it distinct.

### 2. The Design-Systems Architect (tokens & structure)
*Cares about:* is this a **system** or a **pile**?
- Role-based token names, regular scales, variants-as-entries, prose↔token lockstep.
- Redundant/near-duplicate tokens; orphan tokens; one-off values that escaped the scale.
- Is state modeled once and reused, or reinvented per component?
- **Blocks when:** tokens are literal-named, scales have holes, or the same value is hardcoded in five
  places. **Watches for:** premature abstraction — tokens invented for values used once.

### 3. The Accessibility Specialist (perception & operability)
*Cares about:* can **everyone** read and operate it? Runs `references/accessibility.md`.
- Every text/background pair ≥ WCAG AA (4.5:1 body, 3:1 large). Report ratios, not vibes.
- Visible, sufficient focus states on every interactive element.
- Meaning never carried by color alone (dual-code green/red also needs an arrow/label/sign).
- Touch targets ≥ 44px (note domain exceptions like dense trading rows, but flag them).
- **Blocks when:** any body pair fails AA, or focus is invisible, or up/down is color-only. This is a
  hard block — see rubric gate G1.

### 4. The Frontend / DX Engineer (buildability)
*Cares about:* can I ship with this **without fighting it**?
- Do tokens map cleanly to my medium (CSS vars / Tailwind / Style Dictionary / CSS-in-JS)? See `references/codebase-bridge.md`.
- Can I guess the right token in seconds? Is component API consistent enough to build from?
- Are there enough states (disabled, focus, error) that I'm not inventing them per feature?
- **Blocks when:** the system would force inline styles / one-off values to get real work done, i.e. it
  isn't buildable as specified. **Watches for:** docs that describe an ideal the tokens can't actually express.

### 5. The Product / Interaction Designer (fit to real use)
*Cares about:* does the system serve the **actual product and its density**?
- Right density for the domain (dense dashboards vs airy marketing), right components for the real screens.
- Are the domain-specific components present (data tables, price cells, pricing tiers, empty/loading/error)?
- Do responsive + touch behaviors match how the product is actually used?
- **Blocks when:** the system is styled for a marketing page but the product is a data app (or vice
  versa), or core product states (empty/loading/error) are undocumented. **Watches for:** aesthetic
  choices that fail under real data volume.

---

## Panel verdict format

```
### Expert Panel
- 🎨 Art Director — <pass / block>: <one concrete point>
- 🧱 Systems Architect — <pass / block>: <one concrete point>
- ♿ Accessibility — <pass / block>: <ratios / focus / color-only findings>
- 🛠️ DX Engineer — <pass / block>: <one concrete point>
- 🧭 Product Designer — <pass / block>: <one concrete point>

**Panel outcome:** <PASS / PASS WITH WATCHES / BLOCKED>
**Blocking objections:** <list, or "none">
**Consciously accepted:** <objection + why, if any were overridden>
```

A single unresolved **block** means the outcome is BLOCKED — a design system, unlike an essay, has users
who cannot route around its defects. Accessibility blocks are never silently overridden.
