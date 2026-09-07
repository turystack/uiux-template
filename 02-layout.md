# Layout — shell, spacing and density

## Shape

The rhythm of {{PROJECT}}: which shells exist, what the spacing scale is, how
dense surfaces are, and where the breakpoints sit.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-6 | Spacing comes from the scale. A one-off value is a decision the scale should have made. | constitutional | `grit:no-literal-visual-value` |
| UIX-7 | Density is decided per surface kind, not per screen — every table in {{PROJECT}} is as dense as every other. | constitutional | `manual` |

**What a filled layout section looks like:**

```markdown
### Shells
| Shell | Used for | Contains |
|---|---|---|
| default | every authenticated page | sidebar, header with breadcrumbs, content |
| auth | sign-in, recovery | centred card, no navigation |

### Spacing scale
| Token | Value | Used between |
|---|---|---|
| xs | 4px | icon and its label |
| sm | 8px | fields in a group |
| md | 16px | sections of a form |
| lg | 24px | blocks of a page |

### Density
| Surface | Density | Why |
|---|---|---|
| table | compact | operators scan hundreds of rows |
| form | comfortable | one decision at a time |
| detail sheet | comfortable | reading, not scanning |

### Breakpoints
| Token | From | Changes |
|---|---|---|
| md | 768px | sidebar becomes a drawer |
| lg | 1024px | table shows the secondary columns |
```

**Why density is per surface kind.** `UIX-7` is what stops the product feeling
assembled by different people. Deciding it once per kind means a new table
inherits the answer instead of re-deriving it, and a reviewer can say "this is
denser than our tables" with something to point at.

**Breakpoints are tokens too.** A raw pixel value in a media query is the same
defect as a raw hex: it is a decision that exists in one file and nowhere else.

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** {{PROJECT}} has no shells, spacing scale, density or
> breakpoints written down. A surface built now will invent them, and the next
> one will invent them differently.
>
> Replace this block with the tables above.

## Never do

- A spacing value that is not on the scale (`UIX-6`).
- A raw pixel breakpoint in a component (`UIX-6`).
- Deciding density per screen (`UIX-7`).
- Describing how the layout primitive is implemented — that is the primitives
  skill.
