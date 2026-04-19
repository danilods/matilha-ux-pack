---
name: ux-typography-for-reading
description: Use when picking fonts or designing text-heavy content — optimize legibility, line length, and scan-vs-read mode transitions.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the interface carries meaningful prose — docs, article bodies, long
product descriptions, help centers, release notes, onboarding walls of copy —
and the typography decisions haven't been made deliberately. Fires when body
text feels cramped, when readers hit line-wrap errors ("I lost my line"), when
the page mixes scanning surfaces (lists, headings) with reading surfaces
(paragraphs) without signaling the transition, or when a decorative font has
crept into a critical instruction.

## Preconditions

- The content is known to include prose, not just UI chrome or micro-copy.
- The target medium is screen-based (web, desktop app, mobile) rather than
  print, since screen and paper respond differently to the same type choices.
- A draft font stack, body size, and line-height baseline are either set or
  can be proposed.
- The reading goal for each text block is understood: scan mode (quickly
  locate), read mode (understand in order), or reference mode (return to a
  known fact).

## Execution Workflow

1. Use Read to open the page source or stylesheet and record the current font
   family, size, line-height, line length (characters per line at the target
   viewport), and weight for each text role (body, heading, caption, code).
2. Classify every text block as scan, read, or reference. Scanning surfaces
   use headings, bold, and lists; reading surfaces use sustained paragraphs
   with comfortable line length; reference surfaces can be denser because the
   user returns to known targets.
3. For body copy, set size to at least 16px (or the equivalent rem). Smaller
   sizes cause micro-squinting, which bleeds into a negative emotional read of
   the content itself.
4. Tune line length. Aim for roughly 50 to 75 characters per line in reading
   surfaces. Longer lines are technically faster to parse but produce line-wrap
   regressions, so prefer the readable range over the "efficient" one.
5. Choose a font with generous x-height for screen use. X-height, not nominal
   point size, determines how legible a body looks at small scales. Verdana,
   Tahoma, Inter, and Source Sans are safer defaults than display faces.
6. Keep the serif-vs-sans debate subordinate to x-height and rendering. At
   normal body sizes on modern screens, the difference is small; at very
   small sizes or low-DPI screens, sans-serifs with wide x-height tend to win.
7. Reserve decorative or condensed faces for moments of deliberate emphasis.
   Never use them for instructions, errors, or calls to action — readers
   unconsciously judge the underlying task as harder when the type is hard
   to read.
8. Establish a clear scan-vs-read rhythm. Use Edit to introduce descriptive
   headings every few paragraphs, bold key terms sparingly (noise grows
   quickly), and break sequential instructions into numbered lists.
9. Verify with a reading test: scroll through on a representative device and
   confirm you can both skim the surface (headings, bolds, first sentences)
   and sink into a paragraph without hunting for the next line.

## Rules: Do

- Set body text to 16px or larger, then tune line-height between 1.4 and 1.6.
- Target 50 to 75 characters per line in reading surfaces.
- Choose fonts with tall x-height for screen rendering, independent of the
  serif-vs-sans preference.
- Separate scan and read modes with clear headings, lists, and paragraph
  rhythm so readers can choose their mode without effort.
- Use descriptive headings that activate the reader's mental schema before
  they read the paragraph below.

## Rules: Don't

- Don't set long passages in ALL CAPS — readers have had far less practice
  parsing capitals, so speed and comprehension drop.
- Don't use decorative or script faces for instructions, error messages, or
  primary calls to action; the "difficult to read" feel transfers to the task.
- Don't push line length past roughly 80 characters for reading surfaces,
  even if the container looks empty without stretching.
- Don't rely on font size alone to build hierarchy — pair size with weight,
  color contrast, and whitespace.
- Don't bold or italicize so much of the body that emphasis loses meaning.

## Expected Behavior

When typography is tuned for reading, the user can glide through long copy
without micro-fatigue. Eyes move in predictable saccades, regressions stay
under control, and the reader can toggle between scanning and reading without
consciously shifting gears. Headings prepare the brain to accept what comes
next, bolded terms highlight true anchors rather than every second noun, and
paragraphs end before the reader wants them to, not after.

The change is often invisible individually but compounds across a session.
Users stay longer on help articles, finish onboarding walls, and misread
error messages less often because the type system stops fighting them.

## Quality Gates

- Body copy renders at 16px or above on the smallest supported viewport.
- Line length on reading surfaces measures between 50 and 75 characters at
  the default breakpoint.
- No decorative or script font appears in any instruction, error message, or
  primary call to action.
- Headings are descriptive enough that a scan-only reader can follow the
  document's structure.
- Bold and italic together cover less than roughly 10 percent of body text on
  any given surface.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when UX decisions surface. Does not delegate to other packs in
v0.1.0. Pairs with `ux-visual-hierarchy` (hierarchy decides which text ranks
matter) and `cog-cognitive-load` (typography is a cheap lever for lowering
reading-time load).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: 16px minimum body size, 50 to 75 characters per line on
  reading surfaces, no decorative faces in CTAs or errors.
- Use "should" for: x-height preference, specific bold coverage caps.
- Use "may" for: serif vs. sans choice within the legibility envelope.

## Troubleshooting

- **"Readers keep losing their line"**: Line length is almost certainly past
  the comfortable range. Cap the container width or introduce a max-width
  that enforces roughly 65 characters at the default breakpoint.
- **"Users report the page feels unprofessional even though copy is strong"**:
  Decorative or inconsistent fonts are leaking into semi-formal roles. Audit
  every text role and consolidate around one display family and one body
  family at most.
- **"Scanning works but reading mode is exhausting"**: The page is all
  bullets and bolds. Restore paragraph rhythm in the reading sections —
  scanning surfaces and reading surfaces need different treatments.
- **"Small body text looks fine on my desktop"**: Test on a low-DPI laptop or
  phone held at arm's length. Screen rendering at small sizes is where
  x-height and legibility differences start mattering most.

## Concrete Example

A blog template sets article bodies in a condensed display face at 14px, with
paragraphs stretching the full 1024-pixel container — roughly 140 characters
per line. Readers report fatigue and abandon mid-article. Applying the skill,
the template switches to a high-x-height sans at 17px with a 1.55 line-height,
and the article container narrows to a width that yields about 68 characters
per line. Descriptive subheadings appear every few paragraphs to give scanners
a map. Within a week, the share of sessions that reach the article's
footnotes roughly doubles, and complaints about "hard to follow" drop
sharply. The words didn't change; the surface stopped punishing the eye.

## Sources

- `[[concepts/leitura-tipografia]]`
- `[[sources/100-things-every-designer]]`
- Inspired by *100 Things Every Designer Needs to Know About People* (2011,
  Susan Weinschenk), paraphrased further from Danilo's wiki notes on
  saccades, x-height, and Dyson's line-length research.
