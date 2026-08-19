---
sidebar_custom_props:
  icon: Plug
---

# Integrations

Integrations connect QuilrAI to the systems that provide identity, device, SaaS, cloud, and AI
signals. They are the setup and lifecycle surface for connectors and connector instances.

## When To Use It

Use Integrations when you need to:

- Connect QuilrAI to an external system.
- Review existing connected integrations.
- Browse available integrations.
- Configure or update an integration instance.
- Follow setup guidance for supported connectors.
- Manage integration-specific OAuth or configuration flows.

## Key Capabilities

- Connected integrations view.
- Available integrations catalog.
- Search and filter connectors.
- Configure new instances.
- Edit existing instances when permitted.
- Connector-specific setup documentation, including required scopes, permissions, and configuration.
- Separate advanced routes for OAuth, token flow, MCP clients, MCP servers, and tool policies where
  enabled.

## Integration Catalog

Connectors are organized into the following categories:

- **Data Forwarding:** [Webhook](./data-forwarding/webhook.md), [Syslog](./data-forwarding/syslog.md), [Syslog Audit](./data-forwarding/syslog-audit.md), [Email](./data-forwarding/email.md).
- **Identity Providers:** [Microsoft Entra ID](./identity-providers/microsoft-entra-id.md), [Google Workspace](./identity-providers/google-workspace.md), [Okta](./identity-providers/okta.md), [Ping Identity](./identity-providers/ping-identity.md).
- **Manage Users:** [IDP Group to Platform Roles](./manage-users/idp-group-to-platform-roles.md).
- **Single Sign-On:** [SAML](./single-sign-on/saml.md).
- **Microsoft Ecosystem:** [Microsoft Purview](./microsoft-ecosystem/microsoft-purview.md), [Microsoft Calendar](./microsoft-ecosystem/microsoft-calendar.md).
- **Google Ecosystem:** [Google Calendar](./google-ecosystem/google-calendar.md), [Google Drive](./google-ecosystem/google-drive.md).
- **Mobile Device Management (MDM):** [Microsoft Intune](./mobile-device-management/microsoft-intune.md), [Jamf Pro](./mobile-device-management/jamf-pro.md).
- **Communication & Collaboration:** [Microsoft Teams](./communication-collaboration/microsoft-teams.md), [Slack](./communication-collaboration/slack.md), [Zoom ChatBot](./communication-collaboration/zoom-chatbot.md).
- **Asset Discovery:** [AWS Cloud](./asset-discovery/aws-cloud.md), [Azure Cloud](./asset-discovery/azure-cloud.md), [ChatGPT](./asset-discovery/chatgpt.md), [vLLM](./asset-discovery/vllm.md), [Ollama](./asset-discovery/ollama.md).

## Main Workflows

1. Open Integrations.
2. Review Connected integrations or browse Available integrations.
3. Search or filter by connector category.
4. Select a connector.
5. Follow configuration guidance and complete required scopes or credentials.
6. Return to Connected integrations to monitor or update the instance.

## Advanced Integration Areas

Some integration routes are specialized operational areas and may not be visible to every customer:

- OAuth integration configuration.
- Token flow configuration.
- MCP clients and MCP servers.
- Tool policies for MCP or AI tool governance.
- OAuth and token-flow routes that support connector authorization and callback workflows.

## Related Platform Areas

- [Browser Extension](../browser-extension.md)
- [Endpoint Agent](../endpoint-agent.md)
- [MCP Gateway](../mcp-gateway.md)
- [Settings And Administration](../settings-admin.md)

## Access Requirements

Integrations require Integration permissions. Editing existing integrations requires update access.
Some MCP-related integration routes require MCP Gateway permissions.
