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
