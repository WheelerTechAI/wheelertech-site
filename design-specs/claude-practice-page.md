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