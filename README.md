# matilha-ux-pack

> **You lead. Agents hunt.**
> Matilha companion pack — 22 UX and cognitive skills, derived from Weinschenk, Krug, and neuroscience research.

## What this is

`matilha-ux-pack` extends [Matilha](https://github.com/danilods/matilha-skills) with UX and cognitive-psychology skills. Each skill fires automatically when user intent matches — designing a form triggers `cog-cognitive-load`, making a tonal decision triggers `ux-emotion-in-ui`, auditing trust triggers `ux-reservatorio-boa-vontade`.

This pack is the first proof of Matilha's [Companion Contract](https://github.com/danilods/matilha-skills/blob/main/docs/matilha/companions-contract.md): a plugin that extends Matilha's methodology with specialized intelligence for a domain.

## Install

### Claude Code

```
/plugin install matilha-ux-pack
```

Or locally during development:

```
/plugin install /path/to/matilha-ux-pack
```

### Cursor

Same `/plugin install` flow — compatible with Claude Code's `.claude-plugin/plugin.json` format.

### Codex CLI

Point at the repo; enable `multi_agent = true` in `~/.codex/config.toml` if you want subagent dispatch.

### Gemini CLI

Install as an extension via the pack's future `gemini-extension.json` (to land in Wave 5a.1 if needed — the pack ships Claude Code + Cursor + Codex ready out of the box).

## Skills (22 total)

**Visual perception & reading (3)**: `ux-visual-hierarchy`, `ux-typography-for-reading`, `ux-color-meaning`.

**Memory & cognitive load (2)**: `cog-cognitive-load`, `cog-progressive-disclosure`.

**Attention & focus (2)**: `cog-attention-capture`, `ux-flow-state-design`.

**Motivation & behavior (4)**: `ux-goal-gradient`, `ux-variable-rewards`, `ux-intrinsic-motivation`, `ux-dopamine-design`.

**Social, emotion, trust (3)**: `ux-social-proof`, `ux-trust-by-design`, `ux-emotion-in-ui`.

**Errors & usability (2)**: `ux-swiss-cheese-errors`, `ux-yerkes-dodson`.

**Decision-making (2)**: `ux-choice-overload`, `cog-unconscious-decisions`.

**Krug / practical usability (4)**: `ux-krug-satisficing`, `ux-navigation-wayfinding`, `ux-usability-testing`, `ux-reservatorio-boa-vontade`.

Each skill is derived from 2-5 wiki pages plus source-book attribution. See the individual `skills/<slug>/SKILL.md` files for full guidance.

## Integration with Matilha core

When `matilha-skills` (Matilha core) is installed, its core skills delegate to this pack automatically:

- `matilha-design` → invokes pack skills during design decisions.
- `matilha-scout` → invokes `ux-usability-testing` + `cog-unconscious-decisions` during Phase 10 research.
- `matilha-plan` → invokes `cog-cognitive-load` + `cog-progressive-disclosure` during spec authoring.

If Matilha core is absent, pack skills still work standalone — a user with only `matilha-ux-pack` installed gets UX guidance when their intent matches.

## Attribution

Skills synthesize principles from:

- Susan Weinschenk, *100 Things Every Designer Needs to Know About People* (2011).
- Steve Krug, *Don't Make Me Think* (2nd ed., 2005).
- Curated neuroscience and cognitive-psychology frameworks (Self-Determination Theory, Fogg Behavior Model, Hook Model, Yerkes-Dodson, System 1/2, Gestalt, etc.).

Skill content is Danilo's original synthesis via Obsidian wiki paraphrase. Source books are credited but not quoted verbatim.

See `docs/wiki-ingestion-workflow.md` for the authoring discipline.

## Contribute

Pack is open source. To propose a new skill or refine an existing one, read:

1. `docs/wiki-ingestion-workflow.md` in this repo.
2. `matilha-skills/docs/matilha/skill-authoring-guide.md` (upstream style guide).
3. `matilha-skills/docs/matilha/pack-authors.md` (upstream pack-authoring contract).

## License

MIT.
