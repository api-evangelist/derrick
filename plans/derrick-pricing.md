# Derrick pricing

> Derrick is a B2B data enrichment tool that runs as a Google Sheets sidebar, plus a REST API and a native MCP server (Claude, ChatGPT, any MCP client). You pay per verified result in credits, and unused credits roll over. Currency: EUR.

Pricing on the site: https://derrick-app.com/pricing
Machine-readable copies: https://derrick-app.com/pricing.md and https://derrick-app.com/pricing.txt

## Plans

| Plan | Price (EUR/month) | Credits/month | Cost per credit (EUR) | Credit card | Highlights |
| --- | --- | --- | --- | --- | --- |
| FREE | 0 | 100 | n/a | Not required | LinkedIn URL finder, LinkedIn enriching, SIRET/SIREN enrichment, Sales Navigator import, data cleaning tools |
| MINI | 9 | 4,000 | 0.00225 | Required | Everything in FREE + Phone Finder, Email Finder & Verifier, website scraping, website tech lookup, AI enrichment (Claude/OpenAI), 100+ data points |
| STANDARD | 20 | 10,000 | 0.002 | Required | Everything in MINI + Signal change alerts, job history (last 30 days) |
| PLUS | 47.50 | 25,000 | 0.0019 | Required | Most popular. Everything in STANDARD + API access and the MCP server (Claude, ChatGPT, any agent), with a lower cost per credit |
| PRO | 175 | 100,000 | 0.00175 | Required | Everything in PLUS, with a lower cost per credit |
| SCALE | 320 | 200,000 | 0.0016 | Required | Everything in PLUS, with the lowest cost per credit, for the highest volumes |

All paid plans: unused credits roll over (they do not expire month to month). Higher tiers have a lower cost per credit.

## Credit cost per action (how credits are spent)

| Action | Credit cost |
| --- | --- |
| Enrich a company | 1 credit / company |
| Enrich a lead (LinkedIn profile) | 1 credit / profile |
| SIRET/SIREN enrichment | 1 credit / company |
| Company hiring signal (LinkedIn Jobs) | 1 credit / company |
| LinkedIn followers & connections count | 1 credit / profile |
| Search companies or leads | 1 credit each |
| Import LinkedIn leads or companies | 1 credit each |
| Import leads or companies from a prompt | 1 credit each |
| Import companies by NAF code (France) | 1 credit / company |
| Import a company's people | 1 credit / person |
| Import similar companies | 1 credit / company |
| Import LinkedIn post likes & comments | 1 credit / engager |
| Google Maps, Google News | 1 credit / result |
| Email Finder | 5 credits / email found |
| Email Verification | 1 credit / email |
| Phone Finder | 150 credits / phone found |
| Website crawler, Website technologies, Email & Social extractor, Google first result | 2 credits / line |
| Google first-page SERP results | 5 credits / line |
| Ask OpenAI | 1 credit / line |
| Ask Claude | 2 credits / line |
| Push to La Growth Machine, lemlist, Webhook | Free (0 credits) |
| Find Duplicates, Find Gender, Find Names & Domains by Email | Free (unlimited, 0 credits) |

Finders (Email Finder, Phone Finder) bill only for results actually found.

## Billing

- Currency: EUR. Billed monthly.
- Unused credits roll over month to month (they do not expire).
- Free plan: 100 credits per month, no credit card required.
- API access and the MCP server are available from the PLUS plan (EUR 47.5/month) upward.
- Pay per verified result: finders charge only when a result is returned.

## For AI agents and MCP clients

Derrick exposes a native Model Context Protocol (MCP) server, so an AI assistant (Claude, ChatGPT, or any MCP-compatible client) can run enrichments directly. MCP and REST API access are included from the PLUS plan upward.
Start free: https://derrick-app.com/?utm_source=pricing-md&utm_medium=machine-readable&utm_campaign=pricing

## FAQ

### What is a credit?
A credit is the unit Derrick spends per action. Most enrichments cost 1 credit per row; some cost more (Email Finder 5, Phone Finder 150), and a few are free and unlimited.

### Do unused credits expire?
No. On every paid plan, unused credits roll over month to month.

### Do I pay for results that are not found?
No. Finders such as Email Finder and Phone Finder bill only for results actually returned.

### Is there a free plan?
Yes. The Free plan includes 100 credits per month with no credit card required.

### Can AI agents use Derrick?
Yes. Derrick exposes a native MCP server (Claude, ChatGPT, any MCP-compatible client) plus a REST API, available from the PLUS plan upward.

### What currency and billing cycle?
Pricing is in EUR, billed monthly. Higher tiers lower the cost per credit, from 0.00225 EUR on MINI down to 0.00175 EUR on PRO.

