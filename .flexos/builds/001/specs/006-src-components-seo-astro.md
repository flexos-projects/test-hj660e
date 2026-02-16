---
type: spec
subtype: build-spec
title: src/components/SEO.astro
phase: 2
priority: 1
---

## Files to Create/Modify
*   `src/components/SEO.astro` (Create)

## Implementation Details
Create a reusable Astro component to handle all SEO-related meta tags. This component will accept props for title, description, and other metadata, and will also generate a default `Organization` Schema.org script as specified in the technical docs.

```astro
---
// src/components/SEO.astro
import type { Organization, WithContext } from 'schema-dts';

export interface Props {
  title: string;
  description: string;
  ogImage?: string;
  canonicalURL?: URL | string;
}

const { 
  title, 
  description, 
  ogImage = '/default-og-image.png', // A default OG image should be placed in public/
  canonicalURL = new URL(Astro.url.pathname, Astro.site),
} = Astro.props;

const siteName = "Internet Systems Consortium (ISC)";

// As per docs/core/007-technical.md
const organizationSchema: WithContext<Organization> = {
  '@context': 'https://schema.org',
  '@type': 'Organization',
  name: siteName,
  url: Astro.site,
  logo: new URL('/isc-logo-for-schema.png', Astro.site).href, // A logo should be created for this
  sameAs: [
    // Add official social media/profile links here
  ],
};
---
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>{title} | {siteName}</title>
<meta name="description" content={description} />
<link rel="canonical" href={canonicalURL} />

<!-- Open Graph -->
<meta property="og:site_name" content={siteName} />
<meta property="og:title" content={title} />
<meta property="og:description" content={description} />
<meta property="og:url" content={canonicalURL} />
<meta property="og:image" content={new URL(ogImage, Astro.site)} />
<meta property="og:type" content="website" />

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content={title} />
<meta name="twitter:description" content={description} />
<meta name="twitter:image" content={new URL(ogImage, Astro.site)} />

<!-- Favicon -->
<link rel="icon" type="image/svg+xml" href="/favicon.svg" />

<!-- Schema.org -->
<script type="application/ld+json" set:html={JSON.stringify(organizationSchema)} />
```

## Dependencies
*   `astro.config.mjs` must have `site` property configured.

## Acceptance Criteria
*   The file `src/components/SEO.astro` exists.
*   When used in a layout, it correctly renders all `<meta>`, `<title>`, and `<link>` tags with the passed props.
*   The JSON-LD script for the `Organization` schema is correctly rendered in the HTML head.

## Code Patterns
*   Uses a TypeScript `Props` interface for strong typing.
*   Provides sensible defaults for `ogImage` and `canonicalURL`.
*   Uses `Astro.site` and `Astro.url` to construct absolute URLs, which is an SEO best practice.
*   Uses `set:html` to safely inject the JSON-LD string into the script tag.