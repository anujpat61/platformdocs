---
sidebar_position: 5
sidebar_custom_props:
  icon: ShieldCheck
---

# Controls

Controls let teams operationalize policy across postures. A control describes what should happen
when a risk condition is detected and whether QuilrAI should monitor, coach, or take action.

## When To Use It

Use Controls when you want to:

- Review system and custom controls.
- Create a new control for a posture or behavior.
- Edit an existing control.
- Duplicate a control and adapt it for another use case.
- Enable or disable a control.
- Switch a control between monitor mode and action mode.

## Key Capabilities

- Browse all controls or filter by posture.
- Search controls by name.
- Filter controls by system or custom type.
- Review control name, trigger condition, criticality, behavior, status, mode, creator, and actions.
- Enable or disable controls directly from the table.
- Change control mode directly from the table.
- Create and edit controls through the control form.
- Delete controls with options for how associated findings should be handled.

## Control Modes

- **Monitor:** QuilrAI observes and records the control condition without taking the configured
  enforcement action.
- **Action:** QuilrAI applies the configured action when the control condition is met.

Controls configured to **coach** can trigger Quilly outreach in Slack and Microsoft Teams. Review
coaching outcomes in [Quilly](./quilly.md).

## Main Workflows

1. Open Controls.
2. Select All or a specific posture tab.
3. Search or filter to find the relevant control.
4. Review the trigger, behavior, criticality, status, and mode.
5. Create, edit, duplicate, enable, disable, or change mode based on the desired policy outcome.

## Related Platform Areas

- [Findings](./findings.md)
- [Detection Models](./detection-models.md)
- [Users, Applications, And Accounts](./users-accounts-applications.md)
- [Quilly](./quilly.md)
- [Settings And Administration](./settings-admin.md)

## Access Requirements

Controls require Control permissions. Create, update, and delete actions depend on the user's
assigned scopes.
