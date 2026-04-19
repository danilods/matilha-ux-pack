---
name: ux-trust-by-design
description: Use when designing auth, payments, or high-stakes interactions — apply trust signals, anecdotes over data, error-recovery trust repair.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the interaction carries real stakes for the user — paying, sharing
credentials, uploading sensitive data, deleting something irreversible,
consenting to legal terms. Fires when a flow is about to ask for trust and
nothing in the current design has been calibrated for it, when error recovery
is clumsy and the user walks away feeling burned, or when a new audience
encounters the product and the conversion curve dies at the first high-stakes
step. The skill treats trust as a reservoir that fills and drains based on
every micro-interaction, and designs the high-stakes moment to add to it
rather than drain it.

## Preconditions

- The high-stakes surfaces are identifiable (auth, payment, data export,
  deletion, legal consent).
- The product has a real story to tell about how it handles the stakes —
  real security posture, real data policies, real recovery paths. Faking
  the story is out of scope.
- The team can measure drop-off at each high-stakes step so the impact of
  trust signals can be evaluated.

## Execution Workflow

1. Use Read to map every high-stakes surface. Each payment form, data
   upload, credential entry, irreversible action, and consent moment is a
   spot where the trust reservoir is either topped up or drained. Note
   which ones currently carry trust cues and which don't.
2. Layer trust signals appropriate to the stakes. Payment forms need lock
   icons, PCI badges, explicit card-handling language, and a visible
   fallback ("use a different card"). Credential entry needs clear
   explanation of what's stored and why. Consent moments need plain
   language and visible opt-out. Irreversible actions need reversibility
   or at least a prominent undo window.
3. Prefer concrete anecdotes to abstract data. Weinschenk's research on
   anecdotes-over-statistics means "last Tuesday we blocked 10,000 fraud
   attempts" outperforms "99.9% uptime." One real story about a real
   customer recovering from a real incident is worth more than a page of
   compliance badges.
4. Treat error recovery as trust repair. The user's reservoir dropped;
   the recovery interaction either refills it or drains the rest. A
   failed payment should surface what happened, why, and exactly what to
   do next, in the user's language. A bounced email should explain which
   address failed. A rejected upload should say what format worked.
5. Kill anti-patterns that drain without signaling. Hidden pricing that
   surfaces at checkout, surprise charges on the first invoice, friction
   on account deletion, dark-pattern unsubscribe flows — each of these is
   a drain the user feels even if they can't name it. Remove them before
   adding any proactive trust signal; no amount of lock icons covers
   surprise charges.
6. Keep trust promises visible over time. The checkout page says the card
   is handled by a named provider; six months later the recurring-charge
   email still references the same policy. Consistency across the
   lifecycle is what allows trust to compound rather than reset at each
   step.
7. Use Edit to install the trust signals, rewire the error messages for
   recovery, and remove the drain patterns. Instrument drop-off at each
   high-stakes step so the impact is measurable.

## Rules: Do

- Place trust cues at the exact moment the stakes spike — the payment
  form, the credential field, the delete confirmation, the consent
  screen.
- Tell concrete stories: who, what, when, outcome. Anecdote persuades
  where abstract claim does not.
- Make error recovery a deliberate trust repair: acknowledge what
  happened, explain plainly, show the next action.
- Keep promises consistent across the lifecycle — the checkout language
  matches the receipt language matches the support article.
- Remove drains before adding signals; hidden pricing and surprise charges
  undo every other trust-building move.

## Rules: Don't

- Don't rely on generic badges as a substitute for real disclosure — a
  lock icon without clear card-handling language reads as decoration.
- Don't write error messages that blame the user ("invalid input"); the
  user doesn't know what was invalid and now trusts the product less.
- Don't require the user to read a legal page to find out what's actually
  happening; put the consequential facts in plain language on the
  surface.
- Don't add friction to account deletion, data export, or unsubscribe.
  The reservoir drains more on the exit than on the entrance, and word
  spreads.
