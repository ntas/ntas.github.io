# Content Personalisation — Design Spec

**Date:** 2026-06-02
**Status:** Approved

---

## Overview

Replace all placeholder content in `index.html` with Sam Phiri's real information. No structural or styling changes — this is a pure content pass.

---

## Global

| Element | Value |
|---|---|
| `<title>` | `Sam Phiri` |
| `<meta name="description">` | `Sam Phiri is a full stack developer who designs and builds digital products for the web.` |
| Nav logo (`.nav-logo`) | `SP.` |
| Side email (`.side-email`) | `mtaski@31twelve.uk` |
| Footer credit | `Designed & built by Sam Phiri — 2026` |

---

## Hero

| Element | Value |
|---|---|
| Greeting | `Hi, my name is` |
| `.hero-name` | `Sam Phiri.` |
| `.hero-tagline` | `I design and build digital products for the web.` |
| `.hero-desc` | `I'm a full stack developer based in London, specialising in building exceptional web experiences and applications. From e-commerce to custom web apps and browser extensions — crafting digital products at <a href="https://31twelve.uk" class="inline-link">31twelve</a>.` |
| CTA button | `Get In Touch` → `mailto:mtaski@31twelve.uk` |

---

## About

**Bio (four paragraphs):**

1. Hello! I'm Sam Phiri, a full stack developer based in London. I enjoy creating things that live on the internet — websites, applications, and everything in between.
2. My focus is on building great web experiences and applications, from e-commerce platforms to custom web apps and extensions that cater to all types of businesses.
3. I care about writing code that is both technically sound and a pleasure for people to use.
4. Here are a few technologies I've been working with recently:

**Skills list (two-column):**
- HTML
- CSS
- JavaScript
- TypeScript
- React
- Node.js
- PHP
- WordPress
- Shopify

---

## Experience

Two tabs. The third placeholder tab is removed.

### Tab 1 — Ecommerce Manager & Website Administrator

**Company:** Flawlesshalf (Sawsan & Risaaq Ltd)
**Dates:** May 2023 – July 2024
**Bullets:**
- Designed and implemented an online store using WordPress + WooCommerce, customised for an online bridal boutique with a fully featured makeup booking system including custom fields and plugins.
- Managed day-to-day site administration: uploading products, editing content, merchandising, and SEO optimisation to improve performance.
- Monitored Google Analytics and conducted website performance, market, and competitor analysis to surface actionable recommendations for stakeholders.

### Tab 2 — WordPress Developer

**Company:** Key Stage Learning (ksl.org.uk)
**Dates:** May 2021 – June 2023
**Bullets:**
- Developed and maintained WordPress websites, ensuring optimal performance and responsiveness across devices.
- Customised and implemented WordPress themes and plugins to meet evolving business requirements; collaborated with design and content teams on UX.
- Designed and implemented a Learning Management System (Moodle-based) serving 6 teachers and 64 students, with a self-hosted Collabora + Nextcloud server for document collaboration and storage.
- Conducted regular website updates, security audits, and performance optimisations.

---

## Featured Work

Two featured projects. The third placeholder is removed.

### Project 1 — Flawlesshalf

**Overline:** Featured Project
**Title:** Flawlesshalf
**Description:** An e-commerce platform specialising in traditional wedding dresses and accessories. Integrated shipping APIs to auto-calculate rates at checkout, built on a custom PHP/MySQL stack.
**Tech:** HTML, CSS, JavaScript, PHP, MySQL
**Links:** External link → `https://flawlesshalf.com` (GitHub link removed — no repo supplied)
**Layout:** Left-aligned (default)

### Project 2 — Elays Network

**Overline:** Featured Project
**Title:** Elays Network
**Description:** Website for a local charity in Battersea, London, serving a wide range of community members — from at-risk children to the elderly. Built on WordPress with a custom PHP/MySQL backend.
**Tech:** HTML, CSS, JavaScript, PHP, MySQL, WordPress
**Links:** External link → `https://elaysnetwork.com`
**Layout:** Right-aligned (`featured-item--right`)

---

## Other Projects Section

Removed entirely. The `<section id="projects">` block and its heading are deleted from `index.html`.

---

## Side Panels

### Left — Social icons

Keep: GitHub, LinkedIn. Remove: Twitter/X, CodePen.

| Icon | URL |
|---|---|
| GitHub | `https://github.com/ntas` |
| LinkedIn | `https://www.linkedin.com/in/ntas` |

### Right — Email

`mtaski@31twelve.uk`

---

## Contact Section

| Element | Value |
|---|---|
| Overline | `04. What's Next?` |
| Heading | `Get In Touch` |
| Body | `I'm currently open to new opportunities. Whether you have a question, a project in mind, or just want to say hello — my inbox is always open.` |
| CTA button | `Say Hello` → `mailto:mtaski@31twelve.uk` |

---

## Scope

- Touches: `index.html` only
- No changes to `style.css` or `script.js`
- No new files
