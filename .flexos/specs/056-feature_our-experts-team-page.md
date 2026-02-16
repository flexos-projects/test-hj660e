```markdown
---
type: spec
subtype: feature
title: "Our Experts" Team Page
priority: P1
---

### Description

This feature involves creating a professional team page that showcases the core experts at ISC. More than a simple staff list, this page will build trust with potential enterprise buyers by highlighting the deep expertise and credentials of the team they would be working with. It will feature professional photos, detailed biographies, and specific credentials to humanize the organization and underscore the value of its professional services.

### User Stories

-   **As an enterprise buyer,** I want to see the qualifications and experience of the team I'll be entrusting my critical infrastructure to, so I can feel confident in my purchasing decision.
-   **As a conference organizer,** I want to find information about potential speakers from ISC and their areas of expertise, so I can invite them to speak at my event.
-   **As a potential new hire,** I want to see who I would be working with, so I can get a feel for the culture and level of expertise at the organization.

### Acceptance Criteria

-   A dedicated "/team" or "/experts" page is created.
-   The page displays a grid or list of core team members.
-   Each team member profile must include:
    -   A professional, high-resolution headshot.
    -   Full Name.
    -   Job Title.
    -   A detailed biography highlighting their expertise, history, and contributions.
    -   Optionally, links to their professional social media (e.g., LinkedIn) or publications.
-   The page can be filtered by department or area of expertise (e.g., "Engineering," "Support," "Leadership").
-   Clicking on a team member's card might expand their bio in place or open a modal window for a better reading experience.
-   The entire page, including profiles and filtering, is fully manageable through the CMS.
-   The layout is responsive and presents the team professionally on all screen sizes.

### Technical Notes

-   Create a "Team Member" content type in the CMS with fields for photo, name, title, bio, etc.
-   Image optimization is critical for this page to ensure fast load times. Use modern formats like WebP and implement responsive images (`srcset`).
-   The filtering logic should be implemented on the front end (e.g., using JavaScript) for a fast, seamless user experience.
```