# Part 6: Notes → Word Document

> **Time:** ~4 minutes  
> **Goal:** Turn rough, messy notes into a clean, structured Word document — without opening Word

---

## The Problem

You took rough notes during a strategy session. They're a mix of bullet points, half-sentences, and things you meant to clean up. Now you need to send a proper document to stakeholders.

**Without CLI:** 30 minutes reformatting in Word.  
**With CLI:** 2 minutes.

---

## Sample Data for This Exercise

We've included a realistic set of meeting notes to practice with!

📁 **File:** `workshop/sample-data/meeting-notes.txt`

These are rough (intentionally messy!) notes from a fictional Copilot CLI workshop planning session — decisions made, action items, open questions, and random side comments mixed together.

---

## Task 1: Notes → Structured Word Document

**Use the sample file:**

```
read the meeting notes in workshop/sample-data/meeting-notes.txt and create a structured Word document with clear sections, headers, and bullet points
```

**Or use your own file:**

```
take the meeting notes in ~/Documents/my-notes.txt and create a structured Word document with clear sections, headers, and bullet points
```

**Or paste notes directly:**

```
take these meeting notes and create a structured Word document:

[paste your notes here]
```

**Or from SharePoint (requires WorkIQ):**

```
take the latest meeting notes document from the "Strategy" SharePoint library and create a clean Word document from it
```

---

## Task 2: Ask for a Specific Format

Be specific — Copilot will match whatever structure you describe:

```
take these meeting notes and create a 10-slide presentation outline with:
- A title for each slide
- 3-5 key bullet points per slide
- Brief speaker notes for each slide
```

**Example output:**

```
📄 Presentation Outline: Copilot CLI Workshop Planning

Slide 1: Executive Summary
• 200+ attendees registered for June 3rd session
• Room confirmed: Main Auditorium
• Presenter lineup: Priya, James, Aarav, Sofia
Speaker notes: Open with the headline number to grab attention...

Slide 2: Key Decisions Made
...
```

---

## Task 3: Save the Output

Once you're happy with the structure:

```
save this as a Word document at ~/Documents/Workshop-Planning-Summary.docx
```

> ✅ **Result:** A properly structured `.docx` file, ready to open in Word — without touching Word at all.

---

## Prompt Reference

| What You Want | Prompt to Use |
|--------------|---------------|
| Notes → Word doc | `read [file] and create a structured Word document with clear sections and headers` |
| Notes → slide outline | `create a 10-slide presentation outline with titles, bullets, and speaker notes` |
| Save the output | `save this as a Word document at ~/Documents/[filename].docx` |
| From SharePoint | `take the latest notes from the "[site]" SharePoint library and create a Word document` |

---

## ✅ Part 6 Complete

You've learned how to:
- Point Copilot at a local file, pasted text, or SharePoint document
- Generate a structured Word document from messy notes
- Build a presentation outline in seconds

→ [Part 7: Meeting Decisions & Action Items](07-meeting-decisions.md)
