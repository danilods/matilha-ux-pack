---
name: cog-unconscious-decisions
description: Use when designing decision architecture — account for System 1 (unconscious, 95% of decisions) vs System 2 (deliberate), loss aversion, default bias.
category: cog
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the product asks the user to choose, confirm, toggle, opt in, or
opt out — especially when the decision is repetitive, low-stakes, or taken
under time pressure. Fires when a team is designing defaults, writing
framing copy for a confirm dialog, debating whether to default a newsletter
subscription on or off, or trying to reconcile why the same feature
converts radically differently depending on how the choice is presented.
The skill treats the user as a mostly-automatic decider who only wakes up
when the page forces them to, and shapes the architecture accordingly.

## Preconditions

- The decision has a measurable outcome (opt-in rate, conversion, churn,
  completion) so the effect of the architectural change can be seen.
- The team has the authority to change the default, the framing, and the
  ordering — not only the copy.
- The consent rules for the context are known, because a default that
  serves the user in one jurisdiction can be illegal or harmful in another.

## Execution Workflow

1. Use Read to locate every point where the user makes a decision on the
   surface — buttons, toggles, radio groups, confirm dialogs, opt-ins,
   unsubscribes. For each, note the default state, the framing of the
   copy, and the order of options.
2. Classify the decision as System-1 or System-2. The vast majority of
   daily decisions never reach conscious deliberation — Kahneman's rough
   figure is around ninety-five percent. A decision is System-1 when the
   user is tired, repeating, or trusting the product to have sensible
   settings. It is System-2 when the page is unfamiliar, the stakes are
   high, or the user is already frustrated.
3. Set the default to the option that serves the user over time. Default
   bias is strong enough that most users will accept whatever is
   pre-selected; that is a responsibility, not a lever for short-term
   revenue. For regulated choices (marketing consent, data sharing), the
   default must follow the law, not the conversion goal.
4. Frame the choice around loss where loss genuinely applies. Losses hurt
   roughly twice as much as equivalent gains, so "don't lose your work"
   lands harder than "save your work." Use the loss frame only when the
   loss is real; inventing a loss to nudge is manipulation.
5. Guard against the availability heuristic. Users judge risk and
   frequency by how easily an example comes to mind, which means a recent
   outage, a vivid error, or a viral news story can distort their read of
   the product. Surface accurate base rates when the heuristic would
   mislead ("this has happened X times in the last year" beats silence
   when a rare incident makes the news).
6. Name and expose the System-2 path when stakes are high. A destructive
   action (delete account, empty trash, cancel plan) should force a
   moment of deliberation — a typed confirmation, a two-step dialog, a
   visible consequence. Do not make destruction cheap.
7. Use Edit to rewrite defaults, framings, and confirm copy. Verify by
   reading the surface out loud — does the page respect the user who is
   only half paying attention, and wake them up for the choices that
   deserve it?

## Rules: Do

- Set defaults to what serves the user long-term; treat the default as a
  position statement about whose interest the product represents.
