---
title: Release Notes
slug: /release-notes
sidebar_custom_props:
  icon: Newspaper
hide_copy_dropdown: true
---

# Release Notes

## July 16, 2026

### New

- [Quilly](/platform-areas/quilly): Quilr's security
  coaching bot in Slack and Microsoft Teams. The guide covers interaction types (Findings, Coach,
  and User Initiated), where to review conversations in the platform, and main review workflows.

## June 26, 2026

### New

- [Smart Groups](/platform-areas/smart-groups): Added a dedicated **Smart Groups** screen for
  centralized smart group lifecycle management. Admins can create a smart group and assign users at
  creation time, create a smart group without assigning users initially, add users to any existing
  smart group, remove users from any smart group, and delete a smart group. All smart group
  operations are now available from one screen rather than being split across Settings and the
  Users page.

### Improved

- [Settings and Administration](/platform-areas/settings-admin): Smart group management has been
  removed from Settings. The Smart Groups section previously available under Organizational Context
  in Settings has been deprecated; all create, update, and delete operations are now centralized in
  the dedicated Smart Groups screen.

- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): The Smart
  Groups drawer on the Users screen has been removed. Smart group membership management is now
  available from the dedicated Smart Groups screen.

## June 25, 2026

### Fixed

- [Insights](/platform-areas/insights): Fixed the selected time range not being applied to the
  Users table when navigating from an AI Insights chart. Clicking a data point and drilling into
  Users now correctly scopes the table to the same period shown in Insights. Previously the Users
  table loaded without the time range, showing unfiltered results.

- [Insights](/platform-areas/insights): Fixed an overflow issue in the **Top AI Apps** chart when
  more than five applications are listed. The chart body is now scrollable within the card, so all
  entries remain accessible without the content breaking out of the chart container.

- [Insights](/platform-areas/insights): Fixed the AI Insights page crashing when the
  **Usage by Department** chart or **AI Adoption Trend** chart received a large or empty dataset.
  Charts now handle edge-case data sizes without breaking the page layout.

### New

- [LLM Gateway](/platform-areas/llm-gateway): Added an **Agent Monitoring** panel to LLM Gateway
  logs. When an LLM Gateway app has requests that carry agent observability metadata, a new panel
  appears in the logs view showing coverage stats — requests with observability, distinct agent
  runs, distinct agents, and risk events — alongside average and P95 latency. A breakdown panel
  organizes traffic by Agents, Workflows, Workflow Runs, Frameworks, Apps, Models, Providers, and
  Users. A paginated **Runs** table lists agent runs with sort options: newest first, oldest first,
  most risky, most tokens, and most errors. Admins can filter both the monitoring panel and Recent
  Logs using agent-specific filters: agent name, agent ID, framework, version, run ID, workflow ID,
  workflow run ID, trace ID, and conversation ID. The panel appears automatically when observability
  data is present or an agent filter is active; no additional configuration is required.

- [LLM Gateway](/platform-areas/llm-gateway): Added an **Agent** tab to the LLM Gateway log
  details drawer for requests that include agent observability metadata. The tab shows the agent
  name, ID, run ID, framework, version, thread ID, span ID, parent span ID, step name, and step
  type; workflow ID and workflow run ID; and correlation identifiers including trace ID,
  conversation ID, external request ID, correlation ID, and session ID. Baggage, request metadata,
  and gateway-level correlation fields are also displayed when present.

- [LLM Gateway](/platform-areas/llm-gateway): Added **Provider Status** to LLM Gateway. A
  **Provider Status** button on each LLM Gateway app card opens a view showing the health of each
  provider credential configured or observed for that app. A **Provider Status** button on the
  LLM Gateway apps list page opens a cross-app view across all apps. Each credential shows a status
  badge — **Healthy**, **Degraded**, **Failing**, **No traffic**, **Disabled**, or **Not
  configured** — along with request count, failure rate, error rate, input tokens, output tokens,
  P95 latency, and latency normalized by input-token volume. Top HTTP status codes, top error
  messages, and top models by request count are shown inline for each credential. Admins can
  restrict the health window using From and To datetime pickers and refresh on demand.

