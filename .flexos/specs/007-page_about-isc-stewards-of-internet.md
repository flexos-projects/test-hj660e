```markdown
---
type: spec
subtype: page
title: 'About ISC: Stewards of Internet Infrastructure'
route: /about/
layout: about
---
### Purpose
To tell the "Unsung Architects" story, build institutional trust, and clearly communicate ISC's non-profit mission and long-standing commitment to a stable, open internet.

### Components
1.  **PageHeader**
    *   **Description:** A hero section that establishes the "Unsung Architects" narrative.
    *   **Content:** A strong heading like "The Unsung Architects of the Internet" and a concise paragraph that introduces ISC's mission and legacy.

2.  **MissionStatement**
    *   **Description:** A visually distinct section that highlights the 501(c)(3) non-profit status and core mission.
    *   **Content:** The official mission statement, prominently displayed, with emphasis on the public benefit and commitment to open source.

3.  **HistoryTimeline**
    *   **Description:** A section that visually represents ISC's long history and key milestones. For P1, this can be a simple vertical timeline. For P2, this will be the "Interactive History Timeline" feature.
    *   **Content:** A list of key dates and events in ISC's history (e.g., "1994: ISC Founded", "1998: BIND 9 Development Begins"). Each entry has a date and a short description.

4.  **TeamCallout**
    *   **Description:** A section to introduce the team and encourage users to learn more about the experts behind the software.
    *   **Content:** A heading like "Meet Our Experts", a short paragraph about the caliber of the team, a grid of a few featured team member photos, and a clear CTA button linking to the "Our Experts" page (`/about/experts/`).

5.  **ImpactCallout**
    *   **Description:** Connects the mission to tangible results, linking to a future, more detailed impact page or report.
    *   **Content:** A visually compelling block with statistics or a short narrative about ISC's global impact, reinforcing the data seen on the homepage. Includes a link to a (future) detailed impact report.

### Data Requirements
*   **PageHeader:** `heading`, `introduction_text`.
*   **MissionStatement:** `mission_statement_text`.
*   **HistoryTimeline:** A collection of `timeline_events`, each with `date` and `description`.
*   **TeamCallout:** `heading`, `text_content`, a collection of featured `team_members` (name, photo_url), and `cta_link`.
*   **ImpactCallout:** `heading`, `text_content`, `cta_link`.

### User Interactions
*   User scrolls through the history timeline to learn about key milestones.
*   User clicks the CTA in the TeamCallout section to navigate to the "Our Experts" page.

### States
*   **Hover:** All interactive elements (links, buttons) have clear hover states.
```