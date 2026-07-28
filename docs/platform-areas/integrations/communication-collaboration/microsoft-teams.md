---
sidebar_position: 1
sidebar_label: Microsoft Teams
sidebar_custom_props:
  icon: Users
---

# Microsoft Teams

This connector integrates Microsoft Teams with Quilr, allowing secure access to team information, channel details, and messaging.

- **Category:** Communication
- **Integration Type:** OAuth 2.0
- **Vendor:** Microsoft

## Setup

1. Go to **Integrations** and open the **Available** tab.
2. Click **+ Add** on the **Microsoft Teams** tile.
3. Sign in with a Microsoft administrator account and consent to the requested permissions.
4. Click **Allow** to authorize the connection.

## Required Scopes

| Scope Group | Permissions | Purpose |
|-------------|-------------|---------|
| User Information | `openid`, `profile`, `offline_access`, `user.read`, `user.read.all`, `MailboxSettings.Read` | Allows Quilr to read user information and send messages to users. |
| Teams Activity | `TeamsActivity.Read`, `TeamsActivity.Send`, `TeamsAppInstallation.ReadForUser`, `ChannelMessage.Send`, `Chat.ReadWrite`, `Chat.Create`, `ChatMessage.Send` | Allows Quilr to read Teams activity notifications and channel information, and to send messages to channels and chats. |

## What This Integration Does

- Enables Quilr bot notifications in Teams.
- Sends security alerts to Teams channels.
- Monitors Teams activity for security insights.
- Facilitates communication with end users.
- Enables Quilly security coaching for end users in Microsoft Teams.