### Improved

- [LLM Gateway](/platform-areas/llm-gateway): LLM Gateway log rows now display an **Agent** badge
  when a request carries agent observability metadata. The badge shows the agent name, framework,
  and workflow context when available. Agent fields are also included in the log row text search so
  admins can find agent-linked requests by name, framework, or trace ID.

### Fixed

- [MCP Gateway](/platform-areas/mcp-gateway): The MCP Gateway user dashboard URL and OAuth
  callback URL shown in the admin UI are now fetched from the API. Both values are hidden until the
  API response is available, ensuring that the correct gateway endpoint is displayed rather than a
  value derived from the page URL or deployment environment.

- [LLM Gateway](/platform-areas/llm-gateway): Added an **Alerts** tab to each LLM Gateway app
  settings drawer. Admins can configure failure-rate alerting at two independently-enableable
  levels: an **App-level alert** that tracks the failure rate across all providers combined, and a
  **Per-provider alert** that evaluates each provider label separately and fires on any label that
  breaches the threshold. Each alert type has its own analysis window (5 minutes minimum, 24 hours
  maximum), failure-rate threshold (0–100 %), minimum-request floor to suppress low-volume noise,
  cooldown period to suppress repeat alerts during a sustained breach, and an optional **Notify on
  recovery** setting that sends a follow-up when the failure rate drops back below the threshold.
  Notification channels — Slack webhooks, generic webhooks, and email addresses — are shared across
  both alert types. Webhook URLs are encrypted at rest. At least one channel must be configured
  when an alert type is enabled; the drawer validates this on save and redirects to the Alerts tab
  automatically if there is an error.

### Improved

- [LLM Gateway](/platform-areas/llm-gateway): LLM Gateway app cards now display a **Created by**
  field showing the name of the admin who created the app. The creator name is captured
  automatically at creation time (preferring full name, falling back to username then email). Apps
  created before this change show **N/A**. The creation-time label on each card was also renamed
  from **Created** to **Created at** for clarity. A new **Created By** filter dropdown is available
  on the app list, letting admins narrow apps by creator. Active creator filters appear as removable
  pills and are cleared by **Clear all filters**.

## June 15, 2026

- [Audit Log and Exports](/platform-areas/audit-log-and-exports): Findings and Audit Log export
  modals now display an inline row limit hint showing the maximum number of rows that will be
  included in the export. The limit is tenant-configured and defaults to 5,000 rows when no custom
  configuration is set. Admins see the limit before confirming an export, so unexpectedly truncated
  downloads are less likely.

## June 23, 2026

### Improved

- [AI Inventory](/platform-areas/ai-inventory): Added two new top-level tabs to the OpenAI
  Compliance view. **Governance** organizes compliance risk data across three sub-tabs:
  **Token Governance** shows total token consumption, input/output/cached composition,
  cache-efficiency ratio, token field coverage, a daily consumption trend, and consumption
  rankings by user, model, source, and client. **Sharing Blast Radius** surfaces ChatGPT sharing
  activity — conversation shares, GPT access grants, and scope-change signals — with risk
  highlights and a paginated event log. **Egress** shows network egress data for the selected
  period. **Security** organizes OpenAI admin-layer events across seven sub-tabs: **Audit Log**,
  **Logins**, **Denied** (blocked and failed events), **Sessions**, **Admin Access**, **Anomalies**,
  and **Egress**. Each event sub-tab includes a posture header with key stats, an action or outcome
  composition bar, a filterable event table with per-row user and geographic context, and a
  country-based signal callout.

- [AI Inventory](/platform-areas/ai-inventory): Expanded the **Assets** tab in the OpenAI
  Compliance view with new products and asset tabs. **ChatGPT** gains four additional tabs:
  **GPT Inventory** lists stateful GPTs with visibility, sharing, capabilities, knowledge files,
  and external actions, plus a full detail drawer with configuration sections and top-user lists;
  **Knowledge Files** shows files linked to GPTs with link count, GPT count, and owner list;
  **Conversation Files** lists files shared in conversations with appearance, conversation, message,
  and user counts; **Users** shows per-user message, conversation, file, and DLP activity with a
  360 detail view. **Codex** adds **Tasks** and **Environments** asset tabs alongside Sessions.
  **Spreadsheets** is a new product covering Microsoft Excel add-in sessions with event counts,
  content events, model usage, and token totals. **Agents** gains a **Skills** tab showing
  workspace skills with creator, file count, agent cross-references, and skill name chips that
  link directly from conversation and agent run views. **Apps** is a new product showing OpenAI
  app activity, auth events, returned resources, and per-app user reach.

