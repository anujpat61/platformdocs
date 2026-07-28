---
sidebar_position: 5.5
sidebar_custom_props:
  icon: Bot
---

# Quilly

Quilly is Quilr's security coaching bot - an AI assistant that engages end users directly in
**Slack** and **Microsoft Teams**. Quilly acts as a security ally: it surfaces relevant guidance when
security issues arise, helps users understand organizational policies, and supports safe, compliant
use of company tools.

The Quilr platform also records, categorizes, and
surfaces those engagements so security teams can review what happened, who was coached, and how users
responded.

## When To Use It

Use Quilly documentation and review surfaces when you need to:

- See which security findings triggered coaching outreach to end users.
- Review proactive or policy-driven coaching that was not tied to a specific finding.
- Read conversations that end users started with Quilly on their own.
- Understand how users responded to security guidance in Slack or Teams.
- Audit coaching outcomes alongside findings, controls, and user activity.

## Interaction Types

All Quilly engagements are organized into three types. These map to the three tabs in the
**Quilly Conversations** review experience:

- **Findings:** Quilly interactions linked to a security finding. Triggered when a finding affects a
  user and Quilly reaches out to coach them on that specific issue.
- **Coach:** Agent activations that coach end users without a linked finding. Proactive or
  policy-driven coaching - for example, general policy reminders, onboarding guidance, or automated
  security nudges.
- **User Initiated:** Conversations started by the end user. Typically used when a user asks Quilly
  about a company policy, security practice, or company tool.

## Key Capabilities

- Browse Quilly engagement history by interaction type using the **Findings**, **Coach**, and
  **User Initiated** tabs.
- Filter conversations by time range, user, and finding (where applicable).
- Review interaction summaries including action name, severity, user, status, and timestamps.
- Open any interaction to read the full conversation transcript with user and assistant messages.

## Where To Review Quilly In The Platform

### Quilly Engagements

The **Quilly Engagements** drawer opens from the Users page header. It provides a global view
of Quilly engagement history across all users and interaction types. Use it when you need a
tenant-wide picture of coaching activity.

### User Lens

On the **Users** page, open a user row. The **Quilly Engagement** tab shows all Quilly
interactions for that specific user, scoped to their email address.

### Finding Cards

Findings with Quilly outreach show a **Quilly** badge on the finding card with the interaction
count. Clicking the badge opens **Quilly Engagementes** on the **Findings** tab, filtered to that
finding and user.

## Related Platform Areas

- [Findings](./findings.md)
- [Users, Applications, And Accounts](./users-accounts-applications.md)
- [Controls](./controls.md)
- [Slack](./integrations/communication-collaboration/slack.md)
- [Microsoft Teams](./integrations/communication-collaboration/microsoft-teams.md)

## Access Requirements

The **Super Admin** role is required to view Quilly engagements in the platform.

End-user coaching delivery requires configured **Slack** and/or **Microsoft Teams** integrations.
