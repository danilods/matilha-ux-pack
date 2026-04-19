---
name: ux-swiss-cheese-errors
description: Use when designing error handling or high-stakes actions — apply defense-in-depth (Reason's Swiss Cheese model), slip/mistake/violation classification, recovery paths.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a surface can cause real damage if something goes wrong — sending,
deleting, paying, submitting, publishing, escalating permissions. Fires when
the current error strategy is a single validation step, when error messages
blame the user without offering a path forward, when a recent incident
showed the product allowed a preventable mistake, or when "just add a
confirmation" is the only defense the team has considered. The skill
installs defense-in-depth: several imperfect layers that together catch
what any one of them would miss.

## Preconditions

- The high-consequence actions on the surface can be enumerated (send,
  delete, pay, submit, revoke, publish).
- The user's likely state at each moment can be characterized — rushed,
  tired, multitasking — so the defenses target realistic failure modes.
- Telemetry can reveal which errors actually happen and at what
  frequency, so layers target real failure paths rather than imagined
  ones.

## Execution Workflow

1. Use Read to inventory the high-consequence actions. For each one, ask
   what a bad outcome looks like — the wrong message sent, the wrong
   repo deleted, the wrong amount charged — and how recoverable it is.
   Irreversibility raises the defense budget.
2. Classify the realistic failure modes. Reason's taxonomy has three.
   Slips are motor or attention errors — the user clicked the wrong
   button, missed the typo, dragged to the wrong folder. Mistakes are
   mental-model errors — the user thought the button did X when it does
   Y. Violations are deliberate bypasses — the user (or attacker) chose
   to ignore the safeguard. Each needs different defenses.
3. Install the slip layer. Slips respond to undo, confirmation for
   irreversible moves, and visual affordances that make the right target
   easier to hit than the wrong one. Gmail's undo-send window is the
   canonical slip defense.
4. Install the mistake layer. Mistakes respond to clearer feedback,
   inline examples, preview affordances, and micro-copy that shows what
   the action will do before it runs. A mistake defense tells the user
   "this will send to external recipients" before the send happens, not
   after.
5. Install the violation layer. Violation defenses are about policy and
   monitoring — rate limits, permission gates, anomaly alerts,
   escalation flows. The design surface cannot prevent a determined
   violation, but it can make the right choice the easier one and flag
   the wrong choice as it happens.
6. Require a recovery path. Every consequential action needs a way back,
   or at minimum a way to mitigate. Sent emails get undo or retraction.
   Deleted items go to a trash with a visible restore window. Payments
   get refund paths. A product without recovery feels brittle and trust
   drains on the first near-miss.
7. Use Edit to layer the defenses. Verify that no single layer carries
   the whole defense by imagining each layer failing in turn — if one
   miss leads to disaster, add a layer.

## Rules: Do

- Think in layers. Each defense is imperfect; the composition is what
  protects the user.
- Classify the failure mode before picking the defense. Slip, mistake,
  and violation each call for different interventions.
- Always ship a recovery path on consequential actions; undo, trash,
  refund, revoke.
- Write error messages that explain and guide, not ones that blame; a
  good message tells the user what happened, why, and what to do.
- Defend irreversible actions more than reversible ones. Deletion,
  publication, and escalation deserve more layers than they typically
  get.

## Rules: Don't

- Don't rely on a single confirmation dialog as the sole defense on a
  high-consequence action; users click through confirmations under load.
- Don't punish the user in the error copy. "You entered invalid data"
  tells the user nothing and drains trust at the worst moment.
- Don't optimize a defense layer so aggressively for power users that
  first-timers walk into the same trap every time.
- Don't build defenses for imaginary failure modes while ignoring the
  real ones the telemetry shows. Defense budgets are finite.
- Don't treat the violation layer as a UX problem alone; it needs policy
  and monitoring, and the design should route to those systems rather
  than substitute for them.

## Expected Behavior

With the skill applied, near-misses get caught, and real misses remain
recoverable. Users describe the product as "forgiving" or "easy to
trust with real work" — the specific praise varies, but the underlying
feeling is that the product won't punish a moment of distraction. Error
messages feel like help, not blame. When an incident still happens, the
recovery path actually works, and the telemetry captures the pattern so
the defenses evolve. Teams start using the slip/mistake/violation
taxonomy in design reviews, which tightens the conversation.

When the model isn't applied, the signals are vivid. Support tickets
over "I sent the wrong thing and can't get it back." Reviews that
mention "I deleted everything by accident." Incident post-mortems that
reveal a single confirmation dialog between the user and catastrophe.
The taxonomy makes these failures predictable in advance.

## Quality Gates

- Every high-consequence action has layered defenses covering at least
  slip and mistake modes; violations are routed to policy.
- Recovery paths exist and are reachable in two taps from the point of
  regret.
- Error messages explain, guide, and never blame; they are written in
  the user's language.
- The slip/mistake/violation classification has been applied to each
  defense, so the team can articulate which layer catches what.
- Telemetry monitors actual error rates and near-miss patterns, and the
  defense layers evolve based on the data.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when high-consequence flows are being designed. Does
not delegate to other packs in v0.1.0. Pairs with `ux-yerkes-dodson`
(stressed users slip more, so defenses for stressful contexts need to
be more forgiving) and with `ux-trust-by-design` (recovery paths
are where trust either repairs or shatters).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: a recovery path on consequential actions, layered
  defenses on irreversible actions.
- Use "should" for: slip/mistake/violation classification for each
  defense, telemetry on actual near-misses.
- Use "may" for: the specific defense mechanics (undo-window duration,
  trash-retention period, confirmation phrasing).

## Troubleshooting

- **"Users regularly delete the wrong item"**: the slip layer is
  missing. Add a trash with a visible restore window and a short undo
  affordance immediately after the action.
- **"Users say they 'didn't know' what the button would do"**: that's a
  mistake, not a slip. Add inline preview, clearer labels, and micro-
  copy that states the consequence before the action fires.
- **"One user is circumventing the safeguard repeatedly"**: that's a
  violation, not a mistake. Route to policy (rate limits, permission
  review, anomaly alert); design alone can't stop a determined bypass.
- **"Confirmation dialog exists but errors still happen"**: single-layer
  defense. Users click through confirmations under load. Add undo or
  trash to catch what the confirmation misses.

## Concrete Example

Gmail's Send button is layered. A draft autosaves continuously, which
catches the slip of an accidentally closed tab. An external-sender
banner appears when the recipients include addresses outside the
organization, which catches the mistake of sending internal content to
an outside party. A confirmation appears when an attachment is
referenced in the body but missing, which catches the slip of forgetting
the file. A 5-to-30-second undo window after send catches the slip of
clicking too soon. Rate limits and spam detection catch the violation
of bulk send. No single one of these layers is perfect. An attacker can
bypass the external-sender banner, the undo window is short, and the
autosave can lose a last keystroke. Together, they make sending an
email in Gmail feel forgiving in a way that a single confirmation
dialog would not. That's defense-in-depth.

## Sources

- `[[concepts/erros-usabilidade]]`
- `[[sources/100-things-every-designer]]`
- Inspired by James Reason's *Human Error* (1990) and *100 Things Every
  Designer Needs to Know About People* (2011, Susan Weinschenk),
  paraphrased further from Danilo's wiki synthesis of Van der Linden's
  error-consequence classification and Morrell's performance-error
  taxonomy.
