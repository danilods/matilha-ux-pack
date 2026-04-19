---
name: ux-social-proof
description: Use when designing conversion or signup flows — apply testimonials, "X users online", scarcity signals, with ethical limits.
category: ux
version: "1.0.0"
requires: []
optional_companions: []
---

## When this fires

Use when the surface is asking the user to take a decision with uncertainty
— signup, checkout, upgrade, first-time commitment to a product or plan.
Fires when conversion is below expectation on a page with strong copy and
clean design, when a new audience is being approached and trust has to be
established fast, or when the team is weighing whether to add urgency cues
and needs a principled line between legitimate social signal and manufactured
scarcity. The skill installs evidence that "other people made this choice and
it worked out" in a way the user can verify.

## Preconditions

- The product actually has the social evidence claimed — real reviews, real
  customers, real usage volume. Fabricating the signal is a different skill
  (fraud) and is out of scope.
- The target audience can be characterized, so the proof offered resembles
  them (B2B enterprise vs. indie maker vs. consumer buyer).
- The conversion surface can be instrumented so the impact of adding or
  removing proof is measurable.

## Execution Workflow

1. Use Read to inventory the existing proof surfaces. Are there testimonials,
   review counts, customer logos, usage numbers, expert endorsements, or
   third-party badges? Note which ones the user can verify and which look
   like the page is making a claim on its own behalf.
2. Pick the proof type that matches the audience. For B2B, customer logos
   from known firms and named expert endorsements carry weight. For SaaS
   reaching makers, recognizable indie-founder names and transparent usage
   counts work better. For consumer commerce, reviews volume, star ratings,
   and "people who bought this also bought" all pull. The proof has to
   resemble the decision-maker.
3. Favor peer-similar proof when available. A review from someone whose
   situation resembles the user's ("I'm a 5k runner and this app…") beats
   a celebrity endorsement for most products, because similarity is the
   stronger inference channel than fame.
4. Stack proof at the decision point, not on the homepage. The commitment
   page is where the doubt is highest; that's where review counts,
   testimonials, and badges do the most work. Generic homepage proof tends
   to be ignored.
5. Draw the ethical line. Urgency and scarcity cues are legitimate when they
   are accurate — the inventory really is low, the deadline really exists,
   the count of users online really reflects the system. Manufactured
   scarcity ("only 2 left!" when there are unlimited) is deceptive, and the
   pattern is increasingly recognized by users.
6. Provide a fallback for when proof is absent (new product, new audience,
   no reviews yet). Authority signals — a credible founder bio, team page,
   technical credentials, transparent explanation of how the product works
   — substitute for peer proof while the evidence base grows.
7. Use Edit to place proof at the decision surface, phrase it so the user
   can verify it, and trim any claim that crosses into manufactured
   urgency.

## Rules: Do

- Place proof at the moment of highest doubt — the pricing row, the signup
  submit, the checkout confirm — not only on the homepage.
- Prefer proof from people who resemble the user; peer similarity outperforms
  celebrity for most decisions.
- Keep proof verifiable — review counts link to reviews, customer logos
  link to case studies or at minimum appear on the customer's own site.
- Combine several proof types on a high-stakes surface (rating + review
  count + named testimonial + "others bought with" works harder than any
  one alone).
- When proof is absent, substitute credibility signals: a real team page,
  founder background, open technical writing, transparent roadmap.

## Rules: Don't

- Don't manufacture scarcity ("only 2 left" on infinite inventory, "17
  people looking" on a static page). The pattern is recognized and erodes
  trust once spotted.
- Don't display fake review counts, padded customer logos, or uncredited
  testimonials. One public call-out undoes months of trust-building.
- Don't lean on celebrity endorsement for an audience that discounts
  celebrity; B2B buyers trust their peers more than a famous founder.
- Don't bury proof in a footer when the decision is happening above the
  fold — proof has to be where the doubt is, not where SEO wants it.
