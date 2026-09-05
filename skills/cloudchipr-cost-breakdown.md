---
name: cloudchipr-cost-breakdown
description: Break down multi-cloud spend with the CloudChipr Billing Explorer API, discovering valid groupings and filters first and validating the query before running it.
api: CloudChipr Enterprise API
base_url: https://api.cloudchipr.com
operations:
  - get-resource-explorer-possible-groupings
  - get-resource-explorer-possible-filters
  - get-resource-explorer-filter-values
  - validate-billing-explorer
  - billingDataByOrganisation
generated: '2026-09-05'
method: generated
source: openapi/cloudchipr-enterprise-api-openapi.yml + conventions/cloudchipr-conventions.yml
---

# Break down CloudChipr spend

Answer "what did we spend on X, grouped by Y" without guessing a grouping or a filter value.

## Auth

Every call needs the header `x-api-key: <YOUR_CLOUDCHIPR_API_KEY>`. Keys are created in the
CloudChipr app under Settings -> API Keys. A `401` with `{"message":"Unauthorized"}` most often
means the key expired, not that it was revoked.

## Steps

1. **Discover what you may group by.**
   `GET /resource-explorer/possible-groupings` (`get-resource-explorer-possible-groupings`)
   returns the `ResourceExplorerPossibleGroupings` the organization actually supports. Do not
   hardcode a grouping name.

2. **Discover what you may filter on.**
   `GET /resource-explorer/possible-filters` (`get-resource-explorer-possible-filters`).

3. **Resolve the filter's real values.**
   `GET /resource-explorer/filters/{filterProvider}/{filterType}/values`
   (`get-resource-explorer-filter-values`), optionally narrowed with `?key=`. This is what stops a
   query failing on a service or region name that does not exist in this organization.

4. **Rehearse the query before you spend a call on it.**
   `POST /billing-explorer/validate` (`validate-billing-explorer`) with the `BillingDataRequest`
   body. **`204 No Content` means valid.** A `400` returns a free-text `message` — it carries no
   machine code, so surface it to the user rather than trying to parse it.

5. **Run it.**
   `POST /billing-explorer` (`billingDataByOrganisation`) with the same `BillingDataRequest`.
   The `BillingAggregateResponse` carries the items, the total, month-end `ForecastedCostResponse`
   and daily/monthly average details.

## Rules

- **The filter body is a tree, not query parameters.** `FilterTreeNodeRequest` composes
  `FilterGroupNodeRequest` (boolean groups) around `FilterItemNodeRequest`
  (key / operator / value). The same grammar is reused by budgets, dimensions, savings
  opportunities and live resources — learn it once.
- **There is no pagination.** No `page`, `offset`, `cursor` or `limit` parameter exists anywhere in
  this API, and no response carries a truncation flag. Narrow the date range or the filter tree
  instead of trying to page.
- **There is no rate-limit signal.** No `429` is declared on any operation and no `RateLimit-*` or
  `Retry-After` header is documented. Pace yourself conservatively; you will get no warning.
- **Reads only.** Nothing in this skill mutates anything.

## Errors

`400` bad request (free-text `message`), `401` unauthorized, `404` not found, `500` server error.
The envelope is always `{"message": "<string>"}` — **not** RFC 9457 problem+json, and `message` is
declared optional, so handle its absence. See `errors/cloudchipr-problem-types.yml`.

## MCP equivalent

The same flow is available to an agent as MCP tools on `https://mcp.cloudchipr.com/mcp`:
`get_billing_groupings`, `get_billing_filters`, `get_billing_filter_values`,
`validate_billing_query`, `get_billing_data`.
