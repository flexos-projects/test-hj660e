```markdown
---
type: spec
subtype: page
title: Contact The Internet Systems Consortium (ISC)
route: /contact/
layout: contact
---
### Purpose
To provide a clear, functional, and segmented contact page that directs users to the correct channel for their inquiry.

### Components
1.  **PageHeader**
    *   **Description:** A simple header for the contact page.
    *   **Content:** Heading ("Contact Us") and a short paragraph encouraging users to get in touch through the appropriate channel.

2.  **ContactOptions**
    *   **Description:** The primary component of the page, which segments contact methods.
    *   **Content:** A set of distinct sections or cards for different inquiry types:
        *   **Enterprise Sales:** Heading, a short description, and a prominent button/link that directs users to the quote request form (`/enterprise/#quote-form` or similar).
        *   **General Inquiries:** Heading, a short description, and a simple contact form (Name, Email, Message) or a clearly displayed `info@isc.org` email address.
        *   **Security Vulnerabilities:** A very clear, distinct section with a heading, instructions on how to report a vulnerability, a link to the PGP key, and the dedicated security email address. It should NOT be a web form.
        *   **Mailing Address:** A section with the physical mailing address of ISC.

### Data Requirements
*   **PageHeader:** `heading`, `introduction_text`.
*   **ContactOptions:**
    *   `enterprise_sales` (heading, description, cta_label, cta_url)
    *   `general_inquiries` (heading, description, form_endpoint or email_address)
    *   `security_vulnerabilities` (heading, instructions_text, pgp_key_url, security_email_address)
    *   `mailing_address` (heading, address_lines)

### User Interactions
*   User identifies the correct channel for their inquiry.
*   User clicks the "Request a Quote" button to be taken to the enterprise sales form.
*   User fills out and submits the general inquiries form.
*   User copies the security email address and follows instructions to report a vulnerability.

### States
*   **Form Submission (General Inquiries):** The form should have `submitting`, `success`, and `error` states, similar to the quote request form but simpler.
*   **Hover:** All links and buttons must have clear hover states.