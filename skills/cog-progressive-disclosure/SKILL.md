---
name: cog-progressive-disclosure
description: Use when users face information overload — reveal content level-by-level, hide detail until requested.
category: cog
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a surface carries both common needs and advanced options, and the
advanced options are crowding out the common path. Fires when a single screen
tries to serve both novices and power users equally, when a form has optional
fields that most users skip, when documentation mixes tutorial with reference,
or when users report a screen as "a lot" even though individual items are
reasonable.

## Preconditions

- A distinction exists between a common path (what most users do) and an
  advanced path (what a minority of users do, perhaps often).
- Shrinking the common path to core actions is technically possible without
  hiding required inputs.
- The advanced surface can be revealed on demand (link, accordion, modal,
  secondary page) without breaking flow.

## Execution Workflow

1. Use Read to list every element on the crowded surface and classify each
   one: essential to the common task, advanced but frequently used, advanced
   and rare, legacy or historical.
2. Compute the common path. The default visible surface should contain only
   the essentials — the fewest elements that let the user finish the primary
   task.
3. Decide the disclosure mechanism for each hidden tier. Options include a
   collapsible section, a secondary page, a modal, an "Advanced" toggle, a
   help-text drawer, or a link to a reference doc. Match the mechanism to
   how often the content is needed and how destructive returning to it is.
4. Preserve information scent. The disclosure trigger must telegraph what
   lies beneath. "Advanced options" is acceptable; "More" is often too
   vague; "Show billing address if different from shipping" is ideal because
   it names the content and the condition.
5. Never hide something the user cannot complete the task without. Critical
   information has no disclosure tier — if it's mandatory, surface it.
6. Avoid using disclosure as a mask for clutter. If the advanced tier is
   itself overwhelming, the right fix is to cut, not to nest deeper.
7. Accept the click cost. Users will happily take several obvious clicks over
   one confusing screen, because each click carries near-zero cognitive cost
   while parsing a crowded layout carries a high one.
8. Use Edit to collapse, link out, or stage the advanced content, and verify
   the common task can be completed without opening any disclosure tier.

## Rules: Do

- Default to the minimum viable common path; treat the visible screen as
  precious real estate.
- Label disclosure triggers with content and condition, not with "More" or
  an empty caret.
- Tier the disclosure: primary screen, one-click reveal, then deeper detail
  if needed.
- Preserve state when a user opens and closes a disclosure so they don't
  redo entries.
- Measure which disclosures users open; the answer informs whether a tier
  should be promoted or collapsed further.

## Rules: Don't

- Don't hide anything the user must complete to finish the task.
- Don't bury critical safety information (data deletion, billing changes,
  destructive actions) behind a disclosure tier without explicit visible
  warnings.
- Don't use disclosure to mask a fundamentally overwhelming advanced tier —
  reduce it first, then disclose.
- Don't chain more than two or three disclosure levels; each level doubles
  the cost of finding the thing.
- Don't rely on hover-only reveals on touch surfaces.

## Expected Behavior

The surface feels calmer. Novice users see only what they need and finish
the primary task without noticing the advanced machinery. Power users find
the advanced surface in one predictable place — behind a labeled trigger —
and work with full power when they want it. The interface stops feeling like
a compromise between the two audiences and starts feeling correctly shaped
for both.

Teams also find it easier to add features without cluttering. New options
can live inside the advanced tier without crowding the common path, which
removes the pressure to either punt features or overload the main screen.

## Quality Gates

- The common task completes without opening any disclosure tier.
- Every disclosure trigger names the content it reveals, not a generic
  "More" or caret.
- No required field or critical warning hides below a disclosure threshold.
- Disclosure chains are at most two to three levels deep from the primary
  surface.
- The primary surface passes a squint test: the eye lands on the essential
  controls first, not on "advanced options" affordances.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs
in v0.1.0. Pairs with `cog-cognitive-load` (disclosure is the primary fix
for too-many-items screens) and `ux-visual-hierarchy` (the common-path
essentials still need clear rank among themselves).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: no hidden required fields, named disclosure triggers.
- Use "should" for: two-to-three-tier depth limit, state preservation
  across open/close.
- Use "may" for: specific disclosure mechanism (accordion vs. modal vs.
  link) based on content and context.

## Troubleshooting

- **"Advanced users complain the tool feels dumbed down"**: The disclosure
  trigger is probably invisible or mislabeled. Make the advanced affordance
  visible and name it clearly; power users will open it once and remember.
- **"New users still feel overwhelmed"**: The common path itself is probably
  too wide. Count the visible controls — if it's above roughly four to seven
  with grouping, push more to the advanced tier.
- **"Form loses data when users toggle advanced"**: State isn't preserved.
  Persist the values regardless of visibility and only submit the ones the
  user explicitly filled in.
- **"Users never find the advanced tier"**: Information scent is weak.
  Rename the trigger to describe the specific content ("Custom date range"
  rather than "Advanced").

## Concrete Example

A checkout form presents, on a single screen, fields for card number, expiry,
CVV, postal code, promo code, billing address (which may differ from shipping),
VAT number, order notes, preferred delivery time, gift message, and a
newsletter opt-in. First-time buyers describe the form as "a lot" and
abandonment peaks before the first field is touched. Applying the skill, the
default surface shows only card number, expiry, CVV, and postal code — the
essentials for most transactions. A "Have a promo code?" link reveals the
promo field inline. A "Different billing address?" toggle reveals the billing
block. An "Add a note, gift message, or delivery preference" disclosure
expands to a grouped advanced tier. Newsletter opt-in lives outside the
checkout, in the confirmation page. A novice completes checkout in four
visible fields; a power user still hits all nine-plus without losing any
capability. The screen now serves both audiences correctly.

## Sources

- `[[concepts/cognicao-pensamento]]`
- `[[concepts/leis-de-krug]]`
- `[[sources/nao-me-faca-pensar]]`
- Inspired by *Don't Make Me Think* (2005, Steve Krug) and Keller's ARCS
  model, paraphrased further from Danilo's wiki synthesis on click cost
  versus thinking cost and progressive-disclosure pattern fit.
