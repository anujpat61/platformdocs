---
sidebar_position: 1
sidebar_label: Generate Export Key
sidebar_custom_props:
  icon: KeyRound
---

# Generate Export Key

Generate static API keys so external systems — Databricks, data warehouses, or custom pipelines —
can pull findings data programmatically without a login session.

- **Category:** Findings Export
- **Integration Type:** API Key

## Setup

1. Go to **Integrations** and open the **Available** or **Connected** tab.
2. Click **+ Add** on the **Findings Export** tile (or open it from Connected if keys already
   exist).
3. Click **Generate New Key** (or **Generate your first key** when none exist yet).
4. In **Generate export API key**:
   - Enter a **Label** so you can recognize the key later (for example,
     `Databricks Production Pipeline`).
   - Choose an **Expires At** option.
5. Click **Generate Key**.
6. Copy the full key immediately from **Export API key created**, then store it in a secret manager.
   This is the only time the full key is shown.

When at least one active key exists, Findings Export appears as a Connected integration card. When
all keys are revoked, that Connected entry is removed.

## Expiry Options

| Option | Behavior |
|--------|----------|
| Never expires | Key remains active until it is manually revoked. |
| 24 hours | Key stops working after 24 hours. |
| 7 days | Key stops working after 7 days. |
| 30 days | Key stops working after 30 days. |
| 90 days | Default. Key stops working after 90 days. |
| 1 year | Key stops working after 1 year. |
| Custom date & time | Key stops working at the selected date and time. |

## Manage Keys

The Findings Export screen lists keys with:

- Label
- Status: **Active**, **Expired**, or **Revoked**
- Masked key prefix
- Created date
- Expiry (`Never expires` when no expiry was set)

Stats at the top of the page show total, active, and revoked key counts.

### Revoke a Key

1. Open Findings Export from **Integrations**.
2. Hover the key row and click **Revoke**.
3. Confirm **Revoke this API key?**

Revocation takes effect immediately. Any integration using that key loses access. Revoked keys
remain visible in the list with status **Revoked**; they cannot be reactivated — generate a new key
instead.

:::warning
The full key is shown only once at creation. Quilr stores only a hash and a short prefix for
display. If a key is lost, revoke it and generate a replacement.
:::

## Use the Key

Pass the raw key in the `X-Api-Key` header when calling the findings table endpoint. Tenant and
subscriber headers are not required for this auth method — they are resolved from the key record.

**Endpoint**

```
POST https://<base-url>/bff/quilr-query-builder/findings/table/data
Content-Type: application/json
X-Api-Key: <your-export-api-key>
```

**Example request body**

```json
{
  "filters": {},
  "limit": 100,
  "offset": 0
}
```

### cURL

```bash
curl --location --request POST \
  'https://<base-url>/bff/quilr-query-builder/findings/table/data' \
  --header 'Content-Type: application/json' \
  --header 'X-Api-Key: <your-export-api-key>' \
  --data '{
    "filters": {},
    "limit": 100,
    "offset": 0
  }'
```

## Troubleshooting

| Issue | Resolution |
|-------|------------|
| Full key no longer visible | Expected. Keys cannot be recovered. Revoke the old key and generate a new one. |
| HTTP 401 / unauthorized | Key may be revoked or expired. Check status in Integrations and generate a replacement if needed. |
| Findings Export missing from Connected | Connected appears after the first active key is created. Revoking all keys removes the Connected card. |
| Cannot create a key | Confirm you have Integrations access and an active Quilr session. |

## Access Requirements

Managing Findings Export API keys requires Integrations access. Using a generated key does not
require an interactive Quilr login session.
