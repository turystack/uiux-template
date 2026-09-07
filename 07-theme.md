# Theme — the file that makes the library look like {{PROJECT}}

## Shape

The component library ships {{PROJECT}}-agnostic. One file per design system
turns it into {{PROJECT}}, by overriding the class each slot publishes. It is
the only place a project-specific visual value exists, and it is the artifact
`01-brand.md`'s tokens become.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-17 | One theme file per design system, named after it, indexed here with the audiences it serves. Two audiences designed apart are never served by one merged theme. | constitutional | `gate:theme-per-system` |
| UIX-18 | A theme overrides through the class a slot publishes. A structural selector, an `!important`, or a component re-implemented in the application is a fork of the library wearing a theme's name. | constitutional | `gate:theme-override-shape` |
| UIX-19 | This skill holds the canonical theme; an application carries a copy, and the two are compared. A copy nobody compares is a copy that has already drifted. | constitutional | `gate:theme-in-sync` |
| UIX-20 | `theme/template.css` and `theme/example.css` are the skill's own reference files, never a design system this project has. A project's theme is named after its system. | constitutional | `gate:theme-per-system` |

**Layout:**

```text
{{PROJECT}}-uiux/
├── 07-theme.md            this file: the index and the rules
└── theme/
    ├── template.css       where a new system starts — copy, rename, fill
    ├── example.css        a worked one, for reading
    ├── example.html       the same components with and without it
    ├── internal.css       one design system — backoffice and admin
    └── product.css        another — the customer-facing app
```

`template.css` and `example.css` are reference, not identity: `UIX-20` keeps
them out of the index and out of the copy comparison, so a project that has not
written a theme yet is not told it has two. They are still held to `UIX-18` —
an example that breaks the rule it illustrates is worse than no example.

**What a filled index looks like:**

```markdown
| System | File | Audiences | Source | Consumed by |
|---|---|---|---|---|
| internal | `theme/internal.css` | backoffice, admin | Figma › Acme Internal | apps/backoffice, apps/admin |
| product | `theme/product.css` | customer | Figma › Acme Product | apps/web, apps/mobile |
```

**Reading it before writing it.** `theme/example.html` renders the same markup
twice — once as the library ships it, once with the example theme applied. Same
classes, same `data-slot`s, one stylesheet of difference. It is the cheapest way
to see what a theme is allowed to be, and it is also the cheapest way to catch a
theme that is quietly re-implementing a component.

**The three layers of an override**, in the order they are reached for:

```css
/* 1 — tokens. A rebrand is this layer and nothing else. */
:root {
  --primary: oklch(0.42 0.09 258);
  --radius: 0.5rem;
}

/* 2 — a slot, when the design differs in shape and not only in colour. */
.button {
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

/* 3 — a slot in a state or a variant the design treats differently. */
.button[data-variant="destructive"] {
  border-color: var(--destructive);
}
```

Resolving at layer 1 and stopping is the whole discipline. Descending when
layer 1 would have done it is what turns a theme into a second implementation
of the library, maintained by whoever noticed last.

**Why by slot and not by structure.** Every component publishes a class and a
`data-slot` for each of its parts; those are its public surface, and they are
kept stable on purpose. A selector that reaches through the markup instead —
`.card > div > span` — binds {{PROJECT}} to an internal arrangement the library
is free to change in a patch release, and it breaks silently when it does.

`!important` is the same defect with a shorter spelling: it wins the argument
this time and hides which rule was actually wrong.

**When the slot does not exist.** The library is still growing into this, and a
component with no published slot cannot be themed. That is a gap in the library
— a task to add the slot, before the surface that needs it — never a structural
selector added here to get around it. `turystack-frontend-primitives-pattern`
owns how that slot is added.

**Where the file lives, and why there are two copies.** The canonical theme is
here, in this skill, because it is a design decision and it is reviewed with the
other design decisions. An application needs the file in its own build, so it
carries a copy — one file, imported once, at the application's style entry.

`UIX-19` is what keeps the two honest: they are compared, and a difference is a
finding rather than a discovery. In a monorepo the comparison is a check; when
the applications live in other repositories, it is a copy with a version, and
the version is recorded in the index above.

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** {{PROJECT}} has no theme. Every surface built now
> renders in the library's own appearance, and the first person to notice will
> fix it in a component.
>
> Replace this block with the index table above, and put the files in `theme/`.

## Never do

- One theme serving two design systems (`UIX-17`).
- Naming a project's theme `template.css` or `example.css`, so the index and
  the copy comparison skip the one thing that matters (`UIX-20`).
- A selector that reaches through a component's internals (`UIX-18`).
- `!important` anywhere in a theme (`UIX-18`).
- Re-implementing a library component in the application to get the design
  (`UIX-18`).
- An application copy that nothing compares against this skill's (`UIX-19`).
- A literal colour in a component because the theme was inconvenient to open
  (`UIX-1`).
