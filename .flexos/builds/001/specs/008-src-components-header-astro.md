---
type: spec
subtype: build-spec
title: src/components/Header.astro
phase: 2
priority: 3
---

## Files to Create/Modify
*   `src/components/Header.astro` (Create)

## Implementation Details
Create the site's main header component based *exactly* on the pattern from `design/patterns.md` (Section 4.1 & 4.2). This includes the responsive desktop navigation, the mobile hamburger menu, and the client-side JavaScript for scroll behavior and mobile menu toggling.

```astro
---
// src/components/Header.astro
const navLinks = [
  { href: "/products/bind", label: "BIND 9" },
  { href: "/products/kea", label: "Kea" },
  { href: "/enterprise", label: "Enterprise" },
  { href: "/resources", label: "Resources" },
  { href: "/about", label: "About" },
  { href: "/blog", label: "Knowledge Hub" },
];
---
<header id="main-header" class="fixed top-0 left-0 w-full z-50 transition-all duration-300 ease-in-out text-surface-50">
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <div id="header-inner" class="flex justify-between items-center transition-all duration-300 ease-in-out py-6">
      <!-- Logo -->
      <a href="/" class="relative w-24 h-8 flex-shrink-0" aria-label="ISC Homepage">
        <!-- Replace with actual SVG content or <Image> component -->
        <div id="logo-light" class="absolute h-full w-auto transition-opacity duration-300 opacity-100">[LOGO LIGHT]</div>
        <div id="logo-dark" class="absolute h-full w-auto transition-opacity duration-300 opacity-0">[LOGO DARK]</div>
      </a>

      <!-- Desktop Navigation -->
      <nav class="hidden md:flex items-center space-x-6 lg:space-x-8 font-heading font-medium text-base">
        {navLinks.map(link => (
          <a href={link.href} class="header-link hover:text-accent-300 transition-colors duration-200 ease-in-out">{link.label}</a>
        ))}
        <a href="/contact" class="header-cta inline-block bg-accent-500 text-surface-50 py-2 px-5 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-md hover:shadow-lg">Contact</a>
      </nav>

      <!-- Mobile Menu Button (Hamburger) -->
      <button id="mobile-menu-trigger" class="md:hidden header-link" aria-label="Open menu">
        <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
      </button>
    </div>
  </div>
</header>

<!-- Mobile Navigation Overlay -->
<div id="mobile-menu" class="fixed inset-0 bg-primary-900 text-surface-50 z-[49] flex flex-col justify-center items-center transform -translate-x-full transition-transform duration-300 ease-in-out" aria-hidden="true">
  <button id="mobile-menu-close" class="absolute top-8 right-6 text-surface-50" aria-label="Close menu">
    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
  </button>
  <nav class="flex flex-col space-y-8 text-center font-heading font-medium text-3xl">
    {navLinks.map(link => (
      <a href={link.href} class="mobile-nav-link hover:text-accent-300 transition-colors duration-200 ease-in-out">{link.label}</a>
    ))}
    <a href="/contact" class="mobile-nav-link inline-block bg-accent-500 text-surface-50 py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg mt-4">Contact</a>
  </nav>
</div>


<script>
  // This script must not be hoisted to ensure elements exist.
  document.addEventListener('DOMContentLoaded', () => {
    // Header Scroll Behavior
    const header = document.getElementById('main-header');
    const headerInner = document.getElementById('header-inner');
    const links = header.querySelectorAll('.header-link');
    const cta = header.querySelector('.header-cta');
    const logoLight = document.getElementById('logo-light');
    const logoDark = document.getElementById('logo-dark');
    const scrollThreshold = 50;

    const updateHeader = () => {
      if (window.scrollY > scrollThreshold) {
        header.classList.add('bg-surface-50', 'shadow-md', 'text-primary-900');
        header.classList.remove('text-surface-50');
        headerInner.classList.remove('py-6');
        headerInner.classList.add('py-4');
        logoLight.classList.remove('opacity-100');
        logoLight.classList.add('opacity-0');
        logoDark.classList.remove('opacity-0');
        logoDark.classList.add('opacity-100');
      } else {
        header.classList.remove('bg-surface-50', 'shadow-md', 'text-primary-900');
        header.classList.add('text-surface-50');
        headerInner.classList.add('py-6');
        headerInner.classList.remove('py-4');
        logoLight.classList.add('opacity-100');
        logoLight.classList.remove('opacity-0');
        logoDark.add('opacity-0');
        logoDark.classList.remove('opacity-100');
      }
    };
    window.addEventListener('scroll', updateHeader);
    updateHeader(); // Initial check on load

    // Mobile Menu Toggle
    const mobileMenu = document.getElementById('mobile-menu');
    const trigger = document.getElementById('mobile-menu-trigger');
    const close = document.getElementById('mobile-menu-close');
    const navLinks = mobileMenu.querySelectorAll('a.mobile-nav-link');

    const openMenu = () => {
      mobileMenu.classList.remove('-translate-x-full');
      mobileMenu.setAttribute('aria-hidden', 'false');
      document.body.style.overflow = 'hidden';
    };
    const closeMenu = () => {
      mobileMenu.classList.add('-translate-x-full');
      mobileMenu.setAttribute('aria-hidden', 'true');
      document.body.style.overflow = '';
    };

    trigger.addEventListener('click', openMenu);
    close.addEventListener('click', closeMenu);
    navLinks.forEach(link => link.addEventListener('click', closeMenu));
  });
</script>
```

## Dependencies
*   None internally, but this component is used by `src/layouts/BaseLayout.astro`.

## Acceptance Criteria
*   The `src/components/Header.astro` file exists.
*   The header is transparent on page load and becomes solid with a background and shadow on scroll.
*   The logo and text colors change correctly on scroll to maintain contrast.
*   On mobile viewports, the hamburger menu is visible and toggles the full-screen navigation overlay.
*   Clicking a link in the mobile overlay closes the menu.

## Code Patterns
*   The navigation links are stored in an array and mapped over to prevent repetition.
*   Client-side logic is contained within a single `<script>` tag inside the component. `DOMContentLoaded` ensures the script runs after the DOM is ready.
*   CSS classes are used to manage states (e.g., `bg-surface-50`, `-translate-x-full`) which are toggled by the script.