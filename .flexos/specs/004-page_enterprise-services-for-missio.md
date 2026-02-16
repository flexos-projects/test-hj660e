```markdown
---
type: spec
subtype: page
title: Enterprise Services for Mission-Critical Infrastructure | ISC
route: /enterprise/
layout: service_gateway
---
### Purpose
To serve as a polished landing page for the Decision-Maker persona, selling the "why" (reliability, expertise) before the "what" (specific services), and driving them to request a quote.

### Components
1.  **PageHeader**
    *   **Description:** A hero section tailored to the enterprise audience, focusing on outcomes and trust.
    *   **Content:** A strong heading (e.g., "Expertise and Reliability for Your Core Infrastructure"), a subheading emphasizing ISC as the source of the software, and a primary CTA button: "Request a Quote".

2.  **ServicesOverview**
    *   **Description:** A high-level overview of the main service categories offered.
    *   **Content:** A set of 3 cards or feature blocks, one for each service: Support, Training, and Consulting. Each card includes the service name, a short description, and a "Learn More" link to the respective detailed service page.

3.  **SocialProof**
    *   **Description:** A section to build trust and credibility using client testimonials and logos.
    *   **Content:** A carousel or grid of client logos. A selection of 1-2 powerful client testimonials, each with the quote, the person's name, title, and company.

4.  **ValueProposition**
    *   **Description:** A "Why ISC?" section that clearly articulates the key value propositions for choosing ISC services.
    *   **Content:** A list or grid of key benefits, each with an icon, a title (e.g., "Direct from the Source", "Unmatched Expertise", "Proactive Security"), and a brief explanation.

5.  **CallToActionBlock**
    *   **Description:** A final, prominent call-to-action section at the bottom of the page to capture leads.
    *   **Content:** A clear, action-oriented heading ("Ready to Secure Your Infrastructure?"), a brief supporting sentence, and a primary "Request a Quote" button.

### Data Requirements
*   **PageHeader:** `heading`, `subheading`, `cta_label`, `cta_url` (links to quote form).
*   **ServicesOverview:** A collection of `services`, each with `name`, `description`, `url`.
*   **SocialProof:** A collection of `client_logos` (image_url, alt_text) and a collection of `testimonials` (quote, author_name, author_title, company_name).
*   **ValueProposition:** A collection of `value_props`, each with `icon`, `title`, `description`.
*   **CallToActionBlock:** `heading`, `text_content`, `cta_label`, `cta_url`.

### User Interactions
*   User clicks the primary "Request a Quote" CTA in the header or footer block, which either opens a modal form or navigates to a dedicated quote page.
*   User clicks a "Learn More" link on a service card to navigate to the detailed page for that service (e.g., `/enterprise/support/`).
*   User can see different testimonials if a carousel is used.

### States
*   **Hover:** All interactive elements (buttons, service cards, links) must have clear hover states.
```