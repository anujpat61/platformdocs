---
sidebar_position: 1
slug: /
sidebar_custom_props:
  icon: BookOpen
hide_copy_dropdown: true
---

import AskAiBanner from '@site/src/components/AskAiBanner';
import {
  Activity,
  Bot,
  Boxes,
  ClipboardList,
  KeyRound,
  Network,
  Plug,
  ShieldCheck,
  Users,
  UsersRound,
} from 'lucide-react';

# QuilrAI Platform Overview

QuilrAI helps security, governance, and IT teams discover AI usage, understand risk, and safely roll out controls across users, apps, accounts, endpoints, gateways, and integrations.

<AskAiBanner productName="QuilrAI Platform" />

<div className="not-prose mt-8 grid gap-4 md:grid-cols-2 xl:grid-cols-3">
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <Activity className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Visibility</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Track AI adoption, risky behavior, sensitive prompts, top users, top apps, and usage trends from a single insights surface.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <Users className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Users, Apps, Accounts</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Review entity-level risk, usage, interactions, and findings with drilldowns for users, SaaS apps, endpoint apps, and accounts.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <UsersRound className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Smart Groups</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Create and manage smart groups and group membership from one place. Smart groups are used to
      scope access control and rules in MCP Gateway, LLM Gateway, and other platform areas.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <Boxes className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">AI Inventory</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Maintain a live inventory across Browser Extension, Endpoint Agent, LLM Gateway, MCP Gateway, and compliance API sources.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <ClipboardList className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Findings</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Investigate findings across browser extension, endpoint agent, LLM Gateway, MCP Gateway, compliance, identity, and all-source views.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <ShieldCheck className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Controls</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Create, edit, enable, monitor, or enforce controls by posture, with support for system and custom controls.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <Bot className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Quilly</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Review security coaching conversations in Slack and Microsoft Teams — finding-linked outreach,
      proactive coaching, and user-initiated policy questions.
    </p>
  </div>
  <div className="rounded-xl border border-[#c7b99f] bg-[#ebe1cf] p-5 dark:border-[#30343b] dark:bg-[#1f232a]">
    <Network className="mb-3 text-emerald-600 dark:text-emerald-400" size={24} />
    <h2 className="m-0 text-lg font-semibold text-[#252018] dark:text-neutral-50">Gateways</h2>
    <p className="mb-0 mt-2 text-sm leading-6 text-[#554c3f] dark:text-neutral-400">
      Configure LLM Gateway and MCP Gateway protection, logs, routing, guardrails, tools, access control, red teaming, and agent mappings.
    </p>
  </div>
</div>

## Platform Areas

### [Insights](./platform-areas/insights.md)

Use Insights to understand how AI is being adopted across the organization. The dashboard highlights adoption trends, top AI applications, top categories, top users, sensitive data in prompts, and department-level usage.

### [Findings](./platform-areas/findings.md)

Findings centralizes investigation work across the platform. Teams can move between summary insights, all findings, browser extension findings, endpoint findings, LLM Gateway findings, MCP Gateway findings, Compliance Findings, and identity findings.

### [Users, Applications, And Accounts](./platform-areas/users-accounts-applications.md)

The Users, Applications, and Accounts pages show entity-level AI activity. These views combine KPI summaries, trending entities, searchable tables, drilldowns, conversations, findings links, and app intelligence so teams can understand who is using AI, where, and with what risk.

### [Smart Groups](./platform-areas/smart-groups.md)

Smart Groups is the dedicated screen for creating and managing user groups across the platform.
Admins can create groups with or without initial members, add or remove users, and delete groups.
Smart groups defined here are used to scope access control rules in MCP Gateway and LLM Gateway.

### [AI Inventory](./platform-areas/ai-inventory.md)

AI Inventory helps teams track AI assets and AI activity sources from one place. Source views include Browser Extension applications, Endpoint Agent applications and coding inventory, LLM Gateway API keys, MCP Gateway servers, and Compliance APIs for supported providers.

### [Controls](./platform-areas/controls.md)

Controls let teams operationalize policy. Customers can browse controls by posture, filter by system or custom controls, add or update controls, duplicate existing controls, toggle status, and choose monitor or action mode.

### [Quilly](./platform-areas/quilly.md)

Quilly is Quilr's security coaching bot in Slack and Microsoft Teams. Security teams can review finding-linked coaching, proactive outreach, and user-initiated conversations from the Quilly Conversations drawer, User Lens, and finding cards.

### [Detection Models](./platform-areas/detection-models.md)

Detection Models define what QuilrAI should detect. The data-risk experience supports out-of-box and custom detections, contextual and non-contextual data risks, and custom techniques such as precision, semantic, and intent-based detection. Additional adversarial and insider-risk tabs may appear when enabled for the tenant.

### [AI Gateway](./platform-areas/ai-gateway.md)

AI Gateway includes LLM Gateway and MCP Gateway.

- [LLM Gateway](./platform-areas/llm-gateway.md) centralizes provider configuration, API key management, security guardrails, additional guardrails, routing, rate limits, token saving, identity-aware access, prompt store enforcement, logs, and red team testing.
- [MCP Gateway](./platform-areas/mcp-gateway.md) manages MCP servers, OAuth and passthrough connections, tools, access tokens, access control, security guardrails, logs, graph views, library installs, and agent configuration.

### [Browser Extension](./platform-areas/browser-extension.md) And [Endpoint Agent](./platform-areas/endpoint-agent.md)

Browser Extension and Endpoint Agent settings cover deployment, deployment management, deployment status, whitelisting, detection configuration, DLP actions, and browser monitoring behavior.

### [Integrations](./platform-areas/integrations/index.md)

Integrations help connect QuilrAI to identity providers, device management systems, SaaS platforms, cloud services, and AI services. The current platform includes connected and available connector views, instance configuration, and integration documentation for Okta, Jamf, ChatGPT, and AWS.

### [Settings And Administration](./platform-areas/settings-admin.md)

Settings provides organizational context, general settings, organizational policies, user management, user-interaction customization, compliance setup, browser extension setup, endpoint setup, and AI Gateway setup. Smart group management is available from the dedicated [Smart Groups](./platform-areas/smart-groups.md) screen.

### [Audit Log And Exports](./platform-areas/audit-log-and-exports.md)

Audit Log gives teams searchable, filterable event history with expandable snapshots. Exports provides export history and new CSV or JSON exports for supported platform tables.

## Suggested Reading Path

1. Start with Insights to understand adoption and risk trends.
2. Review Users, Applications, Accounts, and AI Inventory to see what exists.
3. Use Findings to investigate high-impact issues.
4. Configure Detection Models and Controls to align enforcement with policy.
5. Set up Browser Extension, Endpoint Agent, Integrations, and Gateways to expand coverage.
6. Use Audit Log and Exports for reporting and operational review.