## June 22, 2026

### New

- [Endpoint Agent](/platform-areas/endpoint-agent): Added an **Access Control** section to the
  Guardrails tab in Endpoint Detection Configurations. Admins can enable or disable each supported
  access-control feature for a configuration and supply the required parameters — including text,
  masked secret, numeric, toggle, and dropdown fields — directly within the drawer. The section
  appears only when at least one access-control feature is supported for the configuration; it is
  hidden automatically when no features apply. Required parameter values are validated inline, and
  a validation error blocks saving until the value is corrected. The Access Control section is
  available from both the Endpoint Configurations settings page and the Guardrails editor in
  AI Inventory.

### Improved

- [Endpoint Agent](/platform-areas/endpoint-agent): Endpoint Detection Configurations now
  auto-save. Changes are saved automatically after a short pause rather than requiring a manual
  Save button. A status indicator in the toolbar shows **Autosave pending**, **Saving...**,
  **Saved**, or **Save failed. Retrying...** so admins can track the save state at a glance. If a
  save fails, it is retried automatically. Invalid Access Control parameter values block auto-save
  until corrected.
- [Insights](/platform-areas/insights): Added an **LLM Gateway** chart to the AI Insights page.
  The chart shows total request tokens, total response tokens, and a model-distribution donut chart
  with a ranked legend for the selected time range. Use it to understand gateway throughput and
  which models are driving token volume.

- [Insights](/platform-areas/insights): Added an **MCP Usage** chart to the AI Insights page. The
  chart shows total MCP requests, blocked request count, and a ranked list of top MCP servers by
  traffic volume for the selected time range. Use it to spot which MCP servers are most active and
  whether requests are being blocked.

### Improved

- [Insights](/platform-areas/insights): The AI Insights page has been redesigned with a new
  responsive card grid. Charts now load in a clean, fixed-position layout that adapts to screen
  size. The previous draggable widget grid has been removed.

- [Insights](/platform-areas/insights): A **time range selector** is now available at the top of
  the AI Insights page. Selecting a preset (for example, 7 days or 30 days) or a custom date range
  updates all charts on the page simultaneously. Previously the charts loaded a fixed default period
  with no visible duration control.

- [Insights](/platform-areas/insights): Clicking a data point on an AI Insights chart now
  navigates to the related platform area — Applications, Users, or Findings — with the selected
  time range automatically applied. Previously charts had limited or no click-through navigation.

- [Insights](/platform-areas/insights): All AI Insights charts now display a structured skeleton
  loader while data is loading, a consistent empty state when no data exists for the selected
  period, and a retry option when a data request fails.

- [Insights](/platform-areas/insights): When a time range shorter than 24 hours is selected, chart
  x-axis labels now show the full date and time instead of only the hour value, making it easier to
  orient data points across days.
- [LLM Gateway](/platform-areas/llm-gateway): Added **OpenAI Assistants** and **OpenAI Assistants
  Azure** as provider options when creating or editing an LLM Gateway app. These providers connect
  to the OpenAI Assistants API (threads and runs). A new **OpenAI Assistants** tab in the provider
  selector lists both options. OpenAI Assistants requires an API key and accepts an optional base
  URL. OpenAI Assistants Azure requires an API key and an Azure endpoint, and accepts an optional
  Azure API version. Like embeddings and rerank providers, both are available for gateway use but
  are not used as standard routing targets.

## June 18, 2026

### Fixed

- [Findings](/platform-areas/findings): Finding Insights time-range presets (**3 days**, **7 days**,
  **30 days**, **3 months**, **6 months**, and **1 year**) now align to calendar boundaries. The
  range ends at the close of today and the start bound is aligned to the opening of the corresponding
  past calendar day or month, so each preset covers complete days or months rather than a partial
  rolling window. The **24-hour** preset continues to use a rolling window ending at the current
  time.

