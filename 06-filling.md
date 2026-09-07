# Filling — how this skill grows

## Shape

How {{PROJECT}}-uiux goes from freshly materialized to filled, and how it stays
true.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-14 | A section is filled when there is something real to decide. An unfilled marker is honest; an invented paragraph is not. | constitutional | `gate:uiux-unfilled` |
| UIX-15 | A visual or verbal decision made during a task lands here in the same change, not only in the component. | constitutional | `manual` |

**Day one — two sections, in this order:**

```text
1. 01-brand.md      tokens, both schemes
2. 03-copy.md       tone, casing, the state patterns
```

Those two are what every screen touches. `02-layout.md` fills when the second
surface disagrees with the first. `04-components.md` fills as concepts appear.
`05-assets.md` fills with the first design.

**The trigger is always a task:**

| The task | Fills or updates |
|---|---|
| introduces a colour, size or spacing | the token table, or uses the existing token |
| writes an empty, error or denied state | the copy pattern, if the shape is new |
| picks a primitive for a new concept | a row in `04-components.md` |
| receives a design | a row in `05-assets.md`, plus the export |
| gets a visual decision answered by a person | the section that owns it |

The last row is the loop with `turystack-proof-mode`: an answer that stays in the
conversation gets asked again, and answered slightly differently.

**Keeping the assets honest.** Exports go stale quietly. Two habits are enough:
re-export when the frame changes rather than when someone notices, and keep the
date column truthful — an old date is information, a wrong one is a trap.

**Updating the shape.** The Shape halves came from `@turystack/uiux-template`.
This skill does not update itself; it was materialized once and belongs to
{{PROJECT}}. Pull a new section in by hand, and only if it earns its place.

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** Nothing project-specific is required here — it is about
> process. Replace this block with {{PROJECT}}'s own conventions (who approves a
> token change, where designs are reviewed), or delete the marker to declare
> that the defaults above are the process.

## Never do

- Filling a section with a plausible guess to remove the marker (`UIX-14`).
- Deciding a colour or a phrasing in a component and leaving this skill
  unchanged (`UIX-15`).
- Letting the assets index describe exports that no longer match the design.
