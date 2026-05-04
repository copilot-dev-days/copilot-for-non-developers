# Part 5: Email Triage & GitHub Issues

> **Time:** ~8 minutes  
> **Goal:** Turn a chaotic inbox into a prioritized action list, then create a GitHub issue from an email thread — all without opening Outlook

---

## The Problem

You open Outlook. 150+ unread emails. Dozens of threads. You spend 30 minutes just figuring out what actually needs your attention today.

**There's a better way.**

---

## Sample Data for This Demo

We've included a realistic email thread to practice with — no need to use your own inbox!

📁 **File:** `workshop/sample-data/email-thread.txt`

This is a fictional thread from the **Contoso GitHub Copilot CLI Workshop Planning** team — multiple senders, decisions made, open questions, and action items buried throughout. Perfect for practicing triage.

> 💡 **To use it:** In Copilot CLI, point to the file:
> ```
> read the email thread in workshop/sample-data/email-thread.txt and summarize it for me
> ```
> 
> Or use your real inbox instead — the prompts below work for both!

---

## What You'll Do in This Demo

1. Triage your inbox by priority
2. Find a specific actionable thread
3. Summarize the key decisions and open questions
4. Draft a professional reply with next steps
5. Create a GitHub issue directly from the email content

---

## Task 1: Triage Your Inbox

Launch Copilot CLI:

```bash
copilot
```

Start with the daily triage skill:

```
show me my inbox and calendar for today
```

Or go deeper with:

```
show me all unanswered emails from last week grouped by priority
```

Copilot will scan your inbox and return something like:

```
🔴 Action Required (3)
  - Budget approval request from Sarah Chen — waiting on you
  - Engineering timeline review — deadline Friday
  - Vendor contract renewal — needs sign-off

🟡 Review (5)
  - Weekly status report from Platform team
  - Design review feedback
  ...

🔵 FYI (12)
  - Team announcements
  - Calendar invites
  ...
```

> 💡 **Try this too:**
> ```
> scan my Teams chats for messages where I am directly asked a question
> ```

---

## Task 2: Dive Into the Most Urgent Thread

Once you've identified a priority thread, read it in full:

```
read the latest email thread from [sender name or subject], summarize the key decisions already made, and list all open questions
```

**Example:**

```
read the latest email thread about the Q3 budget approval, summarize the key decisions already made, and list all open questions
```

Copilot returns a clean structured summary:

```
📧 Thread: Q3 Budget Approval — 7 messages, 4 participants

Decisions Made:
• Engineering headcount approved at 3 new hires
• Marketing budget frozen at current levels
• Decision on cloud infrastructure deferred to Friday call

Open Questions:
• Who owns the final sign-off for the infrastructure line?
• Is the $50K contingency fund included in the current total?
• What's the timeline for the new hire start dates?
```

---

## Task 3: Draft a Professional Reply

Now ask Copilot to draft a reply:

```
draft a professional reply to this thread with a clear summary of next steps and assign owners to each open question
```

Review the draft — Copilot will give you something like:

```
Subject: Re: Q3 Budget Approval — Next Steps

Hi team,

Following our email thread, here's where we stand and what needs to happen next:

✅ Agreed: Engineering headcount (3 hires), Marketing budget frozen
🔄 In Progress: Cloud infrastructure decision — owner: [you] — due: Friday call

Action Items:
• Sarah: Confirm final sign-off authority by EOD Wednesday  
• James: Prepare infrastructure cost breakdown for Friday
• Team: Review proposed hire start dates — respond by Thursday

Let me know if anything above is off.

Best,
[Your name]
```

> You stay in control. **Read it, adjust it, then send from Outlook.** Copilot drafts; you approve.

---

## Task 4: Create a GitHub Issue from the Email

If the email thread surfaces something that needs to be tracked as work, turn it into a GitHub issue:

```
create a GitHub issue in [your-org/your-repo] from this email thread — use the open questions as the issue body and the most urgent item as the title
```

**Copilot will:**
1. Extract the key information
2. Format it as a proper GitHub issue
3. Ask you to confirm before creating it

> ✅ **Expected result:** A GitHub issue created with a clear title, description, and labels — without you leaving the terminal or copy-pasting anything.

---

## Prompt Reference

| What You Want | Prompt to Use |
|--------------|---------------|
| Triage inbox | `show me all unanswered emails from last week grouped by priority` |
| Find specific thread | `read the latest email thread about [topic] and summarize it` |
| Extract decisions | `list all decisions made and open questions in this thread` |
| Draft reply | `draft a professional reply with next steps and assign owners` |
| Create GitHub issue | `create a GitHub issue in [org/repo] from this email thread` |

---

## ✅ Part 5 Complete

You just went from 150 unread emails to:
- A prioritized inbox view
- A structured thread summary
- A ready-to-send reply draft
- A GitHub issue — all in under 3 minutes

→ [Part 6: Notes → Word Document](06-notes-to-docs.md)
