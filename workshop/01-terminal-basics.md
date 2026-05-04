# Part 1: Terminal & CLI 101

> **Time:** ~10 minutes  
> **Goal:** Understand what a terminal is, what CLI and TUI mean, and navigate it with confidence

---

## What Is a Terminal?

A terminal is a **text-based window** where you type instructions and your computer responds.

That's it. Nothing more mysterious than that.

> 🎙️ You already do this all the time:
> - "Hey Siri, set a timer for 10 minutes"
> - Searching Google with a question
>
> A terminal is the same idea — you type a request, your computer does the work.

Every computer has one built in:

| Operating System | How to Open |
|-----------------|-------------|
| **Windows** | Press `Start`, type `Terminal`, press Enter |
| **Mac** | Press `Cmd + Space`, type `Terminal`, press Enter |
| **Linux** | Press `Ctrl + Alt + T` |

---

## What Is a Shell?

If the terminal is the **window**, the shell is the **conversation happening inside it**.

The shell is the program that listens to your commands and talks to your computer for you.

| Shell | Where You'll See It |
|-------|---------------------|
| **PowerShell** (`pwsh`) | Windows (modern) — cross-platform |
| **Command Prompt** (`cmd`) | Windows (classic) |
| **Bash / Zsh** | Mac and Linux |

> 💡 **You don't need to pick one.** Your computer already has a default shell. Just open Terminal and start typing.

---

## CLI vs. TUI

You'll hear both terms in this workshop:

### CLI — Command Line Interface

You type one command, get one result back. Simple input → output.

```
$ git commit -m "fix bug"
[main a1b2c3d] fix bug
$
```

### TUI — Terminal User Interface

An interactive, visual experience *inside* the terminal — menus, selections, real-time updates. You launch it once and have a full conversation.

```
$ copilot
? What would you like to do?
❯ Summarize my unread emails
  Draft a reply
  Create a GitHub issue
```

> **GitHub Copilot CLI is a TUI** — you launch it once, then have a rich back-and-forth conversation right in your terminal.

---

## Anatomy of a Command

When you *do* need to type a command, it follows a simple pattern:

```
❯ copilot -p "summarize my unread emails"
    ↑         ↑            ↑
 Program    Flag        Your prompt
```

- **Program** — what you're talking to (`copilot`, `git`, `ls`)
- **Flag** — an option modifier (`-p` means "run this prompt")
- **Prompt** — what you want, in plain English

---

## 🗺️ Navigation Commands

These commands work the same way on every platform. Open your terminal and try them:

| Command | What It Does | Example |
|---------|-------------|---------|
| `pwd` | Print your current folder location | `pwd` |
| `ls` | List files and folders here | `ls` |
| `cd folder` | Move into a folder | `cd Documents` |
| `cd ..` | Go back up one folder | `cd ..` |
| `mkdir name` | Create a new folder | `mkdir my-workshop` |
| `clear` | Clear the terminal screen | `clear` |

> 💡 **Windows note:** In PowerShell, `ls`, `cd`, `mkdir`, `pwd`, and `clear` all work. If you're in the classic Command Prompt, use `dir` instead of `ls`.

### 🚀 Try It: Navigate Around

Open your terminal and run these in order:

```bash
pwd
```
*(where am I?)*

```bash
ls
```
*(what's here?)*

```bash
cd Desktop
ls
```
*(peek inside Desktop)*

```bash
cd ..
```
*(step back out)*

---

## 📄 File Operations

Now let's work with actual files. Pick your platform:

### View a File

Read the contents of a file right in the terminal — great for checking notes or configs.

**Windows (PowerShell):**

```powershell
Get-Content notes.txt

# Short alias (also works):
cat notes.txt
```

**Mac / Linux:**

```bash
cat notes.txt

# View one page at a time:
less notes.txt  # press Q to quit
```

### Create a File

**Windows (PowerShell):**

```powershell
# Create an empty file:
New-Item notes.txt

# Create a file with content:
"Hello from PowerShell!" | Out-File notes.txt
```

**Mac / Linux:**

```bash
# Create an empty file:
touch notes.txt

# Create a file with content:
echo "Hello from Terminal!" > notes.txt
```

### Write and Append to a File

**Windows (PowerShell):**

```powershell
# Overwrite file content:
"New content" | Out-File notes.txt

# Append a line (keep existing content):
"Another line" | Add-Content notes.txt
```

**Mac / Linux:**

```bash
# Overwrite file content:
echo "New content" > notes.txt

# Append a line (keep existing content):
echo "Another line" >> notes.txt
```

### Copy a File

**Windows (PowerShell):**

```powershell
# Copy a file to a new name:
Copy-Item notes.txt notes-backup.txt

# Short alias:
cp notes.txt notes-backup.txt
```

**Mac / Linux:**

```bash
# Copy a file to a new name:
cp notes.txt notes-backup.txt

# Copy to a different folder:
cp notes.txt ~/Desktop/notes.txt
```

### Move or Rename a File

**Windows (PowerShell):**

```powershell
# Rename a file:
Move-Item notes.txt meeting-notes.txt

# Move to another folder:
Move-Item notes.txt ~/Documents/notes.txt
```

**Mac / Linux:**

```bash
# Rename a file:
mv notes.txt meeting-notes.txt

# Move to another folder:
mv notes.txt ~/Documents/notes.txt
```

### Delete a File

**Windows (PowerShell):**

```powershell
# Delete a file:
Remove-Item notes.txt

# Short alias:
rm notes.txt
```

**Mac / Linux:**

```bash
# Delete a file:
rm notes.txt

# Delete a folder and everything in it:
rm -rf my-folder/
```

> ⚠️ **Heads up:** `rm` is permanent — there's no Recycle Bin. Double-check the filename before pressing Enter!

---

## 🚀 Mini Hands-On Walkthrough

Practice the commands end-to-end. Open your terminal and run these one at a time:

```bash
# 1. Go to your Desktop
cd ~/Desktop

# 2. Create a new practice folder
mkdir copilot-workshop

# 3. Move into it
cd copilot-workshop

# 4. Create a notes file
echo "Day 1: Learning GitHub Copilot CLI" > my-notes.txt

# 5. Verify it was created
ls
```

Now view what you wrote:

**Windows (PowerShell):**

```powershell
Get-Content my-notes.txt
```

**Mac / Linux:**

```bash
cat my-notes.txt
```

Continue:

```bash
# 6. Make a backup copy
cp my-notes.txt my-notes-backup.txt

# 7. Confirm both files exist
ls

# 8. Add a second line to the original
echo "Day 1: Installed Copilot CLI!" >> my-notes.txt

# 9. View the updated file again (use tab above)
```

> ✅ You just created, read, copied, and edited a file — without ever opening a folder window!

---

## CLI vs. UI: When to Use Each

| Use CLI When... | Use a UI When... |
|-----------------|-----------------|
| You do this task every week | You're exploring something new |
| Lots of information to process | You need visual layout or drag-and-drop |
| You need a specific answer fast | Collaborating live with others |
| You want to chain steps together | First-time setup of something |
| Speed and consistency matter | Rich formatting and design |

> **Pro tip:** Explore in the UI, then automate with CLI.

---

## ✅ Part 1 Complete

You now know:
- [ ] What a terminal, shell, CLI, and TUI are
- [ ] How to open a terminal on your machine
- [ ] The anatomy of a command
- [ ] Navigation commands: `pwd`, `ls`, `cd`, `mkdir`
- [ ] File operations: view, create, copy, move, delete

→ [Part 2: Set Up Copilot CLI](02-copilot-cli-setup.md)
