# Claude Practice Page Design Spec

## Purpose And Scan Order
1. Hero: immediately states Claude-specific practice and audience fit.
2. Why Claude: three concise reasons tied to nonprofit risk, context-heavy work, and agentic leverage.
3. Service cards: five clear Claude-specific offerings.
4. Evidence tiles: concrete proof for Anthropic review and buyer trust.
5. Who we serve: explicit market fit list.
6. CTA band: primary contact action and secondary public artifacts action.

Rationale: this order supports a 90-second reviewer scan while still helping a skeptical executive director understand practical value and next steps.

## Typography And Color Treatment
- Reuse existing typography: Plus Jakarta Sans for headings, Inter for body.
- Reuse existing tokens from `:root` in `css/styles.css`:
  - Navy `--navy`, `--navy-mid`, `--navy-dark`
  - Gold `--gold`, `--gold-light`
  - Gray scale `--gray-50`, `--gray-100`, `--gray-200`
  - Text tones `--text`, `--text-mid`, `--text-light`
- Keep tone serious and technical:
  - High contrast headings on navy and white backgrounds.
  - Gold used only for labels, icons, and emphasis.
  - Minimal decorative effects.

## Component Specs

### Service Card
- Base classes: `card claude-service-card`
- Content structure: icon, h3, short paragraph, meta block.
- Default state:
  - Border `1px solid var(--gray-200)`
  - Shadow `var(--shadow-sm)`
  - Background `var(--white)`
- Hover state:
  - Shadow `var(--shadow-lg)`
  - Transform `translateY(-3px)`
  - Border color transparent
- Focus state:
  - `outline: 2px solid var(--navy)`
  - `outline-offset: 2px`

### Evidence Tile
- Base classes: `card evidence-tile`
- Content structure: heading, short evidence paragraph, optional link.
- Default state:
  - Background `var(--white)`
  - Border `1px solid var(--gray-200)`
  - Padding consistent with card rhythm
- Hover state:
  - Border color `var(--navy)`
  - Shadow `var(--shadow)`
- Focus state (focus within):
  - `outline: 2px solid var(--navy)`
  - `outline-offset: 2px`

## Responsive And Mobile-First Guidance
- Reuse existing breakpoints:
  - Tablet: `@media (max-width: 1024px)`
  - Mobile: `@media (max-width: 768px)`
- Grid behavior:
  - Service cards use existing `grid-3` fallback behavior.
  - Evidence tiles use 3 columns desktop, 2 tablet, 1 mobile.
- CTA actions stack vertically on mobile.
- Keep paragraph line length under control with max-width in headers.

## Implementation Class Strings
- Hero section: `page-hero`
- Main sections: `section`, alternate background with `section-alt`
- Headers: `section-header centered`, `section-label`
- Why Claude list: `tiles-grid`, `tile`, `tile-icon`
- Services list: `grid-3`, `card claude-service-card`, `card-icon`, `card-meta`
- Evidence list: `evidence-grid`, `card evidence-tile`
- Who we serve list: `serve-list`
- CTA area: `cta-band`, `cta-band-inner`, `cta-band-actions`
- Actions: `btn btn-gold btn-lg` for primary and `btn btn-outline-white` for secondary

## Accessibility Requirements
- Semantic heading order starts at h1 and moves section by section.
- Visible focus states on interactive elements and linked evidence artifacts.
- Descriptive alt text on social card image and existing logos.
- Maintain color contrast consistent with current palette and WCAG 2.1 AA intent.

## Content Guardrails
- Plain-language copy, no hype.
- No unsupported capability claims.
- No client-specific claims without permission.
- No em dashes in new copy.

---

# Content Specification: claude-practice.html

> **Audience note:** Every section must serve two readers simultaneously. The Anthropic Partner Network reviewer is technically sophisticated and will evaluate whether Claude-specific depth is real. The nonprofit executive director is mission-driven, budget-constrained, and skeptical of AI hype. Copy that works for both is calm, precise, and concrete. Avoid generic superlatives. Let specifics do the work.

