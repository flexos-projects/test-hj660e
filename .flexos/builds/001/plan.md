---
id: builds.001:plan
title: Build 001 Plan
description: Phased implementation plan for build 001
sequence: 1
status: active
type: build
subtype: plan
relatesTo:
  - builds.001:config
tags:
  - build
  - plan
createdAt: "2026-02-16T11:11:18.623Z"
updatedAt: "2026-02-16T11:11:18.623Z"
---
This build plan outlines the sequential creation of all necessary files for the ISC website, based on the project's FlexOS specifications. Each phase builds upon the last, ensuring a logical and dependency-aware workflow.

## Phase 1: Project Skeleton

This phase establishes the foundational configuration for the Astro project, including dependencies, integrations, and the design system's translation into code.

| File | Details |
| --- | --- |
| **Path** | `package.json` |
| **Purpose** | Defines project dependencies, scripts, and metadata. |
| **Depends on** | None |
| **Key context** | `builds/001/config.md`: Specifies Astro 5, Tailwind CSS, Algolia, and Astro Sitemap as key dependencies. `docs/core/007-technical.md`: Confirms the tech stack choices. |
| **Path** | `astro.config.mjs` |
| **Purpose** | Configures the Astro project, including integrations for Tailwind CSS, sitemap generation, and image optimization. |
| **Depends on** | `package.json` |
| **Key context** | `builds/001/config.md`: Lists integrations (`@astrojs/tailwind`, `@astrojs/sitemap`). `docs/core/007-technical.md`: Specifies static site generation and Vercel deployment adapter. |
| **Path** | `tailwind.config.mjs` |
| **Purpose** | Configures Tailwind CSS with the project's specific design tokens for colors, fonts, and spacing. |
| **Depends on** | `package.json` |
| **Key context** | `design/design-system.md`: The primary source for all color palettes (primary, surface, accent, semantic), typography (Poppins, Lora), and the full font size scale. |
| **Path** | `src/styles/global.css` |
| **Purpose** | Imports Google Fonts, applies base Tailwind directives, and defines custom animation classes for scroll-reveal effects. |
| **Depends on** | `tailwind.config.mjs` |
| **Key context** | `design/design-system.md`: Specifies the fonts to import (Poppins, Lora). `design/patterns.md`: Provides the CSS definitions for `.animate-fade-in-up` and other scroll-reveal utility classes. |
| **Path** | `public/favicon.svg` |
| **Purpose** | A simple, clean SVG favicon for the site. Placeholder can be generated. |
| **Depends on** | None |
| **Key context** | `docs/core/005-design.md`: The overall design direction of "Quiet Authority" should inform a simple, professional favicon design. |

## Phase 2: Shared Components & Layouts

This phase creates the reusable Astro components and layouts that form the structure and UI toolkit for all pages.

| File | Details |
| --- | --- |
| **Path** | `src/components/SEO.astro` |
| **Purpose** | A reusable component to manage all SEO-related meta tags, Open Graph, Twitter cards, and Schema.org structured data. |
| **Depends on** | None |
| **Key context** | `docs/core/007-technical.md`: Specifies the requirement for comprehensive structured data (Organization, SoftwareApplication, Article, Person). `docs/core/003-pages.md`: Provides per-page title and meta description patterns. |
| **Path** | `src/layouts/BaseLayout.astro` |
| **Purpose** | The main HTML shell for all pages, including `<head>`, font preloading, analytics scripts, and slots for content. |
| **Depends on** | `src/styles/global.css`, `src/components/SEO.astro` |
| **Key context** | `docs/core/007-technical.md`: Specifies analytics provider (Plausible/Fathom) and performance targets. `design/patterns.md`: References the page transition wrapper concept. |
| **Path** | `src/components/Header.astro` |
| **Purpose** | Renders the site's responsive navigation header, including the logo, navigation links, and mobile hamburger menu logic. |
| **Depends on** | `src/layouts/BaseLayout.astro` |
| **Key context** | `design/patterns.md` (Section 4.1): Provides the exact HTML structure, Tailwind classes, and JavaScript logic for the header's scroll behavior (transparent to solid) and mobile menu toggle. |
| **Path** | `src/components/Footer.astro` |
| **Purpose** | Renders the site-wide footer with navigation, social links, contact info, and legal text. |
| **Depends on** | `src/layouts/BaseLayout.astro` |
| **Key context** | `design/patterns.md` (Section 4.3): Provides the exact HTML structure and Tailwind classes for the multi-column footer layout. |
| **Path** | `src/components/Section.astro` |
| **Purpose** | A foundational wrapper component for consistent section padding and background colors, as defined in the patterns. |
| **Depends on** | None |
| **Key context** | `design/patterns.md` (Section 1): Defines the `Section Wrapper` pattern with variants for light, dark, and accent styles. |
| **Path** | `src/components/Hero.astro` |
| **Purpose** | A versatile component for creating page hero sections, supporting different layouts via props. |
| **Depends on** | `src/components/Section.astro` |
| **Key context** | `design/patterns.md` (Section 2): Provides detailed variants for "Impact Hero," "Split Hero," and "Minimal Hero" with HTML/Tailwind examples. |
| **Path** | `src/components/Card.astro` |
| **Purpose** | A generic, reusable card component for showcasing content like projects, services, or team members. |
| **Depends on** | None |
| **Key context** | `design/patterns.md` (Section 5): Defines the base card styles and provides variants for "Project Card," "Service Card," and "Team Member Card." |

## Phase 3: Content Collections & Core Pages (P1)

This phase defines the content structure and builds out the highest-priority pages for the MVP launch.