- Frame gain-or-loss copy around actual loss when loss is real ("don't
  lose access," "your streak resets") and around actual gain otherwise.
- Force a System-2 pause on destructive or irreversible actions — typed
  confirmation, two-step dialog, review screen with explicit consequence.
- Surface base rates when the availability heuristic would mislead, so
  the user's sense of likelihood reflects reality rather than the last
  thing they read.
- Respect consent law as the floor; a default that converts well and
  violates consent rules is not a viable design.

## Rules: Don't

- Don't hide the unchecked state of an opt-in under a pre-checked one
  when the law requires explicit consent; the short-term conversion is
  not worth the regulatory and trust cost.
- Don't invent a loss where none exists to lean on loss aversion; framing
  a price as "don't miss out" on a product the user doesn't need is a
  manipulation, not a nudge.
- Don't make destruction a one-click path; System-1 will fire it eventually
  and the user will not forgive the product.
- Don't stack System-2 friction on routine decisions the user has made
  before — extra confirmations on repeat tasks train the user to
  click-through without reading, which is worse than no friction.
- Don't treat "user didn't change the default" as evidence the default
  was wanted; it is evidence the default stuck.

## Expected Behavior

With the skill applied, the routine path feels frictionless and the
high-stakes path feels deliberate. Opt-in rates reflect real preference
rather than whichever checkbox was pre-selected. Destruction is rare and
recoverable; when it happens, it happened on purpose. Copy around losses
feels honest because the losses are real. Support tickets about "I didn't
mean to do that" fall, because the surface made the cost visible before
the click.

When the decision architecture is careless, the symptoms compound. Users
accept defaults they later resent and churn as a result. Destruction
happens by accident and generates support load and bad reviews. Framing
around invented losses gets called out publicly and erodes trust on the
entire page it appears on, not only the specific claim.

## Quality Gates

- Every default on the surface has a documented reason tied to user
  benefit, not only revenue.
- Destructive actions require at least one System-2 step (typed
  confirmation, explicit consequence, two-step dialog).
- Loss framings on the surface describe losses that actually occur if the
  user does nothing.
- Consent-related defaults comply with the applicable jurisdiction's
  rules for explicit or implied consent.
- High-volume routine decisions carry no unnecessary confirmation
  friction; confirmation is reserved for consequential moments.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) whenever a decision surface, consent flow, or destructive
action is designed or reviewed. Pairs with `ux-choice-overload` (the
default is the single most powerful variable inside an option set), with
`ux-swiss-cheese-errors` (System-2 confirmation is a slice of defense on
destructive actions), and with `ux-trust-by-design` (default choices and
framing are trust-visible artifacts).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: legal consent defaults, System-2 friction on
  irreversible actions, honesty of loss framings.
- Use "should" for: defaults that serve the user long-term, exposure of
  base rates when availability would mislead.
- Use "may" for: the specific form of the System-2 step (typed word vs.
  re-authentication vs. review screen), the copy register of loss framings.

## Troubleshooting

- **"Opt-in rate is high but churn on the opted-in segment is also high"**:
  the default is converting users who didn't want the thing. Un-default it
  and re-measure; the real demand was lower than the default implied.
- **"A feature gets strong early clicks and angry tickets"**: the action
  was destructive and lacked a System-2 step. Add a confirmation with a
  visible consequence and re-measure the tickets, not the clicks.
- **"Users report the product feels manipulative"**: a loss framing is
  likely inventing the loss. Rewrite around real consequence or remove the
  frame entirely.
- **"Legal pushback on a consent checkbox"**: the default probably
  violates the local consent regime. The correct move is to change the
  default, not the legal analysis.

## Concrete Example

The organ-donation policy literature gives the clearest illustration. In
countries with opt-in consent, registration typically sits near a quarter
to a third of the population. In countries with opt-out consent covering
the same behavior, registration sits near ninety-nine percent. The
population has not suddenly grown more generous; the default carries the
decision because the underlying choice is System-1 — most people never
actively engage with the form. A product applies the same mechanism in
small ways: a backup toggle defaulted on, a currency defaulted to the
user's locale, a notification defaulted to digest rather than real-time.
Each is a default chosen because System-1 will accept it, and each is
defensible only if the default genuinely serves the user — which is what
distinguishes a considered default from a dark pattern.

## Sources

- `[[concepts/tomada-decisao]]`
- `[[sources/100-things-every-designer]]`
- Inspired by *Thinking, Fast and Slow* (2011, Daniel Kahneman) and *100
  Things Every Designer Needs to Know About People* (2011, Susan
  Weinschenk), paraphrased further from Danilo's wiki synthesis of the
  Bechara gambling-card experiment and the Johnson & Goldstein (2003)
  opt-in versus opt-out consent results.