---

## Section 1 -- Page Metadata

### `<title>` tag
```
Our Claude Practice -- Wheeler Tech AI
```

### `<meta name="description">` content
```
Wheeler Tech AI's dedicated Claude practice: readiness assessments, API deployment, responsible governance, and Claude-powered workflow design for nonprofits and civic organizations.
```

### Nav active state
On `claude-practice.html`, the **Services** `<a>` in `.nav-links` receives the `active` class. No new top-level nav item is added. See Section 9 for nav update details.

### File name
`claude-practice.html` -- placed in the root directory alongside `services.html`, `about.html`, etc.

---

## Section 2 -- Hero (`class="page-hero"`)

The hero follows the same `.page-hero` pattern used on `services.html`, `about.html`, and `work.html`. It is a navy background section with the `.section-label` eyebrow, an h1, and a short subheading paragraph.

### Eyebrow label (`class="section-label"`)
```
Claude Practice
```

### h1
```
A Claude Practice Built
for Mission-Driven Organizations.
```

> **Render note:** The line break falls after "Built" on desktop. On mobile the h1 reflows naturally. Do not force a `<br>` unless it is needed to prevent an awkward single-word orphan on desktop.

### Subheading paragraph (`color: rgba(255,255,255,0.72)`, `max-width: 560px`)
```
We help nonprofits and civic organizations adopt Anthropic's Claude with the depth and discipline the work requires. This is not a generic AI consulting offering.
```

> **Copy note:** "Anthropic's Claude" names the model and the maker in the first sentence. "Not a generic AI consulting offering" sets the differentiator without attacking competitors. Both sentences are under 20 words.

---

## Section 3 -- Why Claude (`class="section"`)

Background: `var(--white)`. Centered section header. Three tiles using `.tiles-grid.tiles-grid-3` / `.tile` / `.tile-icon`.

> **Responsive note:** The existing `.tiles-grid` is 4-column by default. Apply the modifier class `.tiles-grid-3` (defined in Section 8) to render 3 columns on desktop. On tablet the tiles stack to 2 columns; on mobile, 1 column. See Section 8 for the CSS.

### Section header

**section-label:**
```
Why Claude
```

**h2:**
```
Claude Is the Right Model for This Work.
```

**Introductory paragraph** (`max-width: 600px`, centered via `.section-header.centered p` rule):
```
Not every AI model is appropriate for mission-driven organizations. Claude's design choices around safety, context capacity, and agentic capability align directly with the operational reality of nonprofits and civic organizations.
```

---

### Tile 1 -- Nonprofit Risk Profile

**Icon:** `&#9651;` (up-pointing triangle, matches site icon vocabulary)

**h4:**
```
Safety Alignment That Matches Nonprofit Risk Tolerance
```

**Paragraph:**
```
Nonprofits face real reputational and fiduciary risk when AI outputs are unreliable, biased, or opaque. Claude is built with Constitutional AI principles that cause it to refuse harmful requests, flag uncertainty, and behave predictably across edge cases. That consistency matters to your board, your funders, and the communities you serve.
```

---

### Tile 2 -- Context-Heavy Mission Work

**Icon:** `&#9654;` (right-pointing triangle)

**h4:**
```
Long Context for the Documents Your Work Actually Involves
```

**Paragraph:**
```
Grants, bylaws, program reports, case files, and board minutes are long and layered. Claude's large context window lets it read, cross-reference, and reason across the full scope of your organizational documents in a single session. Your staff stops copy-pasting fragments and starts getting substantive answers.
```

---

### Tile 3 -- Agentic Operations

**Icon:** `&#9670;` (diamond)

**h4:**
```
Agentic Capability for Operations You Do Not Have Staff For
```

**Paragraph:**
```
Small nonprofits run operations that would require multiple staff roles in a larger organization. Claude's agentic capabilities allow it to execute multi-step workflows: drafting, reviewing, routing, and logging work across your systems. We design and deploy those workflows so your team focuses on mission instead of administration.
```

