---
type: spec
subtype: build-spec
title: public/favicon.svg
phase: 1
priority: 5
---

## Files to Create/Modify
*   `public/favicon.svg` (Create)

## Implementation Details
Create a simple, clean, and professional SVG favicon that reflects the "Quiet Authority" design direction. The favicon will be a monogram "ISC" set in a geometric sans-serif font, enclosed in a rounded square. The color should be the primary brand color to ensure it works well on both light and dark browser tabs.

```xml
<svg width="100" height="100" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
  <rect width="100" height="100" rx="20" fill="#354851"/>
  <text fill="white" x="50" y="62" font-family="Poppins, sans-serif" font-size="42" font-weight="600" text-anchor="middle">ISC</text>
</svg>
```
*Note: The color `#354851` is `primary-700` from the design system, a strong, professional color suitable for a favicon.*

## Dependencies
None.

## Acceptance Criteria
*   The file `public/favicon.svg` exists.
*   When the site is run locally, the SVG icon appears correctly in the browser tab.
*   The SVG is valid and renders without errors.

## Code Patterns
*   A simple, text-based SVG is used for maximum clarity, small file size, and scalability.
*   The font `Poppins` is referenced, which aligns with the heading font from the design system.
*   The color is hardcoded to a specific token value (`primary-700`) for consistency.