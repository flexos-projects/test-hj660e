---
type: doc
subtype: core
title: Technical Architecture & SEO Implementation
---

### 1. Core Stack

*   **Framework:** **Astro**. Chosen for its exceptional performance through a zero-JavaScript-by-default, static-first architecture. Its content-centric features (MD/MDX collections) are a perfect fit for a documentation-heavy site.
*   **Deployment:** **Vercel**. Provides a seamless Git-based workflow, global CDN for fast delivery, and serverless functions for backend tasks like form handling.
*   **Content Management:** **Git-based with Markdown**. Content will live directly in the Git repository as Markdown files. This workflow is ideal for ISC's technical team. For future content contributors, a Git-based CMS like **Decap CMS** can be layered on top to provide a friendlier editing UI.

### 2. Performance Targets

Performance is a reflection of technical excellence. The site must be blazingly fast.
*   **Core Web Vitals:** All metrics must score 'Good' in Google Search Console.
*   **Lighthouse Score:** Target 98+ for Performance, Accessibility, Best Practices, and SEO.
*   **Time to Interactive (TTI):** Under 2 seconds on a standard mobile connection.
*   **Image Optimization:** The Astro `<Image />` component will be used universally to automatically generate optimized, responsive `srcset` images in modern formats (WebP/AVIF). All images will be lazy-loaded by default.

### 3. SEO Technical Requirements

*   **Sitemaps:** A `sitemap.xml` file will be auto-generated at build time, including all static pages, product pages, and resource articles.
*   **Structured Data:** JSON-LD schema will be implemented across the site to provide rich context to search engines.
    *   `Organization`: On all pages, detailing ISC's non-profit status.
    *   `SoftwareApplication`: On Product pages for BIND and Kea.
    *   `Article` / `TechArticle`: On all Knowledge Hub and Documentation pages.
    *   `Person`: On the "Our Experts" pages.
*   **Meta Tags & Open Graph:** The `astro-seo` component or a similar utility will be used to manage canonical URLs, title tags, meta descriptions, and Open Graph/Twitter Card tags for rich social sharing.
*   **Robots.txt:** A `robots.txt` file will be configured to allow crawling of all public assets and point to the sitemap.

### 4. Form Handling

*   **Implementation:** All forms (Contact, Request a Quote) will submit to a Vercel Serverless Function.
*   **Spam Prevention:** A combination of a honeypot field (hidden from users, visible to bots) and Google reCAPTCHA v3 (invisible) will be used to prevent spam.
*   **Data Routing:** The serverless function will validate the data and then forward it to the appropriate ISC internal system (e.g., a sales CRM or ticketing system) via a secure API call. No sensitive data will be stored on the web server.

### 5. Analytics & Tracking

*   **Primary Analytics:** We will use a privacy-focused analytics provider like **Plausible** or **Fathom**. This respects user privacy—a value aligned with ISC's open-source ethos—while providing the necessary traffic insights.
*   **Performance Monitoring:** **Vercel Analytics** will be enabled to monitor Core Web Vitals and real-user performance data.
*   **Event Tracking:** Custom events will be tracked for key conversions, such as "request_quote_submit" and "download_software_click", to measure the site's effectiveness against its goals.

### 6. Search

The Resource Library search is mission-critical.
*   **Service:** We will integrate **Algolia**. Its speed, typo-tolerance, and advanced filtering capabilities provide the "world-class" experience required for the technical audience.
*   **Implementation:** At build time, all documentation and knowledge base content will be indexed in Algolia. The front end will use the Algolia client-side library to provide an instantaneous search experience.

### 7. Third-Party Integrations

*   **Mailing Lists:** The "Community" section will link directly to ISC's existing Mailman archives and subscription pages.
*   **Code Highlighting:** A library like **Shiki** or **Prism** will be used within Astro for fast, accurate, server-side syntax highlighting of code blocks.