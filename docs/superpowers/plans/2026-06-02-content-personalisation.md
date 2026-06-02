# Content Personalisation Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace all placeholder content in `index.html` with Sam Phiri's real information.

**Architecture:** Pure content pass — only `index.html` is touched. No changes to `style.css` or `script.js`. Each task covers one page section and ends with a commit.

**Tech Stack:** Vanilla HTML. No build step. Preview with `python3 -m http.server 8000` at `http://localhost:8000`.

---

## File Map

| File | Change |
|---|---|
| `index.html` | All placeholder content replaced; 3rd experience tab, 3rd featured project, and entire Other Projects section removed |

---

## Task 1: Global metadata, nav logo, and footer

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update `<title>` and `<meta name="description">`**

Find:
```html
  <title>Your Name</title>
  <meta name="description" content="Your Name is a software developer who builds things for the web.">
```
Replace with:
```html
  <title>Sam Phiri</title>
  <meta name="description" content="Sam Phiri is a full stack developer who designs and builds digital products for the web.">
```

- [ ] **Step 2: Update the nav logo**

Find:
```html
      <a href="/" class="nav-logo">YN.</a>
```
Replace with:
```html
      <a href="/" class="nav-logo">SP.</a>
```

- [ ] **Step 3: Update the footer**

Find:
```html
    <p>Designed &amp; built by Your Name &mdash; 2025</p>
```
Replace with:
```html
    <p>Designed &amp; built by Sam Phiri &mdash; 2026</p>
```

- [ ] **Step 4: Verify in browser**

Run: `python3 -m http.server 8000` then open `http://localhost:8000`.
Check: browser tab reads "Sam Phiri", nav logo reads "SP.", footer reads "Designed & built by Sam Phiri — 2026".

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "content: update global metadata, nav logo, and footer"
```

---

## Task 2: Hero section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update the hero content**

Find:
```html
      <p class="hero-greeting fade-in" style="transition-delay:100ms">Hi, my name is</p>
      <h1 class="hero-name fade-in" style="transition-delay:200ms">Your Name.</h1>
      <h2 class="hero-tagline fade-in" style="transition-delay:300ms">I build things for the web.</h2>
      <p class="hero-desc fade-in" style="transition-delay:400ms">I'm a software developer specialising in building exceptional digital experiences. Currently focused on building accessible, human-centred products at <a href="#" class="inline-link">Company Name</a>.</p>
      <a href="mailto:hello@yourname.com" class="btn-primary fade-in" style="transition-delay:500ms">Get In Touch</a>
```
Replace with:
```html
      <p class="hero-greeting fade-in" style="transition-delay:100ms">Hi, my name is</p>
      <h1 class="hero-name fade-in" style="transition-delay:200ms">Sam Phiri.</h1>
      <h2 class="hero-tagline fade-in" style="transition-delay:300ms">I design and build digital products for the web.</h2>
      <p class="hero-desc fade-in" style="transition-delay:400ms">I'm a full stack developer based in London, specialising in building exceptional web experiences and applications. From e-commerce to custom web apps and browser extensions — crafting digital products at <a href="https://31twelve.uk" class="inline-link">31twelve</a>.</p>
      <a href="mailto:mtaski@31twelve.uk" class="btn-primary fade-in" style="transition-delay:500ms">Get In Touch</a>
```

- [ ] **Step 2: Verify in browser**

Open `http://localhost:8000`. Check: hero name reads "Sam Phiri.", tagline reads "I design and build digital products for the web.", description contains "31twelve" as a link, "Get In Touch" button links to `mtaski@31twelve.uk`.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "content: update hero section"
```

---

## Task 3: About section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update the bio paragraphs and skills list**

Find:
```html
        <div class="about-text">
          <p>Hello! I'm Your Name, a developer based in <em>Your City</em>. I enjoy creating things that live on the internet — websites, applications, and everything in between.</p>
          <p>My main focus these days is building accessible, inclusive products and digital experiences. I love the challenge of writing code that is both technically sound and a pleasure for people to use.</p>
          <p>When I'm not at my desk I'm usually [walking / reading / photographing / something human]. I believe the best work comes from curiosity and craft in equal measure.</p>
          <p>Here are a few technologies I've been working with recently:</p>
          <ul class="skills-list">
            <li>JavaScript (ES6+)</li>
            <li>TypeScript</li>
            <li>React</li>
            <li>Node.js</li>
            <li>Python</li>
            <li>PostgreSQL</li>
          </ul>
        </div>
```
Replace with:
```html
        <div class="about-text">
          <p>Hello! I'm Sam Phiri, a full stack developer based in <em>London</em>. I enjoy creating things that live on the internet — websites, applications, and everything in between.</p>
          <p>My focus is on building great web experiences and applications, from e-commerce platforms to custom web apps and extensions that cater to all types of businesses.</p>
          <p>I care about writing code that is both technically sound and a pleasure for people to use.</p>
          <p>Here are a few technologies I've been working with recently:</p>
          <ul class="skills-list">
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
            <li>TypeScript</li>
            <li>React</li>
            <li>Node.js</li>
            <li>PHP</li>
            <li>WordPress</li>
            <li>Shopify</li>
          </ul>
        </div>
