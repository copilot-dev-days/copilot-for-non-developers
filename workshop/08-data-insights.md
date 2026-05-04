# Part 8: CSV Data to Insights

> **Time:** ~5 minutes  
> **Goal:** Analyze a CSV file and surface actionable insights — no Excel, no formulas, no pivot tables

---

## The Problem

You have a spreadsheet: survey results, budget tracker, project list, feedback data. You need answers fast. What do people think? Where are the pain points? What's trending?

**Without CLI:** Open Excel, build pivot tables, write AVERAGEIF formulas, manually scan hundreds of rows.  
**With CLI:** Ask in plain English. Done.

---

## Sample Data for This Demo

We've included a realistic CSV to practice with!

📁 **File:** `workshop/sample-data/copilot-feedback.csv`

This dataset captures **post-onboarding feedback survey results** from teams at Contoso — 4 months of responses across NA and EMEA, covering Platform Engineering, AI Products, Developer Tools, Developer Relations, Product Management, Operations, Finance, and HR.

**Columns:** `Month, Team, Region, Responses, AvgSatisfaction, NPS, WouldRecommend, PerceivedTimeSaving, EasiestTask, TopRequest`

| Column | Description |
|--------|-------------|
| `Responses` | Number of survey responses submitted |
| `AvgSatisfaction` | Average satisfaction score (1–5 scale) |
| `NPS` | Net Promoter Score (0–100) |
| `WouldRecommend` | % of respondents who would recommend to a colleague |
| `PerceivedTimeSaving` | Self-reported time savings per week |
| `EasiestTask` | Most commonly cited easiest task |
| `TopRequest` | Most frequently requested improvement |

---

## Task 1: Point Copilot at the CSV

**Use the sample file:**

```
read workshop/sample-data/copilot-feedback.csv and give me a summary of:
- Overall satisfaction trends across teams and regions
- Which team has the highest NPS?
- How has sentiment changed from January to April?
- Any notable differences between NA and EMEA?
```

**Use your own file:**

Put a CSV file on your desktop or Documents folder, note the path, and run:

```
read ~/Desktop/my-data.csv and give me a summary of the data
```

---

## Task 2: Run the Analysis

```
read workshop/sample-data/copilot-feedback.csv and give me average satisfaction and NPS by region, the top 3 teams by WouldRecommend score, and show how sentiment has trended month over month
```

**Example output:**

```
📊 Copilot Feedback Analysis — copilot-feedback.csv (41 rows)

Satisfaction by Region (April avg):
  NA           4.2 / 5.0  ████████████████ 
  EMEA         4.3 / 5.0  █████████████████

Top Teams by "Would Recommend" (April):
  1. AI Products — NA       94%  (+12% since Jan)
  2. Developer Relations — NA  93%  (+8% since Jan)
  3. AI Products — EMEA     92%  (+12% since Jan)

Month-over-Month NPS (all teams avg):
  Jan → Feb: +8 points
  Feb → Mar: +10 points
  Mar → Apr: +9 points
  Consistent improvement across all regions! 🚀

Perceived Time Savings (April):
  4+ hrs/wk:  Platform Eng, AI Products, Developer Tools, Developer Relations
  2-4 hrs/wk: Product Management, Operations
  1-2 hrs/wk: Finance, HR  ← strong growth opportunity
```

---

## Task 3: Ask Follow-Up Questions

Copilot keeps context between prompts — drill down naturally:

```
which team has the lowest satisfaction score and what do they request most?
```

```
compare NA vs EMEA sentiment trends and highlight the biggest differences
```

```
which teams improved their NPS the most between January and April?
```

```
what are the top 3 most common requests across all teams and regions?
```

---

## Task 4: Export a Clean Summary

Once you have the insights you need:

```
save this analysis as a formatted Word document at ~/Documents/copilot-feedback-summary.docx
```

Or create a summary email:

```
turn this analysis into a brief executive summary email I can send to my manager about how teams feel about Copilot after onboarding
```

---

## Task 5: Build an HTML Report from the Data

Take the analysis one step further — ask Copilot to build a visual web page from it:

```
now build a simple HTML + CSS page that presents this feedback analysis — include a summary section with key stats, a table showing all teams by region with their satisfaction scores and NPS, and simple CSS bar charts for the top 5 teams by WouldRecommend — save it as ~/Desktop/copilot-feedback-report.html
```

**Copilot will generate a complete `.html` file you can open in any browser:**

```
📄 Creating copilot-feedback-report.html...

Sections included:
  ✓ Summary stats (avg satisfaction, top NPS, highest WouldRecommend)
  ✓ Team breakdown table (Month / Team / Region / Satisfaction / NPS)
  ✓ Top 5 teams bar chart (CSS only, no JavaScript)
  ✓ NA vs EMEA comparison

Saved to: ~/Desktop/copilot-feedback-report.html
Open in your browser to view → file:///Users/you/Desktop/copilot-feedback-report.html
```

> 💡 **Try follow-up iterations:**
> ```
> add a section that highlights the 3 most encouraging trends from the data
> ```
> ```
> make the color scheme match Microsoft brand colors — blue and white
> ```
> ```
> add a footer with today's date and a note that this was generated by GitHub Copilot CLI
> ```

---

## More CSV Use Cases

This workflow works for any data you'd normally wrangle in Excel:

| Use Case | Prompt |
|----------|--------|
| Monthly budget review | `read budget.csv and show me actual vs. planned spending by category` |
| Customer list cleanup | `read customers.csv and find all rows with missing email or phone` |
| Inventory check | `read inventory.csv and flag items where stock is below reorder level` |
| Employee survey | `read survey-results.csv and summarize the top themes in the open text responses` |
| Project tracker | `read projects.csv and show me everything overdue grouped by owner` |

---

## Bonus Prompt

```
based on the April trend in copilot-feedback.csv, project what average satisfaction and NPS will look like in July 2026 if the current improvement rate holds
```

Copilot will give you a forward-looking projection — the kind of analysis that usually takes 20 minutes in Excel, done in seconds.

---

## ✅ Part 8 Complete

You just:
- Analyzed a feedback CSV in plain English
- Surfaced satisfaction trends, NPS, and top requests with no formulas
- Drilled down with natural follow-up questions
- Exported a clean summary document

→ [Part 9: Takeaways & Next Steps](09-next-steps.md)
