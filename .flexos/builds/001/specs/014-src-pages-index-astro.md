---
type: spec
subtype: build-spec
title: src/pages/index.astro
phase: 3
priority: 2
---

## Files to Create/Modify
*   `src/pages/index.astro` (Create)

## Implementation Details
Create the homepage. This page uses the `BaseLayout` and several components to build the layout defined in `specs/001-page_isc-the-trusted-foundation-of-.md`. It features the "Impact Hero" and the critical "Dual-Path" audience selector.

```astro
---
// src/pages/index.astro
import BaseLayout from '../layouts/BaseLayout.astro';
import Hero from '../components/Hero.astro';
import Section from '../components/Section.astro';
import Card from '../components/Card.astro';
import { getCollection } from 'astro:content';

const latestPosts = await getCollection('blog', ({ data }) => {
  return !data.draft; // Assuming a draft frontmatter property
}).then(posts => posts.sort((a, b) => b.data.publishDate.valueOf() - a.data.publishDate.valueOf()).slice(0, 3));
---
<BaseLayout 
  title="The Trusted Foundation of the Internet"
  description="The Internet Systems Consortium (ISC) develops and supports the world's most critical open-source internet software, including BIND 9 and Kea DHCP."
>
  
  <Hero 
    variant="impact"
    title="The trusted, modern stewards of the internet's core infrastructure."
    subtitle="For over 30 years, ISC has developed and maintained the foundational software that makes the internet work. We are a non-profit organization dedicated to a stable, resilient, and open internet for all."
    imageUrl={import('../assets/images/hero-network.jpg')} // Placeholder
    imageAlt="Abstract network graphic"
  />

  <!-- Dual-Path Audience Selector -->
  <Section variant="light-alt">
    <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
      <div class="bg-surface-50 p-8 rounded-lg shadow-md text-center flex flex-col items-center">
        <h2 class="font-heading font-semibold text-3xl text-primary-900 mb-4">For the Community</h2>
        <p class="text-primary-700 mb-6 flex-grow">Access open-source software, comprehensive documentation, mailing lists, and technical resources.</p>
        <a href="/resources" class="inline-block bg-primary-700 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-primary-800 transition">Explore Resources</a>
      </div>
      <div class="bg-primary-800 p-8 rounded-lg shadow-md text-center flex flex-col items-center text-surface-50">
        <h2 class="font-heading font-semibold text-3xl mb-4">For the Enterprise</h2>
        <p class="text-surface-300 mb-6 flex-grow">Secure your mission-critical infrastructure with professional support, training, and consulting from the source.</p>
        <a href="/enterprise" class="inline-block bg-accent-500 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-accent-600 transition">Explore Services</a>
      </div>
    </div>
  </Section>

  <!-- Featured Products -->
  <Section variant="light">
    <div class="text-center">
      <h2 class="font-heading font-semibold text-4xl text-primary-900 mb-4">Core Technologies</h2>
      <p class="text-lg text-primary-700 max-w-3xl mx-auto mb-12">The industry standards for DNS and DHCP, built and maintained by ISC.</p>
    </div>
    <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
      <!-- BIND Card -->
      <Card
        href="/products/bind"
        title="BIND 9"
        text="The world's most trusted and widely deployed Domain Name System (DNS) software."
        imageUrl={import('../assets/images/bind-card.jpg')}
        variant="project"
      />
      <!-- Kea Card -->
      <Card
        href="/products/kea"
        title="Kea DHCP"
        text="A modern, high-performance, and extensible open-source DHCP server."
        imageUrl={import('../assets/images/kea-card.jpg')}
        variant="project"
      />
    </div>
  </Section>
  
  <!-- Knowledge Hub -->
  <Section variant="dark">
      <div class="text-center">
        <h2 class="font-heading font-semibold text-4xl text-surface-50 mb-4">From the Knowledge Hub</h2>
        <p class="text-lg text-surface-300 max-w-3xl mx-auto mb-12">Latest insights, tutorials, and announcements from our experts.</p>
      </div>
      <div class="grid md:grid-cols-3 gap-8">
        {latestPosts.map(post => (
          <a href={`/blog/${post.slug}/`} class="block bg-primary-800 p-6 rounded-lg hover:bg-primary-700 transition-colors">
            <p class="font-mono text-sm text-accent-400 mb-2">{post.data.tags[0]}</p>
            <h3 class="font-heading font-semibold text-xl text-surface-50 mb-3">{post.data.title}</h3>
            <p class="text-surface-300">{post.data.excerpt}</p>
          </a>
        ))}
      </div>
  </Section>

</BaseLayout>
```

## Dependencies
*   `src/layouts/BaseLayout.astro`
*   All required components (`Hero`, `Section`, `Card`).
*   Content collections must be set up in `src/content/config.ts` and have some initial content.
*   Placeholder images must exist at `src/assets/images/`.

## Acceptance Criteria
*   The homepage renders at the root URL (`/`).
*   The "For the Community" and "For the Enterprise" buttons are prominent and link to `/resources` and `/enterprise` respectively.
*   The "Featured Products" and "Knowledge Hub" sections are displayed correctly.
*   The page is fully responsive.

## Code Patterns
*   The page is built by composing the `Section`, `Hero`, and `Card` components.
*   `getCollection('blog')` is used at the top of the file to fetch the three latest blog posts to display in the "Knowledge Hub" section. This demonstrates Astro's data-fetching capabilities at build time.