- [Findings](/platform-areas/findings): Clicking a data point on a Finding Insights chart to drill
  into a specific period now selects the correct time window based on the active preset's
  granularity: one hour for within-day views, one full calendar day for ranges up to 30 days, and
  one full calendar month for ranges longer than 30 days. Previously the drilldown could apply a
  mismatched time bucket.

- [Findings](/platform-areas/findings): The **Posting** behavior type on findings cards now
  correctly displays the interaction detail view. Previously, posting-type findings showed an
  incorrect visual state on the card.

- [Findings](/platform-areas/findings): The **Channel** field has been removed from findings card
  details. The channel filter is no longer shown in the findings filter panel.

- [Findings](/platform-areas/findings): For findings linked to guest accounts, the Login Email
  field on a findings card now shows **Not Available** instead of attempting to display a value that
  does not apply to guest accounts.
- [Integrations](/platform-areas/integrations): Fixed a bug where saving changes to a
  non-OAuth integration instance could incorrectly trigger OAuth authorization. The OAuth flow
  is now only advanced for integrations that require it; non-OAuth instances save and close
  without initiating an OAuth redirect.
- [Integrations](/platform-areas/integrations): Fixed severity and checkbox fields in
  integration configuration forms showing stale selections after an update. These fields now
  always reflect the current saved state when the instance editor is reopened.

### Improved

- [Integrations](/platform-areas/integrations): Filter settings configured during new
  integration instance creation are now saved automatically when the instance is created,
  removing the need for a separate save step.
- [Integrations](/platform-areas/integrations): The instance configuration form now reloads
  fresh field values from the server after saving an existing instance, so the next open of
  the editor always shows the latest saved configuration.

## June 17, 2026

### New

- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Added an
  **Export** button to the Applications table toolbar. Clicking it opens an export modal where
  admins choose a format (CSV) and a **Data Scope**: **Current filter** exports only records
  matching the active search and filters; **Full range** exports all records without applying
  filters. When rows are selected in the table, the button shows the selection count and the
  export covers only those rows (no scope selector is shown in that mode). Active filters and a
  row limit are displayed in the modal before the export starts. The export is queued in the
  background; a notification confirms queuing and the completed file appears in export history
  labeled **Applications**. This feature is labeled Beta.

### Improved

- [Audit Log and Exports](/platform-areas/audit-log-and-exports): The export history list now
  automatically refreshes every 30 seconds while any export is still processing, so the status
  and download link update without requiring a manual page reload.

### Fixed

- [Browser Extension](/platform-areas/browser-extension): Fixed the IDP User Status column in
  the Browser Extension Deployment Status screen to correctly display **NA** when the status is
  absent or contains only a placeholder dash. Previously a dash value could be treated as a valid
  status indicator instead of a missing value.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Fixed the
  IDP User Groups column in the Users table and Smart Groups drawer. Values no longer shift
  horizontally on large screens.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Fixed the
  notification bell being obscured by other page elements on the Applications screen. The
  notification icon is now always visible above the toolbar.
- [LLM Gateway](/platform-areas/llm-gateway): Fixed config change detection in Audit Log Config
  History to use locale-aware key ordering, ensuring that configuration differences are
  consistently detected and displayed regardless of key naming.

## June 16, 2026

### New

- [LLM Gateway](/platform-areas/llm-gateway): Added a **Self-Service Dashboard** — a dedicated web
  surface for end users who have been granted self-service access to LLM Gateway apps. Users who
  sign in via OAuth with a self-service access mode land here automatically and cannot reach admin
  pages. The dashboard lists the apps they are allowed to use, with search and refresh. Selecting
  an app opens **Settings**, **Logs**, and **Findings** tabs. In Settings, users with request
  access can view the full configuration panel and submit change requests for admin approval rather
  than writing config directly. Logs are scoped to the signed-in user by default; admins can grant
  all-logs access to widen that scope. Credential access depends on the credential mode the admin
  chose for the app: users with API key access can copy the shared app key, or create and revoke
  named personal keys when the app is set to Named User API Keys mode. MCP Gateway support is
  planned and shows a "Coming soon" notice. Platform admins can reach the dashboard from a new
  **Self-service dashboard** link in the admin sidebar.

