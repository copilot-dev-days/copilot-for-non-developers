# Part 2: Set Up Copilot CLI

> **Time:** ~5 minutes  
> **Goal:** Install GitHub Copilot CLI, authenticate, and run your first prompt

---

## What Is GitHub Copilot CLI?

GitHub Copilot CLI is an **AI assistant that lives in your terminal**. You type in plain English, and it responds with structured results — summaries, drafts, plans, analysis — without ever opening a browser.

```
❯ copilot
copilot> summarize my last 5 emails

📧 Here's what needs your attention today:
1. [URGENT] Budget approval needed from Finance — Sarah...
2. [ACTION] Engineering timeline review due Friday...
...
```

It's included with all GitHub Copilot subscriptions.

---

## Step 1: Install Copilot CLI

Choose the installation method for your platform:

### Windows

```powershell
winget install GitHub.Copilot
```

Or via npm (requires Node.js 22+):

```powershell
npm install -g @github/copilot
```

### Mac

```bash
brew install copilot-cli
```

Or via npm:

```bash
npm install -g @github/copilot
```

### Linux

```bash
npm install -g @github/copilot
```

> 💡 **Not sure if you have Node.js?** Run `node --version` in your terminal. You need **v22 or later** for the npm install method. If not installed, download from [nodejs.org](https://nodejs.org) (get the LTS version), or use Winget/Homebrew instead.

---

## Step 2: Verify the Installation

```bash
copilot --version
```

You should see a version number printed. If you get "command not found", try closing and reopening your terminal, then run it again.

---

## Step 3: Authenticate

Launch Copilot CLI:

```bash
copilot
```

On first launch, Copilot CLI may ask you to confirm that you trust the current folder. Choose the option that matches your comfort level. If you're not signed in, it will then prompt you to use the `/login` command.

```
/login
```

A browser window will open — sign in with your GitHub account. Once authenticated, return to the terminal.

> ✅ You'll see: `Signed in as @yourusername`

---

## Step 4: Explore the Interface

Now that you're in, try a few things:

### Get help

```
/help
```

This shows all available slash commands — your navigation menu inside Copilot CLI.

### Check available models

```
/model
```

Shows which AI models are available to you (GPT, Claude, Gemini, etc.).

### Ask something in plain English

```
What can you help me with today?
```

No special syntax needed — just type like you're sending a message.

---

## How Copilot CLI Works

```
You type a prompt
        ↓
Copilot CLI interprets and plans
        ↓
Fetches from your files, connected services, or knowledge
        ↓
Returns a structured response
```

On its own, Copilot CLI can see:
- Files in your current folder
- Content you paste or reference directly

With the built-in GitHub MCP server and extra **MCP connectors** (Part 3), it can also reach:
- Your Microsoft 365 email, calendar, Teams
- GitHub issues and pull requests
- Databases, APIs, and more

---

## 🎯 Hands-On Practice

Time to put it to work! Make sure you're inside the `copilot-workshop` folder you created in Part 1 (or any folder with a few files in it). Then run:

```bash
copilot
```

Try each of these tasks — just type them naturally, like sending a message:

### Task 1: Explore Your Current Folder

Ask Copilot to look around and tell you what's here:

```
look at the files in this folder and tell me what this project seems to be about
```

Copilot will list your files and give you a summary. Try a follow-up:

```
which of these files is most recently modified?
```

---

### Task 2: Create a File

Ask Copilot to create something for you:

```
create a file called action-items.txt with 5 example action items from a fictional project kickoff meeting — use a team working on a new Microsoft 365 integration
```

Then verify it was created:

```
show me what you wrote in action-items.txt
```

---

### Task 3: Research Something

Ask Copilot a knowledge question — no files needed, just curiosity:

```
what's the difference between GitHub Copilot in VS Code and GitHub Copilot CLI? when would I use each one?
```

Then go deeper:

```
which one is better for someone who doesn't write code?
```

---

### Task 4: Work With an Existing File

Ask Copilot to improve what it just created:

```
read action-items.txt and add two more items to it — one about scheduling a follow-up meeting and one about sharing the meeting notes with stakeholders
```

Confirm the changes:

```
read back the full updated file
```

---

> 💡 **Pro tip:** You don't need special commands. Copilot understands plain English — just describe what you want, like you're asking a colleague.

---

## Quick Reference: Key Slash Commands

| Command | What It Does |
|---------|-------------|
| `/help` | Show all available commands |
| `/model` | Switch between AI models |
| `/plan` | Enter planning mode before executing |
| `/diff` | Review file changes before approving |
| `/context` | See what Copilot knows about your session |
| `/reset-allowed-tools` | Clear any auto-approved tool permissions |
| `Ctrl+C` | Exit the current session |

---

## ✅ Part 2 Complete

You now have:
- [ ] Copilot CLI installed and authenticated
- [ ] Asked Copilot to explore your folder
- [ ] Asked Copilot to create a file
- [ ] Asked Copilot to research a topic
- [ ] A feel for the interactive interface and key slash commands

→ [Part 3: Configure MCP Servers](03-mcp-setup.md)
