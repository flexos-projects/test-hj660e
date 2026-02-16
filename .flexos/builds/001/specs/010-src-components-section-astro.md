---
type: spec
subtype: build-spec
title: src/components/Section.astro
phase: 2
priority: 5
---

## Files to Create/Modify
*   `src/components/Section.astro` (Create)

## Implementation Details
Create a reusable wrapper component for content sections. This component will handle consistent vertical padding, background colors, and the max-width content container, as defined in `design/patterns.md` (Section 1). It will accept props to control its appearance.

```astro
---
// src/components/Section.astro
import { twMerge } from 'tailwind-merge';

export interface Props {
  variant?: 'light' | 'dark' | 'light-alt';
  class?: string; // For additional padding or other utility classes
}

const { variant = 'light', class: className } = Astro.props;

const variantClasses = {
  'light': 'bg-surface-50 text-primary-800',
  'light-alt': 'bg-surface-100 text-primary-800', // For alternating light sections
  'dark': 'bg-primary-900 text-surface-50',
};

const baseClasses = "py-24 lg:py-32";
const finalClasses = twMerge(baseClasses, variantClasses[variant], className);
---
<section class={finalClasses}>
  <div class="max-w-7xl mx-auto px-6 sm:px-8">
    <slot />
  </div>
</section>
```

## Dependencies
*   `tailwind-merge` should be added to `package.json` (`npm install tailwind-merge`) to intelligently merge Tailwind classes passed via props.

## Acceptance Criteria
*   The file `src/components/Section.astro` exists.
*   Using `<Section>` provides the default `py-24 lg:py-32` padding and a `max-w-7xl` container.
*   `<Section variant="dark">` renders a section with a `bg-primary-900` background and light text.
*   `<Section class="pt-0">` successfully overrides the top padding.

## Code Patterns
*   A `Props` interface defines the component's API.
*   A `variantClasses` object maps the `variant` prop to specific Tailwind classes for background and text color. This is a clean way to manage component variations.
*   `tailwind-merge` is used to allow developers to pass in overriding utility classes (like `pt-0` or `max-w-5xl`) without class name conflicts. This makes the component highly flexible.