- [LLM Gateway](/platform-areas/llm-gateway): Added a **Self-Service** tab to each LLM Gateway
  API key settings drawer. The **Credential Mode** selector chooses between **Shared Parent Key**
  (self-service users receive the existing app key) and **Named User API Keys** (each user creates
  a personal key). The **Access** section lets admins grant four capabilities independently, each
  scoped to all users, specific email addresses, or smart groups: viewer access to the app,
  permission to submit settings change requests, visibility of API key values, and visibility of
  all users' logs.

- [LLM Gateway](/platform-areas/llm-gateway): Added an **Audit Log** tab to each LLM Gateway API
  key settings drawer. **Config History** lists saved configuration versions with actor and
  timestamp; expanding a version shows a field-level diff and lets an admin roll back to it
  immediately with a confirmation step. **Change Requests** lists settings requests submitted by
  self-service users, filtered by status (Pending, Approved, Rejected, Failed, Stale); admins can
  approve or reject individual requests from this panel. A global **Audit Log** button on the LLM
  Gateway app list opens a cross-app view of config changes and pending requests, with a link to
  drill into each app's per-key Audit Log tab.

### Improved

- [AI Inventory](/platform-areas/ai-inventory): The OpenAI Compliance inventory view is now
  organized into three tabs. **Overview** is the new default landing tab and shows
  organization-level metrics for the selected period — observed users, events, ChatGPT
  conversations and messages, files, Codex sessions, agent runs, connector calls, and total
  tokens — alongside snapshot cards for ChatGPT inventory totals, Codex activity, and adoption
  highlights, and a data-freshness and source-status panel. **Assets** is the existing inventory
  table, with product tabs for ChatGPT conversations, Codex sessions, and workspace agents,
  search, filters, sort, pagination, and detail drawers. **Usage** adds **Users**, **Sources**,
  and **Rankings** sub-tabs with ChatGPT top-user lists sorted by conversations, Codex top users
  and model rankings, source adoption breakdowns, source overlaps, and cross-source transition
  flows. The default time range for the Compliance APIs view is now **7 days**. Loading states
  inside compliance views are also more reliable; data requests are deferred until the Compliance
  APIs tab is active, reducing background network calls when working in other inventory sources.

## June 15, 2026

### New

- [MCP Gateway](/platform-areas/mcp-gateway): Added a **Group & User Rules** tab to MCP server
  settings, available from the Settings drawer and from AI Inventory MCP Gateway detail drawers.
  Admins can create rules scoped to a smart group or an individual user that partially override tool
  availability and guardrail actions for that MCP server. Rules are partial — anything not set
  inherits the server's default settings. Smart-group rules are evaluated first; user rules apply
  last and take final priority. Rules can be individually enabled or disabled and deleted. An
  **Effective Settings** preview resolves the full configuration for a given user email across all
  matched groups and user rules. A **Group & User Rules** shortcut is also available on each MCP
  server card.

- [MCP Gateway](/platform-areas/mcp-gateway): The **Access Control** section in MCP server settings
  now supports smart group and per-user access rules. Each smart group can be set to **Allow**
  (explicitly permit access), **Deny** (block access), or **Default** (inherit the server-level
  behavior). Individual users can be added to an **Allowed Users** list, which can override a denied
  smart group, or a **Denied Users** list, which is the highest-priority access rule. Previously,
  Access Control only supported enabling or disabling predefined agent clients.

- [AI Inventory](/platform-areas/ai-inventory): Added a **Discovery** view within the Endpoint Agent
  source. Discovery lists applications observed on endpoints through asset inventory with name, users,
  device count, OS type, privilege, category, source, and execution policy columns. Admins can filter
  by app name, user email, category, source, OS type (macOS, Windows, Linux), approval status (Needs
  Review, Approved, Blocked), and criticality (Critical, Not Critical), and toggle off OS system
  processes. Execution policy (Allowed or Blocked) can be updated inline for each discovered
  application.

