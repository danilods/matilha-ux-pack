# Changelog

## [0.1.0] — 2026-04-19 — Wave 5a: First shipped Matilha companion pack

### Added

- **Pack infrastructure**: `.claude-plugin/plugin.json` + `marketplace.json` with `matilha-pack` keyword (discoverable by Matilha core via companion-contract detection).
- **Context primers**: `CLAUDE.md` + `GEMINI.md` + `AGENTS.md` with pack-specific framing and slogan "You lead. Agents hunt."
- **22 skills** synthesized from Danilo's Obsidian wiki:
  - 18 `ux-*` skills (visual-hierarchy, typography-for-reading, color-meaning, flow-state-design, goal-gradient, variable-rewards, intrinsic-motivation, dopamine-design, social-proof, trust-by-design, emotion-in-ui, swiss-cheese-errors, yerkes-dodson, choice-overload, krug-satisficing, navigation-wayfinding, usability-testing, reservatorio-boa-vontade).
  - 4 `cog-*` skills (cognitive-load, progressive-disclosure, attention-capture, unconscious-decisions).
- **`docs/wiki-ingestion-workflow.md`**: 5-step discipline for wiki-to-skill authoring. Reusable pattern for future Matilha packs.
- **`docs/smoke-results.md`**: Wave 5a structural + semantic smoke results.
- Content-validation integration in the `matilha` CLI repo (sibling-dir detection + 158 validation tests).

### Discipline

- **Paraphrase-only body voice**: skills never copy verbatim from source books (Weinschenk, Krug, behavioral-science papers). Three layers of remove: skill → wiki page → source book.
- **Every skill has mandatory `## Sources` section** with wikilinks + book attribution.
- **Activation-uniqueness heuristic**: no two descriptions overlap > 80% of content words. Enforced by validator.

### Notes

- Pack works standalone (22 skills fire on user intent regardless) OR in composition with `matilha-skills` (Matilha core).
- When Matilha core is installed, core skills (`matilha-design`, `matilha-scout`, `matilha-plan`) delegate to pack skills automatically per Wave 4a's companion contract.
- Pack skills do NOT delegate to other packs in v0.1.0. Future versions may add cross-pack integrations (e.g., `ux-choice-overload` ↔ future `matilha-growth-pack:growth-pricing-psychology`).
- Content breadth (Weinschenk + Krug + neuroscience + cognitive + behavioral frameworks) is Matilha's unique moat — no other plugin in the Claude Code / Cursor / Codex / Gemini ecosystems offers this depth.
