---
sidebar_position: 1
sidebar_label: Findings API
sidebar_custom_props:
  icon: SearchCode
---

# Findings API

The Findings API provides programmatic access to finding details from the QuilrAI platform. Use it
to automate finding retrieval, integrate with SIEMs, build reporting pipelines, or perform
scheduled security posture queries — without manual UI interaction.

The API is language-agnostic and works with any scripting or programming language that supports
HTTP requests. This guide includes ready-to-use examples in **PowerShell** and **Python**.

## Prerequisites

| Requirement | Details |
|---|---|
| QuilrAI tenant access | Active user account with valid credentials |
| Scripting environment | PowerShell 5.1+ or Python 3.6+ (or any HTTP-capable tool) |
| Python library | `requests` — install via `pip install requests` |
| Network access | HTTPS connectivity to your QuilrAI platform URL |
| Subscriber ID | Your organization's subscriber identifier (UUID) |
| Tenant ID | Your assigned tenant identifier (UUID) |
| User role | Role with permission to access findings |
| API credentials | Dedicated service account email and password |

:::info
API credentials (email and password) are created exclusively by the QuilrAI team. To obtain your
API credentials, Subscriber ID, and Tenant ID, contact the QuilrAI support team.
:::

## Platform URLs

Use the base URL that matches your region and deployment environment:

| Region | Environment | Base URL |
|---|---|---|
| India | POC | `https://platform.quilr.ai` |
| India | Production | `https://platform.quilrai.com` |
| US | POC | `https://app.quilr.ai` |
| US | Production | `https://app.quilrai.com` |

Replace `<base-url>` in all examples below with the appropriate domain for your environment.

## API Workflow

The integration follows a two-step workflow:

```
┌─────────────────────┐     ┌────────────────────────┐     ┌──────────────────┐
│  1. Authenticate    │────▶│  2. Extract JWT Token  │────▶│  3. Query        │
│  POST /auth/login   │     │  from response/cookie  │     │  Findings API    │
└─────────────────────┘     └────────────────────────┘     └──────────────────┘
```

| Step | Endpoint | Method | Purpose |
|---|---|---|---|
| Authenticate | `/bff/auth/auth/login` | POST | Obtain JWT session token |
| Get Findings | `/bff/quilr-query-builder/findings/table/data` | POST | Retrieve finding records |

## Step 1 — Authenticate

Send your credentials to the login endpoint to receive a JWT token stored in the
`quilr_web_auth` session cookie.

**Endpoint**

```
POST https://<base-url>/bff/auth/auth/login
Content-Type: application/json
```

**Request body**

```json
{
  "email": "<your-email>",
  "password": "<your-password>"
}
```

:::info
The JWT token has a limited lifespan (typically **4 hours**). Generate a new token before it
expires to maintain uninterrupted API access.
:::

### PowerShell

```powershell
# Create a web session
$session = New-Object Microsoft.PowerShell.Commands.WebRequestSession
$session.UserAgent = "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"

# Send login request
$loginResponse = Invoke-WebRequest -UseBasicParsing `
  -Uri "https://<base-url>/bff/auth/auth/login" `
  -Method "POST" `
  -WebSession $session `
  -Headers @{
    "Accept"          = "application/json, text/plain, */*"
    "Origin"          = "https://<base-url>"
    "Referer"         = "https://<base-url>/en/internal-login"
    "Sec-Fetch-Dest"  = "empty"
    "Sec-Fetch-Mode"  = "cors"
    "Sec-Fetch-Site"  = "same-origin"
  } `
  -ContentType "application/json" `
  -Body '{"email":"<your-email>","password":"<your-password>"}'

# Extract JWT token from quilr_web_auth cookie
$authCookie = $session.Cookies.GetCookies("https://<base-url>") |
  Where-Object { $_.Name -eq "quilr_web_auth" }
$decoded   = [System.Web.HttpUtility]::UrlDecode($authCookie.Value)
$authData  = $decoded | ConvertFrom-Json
$token     = $authData.token

Write-Host "Token acquired successfully"
```

### Python

```python
import requests
import json
import urllib.parse

# Create a session
session = requests.Session()
session.headers.update({
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)",
    "Accept":     "application/json, text/plain, */*",
    "Origin":     "https://<base-url>",
    "Referer":    "https://<base-url>/en/internal-login",
})

# Send login request
login_url   = "https://<base-url>/bff/auth/auth/login"
credentials = {"email": "<your-email>", "password": "<your-password>"}
login_response = session.post(login_url, json=credentials)
login_response.raise_for_status()

# Extract JWT token from quilr_web_auth cookie
auth_cookie = session.cookies.get("quilr_web_auth", domain="<base-url>")
decoded     = urllib.parse.unquote(auth_cookie)
auth_data   = json.loads(decoded)
token       = auth_data["token"]

print("Token acquired successfully")
```

## Step 2 — Retrieve Findings

Use the JWT token from Step 1 to query the findings endpoint.

**Endpoint**

```
POST https://<base-url>/bff/quilr-query-builder/findings/table/data
Content-Type: application/json
```

**Required headers**

| Header | Description | Example |
|---|---|---|
| `Authorization` | Bearer token from login | `Bearer eyJhbG...` |
| `subscriberid` | Organization subscriber UUID | `a1b2c3d4-e5f6-7890-abcd-ef1234567890` |
| `tenant` | Tenant UUID | `f9e8d7c6-b5a4-3210-fedc-ba0987654321` |
| `Content-Type` | Request content type | `application/json` |

**Request body parameters**