### Improved

- [AI Inventory](/platform-areas/ai-inventory): Interaction drawers in the Browser Extension and
  Endpoint Agent sources now include a time-range filter. Admins can scope visible interactions to a
  preset or custom duration without leaving the inventory drawer.
- [AI Inventory](/platform-areas/ai-inventory): The Browser Extension interactions table no longer
  shows a Latency column. Account names in Browser Extension interactions are now displayed without
  an internal account ID suffix.
- [AI Inventory](/platform-areas/ai-inventory): Application management controls (status, criticality,
  license, and blocked state) in the Browser Extension inventory source now enforce role-based access.
  Admins without update permission see the current value as read-only.
- [AI Inventory](/platform-areas/ai-inventory): The inventory table header now stays fixed at the
  top of the screen while scrolling through large lists.
- [Settings and Administration](/platform-areas/settings-admin): The tenant timezone preference now
  covers additional screens: Browser Extension deployment-status drilldown timestamps, AI Gateway
  date range filter labels, MCP Connection Status last-activity and last tool-call timestamps, Red
  Team run dates and case detail timestamps, and Controls listing timestamps.

### Fixed

- [AI Inventory](/platform-areas/ai-inventory): Fixed a bug where the refresh button in the Browser
  Extension and Endpoint Agent interaction tables was not working.
- [AI Inventory](/platform-areas/ai-inventory): Fixed a bug where updating app criticality from the
  Browser Extension inventory table did not save correctly.

## June 12, 2026

- [MCP Gateway](/platform-areas/mcp-gateway): Admins can now add custom MCP servers using
  **Upstream API Key** authentication. A new **Upstream API Key** option in the Add MCP auth mode
  selector lets admins provide an admin-owned API key that the gateway stores and injects when
  calling the upstream server. Three credential-placement options are available: **Bearer token**
  (sent as an `Authorization: Bearer` header), **Custom header** (a named HTTP request header), and
  **Query parameter** (appended to the upstream URL). An optional value-prefix field is available
  for custom schemes. When auto-detection identifies that a server requires auth but does not
  support OAuth, the Upstream API Key form appears automatically. If an OAuth server rejects
  dynamic client registration (DCR), the Add MCP form now keeps OAuth fields open, marks client
  credentials as required, and prompts the admin to retry with a custom OAuth app.

## June 11, 2026

- [Settings and Administration](/platform-areas/settings-admin): Admins with Admin or Super Admin
  roles can now configure LLM Gateway app access when creating or editing a user with the AI Gateway
  Admin role. A new App Access selector lets admins allow all LLM Gateway apps or restrict the user
  to a specific subset. The selector appears in the users table and in the user details panel.
- [LLM Gateway](/platform-areas/llm-gateway): Security Guardrails now includes a
  **Set everything to default** button next to the Default Action selector. The button activates when
  any data, EDM, custom, or adversarial category action differs from the current default, and
  clicking it resets all categories to inherit that default. The selector label was also renamed from
  "Default Risk Action" to "Default Action".
- [LLM Gateway](/platform-areas/llm-gateway): Adversarial Risks in Security Guardrails now includes
  an **Enable all / Disable all** bulk toggle that flips all adversarial risk categories on or off at
  once while preserving each category's action and sensitivity settings.
- [LLM Gateway](/platform-areas/llm-gateway): Adversarial risk sensitivity is now shown as a direct
  label (High, Medium, or Low) matching the single configured level rather than a cumulative
  threshold. Adversarial category actions that inherit from the Default Action are now visually
  indicated with a green dot and an "Inherited from default risk action" label.

## June 10, 2026

