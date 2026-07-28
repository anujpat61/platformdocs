---
sidebar_position: 3
sidebar_custom_props:
  icon: Users
---

# Users, Applications, And Accounts

Users, Applications, and Accounts provide entity-level visibility into AI activity. These pages help
teams understand who is using AI, which applications are in use, which accounts are active, and where
risk or policy exposure appears.

## When To Use Them

Use these views when you need to investigate activity from an entity perspective:

- A user is associated with risky AI behavior.
- An application has unusual adoption, sensitive prompts, or open findings.
- An account has high interaction volume, blocked interactions, or sensitive activity.
- A finding, insight, or asset needs more business context.

## Users

The Users page summarizes AI usage by user and department. It includes KPI summaries, top trending
users, a searchable table, and conversation-level drilldowns.

Common use cases:

- Identify AI users and non-AI users.
- Review privileged users using AI.
- Find users associated with sensitive uploads or coaching events.
- Open user conversations for deeper review.
- Review Quilly coaching interactions for a specific user from the **Quilly** tab in User Lens.
  See [Quilly](./quilly.md) for details on interaction types and review workflows.

The Smart Groups drawer previously available on the Users page has been removed. Smart group
creation and membership management are now handled from the dedicated
[Smart Groups](./smart-groups.md) screen.

## Applications

The Applications page is the main app-management and app-intelligence surface. It includes an
inventory view, a source view, KPI filters, trending apps, and app drilldowns. The default time
range is 7 days.

Common use cases:

- Review all observed AI and non-AI applications.
- Understand where an app was seen, including SaaS, browser, endpoint, or gateway sources.
- Inspect app intelligence, posture, usage, exposure, findings, and visitors.
- Review LLM Gateway app activity through the gateway-specific drilldown.
- Review endpoint or desktop app activity through the endpoint-source drilldown.
- Update app classifications or approval-related settings when permitted.
- Export application data as CSV using the **Export** button in the table toolbar.

Inline editable fields in the application table (such as category, risk level, or approval status)
show a "Saving…" label and spinner while a change is being saved, confirming that the edit has
been submitted.

The AI lens and Generative AI category filter target the primary app category. When the page is
reached via an insight or widget drilldown that pre-applies a business-category filter, the
Category chip shows "Business" to reflect the narrower scope applied by the drilldown.

### Exporting Application Data

The **Export** button in the Applications table toolbar opens an export modal that lets admins
download application records as CSV.

- **Data Scope** controls what is exported when no rows are selected: **Current filter** includes
  only records matching the active search and filters; **Full range** exports all records without
  applying filters.
- When one or more rows are selected in the table, the button shows the selection count and the
  export is limited to those rows. The scope selector is not shown in selection mode.
- Active filters and a maximum row limit are displayed in the modal before the export starts.
- Exports are queued in the background and a notification is sent when the file is ready.
  Completed exports appear in export history labeled **Applications**.

This feature is currently in Beta.

## Accounts

The Accounts page focuses on app accounts and account-level interaction data.

Common use cases:

- Review total and newly observed accounts.
- Track sensitive, blocked, and cleaned interactions.
- Identify account status, account type, app status, and login method.
- Open account conversations and related app context.
- Trigger account-related workflows when permissions allow.

## Main Workflows

1. Start from Insights, Findings, or direct navigation.
2. Use search, filters, and KPI shortcuts to narrow the table.
3. Open a row to inspect user, app, or account context.
4. Follow links into Findings, related users, related accounts, or app intelligence.
5. Apply controls, update app posture, or start user/account workflows as needed.

## Related Platform Areas

- [Insights](./insights.md)
- [Findings](./findings.md)
- [Smart Groups](./smart-groups.md)
- [AI Inventory](./ai-inventory.md)
- [Controls](./controls.md)
- [Quilly](./quilly.md)
- [Audit Log And Exports](./audit-log-and-exports.md)

## Access Requirements

Users and Accounts use AI usage permissions. Applications use app-management permissions, with
separate scopes for updates, allow/block operations, and agent-triggered actions.
