---
sidebar_position: 1
sidebar_label: IDP Group to Platform Roles
sidebar_custom_props:
  icon: Users
---

# IDP Group to Platform Roles

IDP Group to Platform Roles maps Microsoft Entra ID groups to QuilrAI platform roles. Members of
each selected group receive the role you assign — for example Super Admin or Viewer — and stay in
sync as Entra membership changes.

This integration is separate from **IDP to Smart Group**. It assigns platform access in
[Manage Users](../../settings-admin.md#manage-users). It does not create or change
[Smart Groups](../../smart-groups.md).

- **Category:** Manage Users
- **Integration Type:** OAuth 2.0 (uses the connected Microsoft Entra ID instance)
- **Vendor:** Microsoft

## Prerequisites

- A connected **[Microsoft Entra ID](../identity-providers/microsoft-entra-id.md)** instance with
  valid Microsoft consent. Group listing uses that instance's existing consent token.
- User Management permission to assign platform roles.
- At least one system platform role in the organization, such as Viewer, Admin, or Super Admin.

## Setup

1. Go to **Integrations** and open the **Available** tab.
2. Click **+ Add** on the **IDP Group to Platform Roles** tile.
3. Confirm Microsoft Entra ID is already connected. If more than one Entra instance exists, choose
   the **Microsoft Entra source** that should provide groups.
4. Under **IdP groups**, search and select the Entra groups to map.
5. Each newly selected group defaults to **Viewer**. Use **Change role** to pick a different
   platform role for that group before you save. Each group has exactly one role.
6. Click **Allow** to save the mappings.

Selected groups appear under **selected groups** with their assigned role. After save, those rows
show a lock and the label **Saved**. Members receive the assigned role in **5 to 6 minutes**. The
same delay applies when you change a group's role before saving, and when Entra membership later
changes.

## What This Integration Does

- Lists Entra groups from the connected Microsoft Entra ID instance.
- Maps each selected group to one **system** platform role, such as Viewer, Admin, or Super Admin.
- Provisions or updates platform users from current group members and assigns that role. The
  assignment typically appears in **5 to 6 minutes** after you save.
- Keeps membership aligned with Entra after the first save:
  - When a user is added to a mapped group, they receive the group's platform role.
  - When a user is removed from a mapped group, they are dropped from that role assignment.
- Leaves [IDP to Smart Group](../identity-providers/microsoft-entra-id.md#idp-to-smart-group)
  untouched. The two utilities store different mappings and can be used together.

## Mapping Groups And Roles

### Select groups

Search Entra groups from the **Search and select groups** field. Selecting a group adds it to the
list and assigns **Viewer** by default.

You can add more groups later. Unsaved rows can still be removed or have their role changed.

### Assign a role

Before saving, click **Change role** on a selected group and choose one **system** platform role,
such as Viewer, Admin, or Super Admin. Other selected groups keep their own roles. After you save a
group, its role cannot be changed from this screen.

Changing the role on an unsaved group, then saving, applies that role to current members in
**5 to 6 minutes**.

### Save

Saving stores the mappings on this integration instance and starts applying roles to current
members. Allow **5 to 6 minutes** for the role assignment to appear on those users. A warning on
the screen states that saving is one-way: a mapped group stays mapped and cannot be removed or
reassigned here.

## Important Behaviors

| Behavior | Detail |
|----------|--------|
| One-way save | A group that has been saved stays mapped. You can add groups later, but you cannot remove a saved group or change its role from this utility. |
| Default role | Newly selected groups default to **Viewer**. Change the role before saving if they should receive a different role. |
| System roles | You can map a group to a built-in **system** role such as Viewer, Admin, or Super Admin. |
| Apply delay | After you save a group or change its role, allow **5 to 6 minutes** for members to receive the updated platform role. Entra add and remove events use the same delay. |
| One role per group | Each Entra group maps to exactly one platform role. |
| Entra required | Groups cannot be loaded until Microsoft Entra ID is connected and consent is still valid. |
| Multiple Entra instances | If more than one Entra instance is connected, choose which instance supplies groups. The source cannot be changed after at least one mapping has been saved. |
| Membership sync | After save, add and remove events in Entra update the platform users for that group. The current members of the group receive the mapped role; a removed user is no longer included. |
| Empty or deleted groups | If a mapped Entra group has no remaining members, or the Entra group itself is deleted, that membership update is skipped. The saved mapping remains. |
| Very large groups | Groups with more than 1,000 members apply the mapped role to the first 1,000 members. |
| Not Smart Groups | This utility does not mirror groups into Smart Groups and does not change IDP-converted smart-group membership. |

## Related Platform Areas

- [Microsoft Entra ID](../identity-providers/microsoft-entra-id.md)
- [Settings And Administration — Manage Users](../../settings-admin.md#manage-users)
- [Smart Groups](../../smart-groups.md)

## Access Requirements

Configuring this integration requires Integration permissions. Assigning platform roles requires
User Management permission. Editing an existing instance requires update access.