| Parameter | Type | Description |
|---|---|---|
| `filters` | Object | Filter criteria for narrowing results. Empty `{}` returns all findings. |
| `limit` | Integer | Maximum records to return per request (default: `10`) |
| `offset` | Integer | Number of records to skip for pagination (default: `0`) |

### PowerShell

```powershell
$headers = @{
  "Accept"         = "application/json, text/plain, */*"
  "Authorization"  = "Bearer $token"
  "Origin"         = "https://<base-url>"
  "Referer"        = "https://<base-url>/en/findings"
  "Sec-Fetch-Dest" = "empty"
  "Sec-Fetch-Mode" = "cors"
  "Sec-Fetch-Site" = "same-origin"
  "subscriberid"   = "<your-subscriber-id>"
  "tenant"         = "<your-tenant-id>"
}

$body = '{"filters":{},"limit":10,"offset":0}'

$findingsResponse = Invoke-WebRequest -UseBasicParsing `
  -Uri "https://<base-url>/bff/quilr-query-builder/findings/table/data" `
  -Method "POST" `
  -WebSession $session `
  -Headers $headers `
  -ContentType "application/json" `
  -Body $body

$findings = ($findingsResponse.Content | ConvertFrom-Json)
$findings.data | Format-Table
Write-Host "Total findings returned: $($findings.data.Count)"
```

### Python

```python
headers = {
    "Accept":        "application/json, text/plain, */*",
    "Authorization": f"Bearer {token}",
    "Origin":        "https://<base-url>",
    "Referer":       "https://<base-url>/en/findings",
    "subscriberid":  "<your-subscriber-id>",
    "tenant":        "<your-tenant-id>",
}
body = {"filters": {}, "limit": 10, "offset": 0}

findings_url      = "https://<base-url>/bff/quilr-query-builder/findings/table/data"
findings_response = session.post(findings_url, json=body, headers=headers)
findings_response.raise_for_status()

findings = findings_response.json()
for finding in findings.get("data", []):
    print(finding)

print(f"Total findings returned: {len(findings.get('data', []))}")
```

## Pagination

Adjust `limit` and `offset` to page through large result sets. For example, set `offset` to `10`
on the second request to fetch records 11–20.

### Python — paginate all findings

```python
all_findings = []
offset = 0
limit  = 50

while True:
    body = {"filters": {}, "limit": limit, "offset": offset}
    resp = session.post(findings_url, json=body, headers=headers)
    data = resp.json().get("data", [])
    if not data:
        break
    all_findings.extend(data)
    offset += limit

print(f"Total findings collected: {len(all_findings)}")
```

### PowerShell — paginate all findings

```powershell
$allFindings = @()
$offset = 0
$limit  = 50

do {
    $body = '{"filters":{},"limit":' + $limit + ',"offset":' + $offset + '}'
    $resp = Invoke-WebRequest -UseBasicParsing `
      -Uri "https://<base-url>/bff/quilr-query-builder/findings/table/data" `
      -Method "POST" -WebSession $session -Headers $headers `
      -ContentType "application/json" -Body $body
    $data        = ($resp.Content | ConvertFrom-Json).data
    $allFindings += $data
    $offset      += $limit
} while ($data.Count -eq $limit)

Write-Host "Total findings collected: $($allFindings.Count)"
```

## Validation and Testing

After setting up the integration, verify it is working correctly:

1. Run the authentication script and confirm an HTTP **200** response.
2. Check that the JWT token is present in the `quilr_web_auth` cookie after login.
3. Execute the findings request and confirm a **200 OK** status.
4. Inspect the response body to confirm finding records appear in the expected JSON structure.
5. Test pagination by adjusting `limit` and `offset` to confirm all records are accessible.

### Quick validation — PowerShell

```powershell
Write-Host "Login Status:        $($loginResponse.StatusCode)"
Write-Host "Findings Status:     $($findingsResponse.StatusCode)"
Write-Host "Records returned:    $($findings.data.Count)"
```

### Quick validation — Python

```python
print(f"Login Status:     {login_response.status_code}")
print(f"Findings Status:  {findings_response.status_code}")
print(f"Records returned: {len(findings.get('data', []))}")
```

## Troubleshooting

| Issue | Resolution |
|---|---|
| HTTP 401 on login | Verify email and password are correct. Check that the account is active in QuilrAI. |
| HTTP 401 on findings request | Token may have expired. Re-run the authentication script to obtain a fresh JWT. |
| HTTP 403 Forbidden | User role does not have permission to access findings. Contact your QuilrAI administrator. |
| Empty response / no findings | Confirm the Subscriber ID and Tenant ID are correct. Remove or adjust filters. |
| Connection timeout | Verify network / firewall allows HTTPS traffic to your QuilrAI platform URL. |
| PowerShell TLS error | Run `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12` before requests. |
| Python SSL error | Upgrade the requests library: `pip install --upgrade requests certifi` |
| JSON parse error | Ensure response `Content-Type` is `application/json`. Check for HTML error pages in the response body. |

## Summary

| Step | Action | Endpoint / Detail |
|---|---|---|
| 1 | Create HTTP session | Language-specific session or client object |
| 2 | Authenticate with credentials | `POST /bff/auth/auth/login` |
| 3 | Extract JWT from response cookie | Parse `quilr_web_auth` cookie value |
| 4 | Configure findings request headers | Set `Authorization`, `subscriberid`, `tenant` |
| 5 | Send findings POST request | `POST /bff/quilr-query-builder/findings/table/data` |
| 6 | Parse and process JSON response | Language-specific JSON parsing |

:::tip
The QuilrAI Findings API is language-agnostic. While this guide provides PowerShell and Python
examples, the same calls can be made from any tool that supports HTTP requests — cURL, Node.js,
Java, Go, C#, and others.
:::
