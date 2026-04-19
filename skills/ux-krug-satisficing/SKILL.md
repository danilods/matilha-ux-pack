---
name: ux-krug-satisficing
description: Use when optimizing conversion or first-use experience — apply Krug's fact that people don't read, they satisfice; design for scanning, not reading.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when a page has strong content but weak conversion, when hero sections
drift past two hundred words, when copy is being written for a first-time
visitor who has twenty other tabs open, or when a team is debating whether
a label should be "accurate" or "clever." Fires on landing pages, signup
flows, docs home pages, checkout surfaces — any screen where the user is
deciding whether to stay in the first few seconds. The skill accepts
Krug's empirical finding that users do not read pages, they skim them,
and pick the first plausible option rather than comparing alternatives.

## Preconditions

- The surface has a primary goal (sign up, buy, click through, find an
  answer) and a way to measure whether first-time visitors reach it.
- There is room to cut copy, not only to restyle it; the skill works by
  removing, chunking, and obvious-naming, not by decorating.
- The team can write plainly; "Sign Up" beating "Join the Community" is a
  voice decision the team has to accept before the skill can land.

## Execution Workflow

1. Use Read to scan the page the way a first-time visitor would — three
   seconds of movement, eye landing on whichever word is largest, hand
   already on the back button. Record what is visible above the fold and
   what is not.
2. Answer the three-second test. Can a new visitor say, within three
   seconds, what this is, what they can do here, and why here rather than
   elsewhere? If any of those three answers is "I'd need to read more,"
   the page is failing the scan.
3. Trim toward satisficing. Users pick the first reasonable option, not
   the best one. That means the page rewards obvious over clever — "Sign
   Up" beats "Join the Community," "Pricing" beats "Investment," "Log
   in" beats "Enter the House." Obvious naming short-circuits the
   comparison the user is not going to make anyway.
4. Design for scanning. The page should be legible as a set of chunks, not
   as a paragraph. Headings act as waypoints, bullets as parallel
   choices, bold keywords as anchors, whitespace as separation. The
   classic F-pattern and Z-pattern describe where the eye moves; arrange
   anchors along those paths.
5. Cut the hero. A two-hundred-word hero section will not be read.
   Rewrite to a one-line headline, a one-line subhead that adds the
   specific, and one primary call-to-action. The goal is that the
   above-fold region communicates in about two seconds, with the rest of
   the page reserved for visitors who have decided to stay.
6. Remove happy talk. Introductory paragraphs that explain the company's
   mission on the homepage, lengthy form instructions, and "we are
   pleased to welcome you" openers are exactly the content users skip.
   Cut them and watch nothing of value disappear.
7. Use Edit to rewrite the hero, rename the buttons, chunk the long
   blocks, and re-scan. Verify that every heading names the content
   below it truthfully, every button names the action it performs, and
   no paragraph exists that the primary reader is expected to actually
   read.

## Rules: Do

- Write labels and buttons that describe the action in the plainest words
  available; clever labels pay a tax on every scan.
- Structure content for the skim: headings, short paragraphs, bullets,
  bold keywords, whitespace between chunks.
- Keep the hero to one headline, one subhead, one primary call-to-action;
  move the long version further down the page.
- Assume the reader is busy, distracted, and already holding the back
  button; design so they can stay without reading anything they did not
  choose to read.
- Trim aggressively, then trim again. Krug's own rule is "get rid of half
  the words on every page, and then get rid of half of what's left."

## Rules: Don't

- Don't write button copy for the voice-and-tone guide at the expense of
  the function; "Join the Community" on a signup button costs conversion
  every time a scanning user doesn't parse it as signup.
- Don't open a homepage with a mission paragraph; put the mission in the
  about page for the few visitors who will read it there.
- Don't assume readers will work out what the product does from context;
  name it explicitly in the headline.
- Don't hide the primary action in a row of equally weighted buttons;
  satisficing users will pick whichever is closest to reasonable, which
  may not be the one the page wanted clicked.