```

- [ ] **Step 2: Verify in browser**

Scroll to About. Check: name and city correct, bio matches, skills list shows all 9 technologies.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "content: update about section"
```

---

## Task 4: Experience section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Replace the entire tab list and tab panels**

Find:
```html
        <div class="tab-list" role="tablist" aria-label="Job experience">
          <button class="tab-btn active" role="tab" data-tab="0" aria-selected="true">Company A</button>
          <button class="tab-btn" role="tab" data-tab="1" aria-selected="false">Company B</button>
          <button class="tab-btn" role="tab" data-tab="2" aria-selected="false">Company C</button>
        </div>
        <div class="tab-panels">
          <div class="tab-panel active" role="tabpanel" data-panel="0">
            <h3 class="job-title">Senior Developer <span class="company-name">@ Company A</span></h3>
            <p class="date-range">January 2023 – Present</p>
            <ul>
              <li>Describe a key achievement or responsibility in one or two sentences, focusing on impact and scope.</li>
              <li>Another responsibility or accomplishment worth highlighting — the more specific the better.</li>
              <li>A third bullet covering measurable outcomes or the scale of your contribution.</li>
            </ul>
          </div>
          <div class="tab-panel" role="tabpanel" data-panel="1">
            <h3 class="job-title">Developer <span class="company-name">@ Company B</span></h3>
            <p class="date-range">June 2021 – December 2022</p>
            <ul>
              <li>Led development of a key product feature used by thousands of users daily.</li>
              <li>Collaborated with design and product teams to ship new features on schedule.</li>
              <li>Improved performance of the core data pipeline by optimising queries and caching strategies.</li>
            </ul>
          </div>
          <div class="tab-panel" role="tabpanel" data-panel="2">
            <h3 class="job-title">Junior Developer <span class="company-name">@ Company C</span></h3>
            <p class="date-range">September 2019 – May 2021</p>
            <ul>
              <li>Worked across the full stack to deliver new features and resolve bugs in a fast-paced environment.</li>
              <li>Wrote unit and integration tests, maintaining coverage above 80% across the codebase.</li>
              <li>Participated in code reviews and contributed to internal technical documentation.</li>
            </ul>
          </div>
        </div>
```
Replace with:
```html
        <div class="tab-list" role="tablist" aria-label="Job experience">
          <button class="tab-btn active" role="tab" data-tab="0" aria-selected="true">Flawlesshalf</button>
          <button class="tab-btn" role="tab" data-tab="1" aria-selected="false">Key Stage Learning</button>
        </div>
        <div class="tab-panels">
          <div class="tab-panel active" role="tabpanel" data-panel="0">
            <h3 class="job-title">Ecommerce Manager &amp; Website Administrator <span class="company-name">@ Flawlesshalf</span></h3>
            <p class="date-range">May 2023 – July 2024</p>
            <ul>
              <li>Designed and implemented an online store using WordPress + WooCommerce, customised for an online bridal boutique with a fully featured makeup booking system including custom fields and plugins.</li>
              <li>Managed day-to-day site administration: uploading products, editing content, merchandising, and SEO optimisation to improve performance.</li>
              <li>Monitored Google Analytics and conducted website performance, market, and competitor analysis to surface actionable recommendations for stakeholders.</li>
            </ul>
          </div>
          <div class="tab-panel" role="tabpanel" data-panel="1">
            <h3 class="job-title">WordPress Developer <span class="company-name">@ Key Stage Learning</span></h3>
            <p class="date-range">May 2021 – June 2023</p>
            <ul>
              <li>Developed and maintained WordPress websites, ensuring optimal performance and responsiveness across devices.</li>
              <li>Customised and implemented WordPress themes and plugins to meet evolving business requirements; collaborated with design and content teams on UX.</li>
              <li>Designed and implemented a Learning Management System (Moodle-based) serving 6 teachers and 64 students, with a self-hosted Collabora + Nextcloud server for document collaboration and storage.</li>
              <li>Conducted regular website updates, security audits, and performance optimisations.</li>
            </ul>
          </div>
        </div>
```

- [ ] **Step 2: Verify in browser**

Scroll to Experience. Check: two tabs visible ("Flawlesshalf", "Key Stage Learning"), correct job titles, dates, and bullet points. Clicking each tab switches the panel correctly.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "content: update experience section with real work history"
```

---

## Task 5: Featured Work section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Replace the entire featured list**

Find:
```html
      <ul class="featured-list">

        <li class="featured-item fade-in">
```
…through to (and including)…
```html
        </li>

      </ul>
    </section>

    <!-- ─── Other Projects ─────────────────────────────────────────────────────── -->
