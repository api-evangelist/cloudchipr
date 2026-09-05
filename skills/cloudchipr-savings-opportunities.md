---
name: cloudchipr-savings-opportunities
description: Find and triage multi-cloud cost-saving opportunities with the CloudChipr Enterprise API, joining each recommendation back to the account and live resource it targets.
api: CloudChipr Enterprise API
base_url: https://api.cloudchipr.com
operations:
  - get-accounts
  - filterSavingsOpportunities
  - lookupResource
  - get-accounts-accountId
generated: '2026-09-05'
method: generated
source: openapi/cloudchipr-enterprise-api-openapi.yml + data-model/cloudchipr-data-model.yml
---

# Triage CloudChipr savings opportunities

Turn "where can we save money" into a ranked, resource-level list.

## Auth

`x-api-key: <YOUR_CLOUDCHIPR_API_KEY>` on every request.

## Steps

1. **List the connected accounts.**
   `GET /accounts` (`get-accounts`), optionally narrowed by `statuses`, `provider` or
   `access_type`. Each `Account` already carries `estimated_monthly_savings`,
   `total_monthly_saved_costs` and `total_costs`, so this single call ranks accounts by waste
   before you fetch a single recommendation.

2. **Fetch the opportunities.**
   `POST /savings-opportunities` (`filterSavingsOpportunities`) with a
   `SavingsOpportunityFilteredRequest`. Each `SavingsOpportunityResponse` carries `action_type`
   (terminate / rightsize / stop), `implementation_effort`, `recommended_type`, `based_on_past`
   (the observation window in days) and its `OpportunityDimension` list.

3. **Join back to the resource.**
   `GET /resources/lookup?resource_id=...` (`lookupResource`), optionally with `resource_type` and
   `account_id`. **Note the identifier mismatch:** `SavingsOpportunityResponse.resource_id` is the
   *cloud provider's* identifier (e.g. `i-0a5ff…`), not CloudChipr's `ResourceDetails.id` uuid.
   Pass it as `resource_id`.

4. **Check the account can act.**
   `GET /accounts/{accountId}` (`get-accounts-accountId`) returns the account's `access_type` and
   any missing permissions. A read-only connection cannot execute the recommended action even
   though the recommendation is valid.

## Rules

- **This API cannot execute a recommendation.** There is no stop / terminate / rightsize operation
  in the 26-operation contract. Remediation happens in the CloudChipr app (Workflows, Off Hours,
  Resource Actions) or in the customer's own cloud. Report the recommendation; do not claim to have
  applied it.
- **`policy_id` and `recommendation_id` are dangling references** — no operation resolves them.
  Pass them through to a human, do not try to dereference them.
- **No pagination.** The response is an unbounded array. Filter server-side rather than expecting
  to page.

## Errors

`{"message": "<string>"}` on 400 / 401 / 404 / 500. Not RFC 9457. See
`errors/cloudchipr-problem-types.yml`.

## MCP equivalent

`get_cloud_accounts`, `get_cloud_account`, `filter_opportunities`, `get_opportunity`,
`get_savings_summary` on `https://mcp.cloudchipr.com/mcp`. The MCP surface is *richer* here: the
organization-wide `get_savings_summary`, per-resource `get_opportunity` and the saved
opportunity views have **no** REST equivalent — see `mcp/cloudchipr-tool-crosswalk.yml`.
