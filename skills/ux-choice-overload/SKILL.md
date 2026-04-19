---
name: ux-choice-overload
description: Use when designing pricing tiers, feature selection, or product lists — apply paradox of choice, smart defaults, anchoring to reduce decision paralysis.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a surface asks the user to pick one item from a set — pricing plans,
feature options, shipping methods, product variants, configuration choices.
Fires when the number of options is high enough that the page starts feeling
"overwhelming" in qualitative research, when pricing experiments lift
conversion by removing a plan rather than adding one, or when a team is about
to ship a seven-tier plan grid because "more options serve more users." The
skill shapes the option set and its presentation so a tired, distracted user
can still arrive at a reasonable pick without comparing every cell.

## Preconditions

- The option set has a defined purpose (buy, subscribe, select, configure)
  and a measurable outcome (conversion, adoption of the picked option,
  satisfaction after the pick).
- The team has access to usage data showing which options are actually
  chosen, not only which are offered.
- There is room to change the shape of the set — trim, group, reorder,
  pre-select a default — rather than only restyling it.

## Execution Workflow

1. Use Read to list the options currently shown and, where available, the
   distribution of actual choices against them. Note any option that gets
   less than a few percent of the traffic; it is almost certainly hurting
   the picks above and below it.
2. Count visible siblings. If the count sits above five, the page is paying
   a paralysis tax. Schwartz's finding is that satisfaction and regret both
   move the wrong way as options grow, and Iyengar's jam-tasting result
   showed a six-option display outsold a twenty-four-option display by an
   order of magnitude in actual purchases despite drawing fewer browsers.
3. Land inside the sweet spot. Three to five options per decision gives the
   user enough contrast to feel the choice is real without forcing them to
   hold every cell in working memory at once.
4. Pick a smart default. In most decisions, roughly four out of five users
   accept whichever option is pre-selected, so the default should be the
   one that serves the majority of users, not the one that maximizes
   short-term revenue. The pick of the default is itself a design decision
   and deserves the same scrutiny as the option set.
5. Anchor the range. The first option a user sees shapes how they read the
   rest. Putting the highest tier first establishes "this is the expensive
   end," which makes the middle feel reasonable by comparison. Starting
   with the cheapest flips the frame toward "this is the cheap end," which
   makes the upsell feel steep.
6. Use a decoy when the goal is to route users to a specific middle option.
   A three-tier layout with a clearly-marked middle ("most popular,"
   "recommended," a visual highlight) combined with neighbors that are
   worse-per-dollar channels the decision without hiding the alternatives.
7. Use Edit to trim the set, reorder for anchor effect, mark the default,
   and verify that a user skimming for ten seconds can still pick a
   reasonable option.

## Rules: Do

- Keep the visible option count between three and five per decision
  surface; if more are truly needed, group them under tabs, filters, or a
  "see all plans" disclosure.
- Pre-select the option that serves the most users by default; treat the
  default as a user-serving choice, not a revenue-maximizing one.
- Show the highest-value option first or alongside the middle to anchor the
  price range before the user reads the details.
- Use a visual highlight and short label ("most popular", "recommended")
  on the option the data says most users should pick.
- Instrument the option set so each choice is attributed, and be willing to
  remove options that draw less than a handful of percent of traffic.

## Rules: Don't

- Don't ship an eight-tier grid because "different users want different
  things"; the distribution always concentrates on two or three, and the
  rest add paralysis without revenue.
- Don't anchor with the cheapest option on the left when the goal is to
  convey premium; the user will read every other option as an upsell from
  that anchor.
- Don't mark a tier as "most popular" when it isn't; a false signal is
  recognized over time and drains trust on the page.
- Don't leave the default unset on a decision the user is likely to accept
  without thought — the absence of a default is still a default, and it
  usually serves no one.
- Don't hide the upgrade path behind a decoy so aggressive that the user
  feels routed; the pattern works as a nudge, not as a trap.

## Expected Behavior

With the skill applied, the decision surface feels calmer. Users land on a
pick within a few seconds, usually the default or the highlighted middle,
and conversion rises without the need to sell harder. Qualitative research
shifts from "I wasn't sure which one to pick" to "the middle one looked
right." Support tickets about plan selection drop, because the set is small
enough to hold in mind and the highlighted option carries its own explanation.

When the option set grows unchecked, the symptoms return. Browser time on
the plan page stretches, scroll depth grows, and submit rate falls. Users
who do pick sometimes regret the pick, because a large set makes every
choice feel like a trade-off against the alternatives they didn't take.
That regret shows up later as cancellation or downgrade.

## Quality Gates

- The visible option count per decision is between three and five.
- A default is pre-selected on every decision the user is likely to accept
  without thinking about each option.
- The anchor option (first in reading order) supports the framing the page
  intends — premium-first when positioning up, budget-first when
  positioning down.
- One option is highlighted as the recommended pick, and the highlight
  matches actual usage data rather than marketing preference.
- Options with less than a few percent of traffic have been removed,
  grouped, or moved behind a disclosure.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) whenever the surface presents a set of options — pricing,
feature selection, product listings, configuration. Pairs with
`cog-cognitive-load` (the option count is a direct working-memory tax) and
with `cog-unconscious-decisions` (the anchor and default mechanisms rely on
System 1 behavior) and with `ux-social-proof` (the "most popular" highlight
is a social-proof signal that must be truthful).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: truthful recommendation labels, a default on every
  acceptable-without-thought decision.
- Use "should" for: three-to-five option ceiling, premium-first anchor for
  up-positioning.
- Use "may" for: the specific ordering inside the sweet spot, the exact
  form of the highlight (badge, border, color).

## Troubleshooting

- **"Plan page has seven tiers and conversion is flat"**: trim to three or
  four; merge the long tail into a "custom" or "enterprise" contact option.
  The long tail is almost never where revenue lives.
- **"Users pick the cheap tier and then churn"**: the middle wasn't
  anchored. Reorder so the premium option sits first or is shown at equal
  visual weight, and mark the middle as recommended.
- **"The 'most popular' badge stopped lifting conversion"**: it may have
  drifted from reality as the mix shifted. Recompute against current data;
  if another tier is now most picked, move the badge.
- **"Users ask support which plan to choose"**: the set is either too
  large or undifferentiated. Cut options, or rewrite each row so the
  difference is visible without reading fine print.

## Concrete Example

A file-storage product landed on a three-tier plan page — Basic at zero
dollars, Plus at ten dollars a month, Family at seventeen. The middle tier
is pre-highlighted with a "most popular" ribbon and a slight background
tint. The Family tier sits on the right with a higher price, anchoring the
upper end so Plus reads as the balanced middle rather than the upsell. A
first-time visitor skimming for ten seconds sees three rows, one of them
visibly recommended, and picks it without opening the feature table.
Conversion on the page climbs because the default-plus-anchor-plus-proof
stack does the work of selling. The same company's prior page had shipped
eight tiers across personal, team, and business, with no highlight and no
default; abandonment on that page was nearly twice as high, and support
tickets asking "which plan is right for me" were a steady weekly stream.

## Sources

- `[[concepts/tomada-decisao]]`
- `[[concepts/frameworks-comportamentais]]`
- Inspired by *The Paradox of Choice* (2004, Barry Schwartz) and *100
  Things Every Designer Needs to Know About People* (2011, Susan
  Weinschenk), paraphrased further from Danilo's wiki synthesis of the
  Iyengar & Lepper jam study (2000) and Kahneman's anchoring-and-adjustment
  heuristic.