- [Settings and Administration](/platform-areas/settings-admin): The timezone display preference
  is now saved to the database and loaded on sign-in, so the setting persists across browsers and
  devices. Admins can select any timezone from a searchable dropdown—the preference is no longer
  limited to UTC or local browser time. A Save button appears when the selection changes, and a
  toast notification confirms the update.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Fixed the AI
  category filter on the Applications page so it correctly targets the primary app category. The
  "AI" lens, Generative AI category chip, and AI KPI shortcut now consistently match apps
  classified as Generative AI. When navigating to Applications from an insight drilldown that
  applies a business-category filter, the Category chip now shows "Business" instead of a
  conflicting separate chip.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): The
  Applications page now defaults to a 7-day time range instead of 30 days.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Fixed a bug
  where clicking the conversation count icon in an application table row opened the app intelligence
  panel instead of the app detail drawer.
- [MCP Gateway](/platform-areas/mcp-gateway): MCP server creation dates on gateway server cards
  now follow the tenant timezone preference and show the alternate time on hover, consistent with
  other timestamps across the platform.
- [LLM Gateway](/platform-areas/llm-gateway): LLM Gateway API key creation dates on key cards now
  follow the tenant timezone preference and show the alternate time on hover, consistent with other
  timestamps across the platform.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Inline
  editable fields in the application table now show a "Saving…" label and spinner while a change
  is being applied, giving clearer feedback during edits.
- [Users, Applications, and Accounts](/platform-areas/users-accounts-applications): Fixed app
  owner names occasionally displaying incorrect values in the application table row tooltip.
- Fixed a bug where typing in a search or input field inside an open detail drawer could cause the
  drawer to flicker or close unexpectedly. This affected drawers across multiple platform areas,
  including [AI Inventory](/platform-areas/ai-inventory),
  [LLM Gateway](/platform-areas/llm-gateway), and [MCP Gateway](/platform-areas/mcp-gateway).

## June 9, 2026

- [AI Inventory](/platform-areas/ai-inventory): Added OpenAI Compliance inventory views for
  ChatGPT conversations, Codex sessions, and workspace agents, including product counts, search and
  filters, pagination, refresh, and detail timelines or runs.
- [AI Gateway](/platform-areas/ai-gateway): Fixed AI Gateway settings access so admins with
  [LLM Gateway](/platform-areas/llm-gateway) or [MCP Gateway](/platform-areas/mcp-gateway)
  permissions can reach the relevant AI Gateway pages.

## June 8, 2026

- [AI Inventory](/platform-areas/ai-inventory): Combined Browser Extension, Endpoint Agent, LLM
  Gateway, MCP Gateway, and Compliance API coverage into one inventory view with source switching,
  source-specific counts and metrics, search, filtering, pagination, and source-aware detail
  drawers.
- [Endpoint Agent](/platform-areas/endpoint-agent): Added richer inventory drilldowns for endpoint
  applications, including overview, tool usage, interactions, guardrails, and related agents,
  skills, MCP servers, models, hooks, permissions, plugins, and repositories.
- [LLM Gateway](/platform-areas/llm-gateway): Added an LLM Gateway inventory source with request,
  blocked, anonymized, model, posture, expiry, and status metrics, plus embedded configuration and
  recent-log drilldowns.
- [MCP Gateway](/platform-areas/mcp-gateway): Added an MCP Gateway inventory source with tools,
  scopes, requests, blocked requests, latency, posture, OAuth state, and embedded logs and settings
  drilldowns.
- [Browser Extension](/platform-areas/browser-extension): Added a Browser Extension inventory
  source with application search, filters, bulk actions, app details, and interaction drilldowns.
- [Settings and Administration](/platform-areas/settings-admin): Added a timezone display
  preference so admins can show timestamps in UTC or local browser time. Timestamps across findings,
  audit logs, exports, apps, users, settings, and gateway logs now follow that preference and show
  the alternate time on hover.
- [LLM Gateway](/platform-areas/llm-gateway): Added quick time-range presets to the logs dashboard,
  provider-label analytics, provider-label details in log drilldowns, and per-model overrides for
  response timeout, concurrency, request rate, and token limits.
- [MCP Gateway](/platform-areas/mcp-gateway): Added MCP Logs & Analytics with MCP server filters,
  preset or custom time ranges, request distribution, DLP outcomes, tool usage, top users, and
  sortable or filterable log entries with detail drawers.
- [Settings and Administration](/platform-areas/settings-admin): Added permission-aware inline user
  management controls for editing a user's name and role from Manage Users.
