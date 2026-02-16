```markdown
---
type: spec
subtype: page
title: Our Experts | The ISC Team
route: /about/experts/
layout: team
---
### Purpose
To humanize the brand, showcase the incredible talent pool at ISC, and build trust with enterprise customers who are paying for access to this expertise. This page directly implements the "Our Experts" P1 feature.

### Components
1.  **PageHeader**
    *   **Description:** A simple header to introduce the team.
    *   **Content:** A heading ("Our Experts") and a short paragraph explaining the team's role and world-class expertise in internet protocols.

2.  **TeamGrid**
    *   **Description:** The main component of the page, a visually appealing grid of all team members.
    *   **Content:** A responsive grid of profile cards. Each card contains a professional photo, the person's name, and their title.

3.  **ProfileModal (or Individual Pages)**
    *   **Description:** A modal window or separate page that displays detailed information about a team member when their card is clicked.
    *   **Content:** A larger version of the photo, name, title, a detailed professional bio, and potentially links to their social profiles (e.g., LinkedIn, GitHub) or published works.

### Data Requirements
*   **PageHeader:** `heading`, `introduction_text`.
*   **TeamGrid:** A collection of `team_members`. Each member object needs:
    *   `name`
    *   `title`
    *   `photo_url` (high resolution)
    *   `bio` (detailed markdown/HTML)
    *   `social_links` (optional collection of platform, url)
    *   `slug` (for individual page URLs, if that approach is chosen)

### User Interactions
*   User scrolls and browses the grid of team members.
*   User clicks on a team member's card.
*   A modal window opens (or the user is navigated to a new page) displaying the detailed bio for that person.
*   User can close the modal to return to the grid.
*   User can click social links within the bio to visit external profiles.

### States
*   **Modal Open:** The rest of the page is obscured by an overlay, and the modal with the team member's details is displayed.
*   **Loading:** A loading indicator could be shown briefly if bios are fetched on demand.
*   **Hover:** The team member cards in the grid should have a clear hover state to indicate they are clickable.
```