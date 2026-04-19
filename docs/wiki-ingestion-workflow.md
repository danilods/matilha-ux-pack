# Wiki Ingestion Workflow

> How to synthesize a Matilha pack skill from the Obsidian wiki.

## Why this exists

The `matilha-ux-pack` skills are derived from Danilo's Obsidian wiki, which is itself a curated paraphrase of source books (Weinschenk, Krug, Tan, etc.) and behavioral-science literature. This doc codifies the discipline so that:

1. Future pack authors (including other Matilha packs) reproduce the same discipline.
2. Attribution is consistent — always 3 layers of remove from source books.
3. Activation is reliable — every skill has a distinct triggering intent.
4. Skill style follows `matilha-skills/docs/matilha/skill-authoring-guide.md`.

## The 5-step process per skill

### 1. Select triggering intent

From the pack's skill inventory (in the spec or `README.md`), pick one row. The row's activation description is the contract — the Skill tool matches this against user intent.

Example: `cog-cognitive-load` → "Use when designing forms, menus, or information-dense UI — apply working memory 4±1 chunks, chunking, recognition>recall."

### 2. Load wiki sources

Read the 2-5 wiki pages listed in the skill's source mapping. Note:

- Key principles (what the skill is teaching).
- Concrete examples from the wiki or source books (which you'll rephrase).
- Citations back to the original source books.

Example sources for `cog-cognitive-load`:
- `~/Documents/Memory/Memory/wiki/concepts/memoria-cognicao.md`
- `~/Documents/Memory/Memory/wiki/concepts/principios-cognitivos-produto.md`

### 3. Paraphrase + synthesize

Draft the skill body in Matilha's voice. Principles:

- **Paraphrase always** — do not copy source-book sentences. Do not copy wiki-page sentences verbatim either. Aim for 3 layers of remove.
- **Include ONE concrete example** per principle: "When a user lands on a signup form, working memory 4±1 chunks means label + 1 helper text, not label + 2 helper texts + 1 tooltip."
- **Cite inline with wikilinks**: "(see `[[concepts/memoria-cognicao]]` for the full cognitive-psychology treatment)".
- **Close the body with a pointer** back to the Matilha core skill that most likely invokes this specialist (`matilha-design`, `matilha-scout`, `matilha-plan`).

### 4. Validate against the style guide

Check:

- [ ] Frontmatter matches `matilha-skills/docs/matilha/skill-authoring-guide.md` strict schema: `name`, `description` starting with "Use when" or "When", `category: ux | cog`, `version: "1.0.0"`, `requires: []`, `optional_companions: []`.
- [ ] Body has all 12 required sections: When this fires, Preconditions, Execution Workflow, Rules: Do, Rules: Don't, Expected Behavior, Quality Gates, Companion Integration, Output Artifacts, Example Constraint Language, Troubleshooting, plus — for pack skills — a mandatory `## Sources` section (13th).
- [ ] Mandatory `## Sources` section: 2-5 wikilinks in `[[wiki-path]]` format, plus book-attribution note.
- [ ] Body length 150-300 lines (longer content moves to `skills/<slug>/references/<topic>.md`).

### 5. Cross-check activation uniqueness

`grep -r "^description: " skills/*/SKILL.md` and visually scan for descriptions that might fire on the same user intent.

- If 2 skills overlap > 80% of words in their descriptions, refactor one to a narrower triggering intent.
- Example refactor: "Use when designing a form" (too broad) → "Use when designing a form that risks cognitive overload" (specific to `cog-cognitive-load`).

## Example: how `cog-cognitive-load` was authored

Approx 30-minute process:
1. Selected intent: "designing info-dense UI" (picked from inventory).
2. Read `concepts/memoria-cognicao.md` + `concepts/principios-cognitivos-produto.md` (12 minutes).
3. Drafted body sections — synthesized the 4±1 rule, recognition>recall, chunking (15 minutes).
4. Added Sources + validated 12 sections (2 minutes).
5. Cross-checked against `cog-progressive-disclosure` activation — narrowed "info-dense UI" to "forms, menus, info-dense UI" to distinguish (1 minute).

## When to promote to a meta-skill

If future Matilha packs (`matilha-growth-pack`, `matilha-design-pack`, etc.) reveal this workflow as repetitive + formulaic, consider promoting to a `matilha-wiki-ingest` meta-skill in Matilha core. That skill would:
- Read a wiki page URL or path.
- Prompt for triggering intent.
- Generate a draft SKILL.md body following this workflow.
- Leave paraphrase + Sources for the author to refine.

Wave 5a ships this as documented discipline. Wave 5b+ may promote.
