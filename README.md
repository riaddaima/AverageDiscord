# AverageDiscord

A comprehensive Discord-Hytale server bridge plugin that seamlessly connects your Hytale game server with Discord, enabling real-time chat synchronization and server status notifications.

## Overview

**AverageDiscord** is a powerful plugin designed for Hytale servers that establishes a two-way communication bridge between your in-game chat and a designated Discord channel. Monitor server activity, receive player join/leave notifications, and allow Discord members to chat with players on your Hytale server—all in real-time.

## Features

### 🔗 **Bi-Directional Chat Bridge**
- Real-time synchronization between in-game chat and Discord
- Formatted message support with proper text parsing
- Discord messages sent to the designated channel appear in-game
- In-game chat messages are forwarded to Discord with player names

### 📢 **Server Status Notifications**
- Automatic server startup notification
- Automatic server shutdown notification
- Player join notifications with player names
- Player disconnect notifications with player names
- Emoji-enhanced messages for better visibility (✅ ☒ ➡️ ⬅️)

### ⚙️ **Easy Configuration**
- JSON-based configuration file
- Hot-reload functionality without restarting the server
- Customizable Discord bot prefix for in-game messages
- Custom bot activity/status message
- Support for formatted color codes in Discord messages

### 🛠️ **Admin Commands**
- `/discordbridge reload` - Reloads plugin configuration on-the-fly
- Aliases: `/gm`, `/agm`, `/groupman`
- Graceful config synchronization

## Installation

1. **Download** the latest AverageDiscord JAR file
2. **Place** it in your Hytale server's plugins folder
3. **Create a Discord bot** at [Discord Developer Portal](https://discord.com/developers/applications)
4. **Configure** the plugin (see Configuration section below)
5. **Restart** your Hytale server or use `/discordbridge reload`

## Configuration

After first run, a `discord_bridge.json` configuration file will be created in your server's `AverageDiscord` folder.

### Configuration File Example

```json
{
  "config": {
    "botToken": "your_bot_token_here",
    "mainChatChannelId": "your_channel_id_here",
    "botActivityMessage": "Playing Hytale!",
    "discordIngamePrefix": "&9[Discord] "
  }
}
```

### Configuration Options

| Option | Type | Description | Example |
|--------|------|-------------|---------|
| `botToken` | String | Your Discord bot token from the Developer Portal | `"token_here"` |
| `mainChatChannelId` | String | The Discord channel ID where chat will be bridged | `"1234567890"` |
| `botActivityMessage` | String | The bot's status message in Discord | `"Playing Hytale!"` |
| `discordIngamePrefix` | String | Prefix for Discord messages in-game (supports color codes) | `"&9[Discord] "` |

### How to Get Your Bot Token and Channel ID

1. **Bot Token:**
   - Go to [Discord Developer Portal](https://discord.com/developers/applications)
   - Create a new application or select an existing one
   - Navigate to the "Bot" tab
   - Click "Add Bot" (if new)
   - Copy the token under the "TOKEN" section

2. **Channel ID:**
   - Enable Developer Mode in Discord (User Settings → Advanced → Developer Mode)
   - Right-click on your desired channel
   - Select "Copy Channel ID"
   - Paste it in the configuration

## How It Works

### Chat Synchronization
- **In-Game → Discord**: When a player types in chat, the message is formatted and sent to the configured Discord channel
- **Discord → In-Game**: When a non-bot user sends a message in the Discord channel, it appears in-game with a customizable prefix

### Event Listeners
The plugin registers listeners for:
- `PlayerChatEvent` - Forwards in-game chat to Discord
- `PlayerReadyEvent` - Notifies Discord when players join
- `PlayerDisconnectEvent` - Notifies Discord when players leave
- `AllWorldsLoadedEvent` - Notifies Discord when the server starts
- `ShutdownEvent` - Notifies Discord when the server stops

## Dependencies

- **Hytale Server** - The core server implementation
- **JDA (Java Discord API)** - Version 6.3.0 for Discord bot functionality
- **SLF4J** - Logging implementation

## Requirements

- Java 11 or higher
- Active Hytale server installation
- Discord bot with proper permissions:
  - `View Channels`
  - `Send Messages`
  - `Read Message History`
  - Intents: `GUILD_MESSAGES`, `MESSAGE_CONTENT`

## Commands

### `/discordbridge reload`
Reloads the plugin configuration without requiring a server restart.

**Aliases:** `gm`, `agm`, `groupman`

**Usage:** `/discordbridge reload`

**Permission:** Server admin/operator

## Color Codes

The `discordIngamePrefix` supports Hytale color codes for customizing message appearance:
- `&9` - Blue
- `&a` - Green
- `&c` - Red
- `&e` - Yellow
- `&f` - White
- And many more standard Minecraft/Hytale color codes

## Troubleshooting

### Bot Token Invalid
- Verify the bot token is correctly copied from the Discord Developer Portal
- Ensure you've copied the entire token without extra spaces
- Regenerate the token if necessary

### Channel ID Not Found
- Ensure Developer Mode is enabled in Discord
- Verify the channel ID is correct (should be numeric)
- Ensure the bot has access to the channel

### Messages Not Appearing
- Check that the bot has permission to send messages in the channel
- Verify the channel ID in the configuration is correct
- Check server logs for any errors
- Try using `/discordbridge reload` to refresh the configuration

### Bot Offline
- Verify the bot token is valid
- Check that your server has internet connectivity
- Look for error messages in the server console

## Author

**Average** (js3 on Hytale)

## Website

[GitHub Repository](https://github.com/RenderBr/AverageDiscord)

## Support

For issues, feature requests, or contributions, please visit the [GitHub repository](https://github.com/RenderBr/AverageDiscord).

## License

See the repository for license information.

---

**Note:** This plugin requires a valid Discord bot token and proper configuration to function. Ensure all prerequisites are met before installation.

