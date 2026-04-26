---
name: matilha-ux-trigger
description: "Use when the user mentions UI, UX, user interface, design system, component, layout, typography, color, visual hierarchy, cognitive load, wireframe, Figma, accessibility, responsive design, mobile design, onboarding flow, navigation, attention, habit, dopamine, pricing, choice, social proof, or any topic related to user experience and interface design. Fires independently of compose to ensure matilha-ux-pack skills activate whenever UX/UI domain appears."
category: ux-pack
version: "1.0.0"
---

## When this fires

User prompt mentions any keyword from matilha-ux-pack's domain: UI, UX, user interface, design system, component, layout, typography, color, visual hierarchy, cognitive load, wireframe, Figma, accessibility, responsive design, mobile design, onboarding flow, navigation, attention, habit, dopamine, pricing, choice, social proof.

This skill fires independently of `matilha:matilha-compose` and `CLAUDE.md` activation rules — its keyword-rich description is the activation surface for the Skill tool's matcher. It guarantees that whenever the user prompt touches the UX/UI domain, at least one matilha-ux-pack skill enters the conversation.

## Execution Workflow

1. **Pack presence check.** Inspect the ambient skill list for skills in the `matilha-ux-pack:*` namespace. Examples: `matilha-ux-pack:cog-cognitive-load`, `matilha-ux-pack:ux-visual-hierarchy`, `matilha-ux-pack:ux-typography-for-reading`.

2. **Pack installed path.** If ≥1 skill from `matilha-ux-pack` is visible:
   - Identify the user's sub-intent within the UX/UI domain (designing a form, picking colors, structuring navigation, planning onboarding, reducing cognitive load, etc.).
   - Emit a compact domain acknowledgment (≤2 lines — no full sigil, that belongs to compose). Example: `UX/UI domain detected. Pulling matilha-ux-pack guidance for <sub-intent>.`
   - Invoke the most relevant pack skill via the Skill tool. Prefer one specific skill over listing many.

3. **Pack not installed path.** If no `matilha-ux-pack` skills are visible:
   - Emit: "UX/UI skills not installed. Run `/matilha-install` and select `ux` to add 22 UX/UI skills."
   - Proceed with default flow (`matilha:matilha-compose` if visible, otherwise `superpowers:brainstorming`).

## Rules

- Do NOT emit the full compose sigil. The sigil belongs to compose; this skill emits a compact pack-specific acknowledgment.
- Do NOT block on pack absence — emit the nudge and continue with the default flow.
- Prefer invoking a specific pack skill over listing all skills.
- This trigger is a routing surface, not a craft skill — hand off to the chosen pack skill quickly.

## Why this exists

Wave 5h adds deterministic activation surfaces to compensate for probabilistic Skill-tool matching. Compose's routing table covers the central path; this trigger covers prompts that bypass compose (e.g., when CLAUDE.md is absent, or when a domain keyword appears mid-conversation without a compose-classifiable phase). Together they form the Maximum Activation guarantee for matilha-ux-pack.
