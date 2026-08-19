---
sidebar_position: 3.5
sidebar_custom_props:
  icon: UsersRound
---

# Smart Groups

Smart Groups is a dedicated screen for managing user-defined groups across the QuilrAI platform.
Admins can create, configure, and delete smart groups, and manage group membership — all from one
centralized place.

## When To Use It

Use Smart Groups when administrators need to:

- Create a new smart group with or without initial members.
- Add one or more users to an existing smart group.
- Remove users from a smart group.
- Delete a smart group that is no longer needed.
- Manage group membership before applying smart groups to access control in MCP Gateway, LLM
  Gateway, or other platform areas.

## Smart Group Operations

### Create a Smart Group

Admins can create a smart group with a name and optionally assign users at creation time. When
users are selected during creation, they are added to the group immediately.

### Create a Smart Group Without Assigning Users

Admins can create a smart group without assigning any users at the time of creation. Users can be
added to the group later. This is useful when setting up a group structure before membership is
known, or when access control rules should be configured before users are onboarded.

### Add Users to a Smart Group

Admins can add one or more users to any existing smart group. Users are searchable by email or
name. Adding a user to a group takes effect immediately for access control evaluations in MCP
Gateway, LLM Gateway, and any other area that references the group.

### Remove Users from a Smart Group

Admins can remove individual users from any smart group. Removing a user from a group revokes any
access or rules that were applied to the group for that user.

### Delete a Smart Group

Admins can delete a smart group. Deleting a group removes it from all platform areas that reference
it, including MCP Gateway access control rules and LLM Gateway self-service access scopes. Confirm
deletion carefully — any access rules or gateway configurations that target the group will no longer
have a matching group to evaluate.

### Groups Converted from Microsoft Entra ID

Smart groups can also be created by mirroring Microsoft Entra ID groups through the
**IDP to Smart Group** utility on the Microsoft Entra ID integration. Those groups appear on the
Smart Groups screen with the label **Converted from IDP group**.

For IDP-converted groups:

- Membership is managed from the Entra integration utility, not by manually adding or removing users
  here.
- The group cannot be deleted from this screen.
- Members are matched by email; Entra members without a matching Quilr user are skipped.

See [Microsoft Entra ID — IDP to Smart Group](./integrations/identity-providers/microsoft-entra-id.md#idp-to-smart-group)
for setup steps and save behaviors.

To assign **platform roles** (for example Viewer or Super Admin) from Entra groups instead of
mirroring Smart Groups, use
[IDP Group to Platform Roles](./integrations/manage-users/idp-group-to-platform-roles.md). The two
utilities are independent.

## How Smart Groups Are Used Across the Platform

Smart groups defined here are referenced in other platform areas as an access-control and scoping
mechanism:

- **[Controls](./controls.md):** Smart groups can be used when configuring controls to include or
  exclude specific groups from enforcement. Admins can target a control at users who belong to a
  smart group, or exempt a smart group from a control entirely — giving fine-grained control over
  which findings are generated for different parts of the organization.
- **[MCP Gateway](./mcp-gateway.md):** Each MCP server's Access Control section lets admins set a
  smart group to Allow, Deny, or Default. Group & User Rules can also scope tool availability and
  guardrail overrides to a specific smart group.
- **[LLM Gateway](./llm-gateway.md):** Self-service access for LLM Gateway apps can be scoped to
  specific smart groups for viewer access, request access, API key access, and all-logs access.

## Related Platform Areas

- [Users, Applications, and Accounts](./users-accounts-applications.md)
- [Microsoft Entra ID](./integrations/identity-providers/microsoft-entra-id.md)
- [IDP Group to Platform Roles](./integrations/manage-users/idp-group-to-platform-roles.md)
- [Controls](./controls.md)
- [MCP Gateway](./mcp-gateway.md)
- [LLM Gateway](./llm-gateway.md)
- [Settings and Administration](./settings-admin.md)

## Access Requirements

Smart Groups management requires the Smart Group permission. Admins without this permission cannot
create, edit, or delete smart groups. Read-only access allows viewing group membership but not
making changes.
