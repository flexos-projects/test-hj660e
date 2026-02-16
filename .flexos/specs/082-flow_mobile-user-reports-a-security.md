`082-flow_mobile-user-report-vulnerability.md`
---
type: spec
subtype: flow
title: Mobile User Reports a Security Vulnerability
trigger: A security researcher needs to find the proper channel to report a potential security vulnerability to ISC using their mobile phone.
---

### Trigger

A security researcher is away from their desk and discovers a potential vulnerability. They need to use their phone to quickly and securely find ISC's official procedure for responsible disclosure.

### Steps

1.  **Entry:** User performs a Google search on their mobile device for "ISC security contact".
2.  **System (Search Results):** The ISC Contact page (`/contact/`) is the top organic result.
3.  **User Action (Search Results):** User taps the link to the Contact page.
4.  **System (Contact Page):** The `/contact/` page loads quickly and is fully responsive for mobile viewing.
5.  **User Action (Contact Page):** User scrolls down the page, past general and sales contact options. They identify a clearly labeled section titled "Report a Security Vulnerability".
6.  **User Action (Contact Page):** User reads the instructions within this section, which provides a dedicated email address and may include a link to a PGP key for secure communication.
7.  **User Action (Device):** User taps the email address, which opens their phone's default mail client with the "To" field pre-populated.

### Decision Points

*   **Information Triage:** On the Contact page, the user must quickly distinguish the specific security reporting section from other general contact methods. The page hierarchy and labeling are critical.

### Error Handling

*   **Poor Mobile Performance:** If the page is slow to load or renders poorly on a mobile screen (e.g., text is too small, elements overlap), the user may be unable to find the information and abandon the task.
*   **Buried Information:** If the "Report a Security Vulnerability" section is not clearly titled or is buried at the very bottom of a long page, the user may miss it and use an incorrect channel.

### Success/Failure States

*   **Success:** The user finds the correct, dedicated security contact information and instructions in under a minute. The mobile experience is fast and frictionless.
*   **Failure:** The user cannot find the specific security contact info due to a poor mobile experience or unclear page structure. They may give up or use a general contact form, which is not the correct procedure for responsible disclosure.