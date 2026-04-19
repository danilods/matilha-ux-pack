---
name: cog-attention-capture
description: Use when designing CTAs or attention-critical UI elements — apply saliency, avoid banner blindness, respect 7-10 min attention caps.
category: cog
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a critical UI element has to win attention against a crowded surface
— a primary call to action, a required warning, a status change the user must
notice, a learning module the user must complete. Fires when users skip over
the element that was supposed to stop them, when alerts are being ignored,
when onboarding or tutorial flows run longer than the brain can sustain, or
when the page is cluttered enough that salience is accidentally distributed
across dozens of competing items.

## Preconditions

- A specific element is expected to capture attention (CTA, alert, progress
  step, notification).
- The surrounding elements can be inventoried for noise and competing
  salience.
- The length of the overall experience (onboarding, tutorial, form flow) is
  known, so the seven-to-ten-minute attention cap can be checked.

## Execution Workflow

1. Use Read to collect every element on the surface and score each one's
   salience: contrast against its surroundings, movement, size relative to
   neighbors, shape distinctiveness, proximity to the focal point.
2. Identify the element that must win attention. There should be one
   per surface, not a parade of equally loud candidates.
3. Apply salience deliberately. The attention-winning element should differ
   from its neighbors on at least two axes — for example, larger and with
   higher contrast, or animated and with distinctive shape.
4. Avoid banner blindness. If the element looks like an advertisement —
   rectangular, off to the side, heavy border, bright but generic — the user
   will filter it out before consciously registering it. Keep the style
   integrated with the rest of the interface.
5. Respect rarity. Signals that matter but occur rarely (safety warnings,
   end-of-flow errors) must look distinctly different from frequent signals
   (inline validation, tooltips). If everything gets the same alert shape,
   the rare ones are treated with the same indifference as the common ones.
6. Budget attention time. Sustained focus on a single topic holds for roughly
   seven to ten minutes before the brain needs novelty, a pause, or a format
   change. Any flow longer than that must include intentional breaks, chapter
   breaks, or rhythm shifts.
7. Reject the multitasking illusion. Humans serial-switch between tasks; they
   don't parallelize. A surface that expects the user to simultaneously watch
   a video, fill a form, and respond to a chat popup will fail all three.
8. Use Edit to boost the target element's salience, reduce the noise around
   it, split long flows into smaller sessions with explicit pauses, and
   differentiate rare-but-critical signals from routine ones.

## Rules: Do

- Make the attention target differ from neighbors on at least two signal
  axes (size, contrast, motion, color, shape).
- Keep critical elements stylistically integrated with the rest of the
  interface so users don't filter them as ads.
- Reserve a distinctive visual treatment for rare, high-stakes signals;
  don't dilute it on routine ones.
- Segment long flows into seven-to-ten-minute modules with clear pause
  points.
- Design for single-focus attention; assume the user will abandon parallel
  demands rather than multitask them.

## Rules: Don't

- Don't boost everything trying to make one thing stand out — salience is
  relative, and a loud page has no focal point.
- Don't place the attention target where users have learned ads or chrome
  live (far right rail, top banner) unless you accept banner blindness.
- Don't animate for decoration; reserve motion for moments where grabbing
  the eye is genuinely needed, because motion wins attention fast and tires
  it just as fast.
- Don't stack long tutorials into one uninterrupted session and assume the
  user will push through; their attention budget has a hard ceiling.
- Don't rely on sound alone for urgent signals in environments with
  background noise or muted devices.

## Expected Behavior

The target element gets noticed. Users complete primary calls to action at
higher rates, dismiss critical alerts intentionally instead of habitually,
and move through multi-step flows without dropping off at the ten-minute
mark. Rare warnings get the attention they deserve because the team stopped
using the same bright treatment for routine ones.

The page also feels calmer overall. Because only one element carries full
salience per view, the eye stops ping-ponging between competing flashes, and
cognitive load across the surface drops.

## Quality Gates

- Exactly one element per surface is tuned to win first attention.
- The target element differs from neighbors on at least two salience axes.
- Critical-but-rare signals have a visual treatment distinct from routine
  validation or inline feedback.
- No flow runs more than roughly ten minutes without a scheduled break,
  chapter boundary, or format shift.
- The page does not rely on hover, animation, or sound as the sole channel
  for any critical signal.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs
in v0.1.0. Pairs with `ux-visual-hierarchy` (hierarchy produces the focal
point that attention capture then amplifies) and `ux-flow-state-design`
(flow protects sustained attention; this skill protects acute attention).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: one attention target per surface, distinct treatment for
  critical rare signals.
- Use "should" for: ten-minute chunking of long flows, two-axis salience
  delta on the target.
- Use "may" for: specific salience axes (motion vs. color vs. size) based
  on context and accessibility constraints.

## Troubleshooting

- **"Users ignore the primary CTA even though it's big"**: Size alone isn't
  enough. Check whether the surrounding elements are equally loud or whether
  the CTA sits in a banner-shaped slot that triggers ad blindness. Move it
  inside the content flow and add a second salience axis.
- **"Warning banner appears every session and nobody reads it"**: Habituation
  killed it. Either reduce its frequency so it stays surprising, or change
  the treatment so the rare critical case looks different from the routine
  reminder.
- **"Onboarding shows strong drop-off around step nine"**: The flow likely
  crossed the ten-minute attention cap. Split the sequence into modules with
  explicit pause points and restart invitations.
- **"Animated element now dominates and other UI feels dead"**: Motion was
  the wrong amplifier. Replace with size and contrast, or reserve motion
  for the moment the target appears and let it rest afterwards.

## Concrete Example

A SaaS onboarding flow packs fifteen minutes of tutorial into a single
uninterrupted sequence: account setup, team invite, integration selection,
preference toggles, and a guided product tour. Completion data shows users
abandon steadily after about ten minutes, landing on roughly 38 percent.
Applying the skill, the flow is restructured into four modules of about three
minutes each, each ending on a small win (connection confirmed, first
teammate invited, preferences saved, first report generated). Between
modules, the user sees a short summary of progress and an explicit option to
pause and resume later, which the product remembers. Critical warnings that
previously shared visual style with routine tips are redrawn with a distinct
treatment used nowhere else. Completion rises to roughly 70 percent, and
users who return from a pause resume in the right module rather than
starting over. The content didn't shrink; the attention budget did.

## Sources

- `[[concepts/atencao-foco]]`
- Inspired by *100 Things Every Designer Needs to Know About People* (2011,
  Susan Weinschenk), paraphrased further from Danilo's wiki notes on
  attention caps, banner blindness, and the task-switching myth.
