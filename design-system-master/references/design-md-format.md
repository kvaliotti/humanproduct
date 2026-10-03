# The DESIGN.md Format

Every skill reads, writes, or refactors a `DESIGN.md`: YAML frontmatter holding the tokens and component
specs, plus a markdown body holding the intent and usage rules. It is the contract a stylesheet or token
pipeline is generated from, not a stylesheet. Keep it implementation-agnostic; `codebase-bridge.md`
handles the mapping to code. Worked examples: `${CLAUDE_PLUGIN_ROOT}/references/exemplars/`. Scaffold:
`${CLAUDE_PLUGIN_ROOT}/skills/create-design-system/assets/DESIGN.template.md`.

Tokens and prose must stay in lockstep: every token the prose names exists in frontmatter, and every
token is explained in the prose.

## Frontmatter

Top-level keys: `version`, `name`, `description` (one sentence of design DNA), then:

- `colors:` — flat map `token: "#hex"`. Name by **role**, not hue (`ink`, `canvas`, `hairline`, not
  `gray-900`). Usual families: accent (`primary`, `primary-active`, `primary-disabled`), ink ladder
  (`ink`, `ink-muted`, `ink-subtle`), surfaces (`canvas`, `surface-1`, `surface-2`), `hairline`,
  on-colors (`on-primary`, `on-dark`), semantic (`semantic-success|warning|error|info`) when warranted,
  domain (`trading-up`, `trading-down`) when the domain demands it, `inverse-*` for modes.
- `typography:` — `role: { fontFamily, fontSize, fontWeight, lineHeight, letterSpacing, fontFeature }`.
  Roles are semantic (`display-xl`, `heading-md`, `body-md`, `caption`, `button`, `number-md`), never
  sizes (`text-56`). `fontFeature` carries OpenType settings such as `tnum` or `ss01`.
- `rounded:` / `spacing:` — small ordered scales with named steps (`xs…xl`, `pill`; `xxs…section`).
- `components:` — flat specs whose fields reference tokens.

### Token references

Use `{group.token}` anywhere a value repeats: `{colors.primary}`, `{typography.body-md}`, `{rounded.md}`,
`{spacing.lg}`. Raw hex or px inside `components:` means the value escaped the token layer. The only
exception is component-local geometry that never repeats (e.g. `padding: 12px 24px`).

```yaml
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: 12px 24px
    height: 40px
  button-primary-active:    { backgroundColor: "{colors.primary-active}", textColor: "{colors.on-primary}" }
  button-primary-disabled:  { ... }
  button-secondary-on-dark: { ... }
```

**Variants and states are separate top-level entries, never nested objects.** Nested states hide
variants and drift out of sync; flat entries make the list a complete record of what exists and let each
pair be contrast-checked.

## Body sections

| Section | Must contain |
|---|---|
| **Overview** | One-paragraph thesis + Key Characteristics bullets; names the signature |
| **Colors** | Every token by role, with hex and usage (Brand · Surface · Text · Hairlines · Semantic · Domain) |
| **Typography** | Family strategy, a `role \| size \| weight \| line-height \| tracking \| use` table, open-source substitute |
| **Layout** | Base unit, spacing tokens, section and card padding norms, grid/container |
| **Elevation & Depth** | The one depth strategy, a level table, the focus-ring spec |
| **Shapes** | Radius scale and a radius-per-component table |
| **Components** | Prose spec per component, grouped by kind, including domain components |
| **Do's and Don'ts** | This system's guardrails: accent rationing, weight rule, domain-token discipline |
| **Responsive Behavior** | Breakpoint table, touch targets (note dense-mode exceptions) |
| **Iteration Guide** | How to extend without breaking it |
| **Known Gaps** | What is not specified yet |

Never omit Do's and Don'ts or Known Gaps: they are what keep contributors on-system.

## Validation

If available, run `npx @google/design.md lint DESIGN.md` after any edit. The linter checks form only;
contrast (`accessibility.md`) and prose/token lockstep still need checking by hand.
