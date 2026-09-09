---
name: derrick-build-target-account-list
description: Build a qualified target-account list with leads, using Derrick's company search, enrichment, and staff-import tools.
api: Derrick MCP Server
generated: 2026-09-09
method: generated
source: mcp/derrick-actions-catalog.json (probed from https://app1.derrick-app.com/api/v1/docs/actions) + featured example in the provider's MCP server card
operations:
  - derrick_import_companies_from_prompt
  - derrick_search_companies
  - derrick_enrich_companies
  - derrick_find_staff_members
  - derrick_search_leads_in_companies
---

# Build a target-account list with Derrick

Turn an ideal-customer-profile description into a list of companies with named leads.

## Steps

1. **Source companies.** Call `derrick_import_companies_from_prompt` with a `description` of the
   ICP (e.g. "Series-A SaaS companies in France, 50-200 employees"); optional `country`,
   `numberOfResults`, `page`. 1 credit per company, billed per call. Alternatively, for French
   targeting by industry code use `derrick_companies_by_naf` (`nafCode`, optional `locationCode`).
2. **Resolve LinkedIn identities.** For companies you already have by name, call
   `derrick_search_companies` (`queryValue` = company name) to get the LinkedIn company profile.
3. **Enrich each company.** Call `derrick_enrich_companies` (`queryValue` = LinkedIn URL, name, or
   domain) for headcount, industry, funding, HQ, and social profiles. 1 credit per company.
4. **Find the right people.** Call `derrick_find_staff_members` (`company`, optional
   `currentFunction`, `offset`) to list a company's people, or
   `derrick_search_leads_in_companies` (`company`, `queryValue` = job-title pattern, optional
   `page`) to pull leads matching a title inside target companies. 1 credit per person/lead.

## Rules

- Confirm the credit spend with the user before batch calls: these are per-call billed —
  an empty result still charges (see `errors/derrick-problem-types.yml`).
- Respect the 60 requests/minute limit; on 429 back off exponentially (2s initial, 60s max) —
  a 429 is never charged.
- LinkedIn-backed tools need the user's Derrick Chrome extension connected; an empty response
  usually means it is not.
- For lists over ~100 rows, the provider recommends the Google Sheets add-on over the MCP.
