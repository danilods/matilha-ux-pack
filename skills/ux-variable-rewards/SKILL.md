---
name: ux-variable-rewards
description: Use when designing engagement mechanics — apply Hook Model reward types (tribe, hunt, self) with anti-dark-pattern ethics.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the product has an engagement loop and the team wants users to come
back without being forced. Fires when onboarding ends and retention becomes the
priority, when an existing loop feels flat or predictable, or when a feature is
being evaluated for the risk of tipping from "helpful pull" into "compulsive
loop." The skill shapes the reward layer so the variability drives return
visits without costing the user anything they didn't consent to.

## Preconditions

- A repeatable core action exists (post, lesson, workout, message) that the
  user performs more than once per week.
- The team can articulate what the user is supposed to gain from the habit —
  a real-world outcome, not "time spent in app."
- The instrumentation can distinguish healthy repeat use from compulsive
  return (session length, time-of-day clustering, self-reported regret).

## Execution Workflow

1. Use Read to map the current return-trigger surface: what currently brings
   the user back today? Notifications, streaks, social prompts, content
   drops. Note which triggers are internal (the user thinks of the product on
   their own) versus external (the product pings them).
2. Identify the core action. The reward will attach to this action, so it has
   to be the behavior the user is actually building — the lesson, the entry,
   the rep, the share. Avoid rewarding proxy actions like "opened the app."
3. Pick the reward palette. The Hook Model defines three families. Tribe
   rewards are social — recognition, validation, belonging. Hunt rewards are
   resource-oriented — new content to find, deals to chase, data to scan.
   Self rewards are intrinsic — a streak, a level, a finished lesson, a
   visible skill gain. A mature loop uses more than one, but not all three
   by default.
4. Design the variability. Predictable rewards lose grip quickly; the reward
   has to be slightly unpredictable to keep pulling. That doesn't mean
   random — it means the user can't perfectly forecast the next outcome.
   Duolingo's XP swings within a range, never a fixed number.
5. Check the ethical filter before shipping. Ask four questions, borrowed
   from the "time well spent" lens: does the user gain something real, can
   the user disengage without loss, are the mechanics disclosed or at least
   non-deceptive, and would the user approve of the loop if they saw it in
   slow motion. If the answer to any is uncertain, redesign.
6. Cap the loop. Compulsive loops have no off-switch. Responsible loops have
   explicit session limits, time-awareness nudges, or natural pauses (a
   lesson ends; a feed has a stopping point; a streak doesn't demand
   multiple sessions per day).
7. Use Edit to implement the chosen reward types, their variability ranges,
   and their caps. Instrument each one so the team can detect drift toward
   dark-pattern behavior post-launch.

## Rules: Do

- Attach rewards to the behavior you actually want (the lesson, the rep, the
  entry), not to opening the app.
- Introduce variability within a bounded range so each return feels slightly
  fresh without becoming a slot machine.
- Use at most two reward families for any single loop to keep the mechanic
  legible.
- Make the user's real-world gain visible — language learned, miles run,
  entries saved — so the loop rewards growth, not just presence.
- Build an explicit off-ramp: a natural pause, a session limit, or a quiet
  mode the user can reach without friction.

## Rules: Don't

- Don't turn the reward into pure hunt with no win state (endless feed,
  infinite scroll without any completion signal).
- Don't manufacture social reward where no real community exists — hollow
  tribe signals erode trust when users notice.
- Don't stack all three reward families on one loop; the result feels
  engineered rather than alive.
- Don't design variability that the user experiences as "the app is broken"
  — variability is in reward magnitude or type, not in whether the reward
  lands at all.
- Don't hide the mechanic. If explaining the loop to the user in plain
  language would embarrass the team, that's the sign to redesign.

## Expected Behavior

With the skill applied, the loop feels like a reason to return, not a tether.
Users talk about the product in terms of what they're getting — a language,
a habit, a practice — rather than in terms of the app itself. Session length
stabilizes rather than creeping upward; return frequency rises; self-reported
satisfaction tracks with observed use. If the team looks at the loop and asks
"is this still healthy," the answer comes from the instrumented caps and
from qualitative signals, not from hope.

When the reward scheme is off — too predictable, too extractive, or too
opaque — the symptoms are specific. Predictable rewards show as steadily
declining engagement per session. Extractive rewards show as long tails of
heavy users who also report regret. Opaque mechanics show as press articles
the team didn't want.

## Quality Gates

- Each reward in the loop attaches to the user's core action, not a proxy.
- Variability exists but is bounded; the user cannot be "punished" by
  variability (no-reward outcomes).
- No more than two reward families operate in a single loop without explicit
  justification.
- The user's real-world gain from the loop can be stated in one sentence.
- An off-ramp (pause, cap, quiet mode) exists and is reachable in two taps.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when engagement mechanics surface. Does not delegate to other
packs in v0.1.0. Pairs with `ux-dopamine-design` (variability and anticipation
share the same neural substrate), `ux-intrinsic-motivation` (self-rewards
should map to SDT's competence), and `ux-flow-state-design` (an in-session
loop should respect flow, not interrupt it).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: attaching reward to the real behavior, offering an
  off-ramp.
- Use "should" for: bounding variability, limiting to two reward families,
  stating the user's gain.
- Use "may" for: the specific mix of tribe / hunt / self appropriate to the
  domain.

## Troubleshooting

- **"Engagement is high but NPS is dropping"**: the loop is extracting more
  than it gives. Audit the user's real-world gain; if you can't name it,
  the reward is a tether, not a pull.
- **"Retention plateaued after week two"**: rewards are too predictable.
  Introduce bounded variability in magnitude or type without making outcomes
  feel random.
- **"Power users describe the loop as addictive"**: that's data, not praise.
  Tighten the cap, add an opt-in quiet mode, and check session-length
  distributions for a long tail that needs attention.
- **"Users ignore social reward features"**: the tribe doesn't exist or
  doesn't feel authentic. Either grow the community surface first or cut
  the feature; manufactured social proof corrodes trust.

## Concrete Example

A language app runs a daily-lesson loop. The reward layer combines three
elements. A leaderboard among friends signals tribe — the user sees peers
progressing, which pulls them back. The XP awarded per lesson swings within a
range rather than landing on a fixed number, providing hunt-style variability
without turning the lesson itself random. A visible streak and a growing
fluency score supply self rewards — the user can point at a number that
reflects actual language gain. The ethical filter holds: the user is learning
a language, can pause or freeze the streak, and the mechanics are disclosed.
Contrast this with an endless-scroll feed that rewards only the hunt of new
content with no win state, no user-visible gain, and no natural off-ramp.
Both loops run on the same neural machinery; only one of them leaves the user
better off when the session ends.

## Sources

- `[[concepts/hook-model]]`
- `[[concepts/dopamina-comportamento]]`
- `[[concepts/frameworks-comportamentais]]`
- Inspired by Nir Eyal's *Hooked* (2014) and its ethical counterweight
  *Indistractable* (2019), paraphrased further from Danilo's wiki synthesis
  of Schultz's prediction-error model and Tristan Harris's "time well spent"
  filter.
