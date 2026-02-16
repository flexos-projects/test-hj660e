---
type: spec
subtype: build-spec
title: src/styles/global.css
phase: 1
priority: 4
---

## Files to Create/Modify
*   `src/styles/global.css` (Create)

## Implementation Details
Create the file `src/styles/global.css`. This file is the entry point for global styles. It imports the required Google Fonts, sets up the base Tailwind CSS layers, and defines the custom animation classes for scroll-reveal effects as specified in the design patterns.

```css
/*
 * 1. Import Google Fonts as specified in design/design-system.md
 */
@import url('https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400..700;1,400..700&family=Poppins:wght@300;400;500;600;700&display=swap');

/*
 * 2. Include Tailwind's base, components, and utilities layers.
 */
@tailwind base;
@tailwind components;
@tailwind utilities;

/*
 * 3. Define base styles and custom utility classes.
 */
@layer base {
  html {
    @apply scroll-smooth;
  }
  body {
    @apply bg-surface-50 font-body text-primary-800 antialiased;
  }
}

/* 
 * 4. Custom Scroll-Reveal Animation Classes from design/patterns.md
 *    These classes are added by a script when an element becomes visible.
 */
.animate-on-scroll {
  opacity: 0;
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
  transition-delay: var(--animation-delay, 0s);
}

.fade-in-up {
  transform: translateY(1.5rem);
}
.fade-in-left {
  transform: translateX(-1.5rem);
}
.fade-in-right {
  transform: translateX(1.5rem);
}

.is-visible {
  opacity: 1;
  transform: translateY(0) translateX(0);
}
```

## Dependencies
*   `tailwind.config.mjs` must be configured.
*   This file will be imported by `src/layouts/BaseLayout.astro`.

## Acceptance Criteria
*   The file `src/styles/global.css` exists.
*   The Poppins and Lora fonts are correctly loaded from Google Fonts.
*   Tailwind's base styles are applied to the site.
*   Elements with the class `.animate-on-scroll` are initially hidden and have a transform applied. Adding the `.is-visible` class transitions them smoothly into view.

## Code Patterns
*   Use `@import` for fonts at the very top.
*   Use `@layer base` to add custom default styles to the HTML and body, ensuring they can be overridden by utility classes.
*   The animation classes are defined exactly as in `design/patterns.md`, ready to be used by a client-side Intersection Observer script.