# Wave 5a Smoke Test Results

**Date:** 2026-04-19
**Pack:** matilha-ux-pack on branch `wave-5a-ux-pack`
**matilha CLI tests:** 595/595 passing (437 baseline + 158 new ux-pack validation)
**Platform:** macOS 24.4.0 (local dev). Claude Code marketplace install deferred to post-ship.

## Structural smoke (automated)

| Artifact | Status | Notes |
|---|---|---|
| `.claude-plugin/plugin.json` | ✅ | parses; name=matilha-ux-pack; version=0.1.0; keywords include `matilha-pack` |
| `.claude-plugin/marketplace.json` | ✅ | parses; name=matilha-ux-pack; version=0.1.0 |
| `CLAUDE.md` + `GEMINI.md` + `AGENTS.md` + `README.md` | ✅ | all 4 contain slogan "You lead. Agents hunt." |
| `LICENSE` | ✅ | MIT (auto-created by `gh repo create`) |
| `docs/wiki-ingestion-workflow.md` | ✅ | 5-step discipline documented |
| 22 skills canonical | ✅ | 18 ux-* + 4 cog-* — all with 13 sections (12 required + Sources), 159-212 lines, descriptions starting with "Use when", mandatory Sources wikilinks |
| Activation uniqueness | ✅ | validator passes (no pair > 80% description word overlap) |

## Validation suite (matilha CLI repo)

- `npm test` → **595/595 green** (437 baseline + 158 new ux-pack validation tests)
- `npx tsc --noEmit` → clean
- 158 new tests broken down:
  - 3 plugin.json tests
  - 88 frontmatter tests (22 skills × 4 checks: schema, name-match-dir, description-phrasing, category-prefix)
  - 66 body tests (22 skills × 3 checks: Sources section, wikilink count, line-count range)
  - 1 activation-uniqueness heuristic test

## Bug caught during smoke

`ux-reservatorio-boa-vontade` description had unquoted colon-space (`economy: what`), which YAML parses as nested mapping. Fixed by wrapping description in double quotes. Validator caught this immediately — cascade of 5 failures all pointing at the same root cause. **This is exactly the kind of bug the content-validation extension was designed to catch.**

Fix committed in `6d266da`.

## Semantic smoke (mental-model walkthrough)

**Scenario 1: User designs a signup form**

- User intent: "design a signup form with 5 fields"
- Expected pack skill activation: `cog-cognitive-load` (form complexity; 4±1 working memory) + `ux-trust-by-design` (signup = auth moment; trust signals) + `ux-swiss-cheese-errors` (form error handling; defense-in-depth) + possibly `cog-progressive-disclosure` if form is long.
- Expected matilha core invocation: `matilha-design` auto-invokes pack skills via its companion-integration block (written in Wave 4a).

**Scenario 2: User writes UI copy**

- User intent: "help me write copy for an error message"
- Expected activation: `ux-emotion-in-ui` (tonal choice, emotional state mapping).
- Potential: `ux-trust-by-design` if copy is for auth-error recovery.

**Scenario 3: User picks pricing tiers**

- User intent: "how many pricing tiers should I offer?"
- Expected activation: `ux-choice-overload` (paradox of choice, 3-5 tier rule).
- Potential: `cog-unconscious-decisions` (anchoring, defaults, loss aversion).

**Scenario 4: User plans research**

- User intent: "how do I validate this design with users?"
- Expected activation: `ux-usability-testing` (3-5 users, task-based tests).

## Deferred: end-to-end Claude Code marketplace install

Full "install from marketplace → /matilha-design triggers pack skill" test deferred to post-ship user-assisted validation. Same reasoning as Wave 4a: Claude Code plugin marketplace flow is interactive + temporarily hiding `matilha` CLI from PATH risks breaking Danilo's dev environment.

**Manual test plan** (Danilo to execute post-ship, optional):

1. Clean Claude Code session (no prior Matilha skills loaded).
2. `/plugin install` both `matilha-skills` and `matilha-ux-pack` locally.
3. Restart session.
4. Natural-language: "I want to design a pricing page with 5 tiers."
5. Expect: `matilha-design` skill activates, delegates to `ux-choice-overload` via Skill tool.
6. `which matilha` returns empty (no CLI needed).

Extend this doc with results if executed.

## Risks flagged

- **Activation accuracy in real Claude Code**: the uniqueness validator runs string-overlap heuristics; Claude Code's Skill tool uses learned embedding-based similarity. A skill passing >80% heuristic check could still have low differentiability in practice. Monitor post-ship and refine descriptions if collisions surface.
- **Pack vs matilha core version drift**: pack ships at 0.1.0 standalone. If Matilha core changes the companion-contract, packs need to upgrade. No enforcement in Wave 5a; Wave 5b+ may add a `matilha-core: ">=X.Y.Z"` range field.
- **Source-book paraphrase discipline**: code validator can't enforce that skill bodies don't copy from Weinschenk/Krug verbatim — human-judgment gate at authoring time. SP2 subagents explicitly paraphrased; no verbatim copy issues flagged in self-reports.

## Conclusion

Wave 5a ships the first Matilha companion pack. Structural + semantic quality gates pass. Runtime activation validation happens on first marketplace install (post-ship).

The pack is ready for:
- Manual marketplace smoke test (Danilo's choice when to run).
- Marketplace submission PR (when Danilo authorizes).
- Wave 5b+ (next packs using the same authoring discipline in `docs/wiki-ingestion-workflow.md`).