- Don't let form instructions grow longer than the form itself; if
  instructions are that long, the field itself is wrong.

## Expected Behavior

With the skill applied, pages read in seconds rather than minutes.
First-time conversion rises without a visual redesign, because the copy
now does the work. Users who do bounce do so quickly and cleanly, which
means the page is actually delivering its message rather than producing
long confused sessions. Support tickets about "what does your product
do" fall. In qualitative research, new visitors describe the product in
close to the page's own words, which is the clearest signal that the scan
worked.

When the page still asks to be read, the symptoms persist. Above-fold
bounces stay high on otherwise-visited sessions. Heatmaps show clicks on
the logo and the nav but not on the primary call-to-action. Users in
research can describe what the page looked like without being able to
describe what the product does — a pure scan with no content retained.

## Quality Gates

- Every button and link describes its action in ordinary words.
- The hero above the fold fits a headline, a subhead, and one primary
  call-to-action.
- Every paragraph over three sentences is either chunked, cut, or moved
  below the fold.
- The page passes the three-second test: what is this, what can I do,
  why here.
- Instructional copy for forms, dialogs, and flows has been reduced to
  the minimum a first-time user actually needs.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) whenever first-use experience, landing pages, or
conversion surfaces are being designed or reviewed. Pairs with
`cog-cognitive-load` (satisficing is the empirical shadow of working-memory
limits) and with `ux-visual-hierarchy` (scanning depends on rank signals
the hierarchy provides) and with `cog-progressive-disclosure` (long copy
that cannot be cut can often be deferred).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: plain-language naming of primary actions, the
  three-second answerability test on landing pages.
- Use "should" for: the one-headline-one-subhead-one-CTA hero shape, the
  halve-the-words discipline on drafts.
- Use "may" for: the specific voice inside the constraint of
  obviousness, the exact style of chunking (bullets vs. numbered vs.
  card-based).

## Troubleshooting

- **"Hero rewrite didn't lift conversion"**: check that the headline
  names the product in the user's language, not the company's. "A
  collaborative canvas for product teams" is better than "The future of
  visual thinking."
- **"Users click the logo instead of the CTA"**: the CTA is too polite
  or too generic. Name the action the page wants — "Start free," "Get
  the template," "See pricing" — and make it visually louder than the
  logo.
- **"Landing page reads great, but sign-ups are still low"**: the
  signup button probably does not match the landing language. Make the
  CTA copy identical on the landing and on the signup page so the user
  recognizes the continuation.
- **"The team insists the long hero is 'on brand'"**: move the long
  version to a below-the-fold section or an about page. The brand voice
  can live in places the scanner chooses to enter; the hero is not one.

## Concrete Example

A SaaS homepage carries a two-hundred-word hero: a paragraph about the
company's origins, a paragraph about its philosophy, and a final sentence
mentioning the product. A first-time visitor bounces within five seconds
having absorbed nothing. The rewrite collapses the hero to a single
headline naming the product ("A shared whiteboard for remote product
teams"), a single subhead adding the specific ("real-time canvas, voice,
and structured frames"), and one primary button ("Start free"). Below
the fold, the original paragraphs live on as an "our story" block for
visitors who opt in to read. Above-fold, the page now communicates in
about two seconds, and the sign-up rate climbs by roughly a third. The
content the team was proud of is still there; it has been moved to where
the few users who will actually read it can find it, instead of blocking
the many who will not.

## Sources

- `[[concepts/leis-de-krug]]`
- `[[sources/nao-me-faca-pensar]]`
- Inspired by *Don't Make Me Think* (2nd edition 2005, Steve Krug) and
  *100 Things Every Designer Needs to Know About People* (2011, Susan
  Weinschenk), paraphrased further from Danilo's wiki synthesis of Gary
  Klein's satisficing work with firefighters and the E. B. White "omit
  needless words" discipline Krug leans on.
