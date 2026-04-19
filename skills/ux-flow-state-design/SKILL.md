---
name: ux-flow-state-design
description: Use when designing productivity or creative apps — balance challenge with skill, minimize interruptions, provide clear feedback loops.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the product is meant to support deep work, creative flow, or
sustained performance — code editors, writing tools, design canvases, data
analysis environments, practice and learning apps. Fires when users report
feeling "kicked out" of their work, when latency or popups break
concentration, when the difficulty curve is badly tuned (bored or
overwhelmed), or when feedback about their actions feels delayed or unclear.

## Preconditions

- The product has a primary activity that benefits from sustained
  concentration rather than brief transactional visits.
- The latency budget for core interactions (typing, dragging, rendering,
  compiling) can be measured.
- The interruption surface (notifications, popups, modals, toasts, auto-save
  dialogs) can be enumerated and controlled.
- The difficulty progression (for learning or gamified products) can be
  tuned against the user's skill growth.

## Execution Workflow

1. Use Read or Bash to measure the latency of primary actions. Typing
   feedback should land well under 100ms; rendering updates should feel
   immediate; longer operations should show a progress indicator rather
   than a silent wait.
2. Inventory every interruption source. Notifications, modals, toasts,
   onboarding nudges, upgrade prompts, permission dialogs — all count. Each
   break is a task-switch, and task-switches cost the user roughly twenty
   minutes to rebuild deep focus.
3. Apply the three flow conditions: clear goals, immediate feedback, and a
   challenge roughly matched to skill. Every interaction should tell the
   user exactly what to do next; every action should produce perceptible
   feedback; the difficulty should neither bore nor overwhelm.
4. Tune the challenge curve. If the user skill grows, the product must
   either open new depth or give the user tools to invent their own
   challenge. Boredom and anxiety both break flow; the narrow channel
   between them is where sustained performance lives.
5. Batch interruptions. If notifications, updates, or nudges are needed,
   group them into scheduled moments between focus sessions rather than
   interrupting mid-flow.
6. Respect the user's model of "done" for each step. Every interaction
   should have a clear end state. Open loops that leave the user wondering
   whether the save worked, whether the command took effect, or whether the
   system is still thinking, break the sense of control that flow requires.
7. Design for invisibility once mastered. When the user is fluent, the
   interface should fade from consciousness; they should feel engaged with
   the work, not with the tool. Affordances can remain available but should
   not compete for attention.
8. Use Edit to cut unnecessary interruptions, tighten feedback latency, and
   tune difficulty ramps. Measure again after each change.

## Rules: Do

- Keep immediate-action feedback under roughly 100ms; longer operations
  show progress rather than silence.
- Batch non-urgent interruptions into scheduled moments outside flow
  sessions.
- Give every action a clear, perceptible end state so the user knows
  "done" without guessing.
- Match challenge to skill, opening depth as the user grows rather than
  raising the floor uniformly.
- Make the interface recede once the user becomes fluent; avoid
  permanent onboarding.

## Rules: Don't

- Don't interrupt flow with upgrade prompts, "did you know" nudges, or
  unrelated notifications during an active session.
- Don't let critical feedback land late — users will assume nothing
  happened and repeat the action, multiplying state errors.
- Don't leave tasks with ambiguous completion (spinner with no resolution,
  autosave with no confirmation, command with silent result).
- Don't gamify for gamification's sake on a product whose users are
  already intrinsically motivated; extrinsic rewards can undermine the
  intrinsic pull that created flow in the first place.
- Don't let onboarding, tutorials, or modal chrome live forever in the
  interface once the user has passed them.

## Expected Behavior

With the skill applied, users describe the product as "fast" and
"unobtrusive" even when the actual tasks are complex. Sessions lengthen;
users make fewer trivial mistakes; creative or analytical work progresses
with less visible friction. Metrics that correlate with deep use — lines
written, problems solved, designs iterated — increase without any single
feature change explaining it, because the underlying attention environment
improved.

When flow breaks, it does so for a reason the user chose (they decided to
switch tasks) rather than one the product imposed. Support conversations
shift from "your tool keeps interrupting me" to substantive questions about
the work itself.

## Quality Gates

- Primary-action feedback lands under roughly 100ms, or a progress indicator
  appears within that window.
- No non-critical interruption fires during an active focus session unless
  the user explicitly requested it.
- Every interaction has a visible and perceptible completion state.
- Difficulty opens new depth as the user gains skill rather than blocking
  beginners or boring experts.
- The interface has a "quiet mode" or equivalent where chrome, tutorials,
  and promotional elements recede.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs
in v0.1.0. Pairs with `cog-attention-capture` (flow protects sustained
attention; the capture skill protects acute attention) and
`cog-cognitive-load` (lower load is a prerequisite for sustained flow).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: immediate-feedback latency budget, clear completion
  states on every action.
- Use "should" for: batching of non-urgent interruptions, a quiet mode
  for fluent users.
- Use "may" for: the specific difficulty ramp (gradual vs. adaptive vs.
  user-selectable) appropriate to the domain.

## Troubleshooting

- **"Users say the app is fast but they still feel tired after a session"**:
  Latency is fine but interruptions are bleeding attention. Inventory
  every popup and notification and cut the ones the user did not ask for.
- **"Beginners abandon but experts love it"**: The challenge floor is too
  high. Add an easier on-ramp or adaptive starting difficulty that opens
  full power as the user demonstrates skill.
- **"Feedback arrives but users still repeat actions"**: The feedback is
  present but not perceptible. Increase its salience (motion, sound,
  position) so the user registers it without hunting.
- **"Tutorial chrome is still on screen for a user who's been on the
  product for a year"**: Onboarding has no exit. Add a dismiss-for-good
  affordance and respect it permanently.

## Concrete Example

A code editor proposes two designs for autocomplete. Design A returns
suggestions in roughly 50ms, commits with Tab, and produces no other
ambient popups during a coding session. Design B returns suggestions in
about 500ms, occasionally injects an unrelated "tip of the day" panel,
and auto-opens a changelog modal once per session. Instrumentation shows
Design A users produce longer uninterrupted coding runs and report fewer
context-switch symptoms. Design B users consistently lose their place
every few minutes, because even when the suggestion is correct, the
latency breaks the keystroke-to-result loop that sustains typing flow,
and the unrelated popups drop them out of the mental model of the code
they were writing. Switching the product to Design A improves not just
latency numbers but also self-reported focus, and support tickets about
"feeling scattered" fall sharply.

## Sources

- `[[concepts/cognicao-pensamento]]`
- `[[sources/neuro-experience-skill]]`
- Inspired by Mihaly Csikszentmihalyi's flow research and *100 Things Every
  Designer Needs to Know About People* (2011, Susan Weinschenk), paraphrased
  further from Danilo's wiki synthesis on feedback latency, challenge-skill
  balance, and interruption cost.
