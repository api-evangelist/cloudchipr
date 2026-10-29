# CloudChipr

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

CloudChipr is a cloud cost-management and FinOps platform that consolidates AWS, Azure, GCP, Kubernetes and AI-vendor spend (OpenAI, Anthropic, Datadog, Snowflake, MongoDB, Confluent) in a single console and automates resource cleanup, rightsizing, and cost governance. The product surface centres on Billing Explorer, dashboards, live resource management, savings opportunities, commitments, budgets and anomaly alerts, no-code automation workflows, and integrations with email, Slack, Jira and webhooks. Two machine surfaces are published: a 26-operation OpenAPI 3.0.3 Enterprise API at api.cloudchipr.com, authenticated with an x-api-key header and served as a spec at cloudchipr.github.io/api-service, and a hosted remote MCP server at mcp.cloudchipr.com/mcp exposing 25 read-only tools over OAuth 2.0 or a bearer API key. CloudChipr is a FinOps Foundation member, states SOC 2 Type II certification, and lists on AWS Marketplace.

**Areas:** AWS · Microsoft Azure · Cloud Cost Management · Cost Optimization · FinOps · GCP · Multi-Cloud · Resource Cleanup · Rightsizing

## CloudChipr on APIs.io

Everything profiled for CloudChipr is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/cloudchipr/](https://apis.io/providers/cloudchipr/)** — or go straight to one of the APIs or properties below.

### APIs (12)

- [CloudChipr MCP Server](https://apis.io/apis/cloudchipr/cloudchipr-mcp-server/) — Hosted, fully remote Model Context Protocol server at https://mcp.cloudchipr.com/mcp exposing 25 read-only tools across five categories - cloud accounts and…
- [CloudChipr Accounts API](https://apis.io/apis/cloudchipr/cloudchipr-accounts-api/) — Everything about accounts
- [CloudChipr Budgets API](https://apis.io/apis/cloudchipr/cloudchipr-budgets-api/) — Everything about budgets
- [CloudChipr Categories API](https://apis.io/apis/cloudchipr/cloudchipr-categories-api/) — Everything about categories
- [CloudChipr Custom Data API](https://apis.io/apis/cloudchipr/cloudchipr-custom-data-api/) — Everything about custom data sources
- [CloudChipr Dashboards API](https://apis.io/apis/cloudchipr/cloudchipr-dashboards-api/) — Everything about dashboards
- [CloudChipr Filters API](https://apis.io/apis/cloudchipr/cloudchipr-filters-api/) — Everything about filters
- [CloudChipr Regions API](https://apis.io/apis/cloudchipr/cloudchipr-regions-api/) — The Regions API from CloudChipr — 1 operation(s) for regions.
- [CloudChipr Resource Explorer API](https://apis.io/apis/cloudchipr/cloudchipr-resource-explorer-api/) — Everything about Resource Explorer
- [CloudChipr Resources API](https://apis.io/apis/cloudchipr/cloudchipr-resources-api/) — Endpoints for resources
- [CloudChipr Savings Opportunities API](https://apis.io/apis/cloudchipr/cloudchipr-savings-opportunities-api/) — Everything about savings opportunities
- [CloudChipr Widgets API](https://apis.io/apis/cloudchipr/cloudchipr-widgets-api/) — Everything about widgets

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Cloudchipr Webhooks](https://apis.io/asyncapis/cloudchipr/cloudchipr-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [cloudchipr](https://apis.io/servers/cloudchipr/cloudchipr/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Cloudchipr Enterprise Api Overlay](https://apis.io/overlays/cloudchipr/cloudchipr-enterprise-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Cloudchipr Authentication](https://apis.io/security/cloudchipr/cloudchipr-authentication/)
- [Cloudchipr Domain Security](https://apis.io/security/cloudchipr/cloudchipr-domain-security/)
- [Cloudchipr Trust Center](https://apis.io/security/cloudchipr/cloudchipr-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Cloudchipr Scopes](https://apis.io/scopes/cloudchipr/cloudchipr-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Cloudchipr Plans Pricing](https://apis.io/plans/cloudchipr/cloudchipr-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Cloudchipr Rate Limits](https://apis.io/rate-limits/cloudchipr/cloudchipr-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Cloudchipr Finops](https://apis.io/finops/cloudchipr/cloudchipr-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://cloudchipr.com/)
- [Documentation](https://docs.cloudchipr.com/reference)
- [Getting started](https://docs.cloudchipr.com/docs/welcome)
- [API reference](https://cloudchipr.github.io/api-service/)
- [Pricing](https://cloudchipr.com/pricing)
- [Sign up](https://app.cloudchipr.com/registration)
- [Support](https://cloudchipr.com/support)
- [Blog](https://cloudchipr.com/blog)
- [Terms of service](https://cloudchipr.com/terms-conditions)
- [Privacy policy](https://cloudchipr.com/privacy-policy)
- [GitHub](https://github.com/cloudchipr)

## API Evangelist rating

**Kin Score 57.7** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 57.7 |
| Contract governance | 18.2 |
| Operational transparency | 26.3 |
| Developer ergonomics | 50.6 |
| Access clarity | 85.5 |

**Agent readiness 51.7** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | verified |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 39.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/cloudchipr/](https://apis.io/providers/cloudchipr/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for CloudChipr: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/cloudchipr/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
