# Create HubSpot Contact

Creates a contact in HubSpot CRM with standard fields. Checks for duplicate contacts and companies first. Creates the company if it doesn't exist. Associates contact to company.

## Arguments
Pass contact details as arguments. Required: first name, last name, email. Optional: job title, LinkedIn URL, company name, lifecycle stage.

Example: `/create-hubspot-contact Susie Warren, susie.warren@steadfast.com.au, Remuneration Consultant, Steadfast Group, linkedin.com/in/susie-warren-4a4b791b8`

## Steps

1. **Parse the arguments** — extract: first name, last name, email, job title, LinkedIn URL, company name. If any required field (first name, last name, email) is missing, ask the user.

2. **Check for duplicate contact** — search HubSpot contacts by email address using `mcp__hubspot__hubspot-search-objects` with objectType `contacts` and filter on `email`. If the contact already exists, show the existing record and ask the user if they want to update it instead. Do NOT create a duplicate.

3. **Check for duplicate company** — if a company name is provided, search HubSpot companies by name using `mcp__hubspot__hubspot-search-objects` with objectType `companies` and query the company name. Also try searching by domain (extract domain from email address). Note the company ID if found.

4. **Create company if not found** — if no matching company exists in step 3, create it using `mcp__hubspot__hubspot-batch-create-objects` with objectType `companies`:
   ```
   properties:
     name: [company name]
     domain: [domain from email address]
   ```
   Note the new company ID.

5. **Create the contact** using `mcp__hubspot__hubspot-batch-create-objects` with objectType `contacts`:
   ```
   properties:
     firstname: [first name]
     lastname: [last name]
     email: [email]
     jobtitle: [job title]
     company: [company name]
     lifecyclestage: lead
   ```
   If a LinkedIn URL is provided, include: `hs_linkedin_url: [full LinkedIn URL]`

6. **Associate contact with company** — use `mcp__hubspot__hubspot-batch-create-associations` to link the contact to the company (from step 3 or 4):
   - fromObjectType: contacts
   - toObjectType: companies
   - associationTypeId: 279 (contact to company, HUBSPOT_DEFINED)

7. **Generate HubSpot links** using `mcp__hubspot__hubspot-get-link` with portalId `147533794`, uiDomain `app-eu1.hubspot.com`, for both the contact and company.

8. **Confirm** — output:
   ```
   Contact created: [First] [Last] ([email])
   Title: [job title]
   Company: [company] (created / existing) — associated ✓
   LinkedIn: [url]
   HubSpot contact: [link]
   HubSpot company: [link]
   ```