| File | Details |
| --- | --- |
| **Path** | `src/content/config.ts` |
| **Purpose** | Defines Astro Content Collection schemas for all dynamic content types (blog posts, team members, products, etc.). |
| **Depends on** | None |
| **Key context** | `docs/core/004-database.md`: This document provides the exact schemas to be defined, including fields for Product, Service, Team Member, and Resource. |
| **Path** | `src/pages/index.astro` |
| **Purpose** | The main homepage, implementing the crucial "Dual-Path" audience segmentation. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro`, `src/components/Hero.astro` |
| **Key context** | `specs/001-page_isc-the-trusted-foundation-of-.md`: The detailed page spec. `specs/050-feature_dual-path-homepage.md`: The spec for the core audience selector component. |
| **Path** | `src/pages/products/bind.astro` |
| **Purpose** | The product showcase page for BIND 9. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro` |
| **Key context** | `specs/002-page_bind-9-the-world-s-most-truste.md`: The detailed page spec. `specs/051-feature_product-showcase-pages.md`: The feature spec for product pages. |
| **Path** | `src/pages/products/kea.astro` |
| **Purpose** | The product showcase page for Kea DHCP. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro` |
| **Key context** | `specs/003-page_kea-a-modern-high-performance-.md`: The detailed page spec. `specs/051-feature_product-showcase-pages.md`: The feature spec for product pages. |
| **Path** | `src/pages/enterprise/index.astro` |
| **Purpose** | The main landing page (gateway) for all enterprise services. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro` |
| **Key context** | `specs/004-page_enterprise-services-for-missio.md`: The detailed page spec. `specs/053-feature_enterprise-services-section.md`: The feature spec for this section. |
| **Path** | `src/pages/resources/index.astro` |
| **Purpose** | The community gateway page, featuring the powerful Algolia-powered search bar. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro` |
| **Key context** | `specs/006-page_technical-resources-for-bind-9.md`: The detailed page spec. `specs/052-feature_world-class-resource-library.md`: The feature spec describing the search functionality. |
| **Path** | `src/pages/about/index.astro` |
| **Purpose** | The main "About Us" page, telling the "Unsung Architects" story. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro` |
| **Key context** | `specs/007-page_about-isc-stewards-of-internet.md`: The detailed page spec. `specs/058-feature_compelling-about-us-page.md`: The feature spec. |
| **Path** | `src/pages/blog/index.astro` |
| **Purpose** | The main archive page for the ISC Knowledge Hub, listing all articles. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/content/config.ts` |
| **Key context** | `specs/009-page_the-isc-knowledge-hub-insights.md`: The detailed page spec. `specs/059-feature_isc-knowledge-hub-blog.md`: The feature spec. |
| **Path** | `src/pages/blog/[...slug].astro` |
| **Purpose** | The dynamic page template for rendering individual blog post articles. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/content/config.ts` |
| **Key context** | `specs/059-feature_isc-knowledge-hub-blog.md`: Implies the need for a detail view. `docs/core/007-technical.md`: Specifies server-side code highlighting with Shiki/Prism. |
| **Path** | `src/pages/contact.astro` |
| **Purpose** | The contact page with segmented contact options and a general inquiry form. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/components/Header.astro`, `src/components/Footer.astro` |
| **Key context** | `specs/010-page_contact-the-internet-systems-c.md`: The detailed page spec. |

## Phase 4: Integrations & Fast-Follow Pages (P2)

This phase implements server-side logic and builds the P2 pages.

| File | Details |
| --- | --- |
| **Path** | `src/pages/api/contact.ts` |
| **Purpose** | A Vercel serverless function to handle submissions from the contact and quote request forms. |
| **Depends on** | `src/pages/contact.astro` |
| **Key context** | `docs/core/007-technical.md`: Specifies using a Vercel function for form handling and spam prevention (honeypot, reCAPTCHA). |
| **Path** | `src/pages/enterprise/support.astro` |
| **Purpose** | The detailed page for enterprise support offerings and tier comparisons. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/pages/api/contact.ts` |
| **Key context** | `specs/005-page_24-7-bind-kea-support-isc-ente.md`: The detailed page spec, including the tier comparison table and quote request form. |
| **Path** | `src/pages/about/experts.astro` |
| **Purpose** | The "Our Experts" team page showcasing ISC talent. |
| **Depends on** | `src/layouts/BaseLayout.astro`, `src/content/config.ts` |
| **Key context** | `specs/008-page_our-experts-the-isc-team.md`: The detailed page spec. `specs/056-feature_our-experts-team-page.md`: The feature spec. |
| **Path** | `src/components/CookieConsent.astro` |
| **Purpose** | An Astro island component to manage cookie consent for GDPR compliance before loading analytics. |
| **Depends on** | `src/layouts/BaseLayout.astro` |
| **Key context** | `builds/001/config.md`: Identifies cookie consent as a required integration. |

## Phase 5: Final Polish

This phase adds final configurations and ensures the site is ready for deployment.

| File | Details |
| --- | --- |
| **Path** | `public/robots.txt` |
| **Purpose** | Instructs web crawlers which pages to index and points to the sitemap. |
| **Depends on** | All pages defined. |
| **Key context** | `docs/core/007-technical.md`: Specifies the need for a `robots.txt` file. |
| **Path** | (Generated by build) |
| **Purpose** | The sitemap is auto-generated by the `@astrojs/sitemap` integration at build time. No manual file creation needed. |
| **Depends on** | `astro.config.mjs`, all pages created. |
| **Key context** | `docs/core/007-technical.md`: Specifies auto-generation of `sitemap.xml`. |