# Product Archetypes & Complexity Calibration

**This is the file that stops the plugin from being wrong.** The single most common way to ruin a design
system is to judge, build, or "optimize" it against a generic ideal of *minimal* — and thereby strip out
complexity the product's domain legitimately requires, or bolt on complexity it will never use. Read this
**before** scoring (review), changing (optimize), or building (create) anything.

The method: (1) classify the archetype, (2) read off its **complexity budget**, (3) judge every piece of
complexity as **essential** (traceable to a real domain need — keep it) or **accidental** (redundant,
one-off, undocumented — remove it). Never confuse the two.

---

## Contents
- **The archetypes and their design fingerprints** — the 9 clusters + their complexity budgets
- **Essential vs. Accidental Complexity — the decision guide** — the tests for keep-vs-remove (the core)
- **Using the budget in each capability** — how review / optimize / create apply it

## The archetypes and their design fingerprints

Products cluster. Each cluster has a characteristic fingerprint and, crucially, a characteristic
**complexity budget** — the complexity that is *correct* for it. Real products blend clusters (a fintech
with a marketing site spans two); take the union of the relevant budgets.

### 1. Developer-tool / minimal
*Linear, Vercel, Notion, Raycast, Warp, Supabase, Sentry, PostHog*
- **Fingerprint:** one accent on a tight neutral ramp; near-black-not-pure-black; restrained type (often
  mid-weight 500 display, 2–3 weights); moderate rounded-rect buttons (*not* pills — Linear/Notion/Supabase
  explicitly reject pills); dark-native or dual; elevation-by-tone, minimal shadow.
