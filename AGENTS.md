# matilha-ux-pack — Matilha Companion Pack

> **You lead. Agents hunt.**
> A harness for building complex projects with AI.

`matilha-ux-pack` is a Matilha companion pack — 22 UX and cognitive skills synthesized from Danilo's Obsidian wiki (Weinschenk's 100 Things Every Designer Needs to Know About People, Krug's Don't Make Me Think, 15 neuroscience frameworks, and curated behavioral-science concept pages).

## How this loads in Codex (and for contributors)

You are reading this because `matilha-ux-pack` is available. On Codex CLI, skills load natively — when a skill's description matches user intent, follow its instructions. Subagent-dispatch skills require `multi_agent = true` in `~/.codex/config.toml`.

For contributors authoring new skills or adapting this pack: read `docs/wiki-ingestion-workflow.md` for the wiki-to-skill discipline, plus `matilha-skills/docs/matilha/skill-authoring-guide.md` for the canonical skill format. Do NOT copy verbatim from Weinschenk / Krug / Tan source books — paraphrase + cite wikilinks.

## What's inside

### 18 `ux-*` skills

- `ux-visual-hierarchy` — Gestalt laws, focal points, scan patterns.
- `ux-typography-for-reading` — fonts, saccades, legibility.
- `ux-color-meaning` — cultural meaning, accessibility.
- `ux-flow-state-design` — Csikszentmihalyi flow, feedback loops.
- `ux-goal-gradient` — Hull's effect, progress bars.
- `ux-variable-rewards` — Hook Model, anti-dark-pattern ethics.
- `ux-intrinsic-motivation` — SDT (autonomy, competence, relatedness).
- `ux-dopamine-design` — anticipation > reward, ethical guardrails.
- `ux-social-proof` — testimonials, scarcity, ethical limits.
- `ux-trust-by-design` — trust signals, error-recovery trust.
- `ux-emotion-in-ui` — Plutchik's 7 emotions, tonal design.
- `ux-swiss-cheese-errors` — defense-in-depth, slip/mistake/violation.
- `ux-yerkes-dodson` — stress degrades performance.
- `ux-choice-overload` — paradox of choice, defaults.
- `ux-krug-satisficing` — "people satisfice", scannable design.
- `ux-navigation-wayfinding` — breadcrumbs, current-location signals.
- `ux-usability-testing` — 3-5 users is enough.
- `ux-reservatorio-boa-vontade` — trust reservoir economy.

### 4 `cog-*` skills (cognitive, cross-cutting)

- `cog-cognitive-load` — working memory 4±1, chunking, recognition > recall.
- `cog-progressive-disclosure` — reveal level-by-level, hide detail.
- `cog-attention-capture` — saliency, 7-10 min caps.
- `cog-unconscious-decisions` — System 1 vs 2, loss aversion.

## Companion integration (upward)

This pack is a **specialist** invoked by Matilha core skills. It does NOT invoke other packs in this version. Future versions may delegate to `matilha-growth-pack` (when pricing-psychology decisions intersect) or `matilha-design-pack` (when visual-execution decisions intersect).

## Attribution

Skills are original synthesis. Wiki wikilinks cite curated paraphrases. Book attribution is credit only, never content transfer. See `docs/wiki-ingestion-workflow.md` for the authoring discipline.

## License

MIT.

## Links

- Core Matilha: https://github.com/danilods/matilha (CLI) + https://github.com/danilods/matilha-skills (plugin)
- This pack: https://github.com/danilods/matilha-ux-pack
