---
name: cloudchipr-budget-monitoring
description: Read CloudChipr budgets, their thresholds and their period-by-period history to report whether spend is tracking to plan.
api: CloudChipr Enterprise API
base_url: https://api.cloudchipr.com
operations:
  - listBudgets
  - getBudget
  - getBudgetHistory
generated: '2026-09-05'
method: generated
source: openapi/cloudchipr-enterprise-api-openapi.yml + data-model/cloudchipr-data-model.yml
---

# Report on CloudChipr budgets

## Auth

`x-api-key: <YOUR_CLOUDCHIPR_API_KEY>`.

## Steps

1. **List budgets.** `GET /budgets` (`listBudgets`). Each `Budget` carries `amount`,
   `planned_amounts`, `actual_to_date`, `forecast`, `progress`, `start_date`, `end_date` and
   `is_expired` — enough to report status without a second call.
2. **Open one.** `GET /budgets/{budgetId}` (`getBudget`) for its `thresholds`
   (`BudgetThreshold[]`) and its `filter_tree` — the `FilterTreeResponse` that defines what spend
   the budget actually covers.
3. **Trend it.** `GET /budgets/{budgetId}/history` (`getBudgetHistory`) returns
   `BudgetHistoryEntry[]`, one per period.

## Rules

- **Read-only.** There is no create, update or delete operation for budgets in this API. Budgets
  are managed in the app.
- **Always read `filter_tree` before interpreting a number.** Two budgets with the same amount can
  cover completely different slices of spend. Reporting "over budget" without saying what the
  budget covers is misleading.
- **Check `is_expired`** before alarming on an expired budget's `progress`.
- `405 Method Not Allowed` is declared on these operations — it means the wrong verb, not a
  permission problem.

## Errors

`{"message": "<string>"}` on 400 / 401 / 404 / 405 / 500. See
`errors/cloudchipr-problem-types.yml`.

## MCP equivalent

**None.** Budgets are not exposed as MCP tools — see `mcp/cloudchipr-tool-crosswalk.yml`
(`rest_only`).
