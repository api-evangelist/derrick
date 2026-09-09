---
name: derrick-enrich-lead-contact-info
description: Enrich a lead from a LinkedIn URL or name into verified email, phone, and profile data with Derrick.
api: Derrick MCP Server
generated: 2026-09-09
method: generated
source: mcp/derrick-actions-catalog.json (probed from https://app1.derrick-app.com/api/v1/docs/actions) + featured example in the provider's MCP server card
operations:
  - derrick_search_linkedin_profile
  - derrick_enrich_profile
  - derrick_find_email
  - derrick_verify_email
  - derrick_find_phone
---

# Enrich a lead's contact info with Derrick

From a name or LinkedIn URL to a verified email and phone.

## Steps

1. **Locate the profile** (skip if you already have the LinkedIn URL). Call
   `derrick_search_linkedin_profile` with `queryValue` (person's name) and optional
   `companyValue`. 1 credit, per call.
2. **Enrich the profile.** Call `derrick_enrich_profile` (`queryValue` = LinkedIn profile URL)
   for title, seniority, location, tenure, education. 1 credit, per call.
3. **Find the work email.** Call `derrick_find_email` with `fullName` and `company` (optional
   `linkedinCompanyURL`). 5 credits, billed **only on success**.
4. **Verify before use.** Call `derrick_verify_email` (`email`) — returns valid / risky /
   catch-all / role-based / disposable. 1 credit, per call (charged even if unknown).
5. **Phone only when justified.** `derrick_find_phone` (`linkedinProfilUrl`) costs **150 credits**
   per found number — confirm with the user before every call. Billed only on success.

## Rules

- State the total expected credit cost before running a multi-step enrichment; check the balance
  with `derrick_account` / `derrick_credits` first.
- Batch across a list at most 60 requests/minute; back off with jitter on 429 (never charged).
- find_email and find_phone are slow; the server emits keepalive notifications — do not retry
  while a call is still in flight (a duplicate completed call is a duplicate charge).
- This tooling handles personal data (emails, phones): only enrich contacts the user has a
  legitimate business purpose for; Derrick's DPA and GDPR posture are linked in
  `conformance/derrick-conformance.yml`.