- Don't rely on a single proof type when the decision is expensive; one
  glowing testimonial looks curated, three from named peers reads as real.

## Expected Behavior

With the skill applied, conversion rises on the surfaces where doubt was the
bottleneck. Users describe the decision as "easier" — they felt less like
they were taking a leap and more like they were joining a choice already
validated by others they recognize. Support questions shift from "is this
real?" to substantive product questions. When a new audience is approached,
the authority-signal fallback carries weight until peer proof accumulates,
so the conversion curve doesn't cliff on day one.

When proof is misplaced or missing, the symptoms show. Homepage-only proof
with none at the decision point presents as strong top-of-funnel and weak
commit. Manufactured scarcity shows as short-term lift followed by review
backlash. Proof mismatched to audience presents as the page "feeling off" in
qualitative research without users being able to name why.

## Quality Gates

- The primary decision surface carries at least two distinct proof types
  (rating + review count, or testimonial + logo, etc.).
- Proof is verifiable — the user can click through, look up the customer,
  or confirm the number elsewhere.
- Urgency and scarcity cues, when present, reflect actual system state and
  can be defended on the record.
- Peer similarity is considered in choosing whose proof to surface.
- A credibility fallback exists for surfaces where peer proof hasn't
  accumulated yet.

## Companion Integration

Invoked by Matilha core skills (`matilha-design`, `matilha-scout`,
`matilha-plan`) when conversion or commitment surfaces are being designed.
Does not delegate to other packs in v0.1.0. Pairs with `ux-trust-by-design`
(proof is one of several trust levers at high-stakes moments) and with
`ux-visual-hierarchy` (proof placement is a ranking decision, not a volume
decision).

## Output Artifacts

- Chat output only.

## Example Constraint Language

- Use "must" for: accurate representation of reviews, counts, and
  availability.
- Use "should" for: peer-similar proof, proof at the decision point,
  multiple proof types on expensive decisions.
- Use "may" for: the specific mix of testimonial / rating / logo / count
  appropriate to the audience.

## Troubleshooting

- **"Homepage converts well but checkout has heavy abandonment"**: proof is
  on the wrong page. Move review counts, star ratings, and testimonials to
  the commit surface.
- **"Reviews are great but the review widget is ignored"**: it's too
  generic. Surface review snippets from peers whose context resembles the
  user, not the five-star average in isolation.
- **"Urgency cues got us a conversion lift but reviews went bad"**: the
  scarcity was manufactured. Remove and rebuild trust with accurate urgency
  only.
- **"New product launched with no reviews — conversion is stuck"**:
  substitute authority signals: named founder with relevant background,
  public case studies, transparent technical writing, while peer proof
  accumulates.

## Concrete Example

An e-commerce product page stacks four proof signals at the decision point.
A four-and-a-half-star rating sits near the price, with a review count in
the thousands — volume implies credibility. A small "Amazon's Choice" badge
signals algorithmic vetting, which readers interpret as a lightweight third
party. A "frequently bought together" block shows the product in the
company of adjacent items other buyers chose, which functions as peer
behavior. Review excerpts surface with named photos, dated posts, and
verified-purchase badges. The combined effect is that a hesitant buyer sees
several independent lines of evidence that the choice is safe. The same
product on a store without reviews converts substantially lower, because
the decision surface offers only the seller's own claims. The difference is
not price, design, or copy — it's whose voice is speaking at the moment of
doubt.

## Sources

- `[[concepts/interacao-social]]`
- `[[concepts/tomada-decisao]]`
- Inspired by Cialdini's *Influence* (1984, updated 2021) and *100 Things
  Every Designer Needs to Know About People* (2011, Susan Weinschenk),
  paraphrased further from Danilo's wiki synthesis of the Latane & Darley
  smoke-filled-room experiment and the Chen (2008) finding that
  peer-similar reviews outperform expert reviews.
