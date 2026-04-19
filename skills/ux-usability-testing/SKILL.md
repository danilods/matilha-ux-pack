---
name: ux-usability-testing
description: Use when planning validation or research — 3-5 users catches 80% of issues; test what users actually do, not what they say they'd do.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a team is about to ship a meaningful change — a new signup
flow, a redesigned dashboard, an onboarding revision — and someone has
suggested "we'll see how it does in production." Fires when a design
debate has gone in circles on opinion, when a stakeholder asks for
"more data" before approving, when the plan is to launch and instrument
instead of testing and fixing, and when research budget discussions
frame usability testing as expensive. The skill installs the smallest
honest research habit that separates what users say from what users do
and catches most issues before they hit production.

## Preconditions

- A testable artifact exists — a prototype, a staging build, a
  clickable mockup, or at minimum a printout with a defined task flow.
- The team can define a small set of concrete tasks the user will
  attempt ("find the pricing page," "change your email notification
  settings," "cancel your subscription").
- Someone on the team is available to run the sessions, or a remote
  platform (Maze, Lookback, UserTesting, a shared Zoom) is set up to
  capture think-aloud sessions.

## Execution Workflow

1. Use Read to confirm the artifact is far enough along to be tested
   against the intended task. A prototype that blocks on every third
   click will produce noise about the prototype, not about the design.
2. Write three to five tasks the real user would actually attempt on
   this surface. Phrase them as goals, not as UI instructions — "find
   out how much the pro plan costs" rather than "click the pricing
   link in the nav." The task wording must not reveal the path.
3. Recruit three to five participants. Nielsen's empirical finding is
   that a small handful catches roughly four-fifths of usability
   issues; additional users produce diminishing returns. Krug's low-
   cost method works the same way — two or three rounds of three to
   four users each will surface more distinct issues than a single
   round of ten, because fixes happen between rounds.
4. Run the sessions with the thinking-aloud protocol. Ask the user to
   narrate as they work — "I'm looking for," "I don't know what this
   means," "I thought this would." The narration catches
   misinterpretations the silent click log misses; a user who hovers
   on the wrong control for ten seconds is telling you something the
   heat map cannot.
5. Watch behavior, not opinion. The strongest finding in usability
   research is that users reliably say things they do not do. They
   claim they would never click a flashy banner and then click it;
   they claim they read terms and scroll past them. Record both
   stated preference and observed behavior, and trust the behavior
   when they disagree.
6. Debrief with the team the same day. Krug's argument against long
   formal reports is that the team's capacity to fix outpaces the
   researcher's capacity to document; a one-hour debrief agreeing on
   the top few issues produces more fixes than a polished twenty-page
   deliverable. Prioritize issues by how many users hit them and by
   how close to the primary task they are.
7. Use Edit to apply the fixes, then re-test in a week with a fresh
   handful of users. The rhythm is test, fix, re-test; one-shot
   testing buys far less than repeated small rounds.

## Rules: Do

- Keep sessions small — three to five users per round — and run more
  rounds instead of larger ones.
- Phrase tasks as user goals, not UI instructions, so the path is
  discovered rather than revealed.
- Use thinking-aloud protocol to catch misinterpretations and dead-end
  paths the click log alone cannot reveal.
- Weight observed behavior over stated preference when the two
  disagree, because they will disagree often.
- Debrief the whole team the same day; the decision about what to fix
  belongs to the same group that can fix it.

## Rules: Don't

- Don't confuse focus groups with usability tests. Focus groups ask a
  small panel what they want in the abstract; usability tests watch
  one person at a time trying to use something. They answer different
  questions and are not substitutes for each other.
- Don't delay testing until a polished prototype exists; a paper
  sketch tested with three users beats a perfect mockup tested with
  none, and the insights arrive when they can still be applied
  cheaply.
- Don't over-recruit for representativeness on early rounds. Krug's
  point is that nearly everyone is a beginner inside an unfamiliar
  flow, so the recruiting bar is lower than the literature implies
  for most cases.
- Don't treat a usability test as a proof; it is a sample of
  behavior, designed to inform judgment rather than settle a debate
  with statistical certainty.
- Don't produce long deliverables at the expense of fixing the
  issues; a short list the team acts on beats a long report the team
  files away.

## Expected Behavior

With the skill applied, issues surface before launch rather than
after. The team's judgment calibrates to what real users actually do,
which changes the nature of design debate — arguments move from
opinion to observation. Conversion on shipped versions climbs because
obvious failures have been found and fixed on the bench. Qualitative
feedback post-launch shifts from "the signup was confusing" to
substantive product questions that only emerge once the surface
actually works.

When usability testing is skipped in favor of production
instrumentation, the symptoms compound. Teams ship a design, watch
metrics, form theories, ship a variant, watch metrics — a cycle that
costs weeks per iteration for findings a morning of testing would
have produced. Users who bounce in production do so silently; the
instrument sees the bounce but not the reason.

## Quality Gates

- Every significant surface has been tested with at least three users
  before launch.
- Tasks used in testing are user-goal framed, not UI-path framed.
- Sessions use thinking-aloud protocol, and observation is captured
  alongside stated preference.
- Findings from each round are discussed same-day with the team that
  can fix them.
- A re-test is scheduled after fixes, rather than treating the first
  round as a single event.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) whenever a design decision reaches a point where
