---
name: ux-reservatorio-boa-vontade
description: Use when designing any critical interaction — Krug's trust reservoir economy: what fills it, what drains it, accessibility as a refill.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a product is assembled from independently-good pieces but the
whole somehow irritates users, when NPS or CSAT trends down despite a
stable feature set, when support load concentrates on "small" complaints
that feel disproportionate, or when an accessibility review has been
deferred with "we'll get to it." Fires on the full user journey — not
only the moment of conversion — because the reservoir mechanism operates
across every touch, not at any single point. The skill treats user
goodwill as a finite account that fills and drains with each interaction
and holds the team responsible for the running balance.

## Preconditions

- The product has real users or realistic proxies who can speak to
  what the experience actually feels like, not only what the team
  intended.
- The full journey can be mapped — entry, core task, error recovery,
  support contact, billing, cancellation — so drains and refills can
  be located precisely.
- The team is willing to treat "small" friction as consequential.
  Reservoir work is cumulative; teams that will only fix what shows
  up in a single metric cannot usually apply this skill.

## Execution Workflow

1. Use Read to walk the full journey as a user. Note every moment
   that drains goodwill — hidden costs, surprise errors, slow loads,
   accessibility failures, broken links, dark patterns, rigid input
   formats — and every moment that refills — fast loads, clear
   pricing, honest error recovery, respected preferences, human-voice
   copy. Treat each as a plus or minus against the running balance.
2. Prioritize the drains by frequency. A small drain on every session
   outweighs a large drain on a rare path; ten little paper cuts each
   weigh more than one dramatic but unusual failure. The reservoir
   metaphor is that the total level is what matters, not the size of
   any single leak.
3. Close the top drains first. Hidden fees are close to the top of
   every list; rigid format rules (phone number with exact hyphens,
   postcode without spaces) are next; surprise errors without recovery
   paths are often third. These are table-stakes fixes that most teams
   carry for longer than they should.
4. Install refills where the user is already tense. A clean error
   screen with a plain-language explanation and a recovery path
   refills goodwill that the error itself drained, often ending the
   net balance roughly where it started. Support messages that sound
   like a person, not a template, carry a similar refill.
5. Treat accessibility as a reservoir refill, not a compliance tax.
   A screen reader-friendly flow works better for the user with a
   hand injury typing one-handed, for the user on a slow connection,
   for the user who prefers keyboard. Accessibility done well refills
   the reservoir for everyone; accessibility absent drains it
   specifically for the users who were already paying the highest
   cost to be there.
6. Run the bad-day test. Ask, on a user's worst day — stressed,
   late, on a weak connection, typing one-handed — will this surface
   irritate or soothe? The answer for most drains is "irritate," and
   the fix is usually to remove the drain rather than add a compensating
   refill.
7. Use Edit to close drains, install refills, and re-walk the journey.
   The goal is not a perfect experience but a running balance that
   stays positive through the expected frictions of real use.

## Rules: Do

- Show real costs early — total price, taxes, fees, shipping — before
  asking the user to commit; late surprises are among the most
  expensive drains on the page where they happen.
- Accept input in any reasonable format the user would naturally type
  (phone numbers with or without hyphens, dates in common forms); the
  machine is the right place to normalize, not the human.
- Write error recovery as a refill: name the problem in plain
  language, say what the user can do, and preserve any work the user
  had already done.
- Treat accessibility improvements as universal-design refills —
  they help the named group directly and help everyone at least
  incidentally.
- Keep the user signed in where it is safe to do so; repeated
  re-authentication on low-stakes actions is a steady drain users
  rarely report but consistently resent.

## Rules: Don't

- Don't bury fees in the final step; the conversion lift from the
  hidden fee is smaller than the cumulative trust loss it causes.
- Don't punish the user for not formatting input the way the system
  prefers; normalize on submit and move on.
- Don't ship dark patterns — trick questions, pre-checked consents
  in consent jurisdictions, misleading urgency — even when the
  short-term metrics approve; the reservoir drains when the user
  catches on, and they do catch on.
- Don't defer accessibility fixes as "phase two" on a journey that
  has already shipped; the users affected are losing goodwill every
  day the phase two doesn't arrive.
