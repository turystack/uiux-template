# @turystack/uiux-template

Template for a project's own **UI/UX skill** — brand tokens, layout and density, copy and tone, concept-to-primitive mapping, and the design exports a surface must match. Materialized once per project as `<project>-uiux` and owned by that project from then on, images included.

## Installation

```bash
pnpm add -D @turystack/uiux-template
turystack skills --claude --skills uiux --project acme
```

That materializes `.claude/skills/acme-uiux/`, substituting the project's name
and creating `assets/`. It is **never overwritten** by a later install.

## Contents

- [Overview](00-overview.md)
- [Brand — the token values](01-brand.md)
- [Layout — shell, spacing and density](02-layout.md)
- [Copy — how the product speaks](03-copy.md)
- [Components — which primitive expresses which concept](04-components.md)
- [Assets — the design a surface must match](05-assets.md)
- [Filling — how this skill grows](06-filling.md)
- [Theme — the file that makes the library look like the project](07-theme.md)
- [Skill manifest](SKILL.md)

## How a section works

Each one has a **Shape** half (from this template, kept) and a **project** half
(starts with `<!-- turystack:unfilled -->`). The marker is machine-readable, so
"there is no design for this screen" is a gate result rather than something
discovered at review.

## Documentation

**https://tury.dev/libs/uiux-template**
