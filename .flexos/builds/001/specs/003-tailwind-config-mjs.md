---
type: spec
subtype: build-spec
title: tailwind.config.mjs
phase: 1
priority: 3
---

## Files to Create/Modify
*   `tailwind.config.mjs` (Create)

## Implementation Details
Create `tailwind.config.mjs` at the project root. This file translates the visual identity from `design/design-system.md` into Tailwind CSS configuration. It defines the custom color palette, font families, and typography scale.

```javascript
import defaultTheme from 'tailwindcss/defaultTheme';

/** @type {import('tailwindcss').Config} */
export default {
  content: ['./src/**/*.{astro,html,js,jsx,md,mdx,svelte,ts,tsx,vue}'],
  theme: {
    extend: {
      colors: {
        primary: { // Slate Blue
          50: '#F0F4F6',
          100: '#DDE6EA',
          200: '#BCCDD4',
          300: '#9BB3BF',
          400: '#7A9AAD',
          500: '#4A6572',
          600: '#3F5661',
          700: '#354851',
          800: '#2A3A42',
          900: '#1E2B33',
        },
        surface: { // Bone White/Sand
          50: '#F8F6F2',
          100: '#F1EDE5',
          200: '#E9E2D7',
          300: '#E0D8CA',
          400: '#D0C4B4',
          500: '#C0B19D',
          600: '#AE9D88',
          700: '#90816F',
          800: '#726556',
          900: '#544A3D',
        },
        accent: { // Muted Terracotta
          50: '#FDF6F3',
          100: '#FAE9E1',
          200: '#F2D3C4',
          300: '#E9BDA7',
          400: '#E0A789',
          500: '#B85C38',
          600: '#A95432',
          700: '#8F472A',
          800: '#753A22',
          900: '#5C2D1A',
        },
        // Semantic colors from design system
        success: '#28A745',
        warning: '#FFC107',
        error: '#DC3545',
      },
      fontFamily: {
        heading: ['Poppins', ...defaultTheme.fontFamily.sans],
        body: ['Lora', ...defaultTheme.fontFamily.serif],
      },
    },
    // Override the default font size scale entirely as per design system
    fontSize: {
      'xs': ['0.75rem', { lineHeight: '1rem' }],      // 12px
      'sm': ['0.875rem', { lineHeight: '1.25rem' }],   // 14px
      'base': ['1rem', { lineHeight: '1.75rem' }],     // 16px
      'lg': ['1.125rem', { lineHeight: '1.75rem' }],   // 18px
      'xl': ['1.25rem', { lineHeight: '1.75rem' }],   // 20px
      '2xl': ['1.5rem', { lineHeight: '2rem' }],      // 24px
      '3xl': ['1.875rem', { lineHeight: '2.25rem' }],  // 30px
      '4xl': ['2.25rem', { lineHeight: '2.5rem' }],   // 36px
      '5xl': ['3rem', { lineHeight: '1.2' }],         // 48px
      '6xl': ['3.75rem', { lineHeight: '1.2' }],        // 60px
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
  ],
}
```

## Dependencies
*   `package.json` with `tailwindcss` and `@tailwindcss/typography` installed.
*   `astro.config.mjs` with the Tailwind integration enabled.

## Acceptance Criteria
*   The `tailwind.config.mjs` file exists.
*   Astro components using classes like `bg-primary-500` or `font-heading` render with the correct styles defined in this file.
*   The font sizes (`text-xs` to `text-6xl`) match the scale specified in `design/design-system.md`.

## Code Patterns
*   The `extend` key is used for `colors` and `fontFamily` to add new values while keeping Tailwind's defaults.
*   The `fontSize` scale is placed outside `extend` to completely replace the default scale, as mandated by the design system.
*   The `@tailwindcss/typography` plugin is included to style markdown content rendered from content collections.