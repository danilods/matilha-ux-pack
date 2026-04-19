---
name: ux-emotion-in-ui
description: Use when writing UI copy or making tonal choices — apply Plutchik's 7 universal emotions, voice/tone matrix, emotional state mapping.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the interface is about to speak to the user — microcopy,
notifications, empty states, success screens, error messages, confirmation
dialogs, celebration moments, offboarding flows. Fires when the product
voice feels inconsistent, when celebration moments land flat or errors feel
punishing, when a new surface needs copy and the team defaults to generic
helpful language, or when the voice-vs-tone distinction has never been made
explicit and the interface reads as monotone across emotional contexts. The
skill tunes what the product says to match what the user is likely feeling.

## Preconditions

- A product voice exists or can be articulated in a few adjectives; if
  the voice is genuinely undecided, that's a strategy step that happens
  before this skill.
- The surfaces where the user speaks to the product have been
  inventoried, so tone can be calibrated surface-by-surface.
- Analytics or research can connect a surface to the user's likely
  emotional state at that moment (first-visit curiosity, failure
  frustration, completion pride, offboarding grief).

## Execution Workflow

1. Use Read to inventory copy-bearing surfaces: empty states, onboarding
   greetings, confirmation prompts, error messages, success celebrations,
   cancellation flows. Note which ones currently read as identical in
   tone and which already adjust.
2. Map each surface to the user's likely emotional state. Onboarding
   sits near curiosity and hope; a failed payment sits near frustration
   and fear; a deleted repo sits near caution and some grief; a shipped
   feature sits near pride and joy. The list doesn't have to be
   exhaustive — anchor each surface to one or two primary emotions from
   the universal seven (joy, sadness, fear, anger, disgust, surprise,
   trust).
3. Separate voice from tone. Voice is the consistent personality — the
   product sounds like the same entity on every surface, whether the
   news is good or bad. Tone is how that personality adapts to the
   moment. GitHub's voice stays recognizable across "welcome to your
   first repo" and "are you sure you want to delete" — the tone shifts.
4. Write for acknowledgment before information on negative surfaces.
   Error and cancellation copy should first name the emotional state
   ("that didn't work," "we're sorry to see you go"), then explain,
   then offer a path forward. Launching straight into the technical
   detail reads as cold.
5. Design peak moments deliberately. The peak-end rule says users
   remember the intensity peak and the ending more than the middle. A
   shipped feature, a finished lesson, or a reached milestone is a
   chance to mark joy or pride in a way the user remembers. A default
   toast reading "done" wastes the moment.
6. Keep the seven emotions as a cross-cultural anchor. Ekman's universal
   set — joy, sadness, fear, anger, disgust, surprise, trust — maps
   reliably across cultures, so copy that targets one of these emotions
   travels better than copy that leans on cultural humor or idiom.
7. Use Edit to rewrite surfaces where tone is mismatched to state, mark
   peak moments with deliberate celebration copy, and keep the voice
   consistent across the set.

## Rules: Do

- Anchor each copy surface to the user's likely emotion at that moment,
  not to the team's default cheerfulness.
- Acknowledge the emotional state first on negative surfaces, then
  explain, then offer a path forward.
- Preserve one consistent voice across every surface; change tone, not
  personality.
- Treat peak moments (completion, success, milestone) as design
  opportunities — generic "done" copy squanders them.
- Use the seven universal emotions as the anchor set; they cross
  cultures where humor and idiom don't.

## Rules: Don't

- Don't use the same cheerful tone for a shipped feature and a failed
  payment; tone is the lever that adapts.
- Don't open error copy with the technical detail. "Database connection
  lost" without acknowledgment reads as hostile; "that didn't save —
  connection dropped" reads as human.
- Don't let voice drift across surfaces. A product that sounds casual on
  the homepage and clinical on the receipt feels like two products.
- Don't mock the user's emotional state. Humor at the wrong moment (a
  failed payment screen with a cartoon) reads as contempt.
- Don't rely on culture-specific humor or references for core surfaces
  that global users will see.

## Expected Behavior

With the skill applied, the interface feels like it speaks with a single
recognizable voice across every surface, and the tone shifts in ways the
user registers without noticing. Users describe the product as "well
written" or "careful with words" even when they can't point at specific
copy. Error surfaces feel handled rather than hostile; celebration
moments feel earned; cancellation flows leave the user with affection for
the product even after the exit. Reviews quote microcopy approvingly,
which is the purest signal that the words did their work.

When voice and tone are tangled or flat, the signals are specific. A
shipped-feature toast reading "saved" on its own reads as indifference —
the user wanted a moment of shared pride and got a log line. An error
opening with a stack trace reads as blame. A cancellation flow that
thanks the user perfunctorily reads as contempt once the team
realizes they aren't coming back.

## Quality Gates

- Voice adjectives can be named in three words and match every major
  surface; tone varies by context.
- Error and cancellation copy acknowledges the emotional state before
  explaining the technical reason.
- Peak moments (completion, success, milestone) have intentional copy,
  not defaults.
- Culture-specific humor and idiom are absent from core surfaces used by
  global audiences.
- The seven universal emotions cover the set of contexts addressed; no
  major surface is emotionally unmapped.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when copy or tonal decisions surface. Does not delegate
to other packs in v0.1.0. Pairs with `ux-trust-by-design` (the error
message is simultaneously a trust-repair action and a tonal one), and
with `ux-goal-gradient` (a completion celebration is where peak-end
meets visible progress).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: consistent voice across surfaces, acknowledgment
  before explanation on negative flows.
- Use "should" for: deliberate peak-moment copy, the seven-emotions
  anchor set.
- Use "may" for: the specific voice adjectives and tonal range
  appropriate to the brand.

## Troubleshooting

- **"Success toasts feel flat"**: they're landing on a peak moment with
  default copy. Rewrite to mark the achievement in the product voice —
  what did the user just accomplish, and why should they care?
- **"Error messages are accurate but users still seem angry"**: the
  copy opens with the technical cause. Rewrite to acknowledge first,
  explain second, offer a path third.
- **"Voice feels inconsistent across surfaces"**: tone is doing voice's
  job. Name the voice in three adjectives, audit each surface against
  them, and rewrite the outliers without losing tonal variation.
- **"Cancellation flow reads as cold"**: it's optimizing for efficiency,
  not affection. Name the emotion, offer a genuine goodbye, keep the
  exit easy; users who leave warmly return warmly.

## Concrete Example

GitHub's UI demonstrates voice-tone separation across two very different
surfaces. An empty repository greets the user with a light, encouraging
message that reads roughly as "your new repository is ready; here are
three things you can do next." The voice is confident and developer-
adjacent; the tone is hopeful. Deleting a repository shows a grave,
deliberate confirmation that names the repository by full path, warns
about irreversibility, and requires typing the repo name to confirm. The
voice is the same — confident, developer-adjacent, direct — but the tone
shifts to caution and weight. Both surfaces belong to the same product.
Neither surface is monotone, and neither is out of character. A product
that used the encouraging tone on the delete screen would feel reckless;
a product that used the grave tone on the empty-state would feel
oppressive. The voice holds; the tone adapts.

## Sources

- `[[concepts/emocoes-sentimentos]]`
- Inspired by *100 Things Every Designer Needs to Know About People*
  (2011, Susan Weinschenk) and Daniel Kahneman's peak-end rule (1993),
  paraphrased further from Danilo's wiki synthesis of Ekman's seven
  universal emotions and the anecdote-over-data finding on narrative
  persuasion.
