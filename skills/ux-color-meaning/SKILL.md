---
name: ux-color-meaning
description: Use when picking colors for UI — apply cultural meaning, accessibility (colorblind, contrast), and emotional associations.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a color choice carries meaning — success versus failure, free tier
versus paid, primary versus destructive action, brand warmth versus brand
authority. Fires when a palette is being set, when color alone is being used
to encode information, when contrast has not been verified against WCAG
thresholds, or when the project ships to audiences with different cultural
color associations.

## Preconditions

- The palette is either being defined or revisited.
- The surfaces where color carries semantic weight (status, risk, category,
  tier) are identified.
- Text-on-color combinations that will occur are known or can be enumerated.
- The audience's dominant cultural context is known well enough to flag
  obvious mismatches (for example, red as celebration versus warning).

## Execution Workflow

1. Use Read to collect the current palette, any semantic tokens (success,
   warning, danger, info), and the combinations where text sits on colored
   backgrounds.
2. For each semantic role, state the meaning in words, not just the hex. Every
   color token must answer "what is this color for?" before it gets shipped.
3. Verify WCAG contrast. Normal text needs at least 4.5 to 1 for AA; large
   text (18pt or 14pt bold) can relax to 3 to 1; AAA pushes to 7 to 1. Use a
   contrast checker or inline script rather than eyeballing.
4. Add redundancy for any color-coded information. Pair color with at least
   one of: a text label, an icon, a shape, a position, or a pattern. Assume
   some viewers won't perceive the color at all.
5. Simulate colorblind perception. Roughly eight to nine percent of men and
   about half a percent of women have a form of color-vision deficiency. Run
   a protanopia and deuteranopia filter (Sim Daltonism, Stark, or equivalent)
   and check that semantic pairs remain distinguishable.
6. Audit cultural associations. Red signals danger, loss, and urgency in most
   Western contexts but luck and celebration in many East Asian ones. Green
   is growth and go in the West but can read as sickness in some contexts.
   White is purity in some cultures and mourning in others. When the audience
   spans multiple contexts, lean on redundancy (icon, label) rather than
   picking one cultural reading.
7. Check emotional register. Saturated, warm hues pull attention and feel
   energetic, often younger; muted, desaturated palettes feel premium and
   quieter. Cool blues skew toward trust and finance; warm oranges and reds
   skew toward action and appetite. Match the register to the product promise.
8. Use Edit to adjust tokens, text pairings, and status components until the
   palette passes contrast, colorblind, redundancy, and cultural checks.

## Rules: Do

- Encode information with at least two channels — color plus label, icon,
  shape, or position.
- Check every text-on-color combination against WCAG AA at minimum.
- Run a colorblind simulation on any status pair (success/failure,
  selected/unselected, free/paid) before shipping.
- Document the semantic role of each color token in plain language, not only
  as a hex value.
- Match color temperature and saturation to the emotional promise of the
  product.

## Rules: Don't

- Don't encode status in color alone. Even "red means bad" fails for the
  colorblind viewer who sees it as a muddy brown.
- Don't assume a single cultural reading of red, white, or green — audit
  against the audience you actually ship to.
- Don't combine saturated red and saturated blue in adjacent text or icons;
  the eye cannot focus both wavelengths simultaneously (chromostereopsis)
  and the result fatigues viewers fast.
- Don't let visual polish override accessibility — if a brand hue fails
  contrast, fix the brand use in that context rather than the standard.
- Don't rely on hover or focus color shifts as the only affordance cue on
  touch surfaces where hover doesn't exist.

## Expected Behavior

With the skill applied, the palette communicates the same meaning across
sighted, colorblind, low-contrast, and cross-cultural viewers. Status shifts
read through at least two channels, so a user who can't see the color still
sees the change. Text meets contrast standards in every combination, which
removes a common accessibility lawsuit vector and also makes the product
usable for everyone with imperfect eyesight or imperfect screens.

The brand also feels deliberate. Because every token has a stated role, new
components slot into the palette without inventing ad-hoc hues, and
designers stop fighting about whether something should be "our blue" or
"that other blue."

## Quality Gates

- Every text-on-color combination meets WCAG AA contrast (4.5:1 normal,
  3:1 large), with AAA preferred where feasible.
- Every color-coded signal includes a second channel (label, icon, shape, or
  position).
- Colorblind simulation confirms semantic pairs remain distinguishable.
- Each semantic color token has a one-line description of what it means.
- No adjacent saturated red-and-blue text or icons appear.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs in
v0.1.0. Pairs with `ux-visual-hierarchy` (color is one of the four hierarchy
levers) and `ux-typography-for-reading` (contrast math covers text-on-color
for both skills).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: WCAG AA contrast on all text, redundant channel for every
  color-coded signal.
- Use "should" for: WCAG AAA where feasible, cultural-association review
  for audiences spanning more than one region.
- Use "may" for: specific hue picks within the temperature and saturation
  envelope.

## Troubleshooting

- **"Brand color fails contrast when used on body copy"**: Treat brand color
  as decorative and use an accessible neutral for body text. Reserve the
  brand hue for large type, icons, and accents where 3 to 1 is enough.
- **"Status colors look the same to colorblind testers"**: The palette almost
  certainly pairs red and green without shape or label redundancy. Add icons
  (check, warning triangle, x), shapes (filled vs. outlined), or text labels
  so the status survives grayscale.
- **"Palette passes all checks but feels wrong"**: Emotional register is off.
  A high-saturation palette on a premium finance product reads as playful; a
  muted palette on a youth app reads as tired. Adjust saturation and
  temperature until the register matches the promise.
- **"International users report the warning color feels wrong"**: You picked
  a culturally loaded hue without a redundant signal. Keep the hue if brand
  requires, but ensure the icon and text do the semantic work independently.

## Concrete Example

A pricing page labels three tiers — Free, Pro, and Enterprise — and uses color
alone to distinguish them: Free in gray, Pro in green, Enterprise in red.
Running a deuteranopia simulation reveals that Pro and Enterprise look nearly
identical. Meanwhile, users in a region where red signals celebration read
Enterprise as the "most attractive" tier rather than the "premium, approach
with care" tier the team intended. The fix adds icons (a sprout for Free, a
rocket for Pro, a shield for Enterprise), labels each tier's benefit
explicitly, and pushes Enterprise to a deep navy with generous whitespace so
it reads as quiet authority. Contrast of every plan name on its tier
background is verified at or above 4.5 to 1. The tiers now parse correctly
for colorblind users and across cultures, and sales reports stop asking why
Enterprise inquiries don't match the team's expectations.

## Sources

- `[[concepts/percepcao-visual]]`
- `[[sources/100-things-every-designer]]`
- `[[concepts/emocoes-sentimentos]]`
- Inspired by *100 Things Every Designer Needs to Know About People* (2011,
  Susan Weinschenk), with accessibility thresholds cross-referenced to
  WCAG and paraphrased from Danilo's wiki notes on color-vision deficiency
  and cultural color readings.