---

## Section 4 -- Services (`class="section section-alt"`)

Background: `var(--gray-50)`. Centered section header. Five service cards using `.grid-3` / `.card.claude-service-card`.

> **Layout note:** Five cards in a `.grid-3` will produce a row of 3 and a row of 2. The partial second row sits left-aligned, which matches the pattern on `services.html`. No special centering is required.

### Section header

**section-label:**
```
Claude Services
```

**h2:**
```
Five Focused Claude Engagements.
```

> No introductory paragraph is needed in this section. Move directly to the card grid.

---

### Card 1 -- Claude Readiness and Fit Assessment

**Icon:** `&#9651;`

**h3:**
```
Claude Readiness and Fit Assessment
```

**Description paragraph:**
```
Before any implementation, we evaluate whether Claude is the right tool for your specific use cases. This assessment maps your data environment, staff workflows, compliance considerations, and existing tools to identify where Claude delivers genuine value and where it does not. You receive an honest recommendation, not a proposal shaped around a sale.
```

**card-meta** (use `<strong>Label:</strong> Value<br>` pattern from services.html):
```
Deliverable: Written assessment with recommended use cases, risk flags, and a go/no-go recommendation per use case
Timeline: 2 to 3 weeks
```

---

### Card 2 -- Claude API and Deployment Implementation

**Icon:** `&#9654;`

**h3:**
```
Claude API and Deployment Implementation
```

**Description paragraph:**
```
For organizations ready to move beyond Claude.ai and integrate Claude directly into their systems. We architect and implement Claude API integrations that fit your infrastructure, security requirements, and staff workflows. Every deployment is tested and documented before handoff, and we do not consider the engagement complete until your team can operate it independently.
```

**card-meta:**
```
Deliverable: Working Claude API integration with technical documentation and runbook
Format: Azure-hosted or self-managed, depending on your environment
Timeline: 4 to 8 weeks
```

---

### Card 3 -- Claude-Powered Workflow Automation

**Icon:** `&#9679;` (filled circle)

**h3:**
```
Claude-Powered Workflow Automation
```

**Description paragraph:**
```
We identify the high-repetition, context-heavy tasks your staff handles daily, then design and deploy Claude-powered automation for them. Common patterns include grant research and synthesis, member communications drafting, meeting summary generation, and intake document processing. Every automation is built with explicit staff oversight and escalation paths designed in from the start.
```

**card-meta:**
```
Deliverable: Deployed workflow automation with staff training documentation and escalation procedures
Engagement: Fixed-scope project or ongoing monthly retainer
```

---

### Card 4 -- Responsible AI Governance for Claude Deployments

**Icon:** `&#9733;` (star)

**h3:**
```
Responsible AI Governance for Claude Deployments
```

**Description paragraph:**
```
Using Claude in an organizational context requires policies your staff will actually follow and your board can actually understand. We help you define acceptable use, document decision accountability, build escalation paths for edge cases, and create the audit record your funders and board may one day request. This is governance designed for the real operational scale of a nonprofit, not a Fortune 500 compliance framework.
```

**card-meta:**
```
Deliverable: Acceptable use policy, governance framework, staff guidance documentation, and board-ready summary
Timeline: 3 to 4 weeks
```

---

### Card 5 -- Claude Staff Training Workshop

**Icon:** `&#9632;` (filled square -- visually distinct from the triangle, circle, and star used above)

> **Icon set summary for this page:** Card 1: `&#9651;` triangle. Card 2: `&#9654;` right triangle. Card 3: `&#9679;` circle. Card 4: `&#9733;` star. Card 5: `&#9632;` square. This set is visually distinct and matches the existing site icon vocabulary.

**h3:**
```
Claude Staff Training Workshop
```

