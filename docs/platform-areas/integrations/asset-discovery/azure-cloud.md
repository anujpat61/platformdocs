---
sidebar_position: 2
sidebar_label: Azure Cloud
sidebar_custom_props:
  icon: Boxes
---

# Azure Cloud

This connector integrates Azure AI Foundry and Azure Machine Learning Studio with Quilr, allowing secure access to AI asset information.

- **Category:** Asset Discovery
- **Integration Type:** OAuth 2.0
- **Vendor:** Microsoft

## Setup

1. Go to **Integrations** and open the **Available** tab.
2. Click **+ Add** on the **Azure Cloud** tile.
3. Sign in with a Microsoft administrator account and consent to the requested permissions.
4. Click **Allow** to authorize the connection.

## Required Scopes

| Scope Group | Permissions | Purpose |
|-------------|-------------|---------|
| Sign-in and offline access | `openid`, `profile`, `offline_access` | Identifies the Azure AD tenant and obtains a refresh token for ongoing access. |
| Azure Management API | `https://management.azure.com/user_impersonation` | Discovers subscriptions, storage accounts, and blob containers via Azure Resource Manager. |
| Azure Blob Storage (optional) | `https://storage.azure.com/user_impersonation` | Reads Azure Storage data-plane APIs when needed. |

In addition to these OAuth scopes, the consented identity needs Azure RBAC **Reader** (or equivalent) on subscriptions/storage accounts so ARM can discover accounts and list blob containers.

## What This Integration Does

- Discovers AI/ML assets in Azure.
- Monitors Azure AI Foundry workspaces.
- Tracks Machine Learning Studio resources.
- Provides AI asset inventory visibility.