```
Replace with:
```html
      <ul class="featured-list">

        <li class="featured-item fade-in">
          <div class="featured-img">
            <div class="img-placeholder">Project Screenshot</div>
          </div>
          <div class="featured-content">
            <p class="overline">Featured Project</p>
            <h3 class="featured-title">Flawlesshalf</h3>
            <div class="featured-desc">
              <p>An e-commerce platform specialising in traditional wedding dresses and accessories. Integrated shipping APIs to auto-calculate rates at checkout, built on a custom PHP/MySQL stack.</p>
            </div>
            <ul class="tech-list">
              <li>HTML</li>
              <li>CSS</li>
              <li>JavaScript</li>
              <li>PHP</li>
              <li>MySQL</li>
            </ul>
            <div class="featured-links">
              <a href="https://flawlesshalf.com" aria-label="External Link" target="_blank" rel="noopener">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
              </a>
            </div>
          </div>
        </li>

        <li class="featured-item featured-item--right fade-in">
          <div class="featured-img">
            <div class="img-placeholder">Project Screenshot</div>
          </div>
          <div class="featured-content">
            <p class="overline">Featured Project</p>
            <h3 class="featured-title">Elays Network</h3>
            <div class="featured-desc">
              <p>Website for a local charity in Battersea, London, serving a wide range of community members — from at-risk children to the elderly. Built on WordPress with a custom PHP/MySQL backend.</p>
            </div>
            <ul class="tech-list">
              <li>HTML</li>
              <li>CSS</li>
              <li>JavaScript</li>
              <li>PHP</li>
              <li>MySQL</li>
              <li>WordPress</li>
            </ul>
            <div class="featured-links">
              <a href="https://elaysnetwork.com" aria-label="External Link" target="_blank" rel="noopener">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
              </a>
            </div>
          </div>
        </li>

      </ul>
    </section>

    <!-- ─── Other Projects ─────────────────────────────────────────────────────── -->
```

- [ ] **Step 2: Verify in browser**

Scroll to Work. Check: two featured projects visible, "Flawlesshalf" on the left with correct description and tech, "Elays Network" on the right with correct description and tech. Each has one external link icon.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "content: update featured work section with real projects"
```

---

## Task 6: Remove Other Projects section; update side panels, contact, and footer email

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Remove the entire Other Projects section**

Find and delete this block in full (from the comment through to the closing `</section>`):
```html
    <!-- ─── Other Projects ─────────────────────────────────────────────────────── -->
    <section id="projects" class="section">
      <h2 class="projects-heading fade-in">Other Noteworthy Projects</h2>
      <ul class="projects-grid">
        …all six .project-card items…
      </ul>
    </section>
```
The line after the deleted block should be the contact section comment:
```html
    <!-- ─── Contact ─────────────────────────────────────────────────────────────── -->
```

- [ ] **Step 2: Update the contact section emails**

Find:
```html
      <a href="mailto:hello@yourname.com" class="btn-primary fade-in" style="transition-delay:300ms">Say Hello</a>
```
Replace with:
```html
      <a href="mailto:mtaski@31twelve.uk" class="btn-primary fade-in" style="transition-delay:300ms">Say Hello</a>
```

- [ ] **Step 3: Update the left side panel — keep GitHub and LinkedIn, remove Twitter and CodePen**

Find the entire `<aside class="side side--left" …>` block:
```html
  <aside class="side side--left" aria-label="Social links">
    <ul class="social-icons">
      <li>
        <a href="https://github.com/" aria-label="GitHub" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>
        </a>
      </li>
      <li>
        <a href="https://www.linkedin.com/" aria-label="LinkedIn" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
      </li>
      <li>
        <a href="https://twitter.com/" aria-label="Twitter / X" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"/></svg>
        </a>
      </li>
      <li>
        <a href="https://codepen.io/" aria-label="CodePen" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><polygon points="12 2 22 8.5 22 15.5 12 22 2 15.5 2 8.5 12 2"/><line x1="12" y1="22" x2="12" y2="15.5"/><polyline points="22 8.5 12 15.5 2 8.5"/><polyline points="2 15.5 12 8.5 22 15.5"/><line x1="12" y1="2" x2="12" y2="8.5"/></svg>
        </a>
      </li>
    </ul>
  </aside>
```
Replace with:
```html
  <aside class="side side--left" aria-label="Social links">
    <ul class="social-icons">
      <li>
        <a href="https://github.com/ntas" aria-label="GitHub" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/></svg>
        </a>
      </li>
      <li>
        <a href="https://www.linkedin.com/in/ntas" aria-label="LinkedIn" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" width="20" height="20"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
      </li>
    </ul>
  </aside>
```

- [ ] **Step 4: Update the right side panel email**

Find:
```html
  <aside class="side side--right" aria-label="Email">
    <a href="mailto:hello@yourname.com" class="side-email">hello@yourname.com</a>
  </aside>
```
Replace with:
```html
  <aside class="side side--right" aria-label="Email">
    <a href="mailto:mtaski@31twelve.uk" class="side-email">mtaski@31twelve.uk</a>
  </aside>
```

- [ ] **Step 5: Verify in browser**

Scroll through the full page. Check:
- No "Other Noteworthy Projects" section
- Contact "Say Hello" button links to `mtaski@31twelve.uk`
- Left side panel shows only GitHub and LinkedIn icons, both linking to the correct URLs
- Right side panel shows `mtaski@31twelve.uk`

- [ ] **Step 6: Commit**

```bash
git add index.html
git commit -m "content: remove other projects section; update contact, side panels, and social links"
```