**Description paragraph:**
```
Practical, hands-on training that teaches your staff how to work with Claude effectively and safely. We cover prompt design, context management, output verification, and the organizational guardrails that apply to your specific deployment. Sessions are built around your actual workflows, not generic AI literacy slides.
```

**card-meta:**
```
Format: Virtual or on-site, half-day or full-day
Deliverable: Session workbook and a prompt library starter kit built around your use cases
Follow-up: 30-day check-in call included
```

---

## Section 5 -- Evidence (`class="section"`)

Background: `var(--white)`. Centered section header. Four evidence tiles using `.evidence-grid` / `.card.evidence-tile`.

> **Layout note:** Use a 2x2 grid for four tiles (see `.evidence-grid` CSS in Section 8). This is more balanced than a 3-column grid with an orphaned fourth tile.

### Section header

**section-label:**
```
Why Trust This Practice
```

**h2:**
```
Demonstrated Capability, Not Stated Intentions.
```

**Introductory paragraph** (`max-width: 600px`, centered):
```
The following are verifiable facts about Wheeler Tech AI and the work behind this practice. We include them here because an Anthropic partnership review and a skeptical nonprofit board deserve the same level of transparency.
```

---

### Tile 1 -- MissionReach Platform

**h3:**
```
MissionReach: AI Platform for Nonprofits, Built on Azure
```

**Supporting statement:**
```
Wheeler Tech AI designed and built MissionReach, a production SaaS platform for nonprofit AI-assisted content workflows, running on Azure with an architecture specifically designed for Claude API integration. The platform demonstrates our ability to design, build, and ship production AI systems for the mission sector.
```

**Link text:** `View the work`
**Link href:** `work.html`
**Link class:** `tile-link`

---

### Tile 2 -- Nonprofit Leadership Credentials

**h3:**
```
Active Nonprofit Leadership Across Illinois
```

**Supporting statement:**
```
Bill Wheeler has served in elected and appointed leadership roles across multiple Illinois nonprofit organizations, including serving as State President of the Illinois Society, Sons of the American Revolution, and in technology leadership for the Marine Corps Coordinating Council of Illinois. This is direct operational experience with the organizations we serve, not borrowed credibility.
```

**Link text:** `About Bill Wheeler`
**Link href:** `about.html`
**Link class:** `tile-link`

---

### Tile 3 -- Anthropic Partner Network Application

**h3:**
```
Anthropic Authorized Partner Candidate
```

**Supporting statement:**
```
Wheeler Tech AI has formally applied to the Anthropic Partner Network to deliver authorized Claude services to mission-driven organizations. This page is part of our published practice documentation supporting that application, and it reflects the standard of transparency we bring to every client engagement.
```

**Link:** None. Do not include a `.tile-link` on this tile.

---

### Tile 4 -- Responsible Use Commitment

**h3:**
```
Responsible AI as a Written Practice Standard
```

**Supporting statement:**
```
Every Claude engagement we deliver follows responsible use principles consistent with Anthropic's usage policies: no fabrication of outputs presented as organizational fact, no use in high-stakes automated decisions without documented human oversight, and transparent disclosure to end users when Claude is involved in producing content. We document these commitments in writing for every client.
```

**Link text:** `Discuss our approach`
**Link href:** `contact.html`
**Link class:** `tile-link`

---

## Section 6 -- Who We Serve (`class="section section-alt"`)

Background: `var(--gray-50)`. Left-aligned section header (not centered -- omit the `centered` modifier from `.section-header`). Introductory paragraph followed by a `.serve-list` unordered list.

### Section header

**section-label:**
```
Who We Serve
```

**h2:**
```
Organizations That Fit This Practice.
```

**Introductory paragraph:**
```
We focus on mission-driven organizations that have the operational complexity to benefit from dedicated Claude implementation and the organizational seriousness to use it responsibly.
```

---

### `.serve-list` items

Render as `<ul class="serve-list">` with eight `<li>` elements. Each `<li>` is plain text only. The gold bullet dot is CSS-generated via `::before` (see Section 8) and must not be added in HTML.

