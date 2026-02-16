---
type: doc
subtype: core
title: Content & Data Models
---

This document defines the structured content models required to power the new ISC website. These models ensure content is consistent, reusable, and optimized for both display and SEO (via JSON-LD). All text fields support Markdown.

### 1. Product

Used for BIND 9 and Kea.
*   **`name`**: Text (e.g., "BIND 9")
*   **`slug`**: Text (e.g., "bind")
*   **`tagline`**: Text (e.g., "The World's Most Trusted DNS Software")
*   **`logo`**: Image
*   **`summary`**: Text (for use on homepage cards)
*   **`body`**: Markdown (full page content)
*   **`features`**: Repeater
    *   **`icon`**: Icon selector
    *   **`feature_title`**: Text
    *   **`feature_description`**: Text
*   **`download_link`**: URL
*   **`documentation_link`**: URL (links to the resource library, pre-filtered)

### 2. Service

Used for Enterprise Support, Training, and Consulting.
*   **`title`**: Text (e.g., "Enterprise Support")
*   **`slug`**: Text (e.g., "support")
*   **`summary`**: Text (for use on the Enterprise gateway page)
*   **`body`**: Markdown (full page content, including tier descriptions)
*   **`audience`**: Tag (pre-set to "Enterprise")
*   **`cta_label`**: Text (e.g., "Request a Support Quote")
*   **`cta_link`**: URL (links to the contact page with a query parameter)

### 3. Team Member (Expert)

Drives the "Our Experts" page.
*   **`name`**: Text (e.g., "Jane Doe")
*   **`title`**: Text (e.g., "Principal Software Engineer")
*   **`photo`**: Image (professional headshot)
*   **`bio`**: Markdown (detailed biography)
*   **`social_links`**: Repeater
    *   **`platform`**: Select (LinkedIn, Twitter, GitHub)
    *   **`url`**: URL
*   **`is_active`**: Boolean (to show/hide members)

### 4. Resource

The core model for the Knowledge Hub and Documentation.
*   **`title`**: Text
*   **`slug`**: Text (auto-generated from title)
*   **`resource_type`**: Select (Documentation, Knowledge Base Article, Announcement)
*   **`author`**: Relation (links to a **Team Member**)
*   **`publish_date`**: Date
*   **`body`**: Markdown
*   **`tags`**: Tag list (e.g., "DNS", "Security", "IPv6")
*   **`related_product`**: Relation (links to a **Product**, e.g., BIND 9 or Kea)
*   **`product_version`**: Text (e.g., "9.18.1")

### 5. Testimonial

For enterprise social proof.
*   **`quote`**: Text (the testimonial itself)
*   **`author_name`**: Text
*   **`author_title`**: Text (e.g., "CTO")
*   **`company_name`**: Text
*   **`company_logo`**: Image (optional)
*   **`is_featured`**: Boolean (to highlight on homepage or enterprise gateway)

### 6. Site Globals

A singleton collection for site-wide settings.
*   **`site_name`**: Text ("Internet Systems Consortium")
*   **`site_tagline`**: Text ("The Trusted Foundation of the Internet")
*   **`contact_email_sales`**: Email
*   **`contact_email_general`**: Email
*   **`security_contact_instructions`**: Markdown
*   **`social_links`**: Repeater (Platform, URL)

These models provide the necessary structure to build a dynamic, content-rich site that is easy to manage and scale over time.