- **Budget — essential:** a **mono family** for code/terminals; a 4-step dark surface ramp; a scoped
  functional palette if the product UI needs state-coding (Cursor's AI-timeline). **Not in budget:** wide
  semantic ramps on marketing, expressive multi-hue, heavy shadows, pills.

### 2. Financial / trading
*Binance, Coinbase, Kraken, Revolut, Wise, Mastercard*
- **Fingerprint:** dense; single strong accent rationed hard; **bold display weight** (700 — must compete
  with data); **dual color-coding** green-up/red-down; often a **dedicated numeric family or `tnum`**;
  **multi-surface theming** (dark trading/marketing + light transactional); small radii, flat color-block
  elevation; tight section padding (~80px).
- **Budget — essential (do NOT simplify away):** trading up/down tokens (signal-only, never a fill, always
  paired with an arrow/sign); a numeric treatment for money legibility; multi-theme where marketing and
  transactional surfaces genuinely differ; a fuller semantic ramp (Wise) for money-state clarity.
  **Accidental:** finite-pill values (90/100/999px) that a true `9999px` replaces; near-duplicate hairlines.
- **Why the complexity is essential:** a trader scans 40 assets in peripheral vision — up/down color and
  tabular digits are *core-task* infrastructure, not decoration. Removing them degrades the product.

### 3. Enterprise / systematic
*IBM (Carbon), MongoDB, HashiCorp, HP, Dell*
- **Fingerprint:** white surfaces + charcoal ink + one confident accent; **full semantic ramp**
  (success/warning/error/info); **inverse tokens** for dark bands; systematic evenly-stepped scales;
  thin-300 or mid-weight display; flat square-ish chrome (IBM 0px); dense-by-design (*"customers expect to
  see a lot on a page"*); governance matters.
- **Budget — essential:** the semantic ramp (enterprise breadth demands unambiguous states across many
  screens); inverse tokens; per-product identity hues when it's really a *suite* (HashiCorp's 7 — wayfinding,
  not vanity); documented governance/extension rules. **Accidental:** colors used once; scale holes.
- **Why essential:** breadth. An enterprise system spans hundreds of screens built by many teams — the
  semantic ramp and governance are what keep it coherent; a "minimal" version fractures immediately.

### 4. Consumer-brand / expressive
*Spotify, Airbnb, Nike, Pinterest, Uber, Starbucks*
- **Fingerprint:** brand voice over system rigor; photography-forward; multi-hue *voltage* (decorative, not
  data-coding); big display type; pill or icon-circle buttons; often light-only public web.
- **Budget — essential:** the brand palette as *punctuation* (removing a signature color changes
  personality); campaign display faces (Nike Futura @96px); generous or dense whitespace matched to the
  medium. **Accidental:** treating decorative color as if it were semantic; excess micro-roles.
- **Note:** here "many colors" is legitimate brand expression, not functional coding — but it is *not*
  essential complexity in the information-architecture sense; it can be rationalized without breaking a task.

### 5. AI-product
*Claude, Cursor, ElevenLabs, Mistral, x.ai, Together, Replicate, Runway, MiniMax, Cohere*
- **Fingerprint:** minimal + one distinctive accent + generous space; often a **serif display voice**
  (Claude, Mistral, ElevenLabs) as the signature; frequently a signature gradient/atmosphere; warm
  near-black or cream canvases; dark or dual.
- **Budget — essential:** the serif-display / sans-body split when it carries the brand voice (the contrast
  *is* the identity); a signature gradient (hero-scale, brand-critical); a scoped functional palette for
  agent/product state (Cursor). **Accidental:** a fourth family; timid half-committed gradients.

### 6. Creative / canvas tools
*Figma, Miro, Framer, Webflow, Airtable, Cal*
- **Fingerprint:** a multi-hue palette; pill/circle *or* tight-rectangle button vocabulary (mixed —
  Webflow is 4px, Airtable 12px, Figma pill); variable-weight single family flexing (Figma 320–540).
- **The important correction (don't overfit here):** it is tempting to call the many colors "functional
  object-coding" and therefore essential — but the corpus doesn't support that at face value. **None of the
  captured specs reach the actual in-app canvas** (no layer-panel / record / cell tokens anywhere); they are
  *marketing* surfaces. On those surfaces, Airtable/Figma/Framer color-blocking is explicitly *editorial
  brand-pacing*, not data-coding. Only **Miro** (tints "echo the live whiteboard sticky-note palette") and
  **Webflow** (5 category hues map 1:1 to real product categories) genuinely tie color to a taxonomy.
- **Budget — essential:** object-coding *only where color maps 1:1 to a taxonomy the user must distinguish
  at a glance* (Miro, Webflow, and the real in-app canvas the marketing specs don't show). A disciplined,
  bounded token set. **Accidental:** editorial color mistaken for semantic coding; Framer's 5px grid
  idiosyncrasy; face-count inflation.
- **The lesson:** the object-coding argument is real *in principle* for a canvas tool's in-app UI — but
  verify it against the actual surface. Marketing color voltage is personality (rationalizable), not a task
  (load-bearing). Don't grant essential status to color just because the product *category* sounds like it
  should have it.

### 7. Automotive / luxury
*BMW, BMW-M, Ferrari, Lamborghini, Tesla, Renault, Bugatti*
- **Fingerprint:** cinematic dark canvas (committed pure-black *or* warm-near-black, defended); brand-
  signature palettes (BMW-M tri-color; Ferrari red); editorial display type; 0px square precision chrome;
  photography/video hero-led; light-transactional track for configurators/pricing.
- **Budget — essential:** the signature brand palette (BMW-M's tri-color is identity, not decoration);
  the committed canvas value; dual dark-editorial + light-transactional tracks. **Accidental:** extra
  accents beyond the signature; drift in the canvas value.

### 8. Media / editorial
*The Verge, Wired*
- **Fingerprint:** bold expressive **very large** display type (The Verge Manuka never <60px), all-caps
  labels with open tracking (a signature); square corners (Wired "printed-magazine"); dark-native; editorial
  color used with attitude.
- **Budget — essential:** the oversized display face and all-caps label tracking (the editorial voice);
  a stated small-size contrast rule (The Verge's `#3cffd0` "vibrates under 16px" caution). **Accidental:**
  over-systematizing what is intentionally expressive.

### 9. Gaming
*PlayStation, Nintendo (2001)*
- **Fingerprint:** playful, high-energy; tier/badge color systems (PS Plus gold); heavy/outlined display
  (Nintendo 900); rationed roundness or chamfered plates; strong per-purpose color voices.
- **Budget — essential:** tier-scoped palettes (PS Plus gold *only* on PS Plus surfaces); the disciplined
  multi-voice color system (Nintendo's three warm hues each = exactly one job). **Accidental:** unrationed
  color energy.

---

## Essential vs. Accidental Complexity — the decision guide

For **every** piece of complexity, ask: *is this traceable to a real domain need?* Keep it if yes,
discipline-but-keep; remove it if no.

### Signals that complexity is ESSENTIAL (keep it — never "simplify" it away)
| Complexity | Essential when… | Examples |
|---|---|---|
| **Dual color-coding** (green/red up/down) | users make fast directional judgments at a glance | Binance, Coinbase trading cells |
| **A full semantic ramp** | the product spans many screens with validity/severity states | IBM, Wise, any app with forms/dashboards |
| **A second/third font family** | there is **code** (mono) or **money/data** (numeric cut), or a serif carries the brand voice | Vercel+Geist Mono, Binance+Plex, Claude+serif |
| **Multi-theme / inverse tokens** | marketing/product surfaces genuinely differ, or app needs light+dark | Binance dark-trade/light-transact, IBM inverse footer |
| **Many colors** | color maps **1:1 to a taxonomy the user must distinguish at a glance** — you can name the exact set it encodes | Miro sticky-notes, Webflow categories, HashiCorp 7 products, Cursor timeline (NOT editorial brand-voltage — see below) |
| **Dense mode / sub-44px targets** | data density is the product, and the row/cell is the effective target | Binance markets table, trading dashboards |
| **A committed non-obvious canvas / on-color** | it's a defended brand decision held everywhere | Revolut pure-black, Binance black-on-yellow |

**The test for all of the above:** would removing it degrade a real user *task* (not just personality)? If
yes → essential. Dual-coding, numeric type, taxonomy object-coding, semantic ramps, wayfinding hues all
pass this test *for their domains* — treat them as load-bearing. **Editorial "brand voltage" color
(Airtable's signature cards, Notion's tints) fails the test** — removing it changes personality, not a
task, so it's rationalizable, not essential. Category membership ("it's a canvas tool, so many colors must
be functional") is *not* evidence — verify against the actual surface.

**A note on multi-color specs and the "1:1 taxonomy" test:** the strongest way to tell functional coding
from decoration is to try to *name the taxonomy*. Miro → sticky-note colors; Webflow → design/animation/
SEO/hosting/ecommerce; HashiCorp → Terraform/Vault/Consul/…; Binance → up/down. If you can enumerate the
exact set the colors encode and a user would misclassify content without it, it's essential. If you can't,
it's brand personality.

### Signals that complexity is ACCIDENTAL (remove / consolidate it)
- **Near-duplicate tokens** — two inks a couple % apart (`ink-mute` vs `ink-mute-2`), two hairlines, two
  radii doing the same job.
- **One-off values** — a color/size/radius used once, off the scale; a value that escaped the token layer.
- **Face-count inflation** — a 4th typeface used for "rare editorial moments" (Warp); a serif that carries no
  brand voice.
- **Finite-pill drift** — 90/100/999px where a true `9999px` is identical and simpler.
- **A *silent* gap (not a stated policy)** — the subtle one. Many strong systems *declare* "no hover state,
  by policy" or "no third color" — a deliberate discipline. The bloat/weakness signal isn't the absence
  itself, it's the absence of a *stated rationale*: a component missing focus/error states with no rule,
  a color used once with no scope note. Absence-with-a-rule is discipline; absence-without-one is a hole.
- **Orphan / speculative components** — a component with no usage rule, no cited evidence, no state
  variants (in the corpus, auto-derived `ex-*` placeholder blocks with literal `TO_FILL` markers are the
  self-flagged version). Candidates for deletion or demotion to "illustrative only."
- **Thinness mistaken for restraint** — a sparse spec only reads as disciplined minimalism when paired with
  an explicit rationale. Kraken (a crypto exchange with *no* markets-table/price-cell/order-book and no
  stated reason) is thin, not minimal. Sparse-with-no-rule is just incomplete.
- **Ceremony without payoff** — a semantic ramp on a pure marketing page with no forms; a second theme the
  product never shows; governance process for a solo MVP.
- **Grid idiosyncrasy** — a 5px base (Framer) where 4/8 is the universal, guessable norm.

### The two-sided failure the plugin must avoid
- **Over-simplifying (the dangerous one):** stripping essential complexity because it "looks like a lot."
  Deleting trading up/down, collapsing a numeric family, dropping a semantic ramp, merging object-coding
  colors — each *breaks a task.* When in doubt whether something is essential, **ask the user**, don't assume.
- **Over-building:** adding a semantic ramp, a second theme, or a component library a small product will
  never use. Match the budget to the archetype and stage.

---

## Using the budget in each capability

- **Review:** name the archetype and write *"judged as a `<archetype>`, I expect `<its budget>`."* Score
  complexity as a gap (under-built) or bloat (over-built) only relative to that budget.
- **Optimize:** run the essential-vs-accidental test on every proposed removal; flag anything touching the
  "Keep" list; require sign-off before removing anything that might be essential.
- **Create:** pick the archetype first, write the complexity budget as an explicit contract, then build
  exactly to it — no more, no less.

**One sentence to carry everywhere:** *complexity is a cost the domain sometimes requires you to pay —
your job is to pay it exactly where it buys a real user task, and nowhere else.*
