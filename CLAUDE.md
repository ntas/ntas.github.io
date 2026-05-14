# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static portfolio site hosted on GitHub Pages. No build step, no dependencies, no package manager. All source files are served directly.

## Development

Preview locally by opening `index.html` in a browser, or with a local server to avoid `file://` quirks:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

There are no tests, no linter, and no CI pipeline.

## Architecture

Three files make up the entire site:

- **`index.html`** — single-page layout with five sections: `#intro`, `#about`, `#work`, `#skills`, `#contact`. All content is static markup.
- **`style.css`** — all styles. CSS custom properties on `:root` drive every colour; the light theme is a single `html[data-theme="light"]` override block that redefines those tokens. No per-component theme overrides.
- **`script.js`** — vanilla JS only. Four concerns: theme init (runs synchronously before first paint via IIFE to prevent flash), nav scroll behaviour, active nav link tracking via `IntersectionObserver`, and scroll-triggered fade-in via a second `IntersectionObserver`.

### Theme system

Theme state lives on `document.documentElement` as `data-theme="dark"` or `data-theme="light"`. The attribute is always explicitly set — there is no implicit "no attribute = dark" state. Persistence is via `localStorage` key `theme`. OS preference (`prefers-color-scheme`) is the fallback on first visit.

The nav backdrop colour (`rgba(11,11,11,…)` in dark, `rgba(245,239,230,…)` in light) is hardcoded in the `.scrolled` rule rather than a token — update both the base rule and `html[data-theme="light"] #nav.scrolled` when changing it.

### Transitions

A `transition` on `body`, `#nav`, `.project-card`, `.photo-placeholder`, `.skill-group li`, and `footer` produces the theme crossfade. The IIFE adds `.no-transition` to `<html>` before setting the initial theme, then removes it on the next animation frame so the init is instant but subsequent user-triggered toggles animate.

## Docs

`docs/superpowers/specs/` holds design specs; `docs/superpowers/plans/` holds implementation plans. These are the source of truth for planned or in-progress features.
