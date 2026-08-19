---
sidebar_position: 13
sidebar_custom_props:
  icon: Settings
---

# Settings And Administration

Settings and Administration provide the tenant, policy, user, communication, gateway, extension,
endpoint, compliance, and user-interaction configuration surfaces for QuilrAI.

## When To Use It

Use Settings when administrators need to:

- Configure organizational context.
- Manage organizational policies.
- Manage platform users and access.
- Configure Browser Extension, Endpoint Agent, and AI Gateway settings.
- Customize end-user interaction content and links.
- Configure compliance service credentials.

To create, edit, or delete smart groups and manage group membership, use the dedicated
[Smart Groups](./smart-groups.md) screen.

## Main Settings Areas

- **Organizational Context:** General settings, organizational policies, profile, and manage users.
  Smart group management has moved to the dedicated [Smart Groups](./smart-groups.md) screen.
- **Browser Extension:** Deployment, deployment management, deployment status, and whitelist.
- **Endpoint:** Deployment management, deployment status, and detection configurations.
- **AI Gateway:** LLM Gateway and MCP Gateway settings.
- **User Interaction Hub:** Review user responses and customize popup content, policies, visual
  styling, and user-facing links.
- **Compliance:** Configure provider credentials used by compliance services, including OpenAI and
  Claude where enabled.

## Organizational Context

Organizational Context captures tenant-level configuration that helps QuilrAI interpret policy,
users, groups, and organizational priorities. It includes general settings, policies, profile
information, and user management where permitted. Smart group creation and membership management
have moved to the dedicated [Smart Groups](./smart-groups.md) screen.

### Manage Users

Manage Users lets administrators create, edit, and remove platform users and assign roles. In
addition to name and role editing, admins with Admin or Super Admin roles can configure LLM Gateway
app access for users assigned the AI Gateway Admin role. The **App Access** control appears inline
when creating a new user or editing an existing one, and lets the admin choose between allowing all
LLM Gateway apps or restricting access to a specific subset.

Platform roles can also be assigned from Entra groups through the
[IDP Group to Platform Roles](./integrations/manage-users/idp-group-to-platform-roles.md)
integration. You can map a group to a system role such as Viewer, Admin, or Super Admin. Members of
each mapped group receive the chosen role in 5 to 6 minutes and stay aligned as Entra membership
changes. That workflow is one-way from the integration screen: a saved group cannot be unmapped or
reassigned there. It does not affect [Smart Groups](./smart-groups.md).

The App Access control is also available directly in the users table — for AI Gateway Admin users,
a compact selector shows the current access state and can be updated without opening the full edit
panel.

### Timezone Display Preference

Administrators can select a timezone for displaying timestamps across the platform. The preference
is saved to the database and loaded on sign-in, so it persists across browsers and devices.

The timezone selector in the Display section of General Settings provides a searchable dropdown of
all available timezones.

The selected timezone applies across findings, users, applications, accounts, AI inventory, Browser Extensions, Controls, Audit Log, Exports, AI Gateway.

A hover tooltip shows the alternate time (UTC when a non-UTC timezone is active; local browser time when UTC
is selected) for any displayed timestamp.

## User Interaction Hub

User Interaction Hub lets teams customize what end users see in QuilrAI interactions.
Administrators can review user responses and configure popup content, policy links, and visual
styling that appear in user-facing prompts or justifications.

## Compliance

Compliance includes provider key setup and key management for compliance services. Current settings
include OpenAI Compliance key management and Claude-related compliance configuration where enabled.
Administrators with write access can save and revoke registered keys.

## Related Platform Areas

- [Smart Groups](./smart-groups.md)
- [IDP Group to Platform Roles](./integrations/manage-users/idp-group-to-platform-roles.md)
- [Browser Extension](./browser-extension.md)
- [Endpoint Agent](./endpoint-agent.md)
- [AI Gateway](./ai-gateway.md)
- [LLM Gateway](./llm-gateway.md)
- [Controls](./controls.md)
- [Findings](./findings.md)

## Access Requirements

Settings visibility is permission-based. Each nested settings area has its own resource requirement,
including Tenant, Organizational Policy, Smart Group, User Management, Extension, Endpoint Agent,
AI Gateway, Template, and Compliance permissions.
