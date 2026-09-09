---
name: derrick-french-company-registry
description: Look up and enrich French companies via SIRET/SIREN registry data and NAF-code imports with Derrick.
api: Derrick MCP Server
generated: 2026-09-09
method: generated
source: mcp/derrick-actions-catalog.json (probed from https://app1.derrick-app.com/api/v1/docs/actions)
operations:
  - derrick_data_gouv
  - derrick_companies_by_naf
  - derrick_enrich_companies
  - derrick_is_hiring
---

# French company registry lookups with Derrick

Official French legal-entity data (data.gouv.fr) combined with LinkedIn firmographics.

## Steps

1. **Registry lookup.** Call `derrick_data_gouv` with `siret` (a SIRET, SIREN, or company name;
   optional `locationCode`) — returns SIRET, SIREN, NAF code, registered address, share capital,
   last filing date. 1 credit, per call.
2. **Prospect by industry code.** Call `derrick_companies_by_naf` with `nafCode` (optional
   `locationCode`) to import companies in a French industry classification. 1 credit per company.
3. **Add firmographics.** Call `derrick_enrich_companies` (`queryValue` = name or domain) to layer
   headcount, industry, funding, and social profiles onto the registry record. 1 credit.
4. **Check hiring signal.** Call `derrick_is_hiring` (`companyLinkedinUrl`, optional `country`,
   `datePosted`, `keyword`) to see whether the company is actively recruiting. 1 credit.

## Rules

- All four tools are per-call billed: a no-match result still consumes the credit — validate
  SIRET/SIREN format before calling.
- Stay under 60 requests/minute; on 429 back off (2s initial, exponential with jitter).
- Registry data is public French government data; the LinkedIn-backed steps require the user's
  Derrick Chrome extension to be connected.
