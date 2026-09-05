---
name: cloudchipr-custom-cost-ingestion
description: Create a CloudChipr custom data source and stream NDJSON cost or telemetry rows into it — the one write flow in the API with replay protection, and the one with no undo.
api: CloudChipr Enterprise API
base_url: https://api.cloudchipr.com
operations:
  - listCustomSources
  - listTelemetries
  - createDataSource
  - ingestCustomData
generated: '2026-09-05'
method: generated
source: openapi/cloudchipr-enterprise-api-openapi.yml + conventions/cloudchipr-conventions.yml
---

# Ingest custom cost data into CloudChipr

Bring a cost or usage stream CloudChipr does not natively integrate into Billing Explorer.

## Auth

`x-api-key: <YOUR_CLOUDCHIPR_API_KEY>`.

> The API Keys documentation describes keys as **read-only**, yet this flow writes. The
> contradiction is CloudChipr's, and it is unresolved — see `scopes/cloudchipr-scopes.yml`.
> Confirm your key can write before building on this flow.

## Steps

1. **Check what already exists — this is not optional.**
   `GET /custom-sources` (`listCustomSources`) and `GET /telemetry` (`listTelemetries`).
   **There is no delete operation for a data source.** If you create a duplicate you cannot remove
   it over the API. Look before you create.

2. **Create the destination.**
   `POST /data-sources` (`createDataSource`) with a `CreateDataSourceRequest` declaring the column
   set (`DataSourceColumnRequest`). Returns `201` and a `CreateDataSourceResponse` containing the
   `id` and an `ingest_url`.
   **This operation has no idempotency key.** If it times out, do *not* blind-retry — re-run step 1
   and match by name first.

3. **Ingest rows.**
   `POST /ingest/{destinationId}` (`ingestCustomData`).
   - `Content-Type: application/x-ndjson` — one JSON object per line.
   - `Idempotency-Key: <uuid>` — **required**, not optional. This is the only replay-protected
     operation in the entire API. Generate one uuid per batch and reuse it verbatim on any retry
     of that same batch.
   - A `date` field must be `yyyy-MM-dd`.
   - `200` returns `{"processed_rows": <int>}`.

## Rules

- **Nothing here is reversible.** There is no delete, purge, rollback or restore operation for a
  data source or for ingested rows. The idempotency key stops you writing the batch *twice*; it
  does not let you take the batch *back*. Validate your rows before you send them.
- **Retention and conflict behaviour for the idempotency key are undocumented.** CloudChipr does
  not state how long a key is remembered or what happens if you replay a key with a different body.
  Treat a key as single-use per batch.
- **Per-line errors are the one place this API returns machine codes.** A `400` from ingest may
  carry `errors[]` keyed on `ErrorCode`: `MISSING_MANDATORY_FIELD`, `INVALID_COLUMN_FORMAT`,
  `INVALID_JSON`. Everywhere else you get free text.

## Errors

Ingest `400`: `oneOf` a structured `{errors:[…]}` array or `{message: string}`.
Everything else: `{"message": "<string>"}`. See `errors/cloudchipr-problem-types.yml`.

## MCP equivalent

**None.** The MCP server is read-only ("Write Actions — coming soon"). `get_custom_sources` lists
sources; nothing on the MCP surface creates or ingests. This flow is REST-only.
