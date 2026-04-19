---
name: ux-yerkes-dodson
description: Use when designing for time-sensitive or stressful contexts — reduce UI surface since stress degrades performance (Yerkes-Dodson), avoid tunnel-action mode.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the user will reach the interface under duress — emergency apps,
checkout timers, medical tools, financial panic moments, tax deadlines,
travel disruptions, security alerts, any moment when the real-world stakes
override the usual patience budget. Fires when a design that tests well in
the office fails badly in the field, when users repeat the same failing
action under pressure, or when the team is designing a high-stakes surface
for the first time and hasn't calibrated for stress. The skill shrinks the
UI surface and clarifies the affordances so a stressed user can still
complete the action.

## Preconditions

- The surface can be identified as likely-stressful in real use (the "test
  in the office" assumption doesn't match the real context).
- The primary action in the stressful context can be named in one sentence
  — the thing the user is actually trying to accomplish under pressure.
- Research, support tickets, or telemetry can reveal the real stress
  contexts; designing for imagined stress without data tends to produce
  the wrong defenses.

## Execution Workflow

1. Use Read to map the stressful-use scenario. When does the user hit this
   surface under pressure? A parent assembling a toy at midnight, a trader
   watching a market crash, a traveler rebooking a flight after a
   cancellation, a patient in an ER checking medication. The context is
   not the surface's ordinary one, and the design has to acknowledge
   that.
2. Apply the Yerkes-Dodson shape. Performance peaks at moderate arousal
   and drops sharply at high arousal. The drop is not gentle; cognition
   narrows, working memory contracts from the usual four-plus-or-minus-
   one to two or three items, and attention tunnels onto what looks like
   the obvious action whether or not it works.
3. Expect tunnel-action under pressure. A user who believes "this button
   does what I need" will click it repeatedly even as it fails to
   accomplish the goal. The design can't prevent tunnel-action, but it
   can shrink the set of plausible buttons so the tunneled action is
   more likely to be the right one.
4. Reduce the UI surface. Remove secondary affordances that the user
   doesn't need in the stressful moment. Collapse decorative elements.
   Increase the contrast and size of the primary action. Do one thing;
   do it large. A checkout timer with fifteen upsells and a buried Pay
   button fails under stress even if it works fine in calm.
5. Use direct language. Under stress, users skim past clever copy and
   parse only the most explicit cues. "Sell now" reads; "Place order to
   liquidate position" confuses. Verb-first, plain words, unambiguous
   labels. Second-person phrasing helps — "your order is ready" beats
   "order ready."
6. Test in stress. Calm user-testing predicts calm-use performance, not
   stress performance. Introduce artificial time pressure, split-
   attention tasks, or emotional prompts during validation. Teams that
   skip this consistently ship interfaces that fail in the exact moment
   they needed to hold.
7. Use Edit to strip the surface, enlarge the primary action, and
   rewrite labels for direct comprehension. Measure completion rates on
   the stressed path, not the calm one.

## Rules: Do

- Name the primary action in one sentence; design the surface around
  completing that action fast and unambiguously.
- Reduce the number of simultaneously visible options in stress contexts
  to two or three, not five or six.
- Increase affordance clarity: larger targets, stronger contrast,
  verb-first labels.
- Test the stressed path, not only the calm path. Simulate the time
  pressure, the split attention, the emotional load during validation.
- Remove decorative and secondary affordances from the stressed surface
  — they compete for attention the user doesn't have.

## Rules: Don't

- Don't assume the calm-use testing result generalizes. A surface that
  passes user testing in a lab can fail in the field under pressure.
- Don't use clever or playful copy on high-stress surfaces. Under load,
  the user parses only the most direct words.
- Don't rely on documentation, help links, or onboarding copy at the
  moment of stress. The user won't read it; they're tunneling on the
  primary action.
- Don't add upsells, promotional elements, or cross-sell content to a
  high-stress surface. The trust cost of interrupting the user in that
  moment far exceeds any revenue upside.
- Don't increase the number of options hoping to give the user flexibility.
  Under stress, more options means worse performance, not more agency.

## Expected Behavior

With the skill applied, the stressed surface becomes something the user
can actually use when they need it. Primary-action completion rates rise
on the stress path even when calm-path metrics stay flat. Support volume
around the stressful context drops — users are finishing the action
rather than calling in. Reviews mention "worked when I needed it" as a
distinct theme from "easy to use," because those are different tests.
Tunnel-action still happens, because it's a feature of stressed
cognition, but it now lands on the right button more often than not.

When the calibration is off, the pattern is recognizable. Users repeat
the same failing action and file angry tickets. Reviews describe the
interface as "okay in normal times but useless when it mattered."
Completion rates on stress paths lag calm-path rates by a margin the
team never investigated, because the metrics weren't split.

## Quality Gates

- The primary action on any stress-context surface is larger and higher-
  contrast than any other element on the screen.
- Simultaneously visible options stay at two or three on stress
  surfaces, not five or more.
- Copy on stress surfaces is verb-first, unambiguous, and free of
  clever or playful language.
- Validation includes at least one stressed-path scenario, not only
  calm-context usability tests.
- Decorative elements, upsells, and secondary affordances are absent
  from surfaces used under duress.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when time-sensitive, high-stakes, or panic-context
surfaces are being designed. Does not delegate to other packs in
v0.1.0. Pairs closely with `ux-swiss-cheese-errors` (stressed users
slip more, so error defenses for stress surfaces need extra layers)
and with `cog-cognitive-load` (working memory contracts under stress,
so the load budget shrinks from roughly four to roughly two).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: stripped surface on stress contexts, one-sentence
  primary action, stressed-path validation.
- Use "should" for: verb-first labels, two-or-three visible options,
  removal of decorative elements.
- Use "may" for: the specific target size and contrast treatment
  appropriate to the platform.

## Troubleshooting

- **"Users repeat the same failing action on the stress surface"**:
  tunnel-action. The surface offers the wrong primary affordance or
  buries the right one. Make the right action the obvious one.
- **"Works fine in testing, fails in reviews"**: the testing was calm,
  the reviews came from stressed use. Re-validate under artificial
  pressure and fix what breaks.
- **"Users say the interface has too many buttons when it matters"**:
  the option count is above the stressed working-memory budget.
  Collapse secondary options behind a revealer or into a later step.
- **"Clever copy gets complaints on the stress surface"**: under load,
  users parse only the most direct words. Rewrite to verb-first plain
  language, save the personality for calm surfaces.

## Concrete Example

A stock-trading app designs two versions of its order-entry surface for a
market-crash context. The first version preserves the full-feature UI
with fifteen toggles — buy, sell, limit, stop, trailing stop, bracket,
options, extended hours, and so on — laid out in a two-column grid. In
calm testing, traders complete orders in roughly three seconds. During a
real panic, completion times double, error rates jump, and the support
queue fills with "I hit the wrong button." The second version, specific
to the crash context, strips the surface to three large buttons: Sell
current position, Buy more, Cancel pending orders. Each button is verb-
first, high-contrast, and consumes roughly a third of the screen. The
advanced controls remain reachable through a secondary view but aren't
visible by default in a detected-stress state. Completion rates on the
stressed path match the calm-path rates for the first time; support
volume during crashes falls. The first version respected the power
user; the second respected Yerkes-Dodson.

## Sources

- `[[concepts/erros-usabilidade]]`
- Inspired by Yerkes & Dodson's original arousal-performance research
  (1908) and *100 Things Every Designer Needs to Know About People*
  (2011, Susan Weinschenk), paraphrased further from Danilo's wiki
  synthesis of Lupien's glucocorticoid replication (2007) and the
  tunnel-action pattern documented in stressed-decision studies.
