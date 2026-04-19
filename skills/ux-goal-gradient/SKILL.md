---
name: ux-goal-gradient
description: Use when designing onboarding or multi-step flows — apply Hull's goal-gradient effect (effort increases near goal) via progress bars and near-completion UI.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the product asks the user to complete a multi-step commitment —
onboarding checklist, profile completion, course module sequence, subscription
setup, referral chain. Fires when completion rates drop in the middle, when
users start but don't finish, when the product hides progress entirely, or
when a loyalty-style flow isn't producing the acceleration into the finish
line that Hull and Kivetz documented. The skill surfaces progress in a way
that turns momentum into motivation.

## Preconditions

- The flow has a defined end state the user can reach (full profile, tenth
  purchase, tutorial complete, trial converted).
- The steps of the flow are countable or can be clustered into tiers.
- Progress can be tracked and displayed without deceptive claims.
- The flow is long enough for momentum to matter (roughly three or more
  meaningful steps, not a single click).

## Execution Workflow

1. Use Read to map the flow end-to-end. Count every step, group them into
   visible tiers if there are more than about five, and identify the
   defined completion criterion at each tier and at the end.
2. Expose progress explicitly. Show a progress bar, step counter, milestone
   ladder, or completion meter at a location the user naturally sees while
   working the flow. Hidden progress is inert; visible progress pulls.
3. Apply endowed progress where it fits. If the user has already taken
   passive steps (signed up, verified email, answered a question during
   sign-up), count those toward the meter. Starting at twenty percent is
   materially more motivating than starting at zero, even when the raw work
   remaining is identical.
4. Tune the gradient. Hull and Kivetz showed that effort and motivation
   accelerate as the user approaches the goal, peaking near ninety percent.
   Break the flow so that the final stretch is achievable in a session —
   users who see "one step left" will almost always close it.
5. Add meaningful milestone acknowledgements. A small visual shift, badge,
   or tier unlock at quarter and half marks converts the meter from a
   passive display into a sequence of small wins.
6. Watch for post-reward collapse. Immediately after a user completes a
   goal, motivation drops sharply. If the flow has a next tier or next
   loop, prepare it visibly before the current one finishes so the
   gradient re-engages instead of resetting to cold zero.
7. Avoid deceptive progress. Inflating the meter, pre-completing imaginary
   steps that don't reflect real effort, or moving the goal mid-flow
   erodes trust. Endowed progress works because the step really did happen,
   not because the bar is lying.
8. Use Edit to add the progress affordance, integrate milestone moments,
   and, where relevant, surface the next tier before the current one
   closes. Instrument the flow so you can confirm the gradient is
   actually accelerating completion.

## Rules: Do

- Make progress visible at a point the user already looks during the flow.
- Credit genuine passive steps as endowed progress to avoid cold starts.
- Break long flows into tiers with small, visible rewards at each milestone.
- Make the last step or two feel within reach in a single session; near-goal
  acceleration only fires if the goal is perceptually close.
- Prepare the next loop before the current one completes so momentum
  carries rather than resetting.

## Rules: Don't

- Don't hide progress because "we don't want to pressure the user" — absence
  of progress is its own pressure, the anxious kind that leads to
  abandonment.
- Don't inflate progress with fake steps; users detect dishonest meters and
  disengage.
- Don't move the goalposts mid-flow by adding new required steps; the
  gradient only works on stable targets.
- Don't pile on heavy extrinsic rewards (large bonuses, sweepstakes) for
  flows that already have intrinsic pull — the extrinsic reward can crowd
  out the user's own motivation.
- Don't design for completion and then leave the user at an empty landing
  after the final step; plan the post-completion experience.

## Expected Behavior

With the skill applied, users who start a flow finish it at materially
higher rates, and the acceleration is visible in the data: once users pass
the halfway mark, the rate of progress increases rather than decays. The
meter becomes part of the product's pull — users return specifically to
close the last tier rather than to use the product incidentally.

Qualitatively, the experience shifts from "I should probably finish that
someday" to "one more step and I'm done." Support questions move from "how
do I even start" to "I did the last bit, is that it?", which is a much
healthier mode of engagement.

## Quality Gates

- Progress is displayed somewhere the user naturally sees during the flow.
- Endowed progress credits real prior actions, not fictional ones.
- The flow is partitioned into tiers with perceptible milestones rather
  than presented as a single monolithic bar.
- The last tier is achievable in a single focused session.
- A post-completion experience (next loop, summary, reward) is designed,
  not left as an empty screen.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs
in v0.1.0. Pairs with `ux-flow-state-design` (flow keeps the user in the
session; gradient keeps them in the flow across sessions) and
`cog-attention-capture` (a well-tuned progress affordance reliably captures
attention at return moments).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: honest progress (no inflated steps), visible completion
  target.
- Use "should" for: endowed progress on real prior actions, tier-based
  milestones.
- Use "may" for: specific motif (bar, dots, badges, meter) based on
  product tone.

## Troubleshooting

- **"Users drop off in the middle"**: The midpoint feels farther from the
  goal than from the start. Add a more granular milestone between halfway
  and completion, or shorten the flow so the final stretch is always in
  view.
- **"Progress meter is present but completion hasn't changed"**: The meter
  may be off-screen or subtle. Move it to a location the user looks at
  during the flow, and increase its visual rank.
- **"Endowed progress triggered a negative reaction"**: The credited steps
  were too loose a stretch of the word "progress" (for example, crediting
  a landing-page visit). Credit only actions the user recognizes as
  meaningful.
- **"Completion rate is high but engagement after completion crashes"**:
  Post-reward collapse. Build the next tier or next loop and expose it
  before the current one closes.

## Concrete Example

A social network shows a profile-completion meter with four tiers at 25,
50, 75, and 100 percent. Upon sign-up, the user is already at 25 percent
because they supplied name, email, and role — endowed progress credits
real input. Each additional tier unlocks a tangible benefit: adding a photo
increases inbound connection requests; adding skills surfaces the user in
search; writing a headline unlocks a richer profile card. The meter sits
on the home surface where the user returns daily, and near 90 percent the
system surfaces a single remaining recommendation ("Add your current role
to reach 100 percent"). Completion rates climb dramatically compared with
the no-meter baseline. When users hit 100 percent, the product
immediately offers a next loop — "Start connecting with your team" — to
avoid the post-reward motivation dip. The same product, same data, with
and without the goal-gradient scaffolding behaves very differently.

## Sources

- `[[concepts/motivacao-comportamento]]`
- `[[concepts/frameworks-comportamentais]]`
- Inspired by Clark Hull's goal-gradient research, Kivetz's loyalty-card
  replication, and *100 Things Every Designer Needs to Know About People*
  (2011, Susan Weinschenk), paraphrased further from Danilo's wiki notes
  on endowed progress and post-reward resetting.
