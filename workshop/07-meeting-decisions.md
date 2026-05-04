# Part 7: Meeting Decisions & Action Items

> **Time:** ~4 minutes  
> **Goal:** Extract clean decisions, owners, and open questions from messy meeting notes — and turn them into a ready-to-send follow-up email

---

## The Problem

You were in a 90-minute working session. Lots of discussion, a few key decisions, several commitments made. Now no one's sure exactly what was agreed, who owns what, or what's still open.

Sound familiar?

---

## Sample Data for This Exercise

📁 **File:** `workshop/sample-data/meeting-notes.txt`

The same workshop planning notes from Part 6 — only this time, instead of formatting them into a document, you're going to extract the signal: decisions, owners, and unresolved questions.

---

## Task 1: Extract Decisions and Action Items

```
read the meeting notes in workshop/sample-data/meeting-notes.txt and extract all decisions made, action items with owners and due dates, and unresolved questions
```

**Copilot returns:**

```
✅ Decisions Made
• Auditorium confirmed for June 3rd, 9:00 AM–12:00 PM
• Intro should explicitly say this is not a coding workshop
• Use sample data files instead of live attendee data
• Demo order confirmed: email triage → meeting notes → CSV
• James will give a 60-second terminal explainer before the first demo
• Agent365 MCP config limited to Mail + Calendar for the workshop

📋 Action Items
• Aarav → Finalize sample data files — due May 15
• Aarav → Send workshop repo link and setup instructions to attendees
• Priya → Add "not a coding workshop" language to slide — due May 12
• James → Complete slide deck and share for review — due May 14
• Sofia → Prepare demo scripts with exact prompts — due May 16
• Sofia → Create take-home cheat sheet PDF — due May 20
• Kenji → Pre-approve WorkIQ admin consent (NA tenant) — due May 23
• Kenji → Loop in EMEA IT — due May 16
• Kenji → Send prereq check script to attendees — due May 28

❓ Open Questions
• Should EMEA registration open now or wait for admin consent?
• Virtual attendance option? (needs Teams Live Event — decision by May 20)
• What's the escalation path if Copilot seat isn't approved in time?
• Cheat sheet: Contoso branding or plain GitHub Copilot branding?
```

---

## Task 2: Extract from a Live Teams Chat

If the discussion happened in Teams (requires WorkIQ MCP):

```
read my Teams chat from the "Workshop Planning" channel today and extract all decisions, action items with owners, and anything still unresolved
```

---

## Task 3: Turn It Into a Follow-Up Email

```
turn these action items and decisions into a brief follow-up email I can send to the team
```

**Example output:**

```
Subject: Meeting Follow-Up — Workshop Planning Sync (May 8)

Hi team,

Thanks for a productive session! Here's what we agreed and what's next:

✅ Decisions
• June 3rd in the Auditorium, 9 AM–12 PM — locked
• We'll use sample data files instead of live attendee data
• Demo order: email triage → notes → CSV
• Agent365: Mail + Calendar only for the workshop

📋 Your Action Items
• Aarav: Sample data files → May 15
• Aarav: Send workshop repo link and setup instructions
• Priya: "Not a coding workshop" slide edit → May 12
• James: Slide deck draft + share for review → May 14
• Sofia: Demo scripts with prompts → May 16
• Sofia: Take-home cheat sheet PDF → May 20
• Kenji: WorkIQ admin consent (NA) → May 23
• Kenji: Loop in EMEA IT → May 16
• Kenji: Send prereq check script → May 28

❓ Still Open — Need Decisions
• EMEA registration: open now or wait? (@Aarav @Priya to decide)
• Virtual/Teams Live Event option: need answer by May 20
• Copilot seat escalation path — Aarav to check with GitHub CSM

Reply if anything above is off!

[Your name]
```

---

## Prompt Reference

| What You Want | Prompt to Use |
|--------------|---------------|
| Extract decisions | `read [file/channel] and extract all decisions made` |
| Extract action items | `list all action items with owners and due dates` |
| Open questions | `list everything that's still unresolved or needs a decision` |
| Follow-up email | `turn these action items and decisions into a follow-up email for the team` |
| Teams chat | `read my Teams chat from [channel] today and extract decisions and action items` |

---

## ✅ Part 7 Complete

You've learned how to:
- Extract structured decisions, owners, and open questions from raw notes
- Pull the same signal from live Teams channel chats
- Generate a clean follow-up email automatically

→ [Part 8: CSV Data to Insights](08-data-insights.md)