- Don't tell abstract stories where concrete ones exist; "we care about
  security" is empty, "here's how we responded to the October incident"
  is evidence.

## Expected Behavior

With the skill applied, high-stakes flows convert closer to the low-stakes
baseline rather than cliffing. Users describe the product as "trustworthy"
in terms they can articulate — they point at the card-handling explanation,
the specific named provider, the fact that deletion actually worked. Error
recovery leaves the user better off than a clean success would have, because
the product handled the failure like an adult. Support volume shifts away
from "did you actually charge me?" and toward substantive product questions.

When trust is drained rather than built, the signals are diffuse but real.
Drop-off spikes at high-stakes steps without obvious UX flaws. Reviews
mention "felt sketchy" without pointing at anything specific. New users
convert once and don't return. The reservoir metaphor catches all of this:
the drains were small individually and fatal in aggregate.

## Quality Gates

- Every high-stakes surface carries at least one concrete trust cue, not
  just a generic badge.
- Error messages state what happened, why, and what to do, in the user's
  language.
- Anecdotes outnumber abstract claims in trust-related copy; specifics
  over platitudes.
- Account deletion, data export, and unsubscribe paths have no more
  friction than signup.
- Pricing and billing language is consistent from checkout through the
  recurring receipt.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when high-stakes surfaces appear. Does not delegate to
other packs in v0.1.0. Pairs with `ux-social-proof` (peer evidence is a
trust signal when authenticity carries the burden) and with
`ux-emotion-in-ui` (trust signals are emotional interventions, not
rational ones — the design speaks to the user's state, not their
reasoning).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: accurate disclosure on payment and credential surfaces,
  no dark-pattern friction on exit paths.
- Use "should" for: concrete anecdote over abstract claim, consistent
  promise across the lifecycle.
- Use "may" for: the specific badge set or copy treatment appropriate to
  the domain.

## Troubleshooting

- **"Checkout conversion cliff with no obvious design flaw"**: the trust
  reservoir is drained somewhere upstream. Audit for hidden pricing,
  surprise fees on the receipt, or recent review patterns that flagged
  friction.
- **"Error rate is fine but support tickets are angry"**: error messages
  are failing as trust repair. Rewrite each one for acknowledgment,
  explanation, and next action.
- **"High-stakes flow has friction but removing it feels risky"**: the
  friction itself may be a trust signal (the user expects a delete
  confirmation), but the friction shape matters. Keep the pause, rewrite
  the message for clarity.
- **"Users report the product feels cold"**: the trust copy is all
  abstract compliance language. Find one or two concrete incidents or
  decisions and tell those stories instead.

## Concrete Example

A checkout page layers five trust cues into a single micro-interaction. A
lock icon sits next to the card field, paired with plain language that
names the payment processor and states the card details never reach the
product's own servers. A small PCI-compliant badge confirms the posture
without leaning on it. The pricing line is consistent with every earlier
pricing surface — no surprise fees. A "use a different card" affordance
sits visibly near the submit, so a failed card doesn't feel like a dead
end. If the charge fails, the error message names the likely cause in the
user's language, offers the fallback, and confirms no charge was attempted.
Each of these elements is small. Taken together, they make the checkout
feel like a place the user can spend money safely. Contrast this with a
checkout that simply says "payment failed, try again" — same payment
processor, same PCI compliance, but the trust reservoir drains by the
second attempt.

## Sources

- `[[concepts/emocoes-sentimentos]]`
- `[[concepts/reservatorio-boa-vontade]]`
- Inspired by Steve Krug's *Don't Make Me Think* (3rd ed., 2014) and *100
  Things Every Designer Needs to Know About People* (2011, Susan
  Weinschenk), paraphrased further from Danilo's wiki synthesis of
  Sillence's 83%-of-rejections-are-design finding and Weiner's
  trust-as-predictor-of-happiness result.
