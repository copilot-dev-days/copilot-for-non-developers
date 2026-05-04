# Part 3: Configure MCP Servers

> **Time:** ~5 minutes  
> **Goal:** Connect Copilot CLI to Microsoft 365 using the Work IQ plugin marketplace

---

## What Is MCP?

**MCP (Model Context Protocol)** is like a universal connector standard for AI — think of it as USB-C for AI tools.

Without MCP, Copilot CLI only sees your local files.  
With MCP, it can reach your email, calendar, Teams chats, documents, and more.

```
You type a prompt
        ↓
Copilot CLI + MCP connectors
        ↓
 📧 Email  📅 Calendar  💬 Teams  📄 Docs  📊 Planner
```

**One-time setup. Then it just works.**

> 🔗 Official Work IQ plugin marketplace: [github.com/microsoft/work-iq](https://github.com/microsoft/work-iq)

---

## Prerequisites

Before starting, make sure you have **Node.js 18 or later** installed:

```bash
node --version   # should show v18.x.x or higher
npm --version
```

If not installed, download from [nodejs.org](https://nodejs.org) (get the LTS version).

> ⚠️ **Admin Note:** Work IQ needs Microsoft 365 tenant admin consent on first use. If you get a permissions error during authentication, ask your IT/tenant admin to follow the [Tenant Administrator Enablement Guide](https://github.com/microsoft/work-iq/blob/main/ADMIN-INSTRUCTIONS.md).

---

## What You're Installing

This workshop uses two plugins from the Work IQ marketplace. You'll also see how to add direct Work IQ Mail and Calendar MCP servers for environments that want explicit MCP connections.

| Tool | Type | What It Does |
|------|------|-------------|
| **workiq** | Plugin | Query M365 data — emails, meetings, docs, Teams messages, people |
| **workiq-productivity** | Plugin | 9 productivity skills — email triage, action item extraction, meeting analysis, and more |
| **Work IQ Mail** | Remote MCP | Optional direct email tools via Microsoft 365 / Agent 365 |
| **Work IQ Calendar** | Remote MCP | Optional direct calendar tools via Microsoft 365 / Agent 365 |

---

## Step 1: Register the Work IQ Marketplace

Launch Copilot CLI:

```bash
copilot
```

Register the marketplace (one-time setup):

```
/plugin marketplace add microsoft/work-iq
```

Verify it's registered:

```
/plugin marketplace list
```

You should see `work-iq` in the list. ✅

---

## Step 2: Install WorkIQ Plugins

Install the core WorkIQ plugin:

```
/plugin install workiq@work-iq
```

Install the productivity skills plugin:

```
/plugin install workiq-productivity@work-iq
```

> 💡 **Restart Copilot CLI** after installing plugins for the new skills to become available:  
> Press `Ctrl+C`, then run `copilot` again.

---

## Step 3: Accept the EULA

On first use, WorkIQ requires you to accept its End User License Agreement:

```
workiq accept-eula
```

---

## Step 4: Verify the Connection

Test that WorkIQ can reach your Microsoft 365 data:

```
show me my calendar for today
```

You should see your actual calendar events. If you do — you're connected! ✅

Try a couple more:

```
show me my unread emails from today
```

```
summarize today's messages in the General Teams channel
```

---

## What Each Plugin Can Do

### workiq — Core M365 Query

| What You Want | Example Prompt |
|--------------|---------------|
| Email | `"What did Sarah say about the proposal?"` |
| Calendar | `"What meetings do I have tomorrow?"` |
| Documents | `"Find my recent PowerPoint presentations"` |
| Teams | `"Summarize today's messages in the Engineering channel"` |
| People | `"Who is working on Project Alpha?"` |

### workiq-productivity — 9 Productivity Skills

| Skill | Example Prompt |
|-------|---------------|
| **Daily triage** | `"Show me my inbox and calendar for today"` |
| **Action items** | `"Extract action items from today's meetings"` |
| **Email analytics** | `"Analyze my email patterns for the past month"` |
| **Meeting cost** | `"How much time did I spend in meetings this week?"` |
| **Org chart** | `"Show the org chart for Sarah Johnson"` |
| **Planner search** | `"Search all my Planner tasks for 'budget review'"` |
| **SharePoint** | `"Browse the Marketing SharePoint site"` |
| **Channel audit** | `"Audit inactive channels in the Engineering team"` |
| **Channel digest** | `"Summarize activity across my Teams channels"` |

### microsoft-365-agents-toolkit (Agent365)

Used for building and deploying M365 Copilot declarative agents:

```
"Scaffold a new declarative agent for HR FAQ"
"Add web search to my agent"
"Deploy my agent"
```

---

## Step 5: Optional Direct Work IQ MCP Servers

For most workshop participants, the WorkIQ plugins above are enough. Some enterprise environments may prefer direct Work IQ MCP server connections for specific services such as Mail and Calendar.

> ⚠️ **Preview feature:** Work IQ MCP servers are currently preview features. They require a Microsoft 365 Copilot license, tenant/admin configuration, and a registered Entra application with the right Work IQ permissions.

For this workshop, Mail and Calendar are the two direct MCP servers most relevant to the demo scenarios.

### Step 5a: Gather Your Entra IDs

You need:
- Your organization's **Tenant ID** (a GUID like `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`)
- A registered Entra application's **Client ID** with the required Work IQ MCP permissions

**Quickest way — Azure Portal:**
1. Go to [portal.azure.com](https://portal.azure.com)
2. Search for **Microsoft Entra ID** in the top search bar
3. On the Overview page, copy the **Tenant ID**
4. In **App registrations**, use an existing app or create a new one, then copy its **Application (client) ID**

**Or — Microsoft Admin Center:**
1. Go to [admin.microsoft.com](https://admin.microsoft.com)
2. Navigate to **Settings → Org settings → Organization profile**
3. Find and copy your **Tenant ID**

Your admin must also grant the relevant Work IQ permissions, such as **WorkIQ-MailServer** for mail tools.

### Step 5b: Add a Workspace MCP Config

GitHub Copilot CLI detects workspace MCP servers from a file named `.mcp.json` in the folder where you start Copilot CLI. It also supports user-level MCP config in `~/.copilot/mcp-config.json`.

For this workshop, create `.mcp.json` in your `copilot-workshop` folder.

Add Mail and Calendar servers (replace `YOUR_TENANT_ID` and `YOUR_CLIENT_ID`):

```json
{
  "mcpServers": {
    "WorkIQ-MailServer": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/YOUR_TENANT_ID/servers/mcp_MailTools",
      "oauth": {
        "clientId": "YOUR_CLIENT_ID",
        "callbackPort": 8080
      }
    },
    "WorkIQ-CalendarServer": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/YOUR_TENANT_ID/servers/mcp_CalendarTools",
      "oauth": {
        "clientId": "YOUR_CLIENT_ID",
        "callbackPort": 8080
      }
    }
  }
}
```

If you prefer the CLI command instead of editing JSON manually, Copilot CLI can add remote MCP servers:

```bash
copilot mcp add --transport http WorkIQ-MailServer https://agent365.svc.cloud.microsoft/agents/tenants/YOUR_TENANT_ID/servers/mcp_MailTools
```

### Step 5c: Restart and Verify

Restart Copilot CLI from the folder containing `.mcp.json`. Copilot CLI 1.0.40 or later detects the file and prompts you to connect to the MCP server. After authenticating, test the connection:

```
what meetings do I have tomorrow?
```

```
show me my unread emails from today
```

> ✅ If you see real calendar events and emails — the Work IQ MCP servers are working!

> ⚠️ **First-time auth:** Work IQ remote servers use OAuth. You may be prompted to sign in with your Microsoft 365 account on first use. This is expected — approve the permissions request in your browser.

> 🔗 Full server catalog: [github.com/microsoft/mcp](https://github.com/microsoft/mcp)

---

## Troubleshooting

**"Admin consent required":**
- You need your M365 tenant admin to grant permissions. Send them the [Admin Enablement Guide](https://github.com/microsoft/work-iq/blob/main/ADMIN-INSTRUCTIONS.md).

**Plugin not found after install:**
- Restart Copilot CLI (`Ctrl+C`, then `copilot` again)
- Run `copilot plugin list` to confirm it's installed

**Node.js version error:**
- Run `node --version` — must be 18 or higher
- Download the latest LTS from [nodejs.org](https://nodejs.org)

---

## ✅ Part 3 Complete

You've:
- Registered the Work IQ plugin marketplace
- Installed the `workiq` and `workiq-productivity` plugins
- Accepted the EULA and verified your M365 connection
- Optionally configured direct Work IQ Mail and Calendar MCP servers

Now let's put it to work. → [Part 4: Exploring with WorkIQ](04-workiq-explore.md)