```
501(c)(3) public charities with staff-led program delivery
State and local membership associations with communications or operations complexity
Veterans service organizations managing constituency outreach and event coordination
Civic and community foundations with grant administration workflows
Religious and faith-based service organizations with limited technology staff
Regional genealogical, historical, and cultural heritage societies
Advocacy organizations managing constituent data and communications at scale
Small associations without in-house technology leadership or a dedicated IT staff member
```

---

## Section 7 -- CTA Band (`class="cta-band"`)

Use the full `.cta-band-inner` two-column layout (text left, buttons right), which is defined in the existing CSS. This differs from the simpler single-column CTA pattern on `services.html` and is the appropriate choice here because there are two distinct actions.

### Structure

```html
<section class="cta-band">
  <div class="container">
    <div class="cta-band-inner">
      <div>
        <!-- h2 and p go here -->
      </div>
      <div class="cta-band-actions">
        <!-- primary and secondary buttons go here -->
      </div>
    </div>
  </div>
</section>
```

### h2
```
Ready to Discuss a Claude Engagement?
```

### Supporting paragraph (`color: rgba(255,255,255,0.72)`)
```
Most Claude engagements start with a 30-minute discovery call. We will tell you honestly whether Claude is the right fit before we propose any work.
```

### Primary button (`class="btn btn-gold btn-lg"`)
- **Label:** `Schedule a Discovery Call`
- **href:** `contact.html`

### Secondary button (`class="btn btn-outline-white"`)
- **Label:** `See All Services`
- **href:** `services.html`

---

## Section 8 -- New CSS Rules for `css/styles.css`

Add the following block immediately after the existing `/* --- CTA Band --- */` block and before the `/* --- Contact --- */` block. Cascade order matters: `.claude-service-card:hover` must appear after `.card:hover` to win the specificity tie on `border-left-color`.

```css
/* --- Claude Practice Page ---------------------------------------- */

/* Nav dropdown: used on all pages once Services becomes a dropdown trigger */
.nav-item-dropdown { position: relative; }
.nav-dropdown {
  display: none;
  position: absolute;
  top: calc(100% + 4px);
  left: 0;
  background: var(--white);
  border: 1px solid var(--gray-200);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  min-width: 210px;
  padding: 0.5rem 0;
  z-index: 200;
}
.nav-item-dropdown:hover .nav-dropdown,
.nav-item-dropdown:focus-within .nav-dropdown { display: block; }
.nav-dropdown a {
  display: block;
  padding: 0.55rem 1.1rem;
  font-size: 0.88rem;
  font-weight: 500;
  color: var(--text-mid);
  white-space: nowrap;
  border-radius: 0;
  transition: background var(--transition), color var(--transition);
}
.nav-dropdown a:hover { background: var(--gray-100); color: var(--navy); }

/* Mobile-only nav items (show Services sub-link in mobile flat menu) */
.mobile-only { display: none; }

/* Service card: left gold accent on top of .card base */
.claude-service-card { border-left: 3px solid var(--gold); }
.claude-service-card:hover { border-left-color: var(--gold); }
.claude-service-card:focus-within {
  outline: 2px solid var(--navy);
  outline-offset: 2px;
}

/* Evidence grid: 2x2 layout for four tiles */
.evidence-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}

/* Evidence tile: padding and link overrides on top of .card */
.evidence-tile { padding: 1.75rem; }
.evidence-tile:hover { border-color: var(--navy); }
.evidence-tile:focus-within {
  outline: 2px solid var(--navy);
  outline-offset: 2px;
}
.evidence-tile h3 { font-size: 1.05rem; margin-bottom: 0.6rem; }
.tile-link {
  display: inline-block;
  margin-top: 1rem;
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--navy);
  text-decoration: underline;
  text-underline-offset: 3px;
  transition: color var(--transition);
}
.tile-link:hover { color: var(--gold); }

/* Serve list: two-column styled list with CSS gold dots */
.serve-list {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0 2.5rem;
  margin-top: 1.5rem;
}
.serve-list li {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  font-size: 0.95rem;
  color: var(--text-mid);
  padding: 0.65rem 0;
  border-bottom: 1px solid var(--gray-200);
}
.serve-list li::before {
  content: '';
  width: 7px;
  height: 7px;
  min-width: 7px;
  background: var(--gold);
  border-radius: 50%;
  margin-top: 0.55rem;
  flex-shrink: 0;
}

/* Tiles-grid 3-column modifier for the Why Claude section */
.tiles-grid-3 { grid-template-columns: repeat(3, 1fr); }
```

