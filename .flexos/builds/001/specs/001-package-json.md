---
type: spec
subtype: build-spec
title: package.json
phase: 1
priority: 1
---

## Files to Create/Modify
*   `package.json` (Create)

## Implementation Details
Create the `package.json` file at the project root. This file defines the project's scripts and dependencies based on the technical specifications. The core framework is Astro, with Tailwind for styling and other specified libraries for functionality.

```json
{
  "name": "isc-website",
  "type": "module",
  "version": "0.1.0",
  "scripts": {
    "dev": "astro dev",
    "start": "astro dev",
    "build": "astro build",
    "preview": "astro preview",
    "astro": "astro"
  },
  "dependencies": {
    "@astrojs/sitemap": "^3.1.5",
    "@astrojs/tailwind": "^5.1.0",
    "@astrojs/vercel": "^7.7.1",
    "astro": "^4.9.2",
    "tailwindcss": "^3.4.3"
  },
  "devDependencies": {
    "@tailwindcss/typography": "^0.5.13"
  }
}
```

## Dependencies
None. This is the first file.

## Acceptance Criteria
*   The `package.json` file exists at the project root.
*   Running `npm install` (or `pnpm install`, `yarn`) successfully installs all listed dependencies.
*   The `dev`, `build`, and `preview` scripts are defined correctly.

## Code Patterns
Use standard JSON format. The dependencies are chosen based on `docs/core/007-technical.md` which specifies Astro, Tailwind CSS, Vercel deployment, and sitemap generation. `@tailwindcss/typography` is added to beautifully style markdown content from Astro's content collections.