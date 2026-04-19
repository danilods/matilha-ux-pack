---
name: ux-visual-hierarchy
description: Use when laying out a page or screen — apply Gestalt laws, focal points, and saccade-aware scanning patterns to guide the user's eye.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a layout is being drafted or critiqued and every element is competing
for attention with equal weight. Fires when a screen has no obvious landing
spot for the eye, when Gestalt grouping is ambiguous, or when the visual flow
contradicts the reading order the user actually performs. The skill tightens
rank between elements, establishes one focal point per view, and aligns the
layout with how eyes actually travel across a surface.

## Preconditions

- A concrete layout exists (wireframe, markup, Figma frame, HTML preview).
- The layout's primary task is known (what the user should do on this screen).
- At least two candidate elements that could plausibly "win" the viewer's first
  glance have been identified.
- The target viewport and reading direction (LTR/RTL) are known.

## Execution Workflow

1. Use Read to inspect the layout source (HTML/JSX/Figma spec) and list the
   elements that would render above the fold.
2. For each element, record its weight signals: size, color contrast against
   background, surrounding whitespace, typographic rank, position relative to
   natural entry point.
3. Decide the focal point. There must be exactly one per view. Use Edit to
   amplify at least two weight signals on that element (for example, larger
   type plus stronger color contrast plus more whitespace around it).
4. Rank the remaining elements into a short list of secondary and tertiary
   groups. Adjust sizes, tones, and spacing so the ranking is readable at a
   squint — if you blur the layout mentally, the primary still dominates.
5. Apply Gestalt grouping deliberately. Related items sit closer; unrelated
   items get breathing room. Prefer whitespace over borders or boxes to create
   groups, because extra lines add noise without communicating structure.
6. Align the layout to the expected scanning pattern. Text-heavy pages usually
   scan in an F-pattern (horizontal header, horizontal secondary, vertical down
   the left). Visual or sparse pages scan in a Z-pattern. Put the decision and
   the call to action on the pattern's endpoints.
7. Check the periphery. The amygdala reacts to peripheral motion and shape
   roughly twice as fast as central vision. Avoid flashing or high-contrast
   elements in the corners unless they genuinely need that urgency.
8. Run a squint test or apply a blur filter and confirm the hierarchy still
   holds. If two elements compete at that resolution, reduce one.

## Rules: Do

- Pick one focal point per view and amplify at least two weight signals on it.
- Group related elements with whitespace before reaching for dividers.
- Let the scanning pattern (F for text, Z for visual) place the key action at a
  natural stopping point.
- Treat size, color, contrast, and whitespace as the four primary hierarchy
  levers — lean on the quieter ones before turning up saturation.
- Use a squint or blur check as a fast rank audit before shipping.

## Rules: Don't

- Don't make every element the same visual weight — absence of ranking is a
  ranking failure, not neutrality.
- Don't bury the primary action in the dead middle of a long column where the
  scanning pattern has already committed to the edges.
- Don't rely on borders or boxed containers to create groups when spacing
  alone would communicate the same relationship with less noise.
- Don't cluster attention-grabbing elements in the periphery if they aren't
  urgent — peripheral vision treats them as threat signals.
- Don't stack more than roughly four sibling groups per region; past that,
  Gestalt similarity breaks down and the eye starts skipping.

## Expected Behavior

After applying this skill, the layout has a clear first stop. A new viewer's
eye should land on the primary element within about a second and then follow a
predictable path through the secondary ranks. Grouping reads as intentional
rather than accidental, and related items no longer feel orphaned from their
labels, metadata, or actions. On interactive surfaces, the user knows where to
look before they know what to click, which cuts the cognitive tax of every
subsequent decision in the session.

The skill also produces a defensible explanation of the layout. Instead of "it
looks right," the author can articulate why the primary won, which Gestalt
principle binds each group, and which scanning pattern the flow assumes.

## Quality Gates

- Exactly one focal point exists per view, confirmed by a squint test.
- Groups are formed by whitespace first; borders appear only when grouping is
  otherwise ambiguous.
- The primary action sits on a natural endpoint of the chosen scanning pattern.
- No more than four sibling groups share a single region without sub-grouping.
- Peripheral elements are either intentionally urgent or intentionally quiet —
  never accidentally loud.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs in
v0.1.0. Pairs naturally with `ux-typography-for-reading` (once the hierarchy is
set, typography tunes the text ranks) and `cog-cognitive-load` (hierarchy is
the primary lever for lowering visual search cost).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: exactly one focal point per view, squint-test pass.
- Use "should" for: whitespace-first grouping, four-or-fewer sibling groups.
- Use "may" for: F-pattern vs. Z-pattern choice, specific contrast ratios
  beyond the WCAG baseline owned by `ux-color-meaning`.

## Troubleshooting

- **"Everything looks equally important"**: The author added weight to every
  element trying to signal importance. Remove signals from secondary items
  until only the primary carries full rank. Contrast is relative; making
  everything bold makes nothing bold.
- **"The layout has a focal point but users click elsewhere"**: The focal point
  and the primary action diverged. Either move the action to the focal point
  or make the action itself the focal point. Viewers trust attention, not
  labels.
- **"Groups feel cluttered even with whitespace"**: Similarity is competing
  with proximity. Check that grouped items share visual traits (color, type,
  shape) beyond just spatial nearness; without similarity, proximity reads as
  crowding rather than grouping.
- **"Eye hits a cold corner"**: An attention-grabbing element sits in the
  periphery without intent. Either quiet it (reduce contrast, drop motion) or
  commit to the urgency and pair it with a matching peripheral signal like an
  icon or short label.

## Concrete Example

A dashboard proposes eight equally-sized metric cards in a four-by-two grid.
Every card is the same hue, same typography, same border. Running the skill
reveals no focal point — the squint test shows a uniform mosaic. The fix
promotes one card to a hero tile roughly four times the area, with a stronger
typographic rank and a subtle tint. Three supporting cards shrink to half
height and keep their original treatment. The remaining four drop to a
tertiary row with muted type and no border, reading as a utility band rather
than first-class data. The primary KPI now wins the first fixation in under a
second; the three secondary metrics form an obvious comparison row; the
tertiary band is available without competing. Same eight numbers, materially
different cognitive cost.

## Sources

- `[[concepts/percepcao-visual]]`
- `[[sources/100-things-every-designer]]`
- `[[analyses/matilha-ux-foundation]]`
- Inspired by *100 Things Every Designer Needs to Know About People* (2011,
  Susan Weinschenk), with Gestalt framing traced to Wertheimer and
  hierarchy practice paraphrased from Danilo's wiki synthesis.
