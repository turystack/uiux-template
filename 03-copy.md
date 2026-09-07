# Copy — how {{PROJECT}} speaks

## Shape

Every user-visible string: labels, buttons, placeholders, empty states, errors
and denial reasons. Words are design material, and this is where {{PROJECT}}
decides its own.

| ID | Law | Class | Gate |
|---|---|---|---|
| UIX-8 | Copy uses the term from `{{PROJECT}}-spec` › glossary. A synonym that reads better on one screen is a second name for one concept. | constitutional | `manual` |
| UIX-9 | Every empty, error and denied state has real copy: what happened, and what to do now. A placeholder sentence is an unwritten state. | constitutional | `manual` |

**What a filled copy section looks like:**

```markdown
### Tone
Direct, second person, no apologies. "Cancel order", not "You may cancel this
order if you wish".

### Casing
| Element | Casing | Example |
|---|---|---|
| button | sentence, verb first | "Cancel order" |
| page title | sentence | "Orders" |
| column header | sentence | "Placed at" |
| label | sentence | "Refund reason" |

### Patterns
| Situation | Shape | Example |
|---|---|---|
| empty list | what is missing + the next action | "No orders yet. Orders appear here once a customer checks out." |
| filtered empty | says it is the filter | "No orders match these filters. Clear filters" |
| denied action | what is missing, from the catalogue | "You need the Cancel orders permission." |
| denied surface | what and who to ask | "You do not have access to reports. Ask an administrator for Read reports." |
| destructive confirm | names the blast radius | "Cancel order #1042? This also releases 3 shipments." |
| API error | the message as it came | rendered verbatim — never rewritten |
```

**Why the API error is rendered as it came.** The backend already produced the
final text and owns the catalogue; rewriting it in the client creates a second
message for one code, and the two drift. `turystack-frontend-pattern` › `11-error-handling.md` owns that law; this
section is where {{PROJECT}} agrees to it in its own voice.

**Why denial copy is a pattern and not a sentence per screen.** `ARC-ERR-9`
requires a blocked action to stay visible with its reason. If every screen
writes its own reason, half say "Not available" — which is `UIX-9`'s failure
case, a state that exists visually and says nothing.

## {{PROJECT}}

<!-- turystack:unfilled -->
> ⛔ **Not filled in.** {{PROJECT}} has no tone, casing or state copy. Any
> string written now is one person's guess at the product's voice.
>
> Replace this block with the tables above.

## Never do

- A word for a concept that is not the glossary's word (`UIX-8`).
- "Not available", "Something went wrong" or any reason that explains nothing
  (`UIX-9`).
- An empty state that looks like a loading state.
- Rewriting an API error message in the client.
- Putting the product's decision here — what an action does belongs to
  `{{PROJECT}}-spec`.
