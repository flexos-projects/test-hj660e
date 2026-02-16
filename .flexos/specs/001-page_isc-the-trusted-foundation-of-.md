---
type: spec
subtype: page
title: 'ISC: The Trusted Foundation of the Internet'
route: /
layout: homepage
---
### Purpose
To instantly communicate ISC's authority and cleanly segment the two primary audiences.

### Components
1.  **Hero**
    *   **Description:** A full-width hero section with a compelling background image/graphic. It contains the primary value proposition.
    *   **Content:** Heading ("The trusted, modern stewards of the internet's core infrastructure."), and potentially a short subheading.

2.  **AudienceSelector**
    *   **Description:** A visually distinct block directly below the hero, featuring two prominent calls-to-action to segment users. This implements the "Dual-Path Homepage" P1 feature.
    *   **Content:** Two large, clickable cards or buttons: "For the Community" and "For the Enterprise". Each has a title, a short description of who it's for, and a clear link.

3.  **ImpactStats**
    *   **Description:** A visually engaging section that uses key numbers to communicate ISC's scale and importance, as per the "Our Impact Showcase" P1 feature.
    *   **Content:** A row of 3-4 key statistics, each with a large number, a descriptive label (e.g., "DNS Queries/Day", "Active Deployments"), and an optional icon.

4.  **FeaturedProducts**
    *   **Description:** A section showcasing the two core products, BIND 9 and Kea.
    *   **Content:** Two cards, one for each product. Each card includes the product logo, name, a brief one-sentence description, and a "Learn More" link.

5.  **FeaturedService**
    *   **Description:** A callout section to highlight the primary enterprise offering (Support). It links to the main Enterprise Gateway page.
    *   **Content:** A visually distinct block with a heading (e.g., "Mission-Critical Support"), a paragraph describing the value of enterprise support, and a primary CTA button ("Explore Enterprise Services").

6.  **ArticleGrid**
    *   **Description:** A section displaying the most recent posts from the Knowledge Hub to showcase thought leadership and recent activity.
    *   **Content:** A grid or list of the 3 latest articles. Each article preview includes its featured image, title, a short excerpt, and publication date.

7.  **MissionCallout**
    *   **Description:** A final section on the page that reinforces the non-profit mission of ISC, building trust and communicating core values.
    *   **Content:** A block with a heading about the non-profit mission, a short paragraph of text, and a CTA to the "About Us" page.

### Data Requirements
*   **Hero:** `heading`, `subheading`, `background_image`.
*   **AudienceSelector:** `community_cta` (title, description, url), `enterprise_cta` (title, description, url).
*   **ImpactStats:** A collection of `stats`, each with `number`, `label`.
*   **FeaturedProducts:** A collection of `products` (BIND, Kea), each with `name`, `description`, `logo`, `url`.
*   **FeaturedService:** `heading`, `description`, `cta_label`, `cta_url`.
*   **ArticleGrid:** A collection of the 3 latest `articles`, each with `title`, `excerpt`, `featured_image`, `url`, `publication_date`. This data will be fetched dynamically.
*   **MissionCallout:** `heading`, `text_content`, `cta_label`, `cta_url`.

### User Interactions
*   User clicks "For the Community" and is navigated to the Resources page (`/resources/`).
*   User clicks "For the Enterprise" and is navigated to the Services page (`/enterprise/`).
*   User clicks a product card and is navigated to the corresponding product detail page.
*   User clicks the Featured Service CTA and is navigated to the Services page (`/enterprise/`).
*   User clicks an article card and is navigated to the full article page.
*   User clicks the Mission Callout CTA and is navigated to the About Us page (`/about/`).

### States
*   **Loading:** The ArticleGrid component should display a loading state (e.g., skeleton placeholders) while fetching posts.
*   **Hover:** All interactive elements (buttons, cards, links) must have clear hover states.
*   **Empty:** If no articles can be fetched for the ArticleGrid, the component should either not render or display a message like "No recent articles available."
```