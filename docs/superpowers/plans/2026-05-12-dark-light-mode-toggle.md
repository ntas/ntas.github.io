# Dark / Light Mode Toggle Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a nav bar toggle that switches between dark and warm-cream light mode, honours OS preference on first visit, and persists the user's choice via `localStorage`.

**Architecture:** CSS custom properties drive all colours; a `html[data-theme="light"]` selector overrides the dark defaults. JS reads OS preference and `localStorage` on load (synchronously, before paint), then wires up the toggle button click handler. No build step, no dependencies.

**Tech Stack:** Vanilla HTML, CSS custom properties, vanilla JS, localStorage, `prefers-color-scheme` media query.

---

## File Map

| File | Change |
|---|---|
| `style.css` | Add light theme token block, transition rules, nav backdrop override, toggle button styles |
| `index.html` | Add `<button>` to nav |
| `script.js` | Add theme init at top, add toggle click handler at bottom |

---

## Task 1: Light theme CSS tokens

**Files:**
- Modify: `style.css` — add immediately after the closing `}` of the `:root` block

- [ ] **Step 1: Add the light theme token block**

Open `style.css`. Find the `:root { … }` block (it ends around line 25). Directly after its closing brace, insert:

```css
html[data-theme="light"] {
  --bg:         #f5efe6;
  --surface:    #ede7dd;
  --border:     #d9d2c8;
  --text:       #1a1a1a;
  --muted:      #8a8070;
  --muted-lt:   #5a5248;
  --accent-dim: rgba(249, 115, 22, 0.12);
}
```

- [ ] **Step 2: Override the hardcoded nav backdrop for light mode**

The nav's `.scrolled` rule uses a hardcoded `rgba(11,11,11,…)` value that won't pick up the token. Add this block directly after the `#nav.scrolled { … }` rule:

```css
html[data-theme="light"] #nav.scrolled {
  background: rgba(245, 239, 230, 0.92);
}
```

- [ ] **Step 3: Add smooth transition + no-flash guard**

Add these two rules anywhere in the global section of `style.css` (after the `body { … }` block is fine):

```css
body,
#nav,
.project-card,
.photo-placeholder,
.skill-group li,
footer {
  transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease;
}

.no-transition * {
  transition: none !important;
}
```

- [ ] **Step 4: Verify in browser**

Open `index.html` in a browser. Open DevTools → Elements. On the `<html>` element, manually add the attribute `data-theme="light"`. The page should immediately switch to a warm cream background (`#f5efe6`) with dark text. Remove the attribute — it should switch back to dark. No colour should remain wrong after toggling.

- [ ] **Step 5: Commit**

```bash
git add style.css
git commit -m "feat: add light theme CSS tokens and transition rules"
```

---

## Task 2: Toggle button — HTML and CSS

**Files:**
- Modify: `index.html` — add button to `<nav>`
- Modify: `style.css` — add button and icon styles

- [ ] **Step 1: Add the button to the nav**

In `index.html`, find the `<nav id="nav">` block. It currently ends with `</ul>` then `</nav>`. Insert the button between the closing `</ul>` and `</nav>`:

```html
    </ul>
    <button class="theme-toggle" id="theme-toggle" aria-label="Toggle light mode">
      <span class="icon-sun">☀</span>
      <span class="icon-moon">☾</span>
    </button>
  </nav>
```

- [ ] **Step 2: Add button and icon styles to style.css**

Add these rules at the end of the `/* ─── Navigation ─── */` section (after the `.nav-links a:hover` rule):

```css
.theme-toggle {
  background: none;
  border: none;
  cursor: pointer;
  color: var(--muted);
  font-size: 1rem;
  padding: 0.25rem 0.375rem;
  line-height: 1;
  display: flex;
  align-items: center;
  transition: color 0.2s;
}

.theme-toggle:hover { color: var(--accent); }

/* Dark mode: show sun, hide moon */
.icon-moon { display: none; }

/* Light mode: show moon, hide sun */
html[data-theme="light"] .icon-sun  { display: none; }
html[data-theme="light"] .icon-moon { display: inline; }
```

- [ ] **Step 3: Verify in browser**

Reload `index.html`. A ☀ icon should appear in the nav to the right of the `[contact]` link. It should be muted grey and turn orange on hover. In DevTools, set `data-theme="light"` on `<html>` — the icon should switch to ☾.

- [ ] **Step 4: Commit**

```bash
git add index.html style.css
git commit -m "feat: add theme toggle button to nav"
```

---

## Task 3: JS — theme init and toggle handler

**Files:**
- Modify: `script.js` — add init block at the very top, add toggle handler at the bottom

- [ ] **Step 1: Add theme init at the top of script.js**

Open `script.js`. The very first line currently is a comment about the nav scroll effect. Insert this block **before** that line:

```js
// Theme init — must run before first paint to prevent flash
(function () {
  document.documentElement.classList.add('no-transition');
  const saved = localStorage.getItem('theme');
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  const theme = saved ?? (prefersDark ? 'dark' : 'light');
  document.documentElement.setAttribute('data-theme', theme);
  requestAnimationFrame(() => {
    document.documentElement.classList.remove('no-transition');
  });
}());
```

The IIFE keeps the variables out of global scope. `requestAnimationFrame` removes the no-transition guard after the first frame so subsequent user-triggered toggles animate smoothly.

- [ ] **Step 2: Add toggle click handler at the bottom of script.js**

After all existing code in `script.js`, append:

```js
// Theme toggle
const themeBtn = document.getElementById('theme-toggle');
themeBtn.addEventListener('click', () => {
  const isLight = document.documentElement.getAttribute('data-theme') === 'light';
  const next = isLight ? 'dark' : 'light';
  document.documentElement.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
});
```

- [ ] **Step 3: Verify — toggle works**

Reload `index.html`. Click the ☀ button. The page should smoothly crossfade to warm cream light mode and the icon should switch to ☾. Click again — back to dark. No flash, smooth transition.

- [ ] **Step 4: Verify — preference persists**

While in light mode, reload the page. The page should load in light mode immediately (no dark flash). Open DevTools → Application → Local Storage → `file://` — confirm `theme: "light"` is stored.

- [ ] **Step 5: Verify — OS preference respected on first visit**

In DevTools → Rendering → Emulate CSS media feature → set `prefers-color-scheme: light`. Clear localStorage (`localStorage.removeItem('theme')`). Reload. Page should load in light mode. Set it to `prefers-color-scheme: dark`, clear localStorage, reload — should load in dark mode.

- [ ] **Step 6: Commit**

```bash
git add script.js
git commit -m "feat: wire up theme toggle — init, persistence, OS preference"
```

---

## Task 4: Final check and tidy

- [ ] **Step 1: Test all three scenarios end-to-end**

  1. Clear localStorage. Set OS emulation to `light`. Reload → loads light. Toggle → goes dark. Reload → stays dark.
  2. Clear localStorage. Set OS emulation to `dark`. Reload → loads dark. Toggle → goes light. Reload → stays light.
  3. No OS emulation. Reload. Toggle several times quickly — transitions should be smooth, no flicker.

- [ ] **Step 2: Check mobile layout**

Resize browser to 375px wide. Toggle button should still be visible in the nav. On very narrow widths the nav links are hidden (by existing CSS) but the toggle button should remain.

- [ ] **Step 3: Commit if anything was fixed, otherwise done**

```bash
git add -p   # stage only intentional changes
git commit -m "fix: toggle mobile and edge-case polish"
```
