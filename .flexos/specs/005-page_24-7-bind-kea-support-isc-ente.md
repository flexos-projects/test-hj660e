```markdown
---
type: spec
subtype: page
title: 24/7 BIND & Kea Support | ISC Enterprise Services
route: /enterprise/support/
layout: service_detail
---
### Purpose
To detail the specific support offerings, tiers, and benefits, with the primary goal of driving qualified users to request a quote.

### Components
1.  **ServiceDetailHeader**
    *   **Description:** A header section that clearly states the service and its primary benefit.
    *   **Content:** Service title ("Enterprise Support"), a compelling tagline ("Direct Access to the Engineers Who Write the Software"), and a brief introductory paragraph.

2.  **TierComparisonTable**
    *   **Description:** A clear, scannable table that breaks down the features of different support tiers (e.g., Premium, Standard). This is the core of the page.
    *   **Content:** A table with tiers as columns and features/SLAs as rows. Features include "Response Time (SLA)", "24/7 Emergency Support", "Access to Engineering", "Named Technical Contact", etc. Each cell clearly indicates if the feature is included. Each column header should have a "Request Quote" button for that specific tier.

3.  **BenefitsList**
    *   **Description:** A section that goes beyond features to explain the tangible benefits of an ISC support contract.
    *   **Content:** A list or grid of key benefits, each with an icon, title (e.g., "Minimize Downtime", "Accelerate Problem Resolution", "Proactive Security Audits"), and a descriptive paragraph.

4.  **ExpertAccess**
    *   **Description:** A section that reinforces the "direct from the source" value proposition, potentially linking to the "Our Experts" page.
    *   **Content:** A content block with a heading like "Your Direct Line to Protocol Experts", a paragraph explaining the value, and potentially a few small profile photos of key engineers.

5.  **QuoteRequestForm**
    *   **Description:** The primary conversion tool on the page. This should be the "High-Fidelity Quote Request Form" from the P1 features. It could be embedded on the page or linked to prominently.
    *   **Content:** A multi-step form that captures necessary details (contact info, company, products used, deployment size, desired support tier) without being overwhelming. Includes clear labels, validation, and a confirmation step.

### Data Requirements
*   **ServiceDetailHeader:** `service_title`, `tagline`, `introduction_text`.
*   **TierComparisonTable:** A collection of `tiers`, each with a `name`, `description`, `cta_link`, and a list of `features` (feature name, value/check mark). A separate list of all possible `feature_rows` with descriptions.
*   **BenefitsList:** A collection of `benefits`, each with `icon`, `title`, `description`.
*   **ExpertAccess:** `heading`, `text_content`, collection of `featured_experts` (name, photo_url, link_to_profile).
*   **QuoteRequestForm:** Form field definitions, validation rules, and submission endpoint.

### User Interactions
*   User compares features across different support tiers in the table.
*   User clicks a "Request Quote" button, which scrolls them to the form or navigates to the quote page.
*   User fills out and submits the quote request form.
*   User clicks on a featured expert to navigate to the "Our Experts" page.

### States
*   **Form Submission:** The form should have clear states for `submitting` (e.g., disabled button, spinner), `success` (confirmation message), and `error` (field-level and global error messages).
*   **Hover:** All interactive elements must have clear hover states.
```