```markdown
---
type: spec
subtype: page
title: 'Kea: A Modern, High-Performance DHCP Server'
route: /products/kea/
layout: product_detail
---
### Purpose
To introduce and promote ISC's modern DHCP solution, highlighting its performance and flexibility to encourage adoption and support inquiries. This is a "Product Showcase Page" as defined in the P1 features.

### Components
1.  **ProductHeader**
    *   **Description:** A hero-style section at the top of the page introducing the product.
    *   **Content:** Product name ("Kea DHCP"), tagline ("A Modern, High-Performance DHCP Server"), and a brief introductory paragraph emphasizing its modernity and advantages over older solutions.

2.  **ProductCTAs**
    *   **Description:** A prominent bar or section with the primary calls-to-action for the product.
    *   **Content:** Two primary buttons: "Download Kea" and "View Documentation". A secondary link/button for "Get Enterprise Support".

3.  **FeatureList**
    *   **Description:** A detailed breakdown of the key features and benefits of the product.
    *   **Content:** A grid or list of features. Each item should have an icon, a feature name (e.g., "High Performance", "Extensible Hooks", "Modern API"), and a short description explaining the benefit.

4.  **AdvantagesOverview**
    *   **Description:** A section comparing Kea to older DHCP solutions, highlighting its key advantages without being overly aggressive.
    *   **Content:** A content block explaining advantages like performance, flexibility via hooks, JSON configuration, and REST API.

5.  **EnterpriseSupportCallout**
    *   **Description:** A dedicated call-to-action block to funnel interested enterprise users to the support services page.
    *   **Content:** A compelling heading (e.g., "Deploy Kea with Confidence"), a paragraph explaining the value of professional support from ISC, and a strong CTA button linking to `/enterprise/support/`.

### Data Requirements
*   **ProductHeader:** `product_name`, `tagline`, `introduction_text`.
*   **ProductCTAs:** `download_url`, `documentation_url`, `support_url`.
*   **FeatureList:** A collection of `features`, each with `icon`, `name`, `description`.
*   **AdvantagesOverview:** `heading`, `content_body` (can be structured markdown).
*   **EnterpriseSupportCallout:** `heading`, `description_text`, `cta_label`, `cta_url`.

### User Interactions
*   User clicks "Download Kea" to navigate to the software download page/repository.
*   User clicks "View Documentation" to navigate to the Kea documentation section.
*   User clicks "Get Enterprise Support" (or the dedicated callout) to navigate to the enterprise support page.

### States
*   **Hover:** All interactive elements (buttons, links) must have clear hover states.
```