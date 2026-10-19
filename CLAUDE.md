# AI Development Residency — Project Memory

This file is loaded automatically at the start of every Claude session in this
repository. It sets the standards Claude should hold all work in this repo to.

## Enterprise-readiness skills — apply these proactively

This project defines three skills in `.claude/skills/`. They encode the standards
that make software enterprise-ready. **Consult and apply the relevant skill on
every applicable task, without being asked** — treat them as the default quality
bar, not optional references.

- **`ux-design`** — apply to any user-facing work (screens, components, forms,
  flows, interface copy, design reviews). Enforces usability heuristics, complete
  interaction states, and clear copy.
- **`accessibility`** — apply to any markup, component, color, or interaction.
  Enforces WCAG 2.2 Level AA: semantic HTML, keyboard access, visible focus,
  color contrast, and text alternatives.
- **`security`** — apply to any code handling input, data, auth, secrets, or
  dependencies. Enforces secure-by-design practices and the OWASP Top 10:2025.

### How to apply them

1. At the start of a task, decide which of the three skills are relevant (often
   more than one — a new form involves all three).
2. Read the relevant `SKILL.md` and follow its guidance while building.
3. Before calling a piece of work done, run its "How to apply this in practice"
   checklist against what you produced.
4. When these standards would meaningfully change an approach, say so and explain
   which skill and principle drove the decision.

The point is consistency: the same high standards applied the same way every
time, so output is predictable and enterprise-ready by default.

## Repository conventions

- `skills/` — coding-challenge work for the residency.
- `.claude/skills/` — the Claude skills above (version-controlled, synced via
  GitHub).

## Working across machines

This repo is the source of truth, synced through GitHub. Pull before starting,
push when done: `git pull` → work → `git add .` → `git commit -m "..."` →
`git push`.