observation would resolve it faster than debate. Pairs with any UX or
cognitive skill in the pack when the pack is being applied — a
usability test is the empirical check on any principle-led change.
Especially useful after `ux-krug-satisficing` (to confirm the scan
actually succeeds) and after `ux-choice-overload` (to confirm the
option-set change changes behavior, not only opinion).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: user-goal task phrasing, behavior-over-opinion
  weighting, same-day team debrief.
- Use "should" for: three-to-five participants per round, thinking-
  aloud protocol, repeat rounds with fixes between them.
- Use "may" for: the specific platform (Maze, Lookback, Zoom,
  hallway), the exact incentive per participant, the recording
  medium.

## Troubleshooting

- **"Stakeholders demanded a 20-person study"**: re-frame. Two
  rounds of five with fixes between them will find more and cost
  less than one round of twenty. Show the team the issue count from
  the first round of five.
- **"Participants said they loved it but didn't complete the task"**:
  this is the canonical behavior-versus-opinion gap. Weight the
  completion data and dig into where they stopped; the answer is
  in the silence, not the praise.
- **"A round found no significant issues"**: check the task set.
  Tasks that match the current design exactly will produce false
  negatives. Re-run with tasks written from a fresh user's goals.
- **"The team disagrees on the priority of fixes"**: the issue
  probably wasn't observed by enough users to carry the argument.
  Run a second small round targeting just that area before
  reopening the debate.

## Concrete Example

A team about to launch a new signup flow faces a choice: run the
"launch and watch the funnel" plan that was in the sprint, or pause
to run Nielsen-style testing. They run five quick Maze sessions with
target users at a total cost of a few hundred dollars and most of
an afternoon. Four of the five hit the same confusing label on step
two, three get lost on the verification email step, and two misread
the pricing at the end as "per user per month" instead of "per
month." The team fixes all three issues the same day, re-tests with
three more users the next morning, and ships. The post-launch
conversion comes in roughly forty percent higher than the prior
version's baseline because the preventable losses were prevented.
The alternative — ship and watch — would have produced the same
insights over four to six weeks of A/B testing at a cost many times
higher, with users churning through the bad version in the
meantime.

## Sources

- `[[concepts/testes-usabilidade]]`
- `[[sources/nao-me-faca-pensar]]`
- Inspired by *Don't Make Me Think* (2nd edition 2005, Steve Krug)
  and the Nielsen Norman Group's empirical work on sample sizes,
  paraphrased further from Danilo's wiki synthesis of Krug's "lost
  our lease" low-cost method and the Bechara finding that people
  know more than they can articulate — so watching matters more
  than asking.
