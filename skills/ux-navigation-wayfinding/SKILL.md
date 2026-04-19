---
name: ux-navigation-wayfinding
description: Use when designing navigation or information architecture — apply breadcrumbs, current-location signals, consistent layout; skeptically evaluate the 3-click rule.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the product has more than a handful of pages and a user arriving
mid-site needs to orient themselves — docs, dashboards, admin consoles,
multi-section marketing sites, any SaaS with settings nested several
levels deep. Fires when a team is debating the depth of a menu, when
search traffic lands users on internal pages without context, when a
redesign is tempted to chase the "three-click rule," or when orientation
complaints appear in research ("I got lost in settings"). The skill
treats navigation as wayfinding — answering where am I, how did I get
here, where can I go — rather than as a click-count problem.

## Preconditions

- The site or app has more than a few pages, and users land on internal
  pages at least some of the time via search, deep links, or share URLs.
- The team can modify the chrome — nav bar, sidebar, breadcrumb slot, page
  title — not only the page bodies.
- A recognizable home or top-level page exists and can be used as the
  fixed reference point users return to.

## Execution Workflow

1. Use Read to land on the deepest page of the product or site without
   going through the home page. Ask three questions out loud: where am
   I, how did I get here, and where can I go? If any answer requires
   guessing, the navigation is failing its primary job.
2. Install the "where am I" signals. The active nav item is highlighted.
   Breadcrumbs show the path from the home down to the current page.
   The page title in the browser tab matches the H1 on the page. The URL
   reads as a human-readable trail.
3. Install the "how did I get here" signals for contexts where depth
   matters — docs, settings, admin trees. Breadcrumbs are the cheapest
   and most effective; "back to X" buttons help when a detail view was
   reached from a specific list.
4. Keep layout consistent across pages. Primary nav at the top, primary
   action on the right, secondary navigation in a predictable location.
   Users build a mental map of the chrome; every deviation forces them
   to re-orient. Consistency carries more weight than cleverness on the
   chrome, even when the individual deviation looks like an improvement.
5. Treat the home page as the north star. Logo in the top left that
   returns home from anywhere is a convention worth every pixel it
   costs. When users are lost, the only reliable recovery is the home
   they recognize.
6. Interrogate the three-click rule. Users do not count clicks; they
   count moments of uncertainty. Ten obvious clicks beat three
   ambiguous ones. A deep tree with clear signposts at every fork is
   easier to use than a shallow one where each fork requires a pause.
   Krug's second law, in short: the number of clicks is almost
   irrelevant if each click is plainly the right one.
7. Use Edit to add breadcrumbs, wire active states, align page titles,
   and stabilize the chrome layout. Re-test by landing on the deepest
   page fresh and re-asking the three wayfinding questions.

## Rules: Do

- Highlight the active item in the primary nav on every page, so the
  current location is visible without reading.
- Show breadcrumbs on any page more than one level deep in the
  information architecture.
- Match browser-tab title, page H1, and breadcrumb leaf to the same
  name; discrepancies erode the user's trust that they know where they
  are.
- Keep chrome layout consistent across the product; treat the nav, the
  primary-action slot, and the secondary nav as fixed positions.
- Make the logo a reliable return-to-home control from any page.

## Rules: Don't

- Don't optimize against the three-click rule at the expense of
  clarity; users prefer many obvious clicks to few ambiguous ones.
- Don't use clever section names on the nav (house-of-X, the-lab) when
  conventional names (Docs, Pricing, Dashboard) work; users scan for
  conventions and skip what they don't recognize.
- Don't hide breadcrumbs on pages reached from search or share links;
  the deep-link arrival is exactly the case where breadcrumbs earn
  their cost.
- Don't reshuffle the chrome between sections of the same product;
  consistency is more valuable than per-section optimization.
- Don't strand users on leaf pages with no visible path back up;
  "back" is the most-clicked control and the page should support it.

## Expected Behavior

With the skill applied, users describe the product as "easy to get
around" without being able to articulate why, which is the sign that
the chrome has become invisible in the helpful sense. Time spent
re-orienting after deep-linked arrivals drops. Search traffic that
lands on internal pages converts at rates closer to home-page arrivals,
because the deep page now supplies the context that search stripped.
Support tickets about "where do I find X" fall because the answer is
visible in the nav and breadcrumbs.

When wayfinding is weak, the symptoms are characteristic. Users return
to the home page between tasks instead of navigating sideways, because
home is the only place they are sure of. Support questions concentrate
on "how do I get back to Y from Z." Analytics shows high re-entry to
home from deep pages, which reads as a breadcrumb absence rather than a
home-page success.

## Quality Gates

- The deepest page in the product answers "where am I, how did I get
  here, where can I go" without a guess.
- Browser-tab title, page H1, and breadcrumb leaf match for every page.
- Breadcrumbs appear on every page more than one level deep.
- The primary nav's active state is visible on every page.
- Chrome layout — nav position, primary action, secondary nav, logo —
  does not shift between top-level sections.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when designing site or product information architecture,
adding a new section, or auditing a redesign. Pairs with
`ux-visual-hierarchy` (active state and breadcrumb depth are ranking
decisions), with `ux-krug-satisficing` (plain, obvious section names
support the scan), and with `cog-cognitive-load` (consistent chrome
reduces the working memory the user has to spend on the shell).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: active nav state on the current section, matching
  tab-title and H1, working return-to-home from the logo.
- Use "should" for: breadcrumbs on any depth-two-or-deeper page,
  consistent chrome layout across sections.
- Use "may" for: the visual style of the breadcrumb, the specific
  treatment of the active state (underline, color, background).

## Troubleshooting

- **"Users ask 'how do I get back to the project list'"**: breadcrumbs
  are missing from the detail view. Add "Projects > My Project" and
  confirm the back-path now reads at a glance.
- **"Search traffic to docs bounces more than docs home traffic"**: the
  deep docs pages lack breadcrumbs, active nav state, or both. A
  search-arriving user never saw the doc nav, so the page has to
  reveal it.
- **"A redesign chased fewer clicks and satisfaction fell"**: the
  navigation probably collapsed too many decisions into one
  mega-menu. Re-expand with obvious intermediate forks; the count
  rises and the user's confidence returns.
- **"The logo doesn't go home on this page"**: fix it today. That one
  broken convention undermines every other recovery path.

## Concrete Example

A developer-tooling docs site presents a deep API reference for an
authentication endpoint. The browser tab reads "OAuth - Authentication
- API - Docs," which matches the breadcrumb near the top of the
content area: "Docs > API > Authentication > OAuth." The left sidebar
highlights "OAuth" inside the expanded "Authentication" group; the
top nav shows "Docs" as the active section. A "Back to Authentication"
link sits above the page title for readers who want to step up one
level without using the breadcrumb. A user arriving via a search
result lands in context immediately and can follow the trail up to
the API overview, across to a related endpoint, or home to the docs
root. The same page without breadcrumbs and without an active sidebar
state roughly doubles the time users take to re-orient, and the
sessions that arrive via search convert at meaningfully lower rates.

## Sources

- `[[concepts/navegacao-web]]`
- `[[sources/nao-me-faca-pensar]]`
- Inspired by *Don't Make Me Think* (2nd edition 2005, Steve Krug) and
  the wayfinding literature in information architecture, paraphrased
  further from Danilo's wiki synthesis of Krug's department-store
  metaphor, Jared Spool's "information scent," and the 30-40 percent
  share of clicks that goes to the back button and the logo.
