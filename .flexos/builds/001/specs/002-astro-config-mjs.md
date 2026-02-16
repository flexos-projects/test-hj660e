---
type: spec
subtype: build-spec
title: astro.config.mjs
phase: 1
priority: 2
---

## Files to Create/Modify
*   `astro.config.mjs` (Create)

## Implementation Details
Create the `astro.config.mjs` file at the project root. This file configures the Astro project, enabling key integrations like Tailwind CSS, sitemap generation, and the Vercel deployment adapter.

```javascript
import { defineConfig } from 'astro/config';
import tailwind from "@astrojs/tailwind";
import sitemap from "@astrojs/sitemap";
import vercel from "@astrojs/vercel/serverless";

// https://astro.build/config
export default defineConfig({
  site: 'https://www.isc.org', // Replace with the actual production domain
  integrations: [
    tailwind({
      // Apply tailwind base styles to all pages
      applyBaseStyles: true,
    }), 
    sitemap()
  ],
  output: 'server',
  adapter: vercel({
    webAnalytics: {
      enabled: true, // Enable Vercel analytics as per spec
    },
    imageService: true // Enable Vercel's built-in image optimization service
  })
});
```

## Dependencies
*   `package.json` must exist with the required Astro integrations listed as dependencies.

## Acceptance Criteria
*   The `astro.config.mjs` file exists at the project root.
*   Running `astro dev` successfully starts the development server with Tailwind and Vercel configurations active.
*   Running `astro build` generates a `.vercel` output directory, and a `sitemap-index.xml` is created in the `dist/` folder.

## Code Patterns
The configuration follows the official Astro documentation.
*   `tailwind()` is included to enable Tailwind CSS utility classes.
*   `sitemap()` is included for automatic sitemap generation.
*   `vercel()` adapter is used with `output: 'server'` to enable server-side rendering on Vercel, which is useful for API endpoints and potential future dynamic features. Image service and web analytics are enabled as per `docs/core/007-technical.md`.