---
name: ux-intrinsic-motivation
description: Use when designing long-term engagement features — apply Self-Determination Theory's autonomy, competence, and relatedness.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the team is designing for a product whose value depends on the user
sticking around for months or years — learning platforms, fitness apps,
creative tools, productivity software, communities. Fires when early retention
looks strong but long-tail retention drops, when extrinsic incentives (points,
badges, coupons) are proposed as the primary engagement lever, or when the
loop needs to sustain itself without constant nudging. The skill shifts the
product from "we keep pulling users back" to "users find their own reason to
return."

## Preconditions

- The core activity has genuine external value to the user (skill gained,
  health improved, work shipped) — not just entertainment consumption.
- Long-term retention can be measured beyond the first 30 days.
- The team is willing to consider that cash incentives and points might be
  doing less than they appear, and in some cases actively hurting.

## Execution Workflow

1. Use Read to audit existing motivation mechanics. Classify each as
   extrinsic (points, coins, badges, cash, leaderboards that rank against
   strangers) or intrinsic (surfaces autonomy, skill growth, or belonging).
   Extrinsic mechanics decay when removed; intrinsic mechanics compound.
2. Apply the three-need frame from Self-Determination Theory. Autonomy is
   the felt sense of choosing. Competence is the felt sense of getting
   better. Relatedness is the felt sense of connection to others who share
   the activity. A durable product addresses all three.
3. Design for autonomy by offering meaningful choices — which path to take,
   which goal to set, which mode to use. Trivial choices (color of the
   button) don't carry autonomy weight; real choices (what to practice,
   what to prioritize) do.
4. Design for competence by making skill growth visible. Not just a number
   climbing, but a change the user can feel — a harder piece played, a
   faster route completed, a more complex feature mastered. Leaderboards
   among peers of similar level work; leaderboards that rank beginners
   against experts break the loop.
5. Design for relatedness by connecting the user to similar others, not to
   a generic community. A user who runs 5ks wants to see other 5k runners,
   not an undifferentiated "fitness community." Relatedness requires
   resonance, not just volume.
6. Prune overjustification risk. If the activity is already intrinsically
   rewarding (playing music, writing, running), overlaying heavy extrinsic
   rewards can reduce interest once the rewards stop. Light extrinsic
   layers (optional badges, shareable achievements) are safer than central
   ones.
7. Use Edit to rewire motivation surfaces — expose the choices, reflect the
   growth, connect the peers, and trim the extrinsic overlay that's doing
   more harm than good.

## Rules: Do

- Offer the user genuine choices about what, how, and when — not just
  cosmetic customization.
- Reflect visible skill growth in the interface: metrics that track real
  capability, paths that open as the user advances.
- Connect users to others whose situation resembles theirs: similar level,
  similar goal, similar constraints.
- Treat intrinsic motivation as the primary engine and extrinsic rewards as
  optional sauce that can be removed without collapsing the loop.
- Measure long-tail retention as the truth signal; 30-day retention reacts
  to extrinsic pushes, but 6-month retention only holds when intrinsic
  needs are met.

## Rules: Don't

- Don't overlay heavy extrinsic rewards on an activity that is already
  intrinsically motivating — it can suppress the very drive you want to
  cultivate.
- Don't mistake customization for autonomy. Picking a theme is not
  autonomy; picking a goal, a path, or a practice schedule is.
- Don't rank users against incomparable peers (beginners vs. experts on the
  same leaderboard) — it demotivates the beginner and bores the expert.
- Don't treat "community" as a feature to add; design for belonging among
  people who share the specific activity and level.
- Don't strip out agency to simplify onboarding. A product that decides
  everything for the user delivers fast time-to-value and zero durable
  motivation.

## Expected Behavior

With the skill applied, users keep returning because the product helps them
become the person they're trying to be. Long-tail retention curves flatten
rather than bleed. Users describe the product in first-person terms — "my
practice," "my runs," "my writing" — rather than talking about the app
itself. When promotional pushes pause, engagement doesn't collapse; the loop
sustains on the growth the user feels from doing the activity.

Extrinsic layers still matter at the margin — a well-placed badge can still
spark a return visit — but they function as frosting, not as structure.
Pulling them out doesn't topple the product.

## Quality Gates

- The user can name at least three meaningful choices they've made in the
  product, not three color preferences.
- Skill growth is visible on screen in a form the user recognizes as
  improvement, not just as a rising number.
- Any social or community surface connects the user to peers with
  comparable level and goal, not to an undifferentiated feed.
- Extrinsic rewards can be removed in a thought experiment without the
  loop collapsing; if removal kills engagement, the loop is not intrinsic.
- Long-tail retention (beyond 90 days) exceeds what extrinsic incentives
  alone would predict.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when long-term retention is the design question. Does not
delegate to other packs in v0.1.0. Pairs with `ux-variable-rewards`
(self-rewards map to SDT's competence dimension), `ux-goal-gradient`
(progress surfaces feed the competence signal), and `ux-flow-state-design`
(flow itself is an intrinsic experience that the SDT lens explains
structurally).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: addressing at least two of the three SDT needs in any
  retention-oriented feature.
- Use "should" for: peer-matched community surfaces, removable extrinsic
  layers.
- Use "may" for: the exact balance of autonomy/competence/relatedness
  appropriate to the domain.

## Troubleshooting

- **"Retention is fine at 30 days but cliffs at 90"**: the early bump came
  from extrinsic pushes; the long tail needs an intrinsic engine. Audit
  autonomy, competence, and relatedness surfaces for what's missing.
- **"We added points and engagement dropped"**: the overjustification effect
  hit. The activity was already intrinsically rewarding, and the points
  reframed it as work. Scale back or remove.
- **"Community feature has low engagement despite thousands of members"**:
  the community surface isn't peer-matched. Segment by level or goal and
  surface the smaller, resonant group.
- **"Expert users describe the product as 'gamey'"**: the extrinsic overlay
  is too central. Offer a power-user mode where badges and points recede.

## Concrete Example

A running app supports casual users for a decade with low acquisition cost
by grounding retention in the three SDT needs. Autonomy lives in the ability
to log any activity, set personal goals, and decide the shape of the
training week. Competence shows up as pace graphs, PRs, segment times, and
fitness trends — the user can see themselves getting stronger. Relatedness
comes from following friends and seeing other runners' routes in the same
neighborhood, so the peer surface is resonant rather than generic. The
product has a leaderboard, but it's sliced by age bracket and segment, so
the comparison feels fair. None of this rests on an extrinsic scaffold. When
the team pauses promotions or cuts a badge system, retention barely moves.
Contrast this with a rewards-card app that spikes on launch, pays every
visit with points, and flatlines the moment the points budget ends.

## Sources

- `[[concepts/motivacao-comportamento]]`
- `[[concepts/frameworks-comportamentais]]`
- Inspired by Deci & Ryan's Self-Determination Theory (1985) and *100 Things
  Every Designer Needs to Know About People* (2011, Susan Weinschenk),
  paraphrased further from Danilo's wiki synthesis of overjustification,
  goal-gradient post-reward reset, and the intrinsic/extrinsic continuum.