### Responsive additions

Append to the existing `@media (max-width: 1024px)` block:
```css
  .evidence-grid     { grid-template-columns: repeat(2, 1fr); }
  .tiles-grid-3      { grid-template-columns: repeat(2, 1fr); }
  .nav-dropdown      { display: none !important; }
  .mobile-only       { display: list-item; }
```

Append to the existing `@media (max-width: 768px)` block:
```css
  .evidence-grid     { grid-template-columns: 1fr; }
  .serve-list        { grid-template-columns: 1fr; }
  .tiles-grid-3      { grid-template-columns: 1fr; }
```

> **Cascade note on `.claude-service-card:hover`:** The existing `.card:hover` rule sets `border-color: transparent`, which removes all four border sides including the gold left accent. The `.claude-service-card:hover` override restores `border-left-color: var(--gold)`. Both selectors have identical specificity (one class + one pseudo-class). The override works only because `.claude-service-card:hover` is defined after `.card:hover` in the file. The placement in the new block above satisfies this requirement. Do not reorder these rules.

---

## Section 9 -- Nav and Footer Updates

The following files must receive both the nav dropdown update and the footer Services column update:

- `index.html`
- `services.html`
- `about.html`
- `work.html`
- `contact.html`

---

### Nav update -- Services dropdown

**Before (in every file):**
```html
<li><a href="services.html">Services</a></li>
```

**After (in every file except `claude-practice.html`):**
```html
<li class="nav-item-dropdown">
  <a href="services.html">Services</a>
  <ul class="nav-dropdown" role="menu">
    <li><a href="services.html" role="menuitem">All Services</a></li>
    <li><a href="claude-practice.html" role="menuitem">Our Claude Practice</a></li>
  </ul>
</li>
<li class="mobile-only"><a href="claude-practice.html" style="padding-left: 1.5rem; font-size: 0.88rem; color: var(--text-light);">Our Claude Practice</a></li>
```

**In `claude-practice.html` specifically:**
```html
<li class="nav-item-dropdown">
  <a href="services.html" class="active">Services</a>
  <ul class="nav-dropdown" role="menu">
    <li><a href="services.html" role="menuitem">All Services</a></li>
    <li><a href="claude-practice.html" role="menuitem">Our Claude Practice</a></li>
  </ul>
</li>
<li class="mobile-only"><a href="claude-practice.html" class="active" style="padding-left: 1.5rem; font-size: 0.88rem;">Our Claude Practice</a></li>
```

> **Keyboard accessibility note:** The CSS-hover-only dropdown is not keyboard accessible without JavaScript. The existing `js/main.js` handles only the mobile toggle. The developer should either (a) add a `focusin`/`focusout` event listener to `.nav-item-dropdown` that toggles a class controlling visibility, or (b) accept that keyboard users will navigate to `claude-practice.html` via the mobile menu or the footer link. Option (b) is acceptable as a first ship; option (a) is preferred for full WCAG 2.1 AA compliance.

---

### Footer update -- Services column

**Before (in every file):**
```html
<div class="footer-col">
  <h5>Services</h5>
  <ul class="footer-links">
    <li><a href="services.html">AI Readiness Assessment</a></li>
    <li><a href="services.html">AI Strategy and Roadmap</a></li>
    <li><a href="services.html">Fractional CTO</a></li>
    <li><a href="services.html">Staff AI Training</a></li>
  </ul>
</div>
```

