# PurePool Slack App Setup Guide 🚗

## Overview
This guide will help you create and configure a Slack app for PurePool, your carpool coordination bot with beautiful Block Kit UI.

## Prerequisites
- Admin access to a Slack workspace
- PurePool bot code deployed on Replit
- Access to your app's deployment URL

## Step 1: Create Slack App

1. **Visit Slack API Portal**
   - Go to [api.slack.com/apps](https://api.slack.com/apps)
   - Click "Create New App"
   - Choose "From scratch"

2. **App Configuration**
   - **App Name**: `PurePool`
   - **Development Workspace**: Select your workspace
   - Click "Create App"

## Step 2: Configure Bot Permissions

1. **Navigate to OAuth & Permissions**
   - In your app settings, go to "OAuth & Permissions"

2. **Add Bot Token Scopes**
   Add these required scopes:
   ```
   chat:write          # Send messages
   chat:write.public   # Send messages to channels
   users:read          # Read user profile info
   channels:read       # Read channel information
   im:read            # Read direct messages
   mpim:read          # Read group messages
   ```

3. **Install App to Workspace**
   - Click "Install to Workspace"
   - Review and approve permissions
   - Copy the **Bot User OAuth Token** (starts with `xoxb-`)

## Step 3: Configure Event Subscriptions

1. **Enable Event Subscriptions**
   - Go to "Event Subscriptions"
   - Toggle "Enable Events" to ON

2. **Set Request URL**
   - Use your Replit app URL + `/api/slack/events`
   - Example: `https://your-app.replit.app/api/slack/events`
   - Slack will verify this URL automatically

3. **Subscribe to Bot Events**
   Add these events:
   ```
   message.channels    # Listen to channel messages
   message.im         # Listen to direct messages
   ```

4. **Save Changes**

## Step 4: Configure Interactive Components

1. **Go to Interactivity & Shortcuts**
   - Toggle "Interactivity" to ON
   
2. **Set Request URL**
   - Same as events: `https://your-app.replit.app/api/slack/interactive`

## Step 5: App Home & Display

1. **Go to App Home**
   - Enable "Home Tab"
   - Enable "Messages Tab"
   - Turn ON "Allow users to send Slash commands and messages from the messages tab"

2. **Basic Information**
   - Add app description: "Coordinate carpools with colleagues and save money while reducing traffic! 🚗🌱"
   - Upload app icon (optional)
   - Set background color: `#1E90FF` (Blue)

## Step 6: Slack Commands (Optional)

1. **Go to Slash Commands**
   - Create command `/purepool`
   - Request URL: `https://your-app.replit.app/api/slack/slash`
   - Description: "Coordinate carpools with colleagues"
   - Usage hint: `register | status | help | find matches`

## Step 7: Deploy & Test

1. **Install to Additional Workspaces**
   - Go to "Manage Distribution"
   - For internal use, no additional setup needed
   - For public distribution, complete app review process

2. **Test the Bot**
   - Invite bot to a channel: `/invite @PurePool`
   - Try these commands:
     - `@PurePool help` - Show help
     - `@PurePool register` - Start registration
     - `@PurePool status` - Check status

## Step 8: Environment Variables

In your Replit deployment, set these environment variables:

```
SLACK_BOT_TOKEN=xoxb-your-bot-token-here
SLACK_SIGNING_SECRET=your-signing-secret-here
```

Get these from your Slack app's "Basic Information" page.

## Rich UI Features

Your PurePool bot now includes:
- 🎨 Beautiful Block Kit welcome messages
- 📋 Rich registration forms with user profiles
- 📊 Elegant status cards showing carpool information
- 🔍 Interactive matching results with user details
- 🆘 Comprehensive help center with organized sections
- ✨ Professional styling with emojis and clear formatting

## Commands Available

| Command | Description | Example |
|---------|-------------|---------|
| `register` | Register for carpooling | `@PurePool register as driver from downtown at 8am` |
| `status` | Check your carpool status | `@PurePool status` |
| `help` | Show help and commands | `@PurePool help` |
| `find matches` | Find carpool partners | `@PurePool find matches` |

## Troubleshooting

**Bot not responding?**
- Check if bot is added to the channel
- Verify event subscription URL is correct
- Check Replit app logs for errors

**Rich messages not showing?**
- Ensure Block Kit is properly implemented (✅ Already done!)
- Check Slack app has proper permissions
- Verify message format in logs

**Authentication issues?**
- Verify SLACK_BOT_TOKEN is correct
- Check SLACK_SIGNING_SECRET matches
- Ensure app is installed to workspace

## Next Steps

1. **Deploy**: Publish your Replit app to make it live
2. **Test**: Try all commands with colleagues
3. **Invite**: Add bot to relevant channels
4. **Monitor**: Check logs and user feedback
5. **Scale**: Add more advanced features as needed

Your PurePool bot is now ready to help employees coordinate beautiful, sustainable carpools! 🚗✨