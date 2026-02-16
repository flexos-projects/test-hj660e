---
type: spec
subtype: build-spec
title: src/layouts/BaseLayout.astro
phase: 2
priority: 2
---

## Files to Create/Modify
*   `src/layouts/BaseLayout.astro` (Create)

## Implementation Details
Create the main layout file that will wrap every page. It includes the HTML document structure, imports global styles, preloads fonts, and uses the `SEO` component. It also defines slots for the header, main content, and footer.

```astro
---
// src/layouts/BaseLayout.astro
import SEO from '../components/SEO.astro';
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';

// Import global styles
import '../styles/global.css';

export interface Props {
  title: string;
  description: string;
}

const { title, description } = Astro.props;
---
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <SEO title={title} description={description} />
  
  <!-- Font Preloading for performance -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400..700;1,400..700&family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  
  <!-- Add privacy-focused analytics script here, e.g., Plausible -->
  <!-- <script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script> -->
</head>
<body class="bg-surface-50 font-body text-primary-800 antialiased">
  <Header />
  <main id="main-content">
    <slot /> <!-- Page content will be injected here -->
  </main>
  <Footer />

  <script>
    // Global client-side script for scroll animations
    document.addEventListener('DOMContentLoaded', () => {
      const animatedElements = document.querySelectorAll('.animate-on-scroll');
      if (animatedElements.length === 0) return;

      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('is-visible');
            observer.unobserve(entry.target);
          }
        });
      }, { threshold: 0.1 });

      animatedElements.forEach(el => observer.observe(el));
    });
  </script>
</body>
</html>
```

## Dependencies
*   `src/components/SEO.astro`
*   `src/components/Header.astro`
*   `src/components/Footer.astro`
*   `src/styles/global.css`

## Acceptance Criteria
*   The file `src/layouts/BaseLayout.astro` exists.
*   Pages using this layout render the header, their specific content, and the footer in the correct order.
*   The page's `<head>` contains the correct SEO tags and font links.
*   The global Intersection Observer script for animations is present.

## Code Patterns
*   The layout is a standard HTML5 document structure.
*   It accepts `title` and `description` props and passes them to the `SEO` component.
*   The client-side script for scroll animations is included here to be available on every page. This script targets the classes defined in `global.css`.