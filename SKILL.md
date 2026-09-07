---
name: "{{PROJECT}}-uiux"
description: "How {{PROJECT}} looks and sounds — its brand tokens, layout, spacing and density, copy and tone, which primitive expresses which product concept, and the design export a screen must match. Read it before building or changing any surface in {{PROJECT}}. Use it when choosing a component for a product concept, writing a label, placeholder, empty state, error or denial reason, deciding spacing, density or a breakpoint, adding a colour or a token, or pointing at the design for a screen. A design system's theme file — one per system, overriding the library through the class each slot publishes — is indexed in `07-theme.md`. A section still carrying the unfilled marker is a decision nobody has made — it stops the task and becomes a question for a person, never a guess. {{PROJECT}}-spec owns what the product does; turystack-frontend-pattern owns how a screen is wired and turystack-frontend-primitives-pattern owns how a primitive is built. This skill owns what they are worth in {{PROJECT}}."
---

# {{PROJECT}}-uiux

Everything {{PROJECT}} decided about **how it looks and sounds**. This skill is
the project's own; it was materialized from `@turystack/uiux-template` and it is
yours to fill and keep — including its images.

## How this skill works

Each section has two halves:

```text
Shape        what this document must decide, and what a good answer looks like.
             Comes from the template. Leave it.

{{PROJECT}}  your content — tokens, words, densities, design exports.
             Starts unfilled. You replace the marker.
```

```markdown
<!-- turystack:unfilled -->
```

The marker is machine-readable. `turystack-proof` reads it, so "there is no
design for this screen" is a gate result rather than something discovered at
review.

## The line against the library

```text
the component library owns   what is true for every Turystack product:
                             a button has a variant, spacing comes from a scale,
                             className is not a prop

this skill owns              what is true for {{PROJECT}}:
                             what `primary` is worth, how dense tables are,
                             whether it says "workspace" or "team"
```

Mixing them produces the two failure modes that kill design systems:
per-product values baked into the library, and library grammar re-litigated per
product.

## Routing

| You need | Read |
|---|---|
| A colour, type scale, radius, elevation — the token values | `01-brand.md` |
| Shell, spacing, density, breakpoints, touch targets | `02-layout.md` |
| Tone, casing, labels, empty states, errors, denial reasons | `03-copy.md` |
| Which primitive expresses which product concept | `04-components.md` |
| The design export for a surface, and its version | `05-assets.md` |
| The theme file a system overrides the library with | `07-theme.md` |
| How to fill a section, and how assets are kept | `06-filling.md` |

## Before you ship a surface

1. **Design.** Did you open the export for this surface, and is it current?
   (`UIX-9`)
2. **Tokens.** Is every colour, size and spacing a token, with no literal value
   introduced? (`UIX-1`)
3. **Copy.** Does every string follow the casing and tone rules, and use the
   glossary's word from `{{PROJECT}}-spec`? (`UIX-5`)
4. **States.** Do the empty, error and denied states have real copy rather than
   a placeholder sentence? (`UIX-6`)
5. **Component choice.** Was the primitive chosen by product concept rather than
   by what looked closest? (`UIX-8`)

## Ownership rule

This skill answers **how {{PROJECT}} looks and sounds**. `{{PROJECT}}-spec`
answers **what it does**. `turystack-frontend-primitives-pattern` answers **how
a primitive is built**. `turystack-frontend-pattern` answers **how a screen is
wired**. A value that would be the same in every product belongs to the library,
not here.
