---
name: design-system-master
description: |
  Entry point and router for all design-system work. Use whenever the user wants to work on a design
  system as a whole and it isn't obvious which action they need — e.g. "look at my design system", "help
  with our design tokens", "our UI feels inconsistent", "sort out our colors and typography", "set up a
  design system", "is our design system any good", or they point at a DESIGN.md / codebase / Figma
  export. Decides whether they need to REVIEW (audit quality), OPTIMIZE (improve an existing system,
  including inside a codebase), or CREATE (build one from scratch), then routes. Calibrates to the
  product's archetype instead of forcing generic minimalism. Keywords: design system, design tokens,
  design audit, design review, color system, typography scale, spacing, theming, dark mode, component
  library, brand consistency, DESIGN.md.
user-invocable: true
argument-hint: "[review|optimize|create] [path to DESIGN.md / codebase / or a description]"
---

# Design System Master

Work out which job the user needs and what input they have, then hand off.

## 1. Classify the intent

| The user wants to… | Skill |
|---|---|
| Judge how good a system is ("review", "audit", "is it any good") | `review-design-system` |
| Improve a system or apply it to a codebase ("clean up", "make consistent", "roll out", "add dark mode") | `optimize-design-system` |
| Build a new system ("from scratch", "we have nothing", "define our tokens") | `create-design-system` |

"Review and fix" → review first, then offer optimize. You can't improve a system until you know what to
keep. An explicit `review` / `optimize` / `create` first argument overrides this.

## 2. Identify the input

- **A `DESIGN.md`** → read it directly. Format: `${CLAUDE_PLUGIN_ROOT}/references/design-md-format.md`.
- **A codebase** → the system is implicit in CSS vars, Tailwind config, tokens.json, or repeated literals.
  Extract it with `${CLAUDE_PLUGIN_ROOT}/references/codebase-bridge.md`.
- **Screenshots / a live product / Figma** → capture the observable tokens first.
- **Nothing yet** → create.

Say what you detected in one line ("Tailwind config plus a lot of inline hex — I'll extract the de-facto
system first") so the user can correct you early.

## The one rule

Calibrate to the archetype; never impose generic minimalism. Read
`${CLAUDE_PLUGIN_ROOT}/references/archetypes.md` before judging, building, or changing anything. Remove
only **accidental** complexity (redundant tokens, one-off values, undocumented states). Keep **essential**
complexity the domain needs (dual-coded green/red, a numeric font, multi-surface theming, a semantic ramp).

## Small questions

"What's a good spacing scale?" or "Is #767676 on white accessible?" → answer from the relevant reference.
Don't run a full review.
