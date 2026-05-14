# Dark / Light Mode Toggle — Design Spec

**Date:** 2026-05-12
**Status:** Approved

---

## Overview

Add a dark/light mode toggle to the portfolio's nav bar. The site defaults to dark mode but respects the user's OS preference on first visit. The user can override at any time; the choice persists via `localStorage`.

---

## Behaviour

- On first visit, read `prefers-color-scheme`. If light, apply light theme. Otherwise apply dark.
- If the user has previously toggled, `localStorage` takes precedence over the OS preference.
- Clicking the toggle flips between dark and light and saves the new preference.
- No flash of wrong theme — theme init runs before first paint.

---

## CSS

### Approach

All colour tokens are CSS custom properties on `:root`. The light theme is defined in a `html[data-theme="light"]` block that overrides them. No per-component overrides are needed — every element already consumes the tokens.

### Token Values

| Token | Dark | Light |
|---|---|---|
| `--bg` | `#0b0b0b` | `#f5efe6` |
| `--surface` | `#131313` | `#ede7dd` |
| `--border` | `#1e1e1e` | `#d9d2c8` |
| `--text` | `#e0e0e0` | `#1a1a1a` |
| `--muted` | `#555` | `#8a8070` |
| `--muted-lt` | `#888` | `#5a5248` |
| `--accent` | `#f97316` | `#f97316` |
| `--accent-dim` | `rgba(249,115,22,0.10)` | `rgba(249,115,22,0.12)` |

Nav backdrop uses `rgba(11,11,11,…)` in dark and `rgba(245,239,230,…)` in light — these are hardcoded in the `.scrolled` rule rather than tokens, so they must be updated directly.

### Theme Transition

A `transition: background-color 0.3s, color 0.3s, border-color 0.3s` on `body` and key elements gives a smooth crossfade when toggling. No transition on first load (the `no-transition` class prevents it).

---

## HTML

A `<button>` added to the nav after `.nav-links`:

```html
<button class="theme-toggle" id="theme-toggle" aria-label="Toggle light mode">
  <span class="icon-sun">☀</span>
  <span class="icon-moon">☾</span>
</button>
```

- `.icon-sun` is shown in dark mode, `.icon-moon` in light mode.
- Icon visibility is controlled by CSS alone (`html[data-theme="light"] .icon-sun { display:none }` etc).
- The button is styled to match the nav: small, muted, turns orange on hover.

---

## JavaScript

All logic lives in `script.js`. Three responsibilities:

### 1. Theme Init (runs before paint)

```js
const saved = localStorage.getItem('theme');
const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
const theme = saved ?? (prefersDark ? 'dark' : 'light');
document.documentElement.setAttribute('data-theme', theme);
```

Runs synchronously at the top of `script.js` to avoid a flash of the wrong theme.

### 2. Toggle Handler

```js
btn.addEventListener('click', () => {
  const isLight = document.documentElement.getAttribute('data-theme') === 'light';
  const next = isLight ? 'dark' : 'light';
  document.documentElement.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
});
```

`data-theme` is always set to either `'dark'` or `'light'` — no implicit "no attribute = dark" state.

### 3. Icon Sync

Handled entirely by CSS — no JS needed.

---

## Scope

- Touches: `index.html`, `style.css`, `script.js`
- No new files
- No dependencies