**After (in every file):**
```html
<div class="footer-col">
  <h5>Services</h5>
  <ul class="footer-links">
    <li><a href="services.html">AI Readiness Assessment</a></li>
    <li><a href="services.html">AI Strategy and Roadmap</a></li>
    <li><a href="services.html">Fractional CTO</a></li>
    <li><a href="services.html">Staff AI Training</a></li>
    <li><a href="claude-practice.html">Our Claude Practice</a></li>
  </ul>
</div>
```

---

### services.html -- Contextual callout

Add the following immediately before the closing `</section>` of the main services section (after the `.grid-3` div closes). This surfaces the Claude Practice page for visitors who arrive at Services directly.

```html
<div style="margin-top: 3rem; padding-top: 2rem; border-top: 1px solid var(--gray-200); text-align: center;">
  <p style="color: var(--text-light); font-size: 0.95rem; margin-bottom: 0.75rem;">
    Working specifically with Anthropic's Claude? We maintain a dedicated practice for that.
  </p>
  <a href="claude-practice.html" class="btn btn-outline">Explore Our Claude Practice</a>
</div>
```

---

## Appendix A -- Complete Page Structure Reference

Structural skeleton for `claude-practice.html`. Copy is fully specified in Sections 2 through 7.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Our Claude Practice -- Wheeler Tech AI</title>
  <meta name="description" content="Wheeler Tech AI's dedicated Claude practice: readiness assessments, API deployment, responsible governance, and Claude-powered workflow design for nonprofits and civic organizations.">
  <!-- Font links: copy verbatim from services.html -->
  <link rel="stylesheet" href="css/styles.css">
  <link rel="icon" href="assets/images/favicon.png">
</head>
<body>

  <!-- NAV: updated Services dropdown. Active class on Services <a>. See Section 9. -->
  <nav class="nav">...</nav>

  <!-- HERO: class="page-hero" -->
  <!-- .section-label | h1 | p -->

  <!-- WHY CLAUDE: class="section" -->
  <!-- .section-header.centered > .section-label + h2 + p -->
  <!-- .tiles-grid.tiles-grid-3 > 3x .tile > .tile-icon + h4 + p -->

  <!-- SERVICES: class="section section-alt" -->
  <!-- .section-header.centered > .section-label + h2 -->
  <!-- .grid-3 > 5x .card.claude-service-card > .card-icon + h3 + p + .card-meta -->

  <!-- EVIDENCE: class="section" -->
  <!-- .section-header.centered > .section-label + h2 + p -->
  <!-- .evidence-grid > 4x .card.evidence-tile > h3 + p + optional .tile-link -->

  <!-- WHO WE SERVE: class="section section-alt" -->
  <!-- .section-header (not centered) > .section-label + h2 + p -->
  <!-- ul.serve-list > 8x li -->

  <!-- CTA BAND: class="cta-band" -->
  <!-- .cta-band-inner > div(h2+p) + .cta-band-actions > (btn btn-gold btn-lg) + (btn btn-outline-white) -->

  <!-- FOOTER: updated Services column. See Section 9. -->

  <script src="js/main.js"></script>
</body>
</html>
```

---

## Appendix B -- Tone and Voice Quick Reference

| Principle | Do | Do Not |
|---|---|---|
| Claude-specific | Name Claude in headings and copy naturally | Say "AI" when you mean Claude specifically |
| Concrete | Name deliverables, timelines, and formats | Say "tailored solutions" or "cutting-edge" |
| Honest | State what we have built and who Bill is | Fabricate client outcomes or partner status |
| Peer register | Write to a peer executive, not a prospect | Use sales language or excitement punctuation |
| Plain language | Short sentences, active voice | Nested clauses, jargon, or unexpanded acronyms |
| No em dashes | Use a comma, period, or colon instead | Use -- or &mdash; anywhere on this page |