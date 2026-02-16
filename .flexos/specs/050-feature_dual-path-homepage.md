---
type: spec
subtype: feature
title: Dual-Path Homepage
priority: P1
---

### Description

This feature establishes the primary user segmentation mechanism on the homepage. The hero section will present two clear, distinct, and equally prominent choices: one funneling users towards open-source community resources ("For the Community") and the other towards professional B2B offerings ("For the Enterprise"). This is the most critical component for solving the split-audience challenge, ensuring visitors are immediately directed to the content most relevant to their needs.

### User Stories

-   **As a community developer,** I want to quickly find open-source downloads and documentation so that I can get started with the software without sifting through enterprise marketing material.
-   **As an enterprise IT manager,** I want to easily navigate to information about professional support, training, and consulting so that I can efficiently evaluate ISC as a potential vendor for my company.
-   **As a new visitor unsure of my path,** I want to see clear, concise descriptions for each option so that I can make an informed choice and understand what ISC offers to different audiences.
-   **As a marketing manager,** I want to track user choices on the homepage so that I can measure the effectiveness of our audience segmentation and understand our visitor demographics.

### Acceptance Criteria

-   **Given** a user lands on the homepage,
    -   **When** they view the main hero section,
    -   **Then** they must see two distinct, clickable paths.
-   **Given** the two paths are displayed,
    -   **Then** one path is clearly labeled "For the Community" (or similar) with a sub-heading that mentions open source, documentation, and downloads.
    -   **And** the other path is clearly labeled "For the Enterprise" (or similar) with a sub-heading that mentions support, services, and reliability.
-   **Given** a user is on the homepage,
    -   **When** they click the "For the Community" path,
    -   **Then** they are navigated to a community-focused landing page (e.g., the Product Showcase).
-   **Given** a user is on the homepage,
    -   **When** they click the "For the Enterprise" path,
    -   **Then** they are navigated to the Enterprise Services Section landing page.
-   **Given** the homepage is loaded on any device,
    -   **Then** the dual-path component must be fully responsive, visually appealing, and functional on mobile, tablet, and desktop viewports.
-   **Given** a user interacts with the homepage,
    -   **Then** clicks on each path are tracked as distinct events in the site's analytics platform.

### Technical Notes

-   The text, sub-headings, and destination URLs for these CTAs should be easily editable in the Headless CMS.
-   Implement analytics event tracking (e.g., Google Analytics, Plausible) for clicks on each path to measure audience segmentation and funnel effectiveness.
-   The design should be A/B testable in the future to optimize wording or presentation.
-   Ensure the component is accessible, with proper ARIA attributes and keyboard navigation support.
```