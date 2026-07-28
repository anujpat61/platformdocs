---
sidebar_position: 2
sidebar_label: Slack
sidebar_custom_props:
  icon: Hash
---

# Slack

Integrate Slack with Quilr to streamline team communication, improve collaboration, and enhance productivity.

- **Category:** Communication
- **Integration Type:** OAuth 2.0 / Bot

## Setup

1. Go to **Integrations** and open the **Available** tab.
2. Click **+ Add** on the **Slack** tile.
3. Sign in to your Slack workspace and approve the requested bot scopes.
4. Click **Allow** to authorize the connection.

## Required Scopes

| Scope Group | Permissions | Purpose |
|-------------|-------------|---------|
| App Mentions | `app_mentions:read` | Allows the app to read messages where it is mentioned. |
| Channels Access | `channels:history`, `channels:write.invites`, `channels:read` | Allows the app to read public channels, access message history, and manage invitations. |
| Chat Permissions | `chat:write`, `chat:write.customize`, `chat:write.public` | Allows the app to send messages, customize them, and post messages in public channels. |
| Files | `files:read` | Allows the app to read files shared in Slack. |
| Groups | `groups:read`, `groups:write` | Allows the app to read and manage private channel (group) information. |
| Direct Messages | `im:history`, `im:read`, `im:write`, `im:write.topic` | Allows the app to read direct messages, send messages, and set topics in DM conversations. |
| Multi-Party DMs | `mpim:write` | Allows the app to send messages to multi-party direct messages. |
| Team Info | `team:read` | Allows the app to read team information. |
| User Management | `users:read`, `users:write`, `users:read.email` | Allows the app to read and update user profiles, including accessing email addresses. |
| Metadata | `metadata.message:read` | Allows the app to read metadata for messages. |
| Conversations | `conversations.connect:read`, `conversations.connect:write` | Allows the app to read and write conversations with other apps. |
| Reminders | `reminders:read`, `reminders:write` | Allows the app to read and write reminders. |

## What This Integration Does

- Sends security alerts and notifications to Slack channels.
- Enables interactive bot communication within Slack.
- Allows users to respond to security workflows via Slack.
- Facilitates collaboration across teams and channels.
- Enables Quilly security coaching for end users in Slack.
