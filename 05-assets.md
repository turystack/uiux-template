# Assets — the design a surface must match

## Shape

Where {{PROJECT}}'s design exports live, how they are named, and how a surface
is tied to the picture it has to match. The delivery report shows the two side
by side, so this is evidence infrastructure, not a filing convention.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-12 | Every surface with a design has an export in `assets/`, named after the surface, with a recorded version. | constitutional | `gate:design-export` |
| UIX-13 | The editable source and the export are both recorded; a picture nobody can regenerate is a picture that goes stale silently. | constitutional | `manual` |
| UIX-16 | A design carries its requirements as `UX-DR-n` — what the picture obliges, in words a test can cite. A screenshot alone says what it looks like, never what it must do. | constitutional | `gate:design-requirement-ids` |

## What a design obliges

A picture is not a requirement. Two people look at the same export and one of
them ships a toast where the other ships an inline message — both matching the
screenshot, only one matching the intent.

So an export ships with the obligations it carries, each with an id:

```markdown
### Orders table — cancel action
Export: assets/orders-table-cancel.png (2026-08-12)
Source: Figma › Orders / Cancel (frame 4:812)

| UX-DR | Requirement |
|---|---|
| UX-DR-1 | The action sits in the row, not behind a kebab — it is the primary operator task on this screen |
| UX-DR-2 | Denial reads inline, beside the action; never a toast, which leaves nothing to re-read |
| UX-DR-3 | The confirmation lists the released shipments by name, not a count |
| UX-DR-4 | Empty renders the "no orders yet" state, not a zero-row table |
```

The ids are the point. A request arrives in someone's own words — *"o cancelar
tem que ficar visível na linha"* — and `turystack-proof-mode` resolves it to
the surface and the `UX-DR-n` it satisfies. From there the delivery report can
put the export beside the shipped screen **and** say which obligations were
checked, instead of asking a reader to compare two pictures and trust their
eyes.

`UX-DR-4` is the kind that only exists because someone wrote it down: an empty
table and an empty state look identical in a screenshot of the happy path.

**Layout:**

```text
{{PROJECT}}-uiux/
├── 05-assets.md              this file: the index
└── assets/
    ├── orders-table.png      one export per surface
    ├── orders-table@denied.png
    ├── order-detail.png
    └── ...
```

**What a filled index looks like:**

```markdown
| Surface | Route | Export | Source | Exported |
|---|---|---|---|---|
| Orders table | `/orders` | `assets/orders-table.png` | Figma › Orders › Table v4 | 2026-08-12 |
| Orders table, denied | `/orders` | `assets/orders-table@denied.png` | same frame, Denied variant | 2026-08-12 |
| Order detail sheet | `/orders?resourceId=` | `assets/order-detail.png` | Figma › Orders › Detail v2 | 2026-08-12 |
```

**Why the state variants are listed separately.** The delivery report requires
captures for `success`, `empty` and `denied`. A design that only ever exported
the populated state leaves two of the three with nothing to compare against —
and those two are where `ARC-ERR-8` and `ARC-ERR-9` live. Exporting them is a
design task, and listing them here is what makes it visible before
implementation, not after.

**Why the source and the date.** `UIX-13` exists because a PNG is a snapshot. Six
months later the only questions that matter are "is this current?" and "where do
I change it?", and a file alone answers neither.

**When there is no design.** That is not a blocker for every task — plenty of
work has no visual surface. It is a blocker for **this** surface: the report
will show a missing capture and the `visual` rung fails. The right move is to
ask for the export, not to build something and call it the design.

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** {{PROJECT}} has no design index. Any surface built now
> has nothing to be compared against in the delivery report.
>
> Replace this block with the table above, and put the exports in `assets/`.

## Never do

- Building a surface from a screenshot pasted in a conversation (`UIX-12`).
- An export with no recorded source or date (`UIX-13`).
- Exporting only the populated state.
- Treating "no design yet" as permission to invent one.
