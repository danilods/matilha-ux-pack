---
name: ux-dopamine-design
description: Use when designing habit or frequency features — apply dopamine release patterns, anticipation over reward, ethical guardrails.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the product is trying to establish a daily or near-daily habit —
health apps, meditation tools, journaling, language practice, habit trackers
— and the team is weighing how strong to make the pull. Fires when a feature
proposal includes streaks, daily cues, surprise reveals, or notifications,
and the team needs to decide whether the pull is serving the user or
extracting from them. The skill calibrates anticipation-driven design so the
neurochemistry works for the user, not against them.

## Preconditions

- The activity being habituated has plausible upside for the user's life
  (health, skill, connection, craft) — not just attention capture.
- The team understands that dopamine is a "wanting" signal, not a "pleasure"
  signal, and is willing to design accordingly.
- Session-length and return-cadence instrumentation exists or can be added,
  so creep toward compulsion is observable.

## Execution Workflow

1. Use Read to map the return-loop triggers. Which cues bring the user back
   today — a notification, a streak-at-risk, a surprise reveal, a time-of-day
   habit? Note whether each cue is internal (the user remembers on their own)
   or external (the product pings them).
2. Understand the neural grammar. Dopamine fires strongest at anticipation,
   not at the payoff. Brain scans show more activation while the user is
   about to pull the lever than when the reward lands. That means the design
   lever is the expectation window, not the reward magnitude itself.
3. Prefer variable reinforcement over fixed. Schultz's prediction-error work
   shows that predictable rewards habituate quickly — the nucleus accumbens
   stops responding once the pattern is learned. Variable reinforcement
   (within bounds) keeps the anticipation live.
4. Check the ethical filter. The same mechanism powers Headspace's 47-day
   meditation streak and a social feed's pull-to-refresh. The difference
   isn't the neurochemistry; it's whether the user ends the session better
   off. If you can't name the user's gain, the loop is extractive by
   default.
5. Build guardrails from the start. Session limits, time-of-day fencing,
   awareness nudges ("you've used this for 45 minutes"), and explicit
   opt-out of the habit mechanic all belong in the initial design. Adding
   them later is rarely politically possible.
6. Distinguish the two use cases. Anticipation-driven design is appropriate
   for health-habit formation where the user's baseline benefits from daily
   practice. It is not appropriate as the primary engine for ad-supported
   consumption loops, where the product benefits from compulsive use and
   the user does not.
7. Use Edit to shape the trigger cadence, variability bounds, and guardrail
   surfaces. Instrument session-length distributions to detect creep toward
   compulsive patterns post-launch.

## Rules: Do

- Design the anticipation window deliberately — a visible count-up, a
  scheduled reveal, a ritual cue — rather than leaving it accidental.
- Use bounded variable reinforcement so each return feels slightly fresh
  without becoming random.
- Build session limits and time-awareness nudges in from the start, not
  after PR problems surface.
- Tie the loop to an activity with real-life upside; name the user's
  concrete gain in one sentence.
- Instrument for compulsive-use signatures: long tails of daily session
  length, high return frequency with low self-reported satisfaction.

## Rules: Don't

- Don't borrow the dopamine mechanic from an addictive product and assume
  it will be safe in yours; the neural substrate is identical, only the
  ethics differ.
- Don't use streaks as punishment architecture — the loss-aversion edge of
  breaking a streak is powerful and can cross into cruelty if the stakes
  feel too high.
- Don't let variability become so wide that the user experiences the loop
  as a slot machine; bounded variability pulls, random outcomes corrode
  trust.
- Don't design an anticipation loop for ad-supported consumption as though
  it's the same as a health-habit loop — the user's interests diverge from
  the product's, and the ethics follow.
- Don't hide the mechanic. If the user would recoil seeing the internal
  model of how the loop works, redesign.

## Expected Behavior

With the skill applied, the product establishes a durable daily or
near-daily habit without the user feeling pulled against their will. Return
cadence rises; session lengths stabilize rather than creep upward;
self-reported satisfaction tracks observed use. Users describe the product
as "something I do" rather than "something that grabs me." If the team
inspects the long-tail session distribution, it doesn't fan out into a set
of heavy users who also report regret.

When the calibration is off, the signals are specific. Excessive variability
without bounds shows as users describing the reward as "random." Absent
guardrails show as the long-tail compulsive pattern. Missing real-world gain
shows as high engagement paired with press articles the team didn't want.

## Quality Gates

- Each anticipation cue in the loop can be mapped to an activity with a
  stated user-life benefit.
- Variability is bounded; the user never experiences a no-reward outcome
  as a "punishment" for returning.
- At least one guardrail (session limit, time awareness, opt-out) is
  reachable in two taps.
- Session-length distribution is monitored post-launch; long-tail
  compulsive patterns are tracked as a risk signal, not as a win.
- The loop's mechanics can be disclosed in plain language without
  embarrassing the team.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when habit-formation features surface. Does not delegate
to other packs in v0.1.0. Pairs closely with `ux-variable-rewards`
(variability is the structural lever; dopamine is the why) and with
`ux-intrinsic-motivation` (a dopamine loop without an intrinsic payoff
becomes extractive).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: naming the user's real-life gain, shipping at least one
  guardrail.
- Use "should" for: bounded variability, instrumentation of session-length
  distributions.
- Use "may" for: the specific cadence (daily, every-other-day, weekly)
  appropriate to the domain.

## Troubleshooting

- **"Streak anxiety is showing up in reviews"**: the loss-aversion edge is
  too sharp. Soften — add streak freezes, pause options, or a grace day.
- **"Daily return is strong but satisfaction surveys are flat"**: the pull
  exists without the payoff. Audit whether the activity is actually making
  the user's life better; if not, the loop is extracting.
- **"Power users describe the loop as addictive"**: that's a warning, not a
  win. Tighten the cap, add explicit opt-out, and inspect the long tail of
  session lengths.
- **"Variability feels random to the user"**: bounds are too wide.
  Tighten the reward range so the user can predict the shape without
  predicting the exact value.

## Concrete Example

A meditation app uses anticipation-driven design ethically. The daily
session surfaces at a consistent time, which the user chose during setup —
the anticipation cue is the time-of-day and a light, non-punitive
notification. The streak counter climbs, and on day 47 a small celebration
appears: a message that notes the consistency and reflects a trait growth
("you've built the practice"), not a scoreboard comparison. Variability is
bounded: the guided sessions vary in voice, theme, and length within a
range, so the user anticipates something slightly fresh without rolling dice
on whether the reward lands at all. Session limits don't exist because the
underlying activity self-limits at 10-20 minutes. Contrast this with a photo
app's streak mechanic, which uses the same neural circuitry to pull users
back daily at the cost of genuine sleep or connection — same dopamine
scaffolding, opposite effect on the user's life.

## Sources

- `[[concepts/dopamina-comportamento]]`
- `[[concepts/hook-model]]`
- Inspired by *100 Things Every Designer Needs to Know About People* (2011,
  Susan Weinschenk) and Wolfram Schultz's prediction-error research (1997),
  paraphrased further from Danilo's wiki synthesis of the Berridge
  wanting/liking distinction and the ethical guardrails proposed in Nir
  Eyal's *Indistractable*.
