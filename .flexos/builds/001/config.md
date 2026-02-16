---
id: builds.001:config
title: Build 001 Configuration
description: Tech stack, scope, and constraints for build 001
sequence: 0
status: active
type: build
subtype: config
relatesTo:
  - docs:core:007-technical
tags:
  - build
  - config
createdAt: "2024-07-30T12:00:00.000Z"
updatedAt: "2024-07-30T12:00:00.000Z"
---

## Stack (Fixed)
- **Framework**: Astro 5 (static site generation, content collections)
- **Styling**: Tailwind CSS 4
- **Deployment**: Vercel (static hosting, global CDN)
- **Images**: Astro Image / Sharp (for automatic optimization and responsive images)
- **SEO**: @astrojs/sitemap + custom meta components (`astro-seo` utility mentioned in `docs/core/007-technical.md`)
- **Search**: Algolia (for "World-Class Resource Library" and "Advanced Search Analytics")
- **Code Highlighting**: Shiki or Prism (server-side syntax highlighting, from `docs/core/007-technical.md`)

## Integrations Needed
Based on the project specs, identify what extras this site needs:
- [x] Contact form handling (Vercel serverless function or external like Formspree, as per `docs/core/007-technical.md` and `specs/010-page_contact-the-internet-systems-c.md`)
- [ ] Google Maps / OpenStreetMap embed
- [x] Newsletter signup (implicitly covered by general form handling for footer form in `design/patterns.md`)
- [ ] Calendar/booking (Future P3 feature, not for build 001)
- [ ] E-commerce
- [x] Client portal / login area (for "Documentation Personalization", requires authentication in `specs/065-feature_documentation-personalization.md`)
- [x] Blog with RSS feed (ISC Knowledge Hub in `specs/059-feature_isc-knowledge-hub-blog.md`)
- [ ] Multilingual (i18n routing — de/en) (Not explicitly defined for this project's scope)
- [x] Analytics (Plausible or Fathom, from `docs/core/007-technical.md`)
- [x] Cookie consent (GDPR required in EU/DACH, good practice for a global org like ISC)
- [x] Schema.org structured data (Organization, SoftwareApplication, Article, Person, from `docs/core/007-technical.md`)

## Pages to Build
List every page from the sitemap with its Astro file path (src/pages/...).
Mark build priority: P1 (MVP launch), P2 (week 1 post-launch), P3 (future).

- `/` (Homepage) - P1: `src/pages/index.astro`
- `/products/bind/` (Products > BIND 9) - P1: `src/pages/products/bind.astro`
- `/products/kea/` (Products > Kea DHCP) - P1: `src/pages/products/kea.astro`
- `/enterprise/` (Services > Enterprise Gateway) - P1: `src/pages/enterprise/index.astro`
- `/enterprise/support/` (Services > Enterprise Support) - P2: `src/pages/enterprise/support.astro`
- `/resources/` (Resources > Community Gateway) - P1: `src/pages/resources/index.astro`
- `/about/` (About Us) - P1: `src/pages/about/index.astro`
- `/about/experts/` (About Us > Our Experts) - P2: `src/pages/about/experts.astro`
- `/blog/` (Knowledge Hub) - P1: `src/pages/blog/index.astro`
- `/contact/` (Contact) - P1: `src/pages/contact.astro`

## Performance Targets
- Lighthouse: 90+ across all categories (`docs/core/007-technical.md` targets 98+)
- Core Web Vitals: LCP < 2.5s, CLS < 0.1, INP < 200ms (`docs/core/007-technical.md` mentions TTI < 2s)
- Total page weight: < 500KB per page (excluding images)
- No layout shift from font loading (use font-display: swap + preload)

## Content Requirements
What content is READY (from research/imports) vs. what needs to be WRITTEN?

**Ready Content:**
- Core narrative: "Unsung Architects of the Internet" (`docs/core/001-vision.md`)
- Basic product descriptions for BIND 9 and Kea.
- High-level mission statement.
- Existing general team member names and roles (placeholder bios in `prototype/shared/mock-data.js`).
- Basic sitemap structure.
- Content about ISC's history (to be refined for timeline).

**Needs to be Written / Sourced:**
- Quantified Impact Metrics: Specific stats (e.g., "% of world's DNS lookups", "million active installations") for "Our Impact" showcase (`docs/core/000-import.md`, `specs/055-feature_our-impact-showcase.md`).
- High-Quality Visuals: Professional headshots for "Our Experts" page, brand photography, abstract graphics (`docs/core/000-import.md`, `imports/image-analysis.md`).
- Enterprise Testimonials & Case Studies: Approved quotes, logos, detailed success stories (`docs/core/000-import.md`, `specs/060-feature_case-studies-testimonials.md`).
- Pricing Details: Specifics on support contract tiers and pricing for enterprise services (`docs/core/000-import.md`).
- Detailed Team Member Bios: Comprehensive biographies and credentials (`specs/056-feature_our-experts-team-page.md`).
- Knowledge Hub Articles: Content for the blog (`specs/059-feature_isc-knowledge-hub-blog.md`).

## Build Constraints
- No JavaScript frameworks (no React, Vue, Svelte, etc.) for UI components – Astro components only, leveraging Astro Islands for client-side interactivity where absolutely necessary (`docs/core/007-technical.md` implies minimal JS, prompt explicitly states "no React, Vue").
- CSS via Tailwind utility classes – no custom CSS files except global tokens (`design/design-system.md` uses Tailwind, `design/patterns.md` details Tailwind classes).
- All images optimized via Astro Image (`docs/core/007-technical.md`).
- Semantic HTML throughout (proper heading hierarchy, landmarks, ARIA where needed, from `design/design-system.md` and `specs` general accessibility).
- Mobile-first approach for all layouts and components (`design/design-system.md`, `docs/core/005-design.md`, `specs/057-feature_modern-responsive-design.md`).