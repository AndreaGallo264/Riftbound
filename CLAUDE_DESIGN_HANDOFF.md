# Handoff: Riftbound MVP prototype and design system

## Mission

Create a distinctive responsive prototype and the initial design system for the Riftbound Collection Assistant. This is a design exploration and validation pass, not production implementation. Preserve the product and domain decisions already made; focus on visual direction, interaction clarity, reusable foundations, and key user journeys.

The intended audience is a closed, informal beta of up to 25 invited Riftbound players. The product combines a private card Collection, Deck building/validation, and an evidence-grounded rules Assistant in Spanish and English.

## Repository State

- Repository: <https://github.com/AndreaGallo264/Riftbound>
- GitHub Project: <https://github.com/users/AndreaGallo264/projects/3>
- Branch: `main`
- Current commit: `b20a7ae` (`docs: add Riftbound MVP specification`)
- The repository currently contains planning, research, a structural HTML prototype, and implementation tickets. There is no production application scaffold yet.
- GitHub contains 28 MVP Issues with native dependency links. The first technical frontier item is [#2 Desplegar la shell bilingüe responsive](https://github.com/AndreaGallo264/Riftbound/issues/2).

## Read First

Do not duplicate these artifacts. Read and reference them:

1. Product specification: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/.scratch/riftbound-mvp-spec/SPEC.md`
2. Domain vocabulary: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/CONTEXT.md`
3. Validated UX direction: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/.scratch/riftbound-mvp-spec/issues/10-prototipar-la-experiencia-bilingue.md`
4. Existing disposable prototype: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/.scratch/riftbound-mvp-spec/prototypes/bilingual-experience-prototype.html`
5. Accessibility and compatibility boundaries: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/.scratch/riftbound-mvp-spec/issues/13-fijar-requisitos-no-funcionales-del-mvp.md`
6. Assistant response contract: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/.scratch/riftbound-mvp-spec/issues/06-definir-contrato-de-respuesta-del-asistente.md`
7. Collection and Deck behavior: `/Users/patricioperezherrero/code/Blarsamio/riftbound-project/.scratch/riftbound-mvp-spec/issues/08-definir-comportamiento-de-colecciones-y-mazos.md`
8. Implementation tickets relevant to design: GitHub Issues #2 through #20, especially #5-#18.

## Validated UX Direction

The structural prototype compared three alternatives. The chosen product combines their strongest interaction patterns rather than their incompatible visual styles:

- **Collection:** visual archive/gallery approach. Search, counts, and add actions are prominent. Card and Printing should feel like collectible objects without reducing the entire experience to a spreadsheet.
- **Deck:** denser command workspace. Composition, Deck legality, Collection coverage, editing, export, and contextual Assistant need to coexist clearly.
- **Contextual Assistant:** a collapsible right panel on desktop and full-screen surface on mobile. Opening or closing it never loses the selected context.
- **Ask:** independent full-width destination for questions without an open entity. The user can select Current rules, My collection, or a named Deck as context.
- **Desktop navigation:** persistent access to Collection, Decks, Ask, and Imports.
- **Mobile navigation:** persistent bottom navigation for Collection, Decks, and Ask. Imports and secondary actions live inside related routes.

The existing HTML is evidence of information architecture and interaction only. Do not copy all of its palettes and typefaces into one visual system.

## Required Visible Semantics

- Every Assistant composer visibly identifies context: `Current rules`, `My collection`, or a named/current Deck.
- Every response exposes one state before its content: `grounded`, `needs_clarification`, `no_official_answer`, `official_conflict`, `missing_context`, or `unavailable`.
- Facts/rules and Recommendations must be visually and semantically distinct.
- Sources are collapsed by default but remain clearly available. Expanded evidence includes title, link, date, language, and supporting excerpt.
- Deck legality and Collection coverage are separate concepts. Missing owned cards never visually imply that a Deck is illegal.
- Current official text and printed card text can differ; the design must not silently conflate them.
- The Assistant proposes changes but never applies them. Mutation always uses explicit controls outside chat.
- Names of Cards stay official when UI or responses switch between Spanish and English.

## Prototype Scope

Produce a high-fidelity responsive prototype covering these connected surfaces:

1. Invitation acceptance and magic-link entry.
2. Collection gallery with search/filter, quantities, Printing recognition, empty/loading/error states, and add/edit Owned copy flow.
3. Collection CSV import preview showing additions, updates, deletions, warnings, unresolved rows, and `append` versus `replace` confirmation.
4. Deck workspace with sections, card quantities, Deck legality, Collection coverage, missing Cards, and contextual Assistant.
5. Ask route with context selection and representative responses for all six response states.
6. Expandable source/evidence treatment and explicit translated-from-English treatment.
7. Conversations list/history and deletion confirmation.
8. Minimal Admin views for invitations/accounts and Knowledge source draft/review/publication states.
9. Mobile versions of Collection, Deck, Ask, Assistant, import review, and critical confirmations.

Use realistic but invented fixture content. Do not rely on network calls.

## Design System Scope

Define enough of a system to build the MVP consistently, without turning this into a generic component library:

- Visual principles and a named design direction appropriate to a collectible strategy card companion.
- Color tokens for surfaces, text, borders, actions, selection, rules/evidence, Recommendations, success, warning, conflict, and unavailable states.
- Typography roles for navigation, page titles, dense deck data, card metadata, conversation content, and source excerpts.
- Spacing, radius, border, elevation, iconography, and motion principles.
- Responsive layout/grid rules for desktop, tablet, and 320 px mobile.
- Focus, hover, active, selected, disabled, loading, skeleton, empty, error, destructive, and reduced-motion states.
- Components needed by the prototype: navigation, buttons, inputs, combobox/search, filters, Card/Printing tile, Owned copy editor, data rows, badges, tabs, drawers, dialogs, toasts, import diff table, Deck section, legality issue, coverage meter/list, Assistant composer, response block, status banner, source disclosure, conversation item, job/progress item, and Admin review controls.
- A token and component naming scheme suitable for later implementation in Next.js and Tailwind/shadcn-style primitives, without requiring those tools in the prototype.
- English and Spanish examples that test expansion, wrapping, overflow, and official Card names.

## Accessibility and Responsive Requirements

- Use semantic structure, complete keyboard operation, visible focus, associated labels, announced errors/statuses, and meaning that does not depend only on color.
- Aim for WCAG 2.1 AA color contrast even though the MVP does not claim formal conformance.
- Respect `prefers-reduced-motion`.
- Ensure critical actions and context remain available from 320 px upward.
- Avoid hover-only disclosure and pointer-only drag interactions; provide explicit alternatives.
- Plan for VoiceOver and axe smoke testing on central journeys.

## Content and Rights Constraints

- `slimtreble/Riftbound-card-data` may be used only as a replaceable local prototype fixture.
- Its MIT license covers scripts only. Card names, text, data, and artwork remain Riot property and are not open source.
- Do not embed or redistribute Riot artwork in the handoff deliverable. Use neutral placeholders, abstract crops created for the prototype, or clearly synthetic visual blocks.
- The fixture contains printed card text, not authoritative errata. It cannot represent Current rules state.
- Official rules sources remain authoritative for rules, but production ingestion/storage is gated on verified rights.
- Do not invent rankings, win rates, play rates, matchup percentages, or other aggregate Metagame data.

## Visual Guardrails

- Avoid a generic SaaS dashboard, neon gaming HUD, glassmorphism overload, and interchangeable AI-chat styling.
- Do not imitate Riot, League of Legends, or official Riftbound trade dress closely enough to imply affiliation.
- The interface should support collectible tactility and strategic density while remaining calm enough for rules reading and evidence inspection.
- Prefer one coherent visual language across Collection, Deck, Assistant, and Admin. Differences should come from information density and task, not unrelated themes.
- Preserve user trust: uncertainty, conflict, destructive actions, private context, and source provenance should feel deliberate rather than decorative.

## Open Design Decisions

These were intentionally not fixed by product planning and should be explored by Claude Design:

- Brand name treatment, logo/wordmark direction, and original non-infringing motif.
- Final palette, typography, icon style, card placeholder style, and light/dark strategy.
- Exact density controls for Collection and Deck.
- How the contextual Assistant transitions between panel and full-screen mobile presentation.
- How evidence, conflict, translated content, legality, and ownership status share visual hierarchy without badge overload.

Present a small number of genuinely distinct visual directions before committing to the final one. Do not reopen settled product behavior unless a concrete usability conflict is demonstrated.

## Expected Deliverables

1. A concise visual-direction rationale and the selected direction.
2. A responsive, navigable prototype covering the scoped surfaces and representative edge states.
3. Design tokens and component specifications sufficient for implementation.
4. A component/state inventory mapping prototype elements to the system.
5. Accessibility annotations for keyboard, focus, labels, announcements, contrast, and reduced motion.
6. A short implementation handoff describing layout behavior, responsive transitions, and interactions that must not be inferred from static screens.
7. A list of unresolved design questions or assumptions, limited to items that block implementation.

Keep prototype code or design artifacts separate from production code unless explicitly asked to begin implementation. If files are added to the repository, follow existing issue scope and do not modify product specs or implementation tickets without recording why.

## Suggested Skills

Call the Skill tool for:

- `prototype` first, to structure the disposable design-validation artifact.
- `frontend-design` for a distinctive, production-grade visual direction.
- `design-system-patterns` for token and component architecture.
- `visual-design-foundations` for typography, color, spacing, and iconography.
- `responsive-design` and `adapt` for desktop/mobile behavior.
- `accessibility` for semantics, focus, contrast, keyboard use, and announcements.
- `critique` after the first complete direction.
- `polish` only after structure and system decisions are accepted.

## Completion Signal

This handoff is complete when the team can inspect a coherent responsive prototype, understand the reusable visual system behind it, and implement GitHub Issue #2 and subsequent UI slices without guessing core visual or interaction decisions.