- Don't rely on human-warmth copy to compensate for a broken flow;
  the tone can refill a small drain, but the fix for a structural
  drain is structural.

## Expected Behavior

With the skill applied, the product feels unaccountably pleasant to
use, which is the correct symptom of a positive running balance.
Support tickets shift in shape — fewer complaints about "small"
irritations, more substantive product conversations. Churn at the
edges (the users who were only half-convinced) falls, because the
small accumulation of goodwill is enough to carry them through the
frictions the product still has. Accessibility coverage expands
without drama, because the team now reads accessibility as a refill
rather than a cost center.

When the reservoir is ignored, the symptoms compound across the
journey rather than concentrating in any one place. NPS drifts down
without a clear cause. Users describe the product as "fine" and
shop alternatives. Support load rises on small issues that each feel
too minor to fix. New users onboard, see the drains early, and churn
before the product has a chance to make its case.

## Quality Gates

- Costs, fees, and commitments are visible before the user commits;
  no surprise line items appear at the final step.
- Input validation accepts reasonable user formats and normalizes
  server-side; the machine does the work the human otherwise would.
- Error screens name the problem plainly and provide a recovery
  path without losing the user's prior work.
- Accessibility baseline (alt text, keyboard navigation, labels,
  sensible heading structure, screen-reader-friendly flow) is
  present throughout, not deferred.
- The journey passes the bad-day test — a tired, stressed, or
  tentative user can complete the core tasks without encountering
  a drain the design could have prevented.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) on any full-journey or critical-interaction review,
and whenever support or NPS feedback is being interpreted. Pairs with
`ux-trust-by-design` (the reservoir is where trust accumulates over
time), with `ux-krug-satisficing` (plain, obvious design is a steady
refill), with `ux-swiss-cheese-errors` (graceful error recovery is the
canonical refill), and with any pack skill applied to the surfaces the
reservoir is being measured against.

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: early disclosure of real cost, accessibility
  baseline, lossless error recovery.
- Use "should" for: format-permissive input validation, human-voice
  error and support copy, retained sign-in where safe.
- Use "may" for: the specific tone of human-voice copy, the exact
  form of the accessibility audit, the priority order among drains of
  similar frequency.

## Troubleshooting

- **"NPS dropped two points across a quarter without a feature
  change"**: walk the journey fresh. The drains probably accumulated
  through small decisions — a new consent modal, a longer cookie
  banner, a tightened input format — each of which seemed harmless.
- **"Support load is heavy on 'small' issues"**: the issues aren't
  small to the users. Close the drains before rewriting the help
  center; a drain the help center explains is still a drain.
- **"Accessibility keeps getting deferred"**: the skill's lens reads
  that as goodwill bleeding every sprint it doesn't happen. Move at
  least the baseline into the current sprint; treat it as a refill
  line item rather than a compliance line item.
- **"The product feels 'fine' but churn is rising"**: "fine" is a
  warning, not a baseline. Reservoir work is usually the right
  response, because "fine" is the running balance sitting near zero
  while small drains pull it negative.

## Concrete Example

An airline booking site illustrates both directions. In the filling
direction: clear all-in pricing from the search page, a date-change
control that doesn't force a restart, saved passenger details that
don't demand re-entry, a session that stays logged in across the
journey, and a support link visible on every page. A user completing
a booking in that flow lands at the end with a small positive
balance, enough to weather a later friction without churning. In the
draining direction, on the same airline's old version: a base fare
quoted up front, a baggage fee surfaced only at seat selection, a
captcha that fails once and forces a restart, and a support number
hidden behind three menus. A user completing the same booking on
that flow lands at the end irritated, writes a review naming one of
the drains, and avoids the brand next time. The journeys look
structurally similar on paper; the reservoir balance at the end is
opposite, because the small design decisions ran in opposite
directions across the whole journey.

## Sources

- `[[concepts/reservatorio-boa-vontade]]`
- `[[sources/nao-me-faca-pensar]]`
- Inspired by *Don't Make Me Think* (2nd edition 2005, Steve Krug),
  paraphrased further from Danilo's wiki synthesis of Sillence's
  trust-is-visual finding, the Theofanos & Redish screen-reader
  scanning research Krug cites, and the universal-design argument
  that accessibility done well refills goodwill for every user.
