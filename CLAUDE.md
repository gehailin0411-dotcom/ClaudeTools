# CLAUDE.md

Guidance for Claude Code (and any other AI assistant) working in this repository.

## Stack & Conventions

This project has two hard constraints that must never be violated:

1. **Single-file project.** The entire project must live in one `index.html`
   file, with all CSS and JavaScript inlined using `<style>` and `<script>`
   tags — never in separate `.css` or `.js` files, and never split across
   multiple HTML pages. Linking external images, and external CSS/JavaScript
   libraries (e.g. via a `<link>` or `<script src="https://...">` to a CDN),
   is allowed. No additional pages of any kind. This constraint exists so the
   finished project can be copy-pasted as a single file for sharing in class
   and on single-file code platforms (e.g. CodePen, JSFiddle, gists).
2. **Vanilla only.** Use plain HTML, CSS, and JavaScript only — no
   frameworks or libraries that require a build step (no React, Vue,
   Svelte, TypeScript, Tailwind CLI, bundlers, etc.), and no build process
   of any kind. External libraries loaded directly via a `<script>`/`<link>`
   tag from a CDN are fine as long as they don't require compiling or
   bundling.

When implementing any feature, keep everything inside `index.html` and avoid
introducing new files, frameworks, or build tooling.

## Tech stack (hard constraints — do not deviate)
- Vanilla HTML, CSS, and JavaScript only. No React, Vue, or any JS framework.
- Tailwind CSS for all styling (via CDN only).
- No backend, no database. Fully static site.
- A toggle for light and dark theme, with the choice remembered
  across visits.

## Working conventions
- Before implementing any non-trivial feature, ask clarifying
  questions about scope, edge cases, and constraints first —
  don't propose a plan until you've asked.

## Feature Plan

Status per phase: `[ ]` not started, `[~]` in progress, `[x]` done. Mark phases
done (or prune their detail down to a one-line summary) as they ship, so this
section stays skimmable as the collection grows.

### Phase 1 — Portal shell + Unit Converter + Regex Tester `[ ]`

**Data model:** a single `TOOLS` array in the page script:
`{ id, title, description, category }` per tool. It drives the card grid, the
jump-links, and the category badges — adding a tool later is one array entry
plus its `<section id="...">` and script block, nothing else.

**Key flows:**
- *Theme toggle* — read `localStorage.theme`, fall back to
  `prefers-color-scheme`; toggle button flips the `dark` class on `<html>` and
  persists the choice.
- *Navigation* — hero → card grid (rendered from `TOOLS`, plus a disabled
  "more coming soon" card) → clicking a card jump-scrolls to its `#id` section.
- *Unit Converter* — category select (Length / Weight / Temperature / Volume)
  → From/To unit selects → live conversion (factor-based via a common base
  unit per category; Temperature special-cased with direct formulas).
- *Regex Tester* — pattern + flag checkboxes (g/i/m/s) + test string →
  `new RegExp(...)` in try/catch → live HTML-escaped `<mark>`-highlighted
  matches, a match list with capture groups, and a replace-mode live output.

### Phase 2+ — Additional tools/lessons `[ ]`

Extend `TOOLS` with new entries (introduce category `"Lesson"` when the first
one is added), each with its own `<section>` and script block, following the
Phase 1 pattern exactly — no changes to the grid/nav/theme logic.

Candidate backlog (unordered, not yet scoped): _to be filled in as decided_.
