---
type: spec
subtype: build-spec
title: src/components/Footer.astro
phase: 2
priority: 4
---

## Files to Create/Modify
*   `src/components/Footer.astro` (Create)

## Implementation Details
Create the site-wide footer component, following the structure and styling from `design/patterns.md` (Section 4.3). It will have a multi-column responsive layout containing the logo, tagline, social links, navigation links, and contact info.

```astro
---
// src/components/Footer.astro
const quickLinks = [
  { href: "/products/bind", label: "BIND 9" },
  { href: "/products/kea", label: "Kea" },
  { href: "/enterprise", label: "Enterprise Services" },
  { href: "/blog", label: "Knowledge Hub" },
];

const aboutLinks = [
  { href: "/about", label: "About ISC" },
  { href: "/about/experts", label: "Our Experts" },
  { href: "/resources", label: "Resources" },
  { href: "/contact", label: "Contact Us" },
];
---
<footer class="bg-primary-900 text-surface-300 py-16 md:py-20 font-body">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <div class="grid grid-cols-1 md:grid-cols-12 gap-12 mb-12">

      <!-- Column 1: Logo & Tagline -->
      <div class="md:col-span-12 lg:col-span-5">
        <a href="/" class="inline-block mb-6" aria-label="ISC Homepage">
          <!-- Replace with actual light logo SVG -->
          <div class="h-10 text-surface-50">[LOGO LIGHT]</div>
        </a>
        <p class="text-surface-400 text-lg max-w-sm">
          The trusted, modern stewards of the internet's core infrastructure.
        </p>
        <div class="flex space-x-4 mt-6">
          <!-- Replace # with actual social links -->
          <a href="#" aria-label="LinkedIn" class="text-surface-400 hover:text-accent-400 transition-colors duration-200"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">...</svg></a>
          <a href="#" aria-label="Twitter" class="text-surface-400 hover:text-accent-400 transition-colors duration-200"><svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">...</svg></a>
        </div>
      </div>

      <!-- Column 2: Quick Links -->
      <div class="md:col-span-6 lg:col-span-2">
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-6">Products</h4>
        <ul class="space-y-3">
          {quickLinks.slice(0, 2).map(link => <li><a href={link.href} class="hover:text-accent-400 transition-colors duration-200">{link.label}</a></li>)}
        </ul>
      </div>

      <!-- Column 3: Resources -->
      <div class="md:col-span-6 lg:col-span-2">
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-6">Company</h4>
        <ul class="space-y-3">
          {aboutLinks.map(link => <li><a href={link.href} class="hover:text-accent-400 transition-colors duration-200">{link.label}</a></li>)}
        </ul>
      </div>

      <!-- Column 4: Contact -->
      <div class="md:col-span-12 lg:col-span-3">
        <h4 class="font-heading font-semibold text-xl text-surface-50 mb-6">Connect</h4>
        <p class="mb-4">
          <a href="mailto:info@isc.org" class="hover:text-accent-400 transition-colors duration-200">info@isc.org</a>
        </p>
        <p class="mb-6">
          For sales inquiries, please visit our <a href="/contact" class="underline hover:text-accent-400">contact page</a>.
        </p>
      </div>

    </div>

    <div class="border-t border-primary-700 pt-8 text-center text-sm text-surface-400">
      <p>&copy; {new Date().getFullYear()} Internet Systems Consortium. All rights reserved. | <a href="/privacy" class="hover:text-accent-400 transition-colors duration-200">Privacy Policy</a></p>
    </div>
  </div>
</footer>
```

## Dependencies
*   None internally, but this component is used by `src/layouts/BaseLayout.astro`.

## Acceptance Criteria
*   The `src/components/Footer.astro` file exists.
*   The footer renders correctly at the bottom of each page.
*   The layout stacks to a single column on mobile and expands to the multi-column layout on larger screens.
*   Links have the specified hover effect.

## Code Patterns
*   Uses Tailwind's responsive grid system (`grid`, `md:grid-cols-12`, `lg:col-span-X`) for the layout.
*   Navigation links are stored in arrays and rendered with `.map()` to keep the template DRY.
*   The copyright year is generated dynamically with `{new Date().getFullYear()}`.