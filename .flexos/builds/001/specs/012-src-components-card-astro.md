---
type: spec
subtype: build-spec
title: src/components/Card.astro
phase: 2
priority: 7
---

## Files to Create/Modify
*   `src/components/Card.astro` (Create)

## Implementation Details
Create a generic `Card` component for displaying content snippets. This component will have a base style and support variants for different use cases like projects and services, as detailed in `design/patterns.md` (Section 5).

```astro
---
// src/components/Card.astro
import { Image } from 'astro:assets';

export interface Props {
  href: string;
  title: string;
  text: string;
  imageUrl?: ImageMetadata;
  imageAlt?: string;
  variant?: 'project' | 'service'; // Add more variants as needed
}

const { href, title, text, imageUrl, imageAlt = "Card image", variant = 'project' } = Astro.props;
---
{variant === 'project' && (
  <a href={href} class="block bg-surface-50 rounded-lg shadow-md overflow-hidden transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1 group">
    {imageUrl && (
      <div class="relative w-full aspect-[4/3] overflow-hidden">
        <Image src={imageUrl} alt={imageAlt} class="w-full h-full object-cover group-hover:scale-[1.03] transition-transform duration-300 ease-in-out" />
      </div>
    )}
    <div class="p-6">
      <h3 class="font-heading font-semibold text-xl text-primary-900 mb-2 group-hover:text-accent-500 transition-colors duration-200">{title}</h3>
      <p class="font-body text-base text-primary-700">{text}</p>
    </div>
  </a>
)}

{variant === 'service' && (
  <div class="bg-surface-50 rounded-lg shadow-md p-6 text-center transition duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1 group h-full flex flex-col">
    <div class="flex-grow">
        <div class="inline-block p-4 rounded-lg bg-primary-100 text-primary-700 mb-6 group-hover:bg-accent-100 group-hover:text-accent-700 transition-all duration-200">
            <slot name="icon" />
        </div>
        <h3 class="font-heading font-semibold text-xl text-primary-900 mb-3 group-hover:text-accent-500 transition-colors duration-200">{title}</h3>
        <p class="font-body text-base text-primary-700">{text}</p>
    </div>
    <a href={href} class="text-accent-500 font-medium mt-4 inline-block group-hover:underline transition-colors duration-200">Learn More &rarr;</a>
  </div>
)}
```

## Dependencies
*   Astro's built-in `Image` component (`astro:assets`).

## Acceptance Criteria
*   The `src/components/Card.astro` file exists.
*   The component renders a clickable card with the specified hover lift effect.
*   The `project` variant displays an image at the top with text content below.
*   The `service` variant displays a centered icon (passed via a slot) with text and a "Learn More" link.

## Code Patterns
*   The entire card is wrapped in an `<a>` tag for the `project` variant, making the whole unit clickable.
*   A named slot `<slot name="icon" />` is used for the `service` variant, allowing developers to pass in any SVG icon when using the component. Example usage: `<Card variant="service" ...><svg slot="icon">...</svg></Card>`.
*   The `group` and `group-hover` utilities from Tailwind are used to coordinate hover effects across child elements (e.g., image scales and title color changes when hovering over the parent card).