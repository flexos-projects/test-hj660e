`081-flow_decision-maker-request-quote.md`
---
type: spec
subtype: flow
title: Decision-Maker Evaluates Enterprise Support and Requests a Quote
trigger: A CTO needs to find and evaluate a commercial support partner for their organization's business-critical BIND infrastructure.
---

### Trigger

A CTO (Persona: David) at a regional bank has identified a business risk with their current unsupported BIND setup. He is actively seeking a trustworthy, professional partner to provide expert support and mitigate this risk.

### Steps

1.  **Entry:** User lands on the ISC homepage, referred by a colleague or via a search for "commercial BIND support".
2.  **User Action (Homepage):** User sees the headline "The Trusted Foundation of the Internet" and the prominent "For the Enterprise" CTA. He clicks the CTA.
3.  **System (Enterprise Gateway):** The `/enterprise/` page loads, presenting key value propositions (reliability, expert access, business continuity) and social proof (customer logos).
4.  **User Action (Enterprise Gateway):** User scans the page and clicks on a link or button to learn more about support offerings (e.g., "Explore Support Plans").
5.  **System (Support Page):** The `/enterprise/support/` page loads, detailing the support tiers, features like 24/7 availability, and pricing structure.
6.  **User Action (Support Page):** Intrigued by claims of expertise, the user navigates to the "Our Experts" page via a link in the main navigation or on the page.
7.  **System (Experts Page):** The `/about/experts/` page loads, showcasing the team's credentials and experience.
8.  **User Action (Experts Page):** Confidence built, the user navigates back to the `/enterprise/support/` page.
9.  **User Action (Support Page):** User clicks the prominent "Request a Quote" button.
10. **System (Form):** A modal or dedicated page loads with a clear, professional quote request form.
11. **User Action (Form):** User fills in their contact information and details about their infrastructure.
12. **User Action (Form):** User clicks the "Submit" button.
13. **System (Confirmation):** The system validates and processes the form. It then displays a "Thank You" message, confirming the submission and setting expectations for a response time.

### Decision Points

*   **Homepage:** The user must feel the "For the Enterprise" path is the correct one for them, as opposed to community-focused "Resources".
*   **Enterprise/Support Pages:** The user decides if the information presented is compelling enough to continue exploring or to proceed directly to requesting a quote.
*   **Build Confidence:** The user makes a conscious or subconscious decision to investigate the team's expertise, which is a critical step in the B2B trust-building process.

### Error Handling

*   **Form Validation:** If the user submits the form with missing required fields or invalid data (e.g., malformed email address), the system must display clear, inline error messages next to the corresponding fields without clearing the valid data.
*   **Form Submission Failure:** If the form fails to submit due to a server error, the system must display a non-technical error message (e.g., "Something went wrong. Please try again later or contact us at...") and preserve the user's entered data.

### Success/Failure States

*   **Success:** The user feels the website is professional and informative, finds the information needed to build confidence in ISC, and successfully submits the quote request form.
*   **Failure:** The user abandons the flow because the value proposition is unclear, the site feels unprofessional, key information is missing (e.g., no details on support tiers), or the contact form is broken.