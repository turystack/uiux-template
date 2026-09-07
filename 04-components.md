# Components — which primitive expresses which concept

## Shape

The library offers a vocabulary. This section records which word {{PROJECT}}
uses for which idea, so the same product concept looks the same everywhere.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-10 | A primitive is chosen by the product concept it expresses, never by which one looks closest to the mockup. | constitutional | `manual` |
| UIX-11 | A concept maps to exactly one primitive across {{PROJECT}}; a second mapping is a decision that was made twice. | constitutional | `manual` |

**What a filled components section looks like:**

```markdown
| Product concept | Primitive | Why, and when not |
|---|---|---|
| destructive confirmation | `Confirm` | always, including "are you sure" flows; never a hand-built Modal |
| a record opened from a list | `Sheet` (md) | keeps the list in context; a full route only when the record has its own sub-navigation |
| a blocked action | `Protected` wrapping the control | stays visible and inert with its reason (ARC-ERR-9) |
| a denied read surface | `Unavailable` in the content's place | never `null`, never a plain empty state |
| a filter over a list | `Toolbar` | bound to the route's search, never local state |
| a transient outcome | `Toast` | for results the user does not need to act on |
| a blocking outcome | inline feedback at the action | for anything requiring a decision |
```

**Why concept, not appearance.** `UIX-10` is the rule that keeps the product
coherent as it grows. Choosing by appearance produces three different
confirmations, because three mockups looked slightly different — and then a
change to how {{PROJECT}} confirms things has to be made in three places.

**The "when not" column** is what makes the table usable under pressure. A
mapping with no boundary gets applied to the case it was never meant for, and
nobody can argue against it because the table said so.

**Missing capability.** If the concept has no primitive that expresses it, that
is a gap to close in the library — a new prop or a new primitive — not a
parallel implementation in the app. `turystack-frontend-pattern` › `03-components-client-state.md` and
`turystack-frontend-primitives-pattern` › `07-consumption.md` own that rule.

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** {{PROJECT}} has no concept-to-primitive mapping. Each
> screen will pick by appearance, and the product will look assembled by
> different people.
>
> Replace this block with the table above.

## Never do

- Choosing a primitive because it resembles the mockup (`UIX-10`).
- Two primitives for one concept (`UIX-11`).
- A mapping with no "when not" boundary.
- Building a parallel component because the library's is missing a prop.
