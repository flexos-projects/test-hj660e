---
type: spec
subtype: build-spec
title: src/content/config.ts
phase: 3
priority: 1
---

## Files to Create/Modify
*   `src/content/config.ts` (Create)

## Implementation Details
Create the Astro Content Collections configuration file. This file defines the TypeScript schemas for all content types, ensuring data consistency and providing type safety. The schemas will be based directly on `docs/core/004-database.md`.

```typescript
// src/content/config.ts
import { defineCollection, z } from 'astro:content';

const blogCollection = defineCollection({
  type: 'content', // 'content' for Markdown, 'data' for JSON/YAML
  schema: z.object({
    title: z.string(),
    publishDate: z.date(),
    author: z.string(), // For simplicity; could reference a 'team' collection
    tags: z.array(z.string()),
    featuredImage: z.string().optional(),
    excerpt: z.string(),
  }),
});

const teamCollection = defineCollection({
  type: 'data',
  schema: z.object({
    name: z.string(),
    title: z.string(),
    photo: z.string(), // Path to image in /src/assets
    bio: z.string(),
    social: z.object({
      linkedin: z.string().url().optional(),
      twitter: z.string().url().optional(),
      github: z.string().url().optional(),
    }).optional(),
  }),
});

const productsCollection = defineCollection({
    type: 'data',
    schema: z.object({
        name: z.string(),
        slug: z.string(),
        tagline: z.string(),
        summary: z.string(),
        features: z.array(z.object({
            icon: z.string(),
            title: z.string(),
            description: z.string(),
        })),
        downloadLink: z.string().url(),
        documentationLink: z.string().url(),
    })
});

const servicesCollection = defineCollection({
    type: 'data',
    schema: z.object({
        title: z.string(),
        slug: z.string(),
        summary: z.string(),
        ctaLabel: z.string(),
        ctaLink: z.string().url(),
    })
});

export const collections = {
  'blog': blogCollection,
  'team': teamCollection,
  'products': productsCollection,
  'services': servicesCollection,
};
```

## Dependencies
*   Astro's content collections feature.
*   Zod for schema validation (comes with Astro).

## Acceptance Criteria
*   The file `src/content/config.ts` exists.
*   The schemas for `blog`, `team`, `products`, and `services` are defined.
*   Astro's dev server recognizes these collections and provides type hints when querying them with `getCollection`.
*   Attempting to build with content files that do not match the schema results in a build error.

## Code Patterns
*   Uses `defineCollection` from `astro:content` to create each collection.
*   Uses `zod` (`z`) to define the schema for each field, including types (`z.string()`, `z.date()`) and structure (`z.array()`, `z.object()`).
*   The `type` property is set to `'content'` for collections that will have Markdown body content (like blog posts) and `'data'` for collections that are pure data (like team members).