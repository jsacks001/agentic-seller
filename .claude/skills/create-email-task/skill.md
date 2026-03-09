# Create Email Task

Creates a HubSpot task with the email body, associated with a contact, so the seller can copy-paste and send from Outlook. Includes the email subject, body, and recipient details.

## Arguments
Pass either:
- A file path to an outreach markdown file (e.g., `accounts/steadfast-group/emails/2026-03-09-susie-warren-outreach.md`)
- Or: contact name + email + subject + body inline

Example: `/create-email-task accounts/steadfast-group/emails/2026-03-09-susie-warren-outreach.md`

## Steps

1. **Parse the input:**
   - If a file path is provided, read the file and extract: contact name, email address (from account research or ask user), subject line, email body
   - If inline, parse the arguments directly
   - Strip markdown formatting from the body — convert to plain text suitable for copy-paste into Outlook (no markdown links, no bold/italic markers)

2. **Find the contact in HubSpot** — search by email using `mcp__hubspot__hubspot-search-objects` with objectType `contacts`. If not found, tell the user to run `/create-hubspot-contact` first.

3. **Get owner details** — use ownerId `86830490` (Josh Sacks).

4. **Create the task** using `mcp__hubspot__hubspot-create-engagement`:
   ```
   type: TASK
   ownerId: 86830490
   associations:
     contactIds: [contact HubSpot ID]
   metadata:
     subject: "Send email: [subject line] — [Contact Name]"
     body: |
       <b>To:</b> [contact name] &lt;[email]&gt;<br>
       <b>Subject:</b> [subject line]<br>
       <b>LinkedIn:</b> [linkedin url if known]<br>
       <hr>
       [email body as HTML — convert newlines to <br>, keep paragraphs readable]
       <hr>
       <i>Created by Claude Code — copy/paste into Outlook to send</i>
     status: NOT_STARTED
     forObjectType: CONTACT
   ```

5. **Generate HubSpot link** to the task using `mcp__hubspot__hubspot-get-link` with portalId `147533794`, uiDomain `app-eu1.hubspot.com`.

6. **Confirm** — output:
   ```
   Task created: "Send email: [subject] — [Contact Name]"
   Contact: [name] ([email])
   Status: Not started
   HubSpot: [link to contact record]

   Copy-paste the email body from the task in HubSpot, paste into Outlook, and send.
   After sending, mark the task as complete in HubSpot.
   ```
