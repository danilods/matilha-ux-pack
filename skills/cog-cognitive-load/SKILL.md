---
name: cog-cognitive-load
description: Use when designing forms, menus, or information-dense UI — apply working memory 4±1 chunks, chunking strategies, and recognition over recall.
category: cog
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the interface asks the user to hold, compare, or recall information
across steps, fields, or screens. Fires for long forms, dense menus, multi-page
wizards, comparison tables, dashboards with many simultaneous metrics, or any
surface where users visibly hesitate, backtrack, or abandon. The skill trims
how much working memory the interface demands and replaces recall with
recognition wherever possible.

## Preconditions

- A concrete surface that asks the user to process multiple items at once
  exists (a form, a menu, a table, a step flow).
- The count of distinct items or fields the user must consider simultaneously
  is known or countable.
- The task's goal is understood, so "necessary complexity" (intrinsic load)
  can be separated from "accidental complexity" (extraneous load).

## Execution Workflow

1. Use Read to inventory the surface. Count the number of discrete items the
   user must hold in mind at once: form fields, menu options, dashboard cards,
   columns in a comparison table.
2. Classify load type for each item. Intrinsic load is the irreducible
   difficulty of the task (a tax form genuinely has many fields). Extraneous
   load is noise added by poor design (unclear labels, redundant fields,
   arbitrary ordering). Germane load is effort that helps the user build a
   lasting mental model. The skill attacks extraneous load first.
3. Apply the working-memory budget. Aim for roughly four items per visible
   group, recognizing that the historical "seven plus or minus two" is an
   overestimate from a throwaway 1956 remark; current consensus lands closer
   to four plus or minus one.
4. Chunk anything longer than that. Break long inputs into logical groups
   (phone number as area-prefix-line, not eleven unbroken digits), split
   forms into stages, and cluster menu items by category.
5. Convert recall into recognition wherever possible. Replace free-text inputs
   with dropdowns when the option set is known; offer autocomplete on typed
   fields with a known domain; surface recent or frequent choices rather than
   asking users to remember them.
6. Never demand information across screens without showing it. If step three
   needs a detail from step one, either display the detail, remind the user,
   or let them navigate back without losing state.
7. Re-order fields and options using primacy and recency. The first and last
   items in a list are remembered more reliably than the middle. Put anchor
   questions and critical confirmations at the extremes.
8. Use Edit to apply the chunking, relabeling, reordering, and dropdown
   conversions. Verify by counting — the squint-and-count test for each
   region should land at or under four distinct items.

## Rules: Do

- Limit visible sibling items to roughly four per group; use sub-groups or
  progressive disclosure when you exceed that.
- Chunk long sequences (numbers, codes, steps) into meaningful clusters.
- Prefer recognition (dropdowns, autocomplete, visible options) over recall
  (free-text answers to known-domain questions).
- Keep state visible across steps when a later step depends on an earlier
  answer.
- Place the most important items at the start or end of a list, not buried in
  the middle.

## Rules: Don't

- Don't justify a twelve-field single-page form with "the user already has
  all this information" — the issue is holding it in mind, not knowing it.
- Don't replace a recognition surface with a recall one for cosmetic reasons
  (for example, turning a dropdown into a styled text input).
- Don't require users to remember codes, IDs, or previous selections to
  complete a later step.
- Don't group items only by visual style while leaving them semantically
  arbitrary — grouping must match the user's mental model.
- Don't defer error-prone work to the user when the system has the data
  (pre-fill, auto-detect, suggest defaults that serve the user).

## Expected Behavior

With the skill applied, forms feel lighter, menus feel navigable, and
dashboards feel readable without effort. Users complete multi-step flows
without backtracking to "check what I put earlier." Completion rates rise,
error rates fall, and subjective reports shift from "this is a lot" to
"this was quick."

The interface also becomes more forgiving. Because it shows options rather
than demanding recall, users who return after a long pause can pick up where
they left off without needing to rebuild context. Support tickets about "I
don't know what to put here" quiet down, because the input surface itself
answers the question.

## Quality Gates

- No single visible group contains more than roughly four distinct items
  without sub-grouping.
- Long numeric or alphanumeric inputs are chunked into readable clusters.
- Known-domain questions use recognition affordances (dropdown, autocomplete,
  chips) rather than free text.
- Multi-step flows show prior state on screens that depend on it.
- Key items sit at the start or end of lists; the middle holds filler, not
  anchors.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs in
v0.1.0. Hands off to `cog-progressive-disclosure` when the right fix is to
hide optional detail behind a revealer, and to `ux-visual-hierarchy` when the
real issue is rank, not item count.

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: four-or-fewer sibling items per visible group, recognition
  for known-domain inputs.
- Use "should" for: chunking long sequences, showing prior state in later
  steps.
- Use "may" for: specific chunk sizes within the four-plus-or-minus-one
  envelope, primacy-vs-recency ordering choices.

## Troubleshooting

- **"Users complete the form but fail at submit"**: Final-step errors usually
  come from fields buried in the middle. Move validation to the field that
  caused the failure or move the field to a more memorable position.
- **"Step three of a wizard shows high drop-off"**: Check whether step three
  demands recall from step one. If yes, surface the relevant answer on step
  three rather than forcing memory.
- **"Dropdowns have 80 options and scroll forever"**: A dropdown is
  recognition only for small sets. Convert to a searchable combobox with
  autocomplete, or introduce category grouping and a two-level selector.
- **"Users ignore help text and ask the same question in support"**: The help
  text competes with the field for attention. Move hints next to the field,
  not at the top of the form, and prefer inline examples to paragraphs.

## Concrete Example

A signup form asks nine fields in a single column: name, email, password,
confirm password, phone, date of birth, country, city, and postal code. The
user must hold each answered field in mind while scrolling; primacy anchors
name, recency anchors postal code, and the middle fields quietly erode
confidence that anything was answered correctly. Completion is at 58 percent,
with most abandonment happening around field six. Applying the skill, the
form splits into three steps. Step one collects identity (name, email,
password, with confirm password collapsed into a strength meter). Step two
collects contact (phone, date of birth). Step three collects location with a
country dropdown that auto-suggests city and postal code based on selection,
turning two recall fields into recognition. Each step fits inside the
working-memory budget, and the form can show a progress indicator with
roughly a third completion per step. Completion climbs above 80 percent
without losing any of the original data.

## Sources

- `[[concepts/memoria-cognicao]]`
- `[[concepts/principios-cognitivos-produto]]`
- `[[analyses/matilha-ux-foundation]]`
- Inspired by *100 Things Every Designer Needs to Know About People* (2011,
  Susan Weinschenk) and Sweller's Cognitive Load Theory, paraphrased further
  from Danilo's wiki synthesis of Cowan's 4±1 correction and Mandler's
  recall-rate curve.
