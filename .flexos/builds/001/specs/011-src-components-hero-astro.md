---
type: spec
subtype: build-spec
title: src/components/Hero.astro
phase: 2
priority: 6
---

## Files to Create/Modify
*   `src/components/Hero.astro` (Create)

## Implementation Details
Create a versatile `Hero` component that can render the different hero variations defined in `design/patterns.md` (Section 2). The component will use props to control the variant, content, and imagery.

```astro
---
// src/components/Hero.astro
import { Image } from 'astro:assets';

export interface Props {
  variant: 'impact' | 'split' | 'minimal';
  title: string;
  subtitle: string;
  ctaLabel?: string;
  ctaHref?: string;
  imageUrl?: ImageMetadata; // For 'split' variant
  imageAlt?: string;
}

const { 
  variant, 
  title, 
  subtitle, 
  ctaLabel, 
  ctaHref,
  imageUrl,
  imageAlt = 'Descriptive image alt text'
} = Astro.props;
---
{variant === 'impact' && (
  <section class="relative h-screen min-h-[600px] flex items-center justify-center text-surface-50 overflow-hidden">
    <div class="absolute inset-0 z-0">
      {imageUrl && <Image src={imageUrl} alt={imageAlt} class="w-full h-full object-cover" densities={[1, 1.5, 2]} />}
      <div class="absolute inset-0 bg-primary-900 opacity-60"></div>
    </div>
    <div class="relative z-10 text-center max-w-4xl px-6 sm:px-8 animate-on-scroll fade-in-up">
      <h1 class="font-heading font-bold text-5xl md:text-6xl mb-4 leading-tight">{title}</h1>
      <p class="font-body text-lg md:text-xl max-w-2xl mx-auto mb-8 opacity-90">{subtitle}</p>
      {ctaLabel && ctaHref && (
        <a href={ctaHref} class="inline-block bg-accent-500 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg hover:shadow-xl">{ctaLabel}</a>
      )}
    </div>
  </section>
)}

{variant === 'split' && (
  <section class="bg-surface-50 text-primary-900 py-24 md:py-32">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 grid md:grid-cols-2 gap-12 items-center">
      <div class="relative animate-on-scroll fade-in-left">
        {imageUrl && <Image src={imageUrl} alt={imageAlt} class="w-full h-auto rounded-none shadow-md" />}
      </div>
      <div class="animate-on-scroll fade-in-right">
        <h1 class="font-heading font-bold text-4xl md:text-5xl mb-4 leading-tight">{title}</h1>
        <p class="font-body text-lg text-primary-700 mb-8">{subtitle}</p>
        {ctaLabel && ctaHref && (
          <a href={ctaHref} class="inline-block bg-accent-500 text-surface-50 font-medium font-heading py-3 px-8 rounded-md hover:bg-accent-600 transition duration-300 ease-in-out active:scale-95 shadow-lg hover:shadow-xl">{ctaLabel}</a>
        )}
      </div>
    </div>
  </section>
)}

{variant === 'minimal' && (
  <section class="bg-surface-100 text-primary-900 py-24 md:py-32 text-center">
    <div class="max-w-3xl mx-auto px-6 sm:px-8 animate-on-scroll fade-in-up">
      <h1 class="font-heading font-bold text-4xl md:text-5xl mb-4 leading-tight">{title}</h1>
      <p class="font-body text-lg text-primary-700 mb-8">{subtitle}</p>
    </div>
  </section>
)}
```

## Dependencies
*   Astro's built-in `Image` component (`astro:assets`).

## Acceptance Criteria
*   The `src/components/Hero.astro` file exists.
*   Passing `variant="impact"` renders the full-screen hero.
*   Passing `variant="split"` renders the two-column hero with an image on the left.
*   Passing `variant="minimal"` renders the text-focused hero.
*   The component correctly displays the `title`, `subtitle`, and CTA button when provided.

## Code Patterns
*   Uses Astro's conditional rendering syntax (`{condition && (...) }`) to render the markup for the selected variant. This keeps all variants within a single file for easy management.
*   Uses `astro:assets`'s `<Image>` component for automatic image optimization for the `split` and `impact` variants. The `imageUrl` prop is typed as `ImageMetadata` for type safety.