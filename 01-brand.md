# Brand — the token values

## Shape

The library declares which tokens exist; this section declares what they are
worth in {{PROJECT}}. It is the only place a project-specific visual value is
allowed to appear.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-4 | A token is named for its role, never its appearance: `primary`, `danger`, `muted` — never `blue`, `red-500`, `light-grey`. | constitutional | `gate:token-role-names` |
| UIX-5 | Every token has a value in both colour schemes. A token defined for one scheme only breaks in the other. | constitutional | `gate:token-scheme-parity` |

**What a filled brand section looks like:**

```markdown
### Colour
| Token | Light | Dark | Used for |
|---|---|---|---|
| primary | #2f4a7a | #8ba6dd | the main action, links, focus |
| danger | #a8322d | #e88b85 | destructive actions and errors |
| success | #1c7d54 | #5cc394 | confirmed outcomes |
| muted | #6d7783 | #8891a0 | secondary text |
| surface | #ffffff | #181c23 | cards, sheets, menus |

### Type
| Role | Family | Size | Weight |
|---|---|---|---|
| display | system serif | 2.1rem | 600 |
| body | system sans | 0.94rem | 400 |
| data | system mono | 0.78rem | 400 |

### Radius and elevation
| Token | Value | Used for |
|---|---|---|
| radius-sm | 4px | chips, inputs |
| radius-md | 10px | cards, sheets |
```

**Why role names, not appearance names.** `UIX-4` decides whether a rebrand is a
config change or a migration. A component styled with `danger` keeps working
when danger becomes orange; one styled with `red-500` has encoded a colour that
is now a lie, in every file that used it. Role names are also auditable — "does
anything use `success` for something that failed?" is a question you can ask.

**Both schemes, always.** `UIX-5` exists because the failure is invisible while
you build: whoever added the token was in light mode, and the missing dark value
fell back to something legible on their screen. Declaring both is the only way
the second scheme is a decision instead of an accident.

**Where these values end up.** The table is the decision; `07-theme.md` is the
file that carries it into the applications — one theme per design system,
overriding the library through the class each slot publishes.

**Before adding a token:**

```text
is there a token for this role already?   → use it
is this a one-screen exception?           → not a token; reconsider the design
would every product need it?              → it belongs to the library (UIX-2)
```

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** {{PROJECT}} has no token values. Any surface work stops
> here — a colour picked from a design file and pasted into a component is
> exactly what `UIX-1` forbids.
>
> Replace this block with the tables above, filled for {{PROJECT}}.

## Never do

- A token named after its colour or its shade number (`UIX-4`).
- A token with a value in one scheme only (`UIX-5`).
- A hex value in a component instead of a token (`UIX-1`).
- Adding a token to avoid a conversation about why one screen needs a colour
  nothing else uses.
