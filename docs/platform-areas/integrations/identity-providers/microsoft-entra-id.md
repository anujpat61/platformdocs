---
sidebar_position: 1
sidebar_label: Microsoft Entra ID
sidebar_custom_props:
  icon: KeyRound
---

# Microsoft Entra ID

Microsoft Entra ID (formerly Azure AD) secures identities and access, enhanced by Quilr's exclusive, advanced Identity Security Checks.

- **Category:** Identity
- **Integration Type:** OAuth 2.0
- **Vendor:** Microsoft

## Setup

1. Go to **Integrations** and open the **Available** tab.
2. Click **+ Add** on the **Microsoft Entra ID** tile.
3. Sign in with a Microsoft Entra ID administrator account and consent to the requested permissions.
4. Click **Allow** to authorize the connection.

## Required Scopes

| Scope Group | Permissions | Purpose |
|-------------|-------------|---------|
| User Information | `openid`, `profile`, `offline_access`, `User.Read.All`, `User.ReadBasic.All`, `User.Read`, `Domain.Read.All` | Allows Quilr to access user details from Microsoft Entra ID to help improve your organization's security posture. |
| Enterprise Applications | `Directory.Read.All`, `Application.Read.All`, `AuditLog.Read.All`, `Reports.Read.All` | Allows Quilr to read application details, audit logs, and reports from Microsoft Entra ID to help improve your organization's security posture. |
| Devices | `DeviceManagementManagedDevices.Read.All` | Allows Quilr to read device details from Microsoft Entra ID to help improve your organization's security posture. |

## What This Integration Does

- Collects users along with their department, group, and role assignments.
- Discovers enterprise applications and their access and configuration.
- Surfaces identity security posture through Quilr's Identity Security Checks.
- Mirrors selected Entra ID groups into Quilr [Smart Groups](../../smart-groups.md) through the
  **IDP to Smart Group** utility.

## IDP to Smart Group

After Microsoft Entra ID is connected, admins can mirror Entra groups into Quilr smart groups from
the integration configure screen. Mirrored membership is matched by email. Entra members that do
not already exist as Quilr users are skipped.

### Setup

1. Go to **Integrations** and open **Connected** (or **Available** if you are still configuring the
   instance).
2. Open the **Microsoft Entra ID** integration.
3. Confirm an instance exists and Microsoft consent is still valid. The utility needs a connected
   instance to load Entra groups.
4. In the **Utilities** section, open **IDP to Smart Group**.
5. Under **Entra groups**, either:
   - Search and select individual groups, or
   - Choose **All groups** to mirror every Entra group, including groups created later.
6. Click **Save**.

Selected groups appear under **Smart groups to mirror**. After save, the mirrored groups are
available on the [Smart Groups](../../smart-groups.md) screen with the label
**Converted from IDP group**.

### Important Behaviors

| Behavior | Detail |
|----------|--------|
| One-way save | A group that has been saved stays mirrored. You can add groups later, but you cannot remove a saved mirrored group from this utility. |
| All groups | When **All groups** is saved, every current and future Entra group is mirrored. The selection cannot be narrowed from the utility afterward. |
| Membership matching | Members are matched by email. Emails with no matching Quilr user are skipped. |
| Name conflicts | An Entra group cannot be selected if a Quilr smart group with the same display name already exists. Rename the existing smart group first, or choose a different Entra group. |
| Membership management | Membership for IDP-converted groups is managed through this utility, not by manually adding or removing users on the Smart Groups screen. |
| Deletion | Groups converted from IDP cannot be deleted from the Smart Groups screen. |

### Related Platform Areas

- [Smart Groups](../../smart-groups.md)
- [Controls](../../controls.md)
- [MCP Gateway](../../mcp-gateway.md)
- [LLM Gateway](../../llm-gateway.md)
