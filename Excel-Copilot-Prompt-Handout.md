# 📊 Copilot in Excel: Student Prompt Handout

### Summarize ➜ Clean ➜ Analyze

**Practice file:** `Meridian-Airport-Ops-Travel-FY26.xlsx`

> **Work through your data in order.** Start by understanding what you have, then fix it, then get insights from it. If you skip ahead to analysis on messy data, you'll get messy answers.

```
 ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
 │ 1. SUMMARIZE │ ──▶ │   2. CLEAN   │ ──▶ │  3. ANALYZE  │
 │  What do I   │     │  Can I trust │     │  What does   │
 │    have?     │     │    it?       │     │  it tell me? │
 └──────────────┘     └──────────────┘     └──────────────┘
```

---

## 📑 Contents

- [The Scenario](#-the-scenario)
- [Meet Your Data](#-meet-your-data)
- [Before You Start](#-before-you-start)
- [How to Use This Handout](#-how-to-use-this-handout)
- [Step 1: Summarize the Data](#-step-1-summarize-the-data)
- [Step 2: Clean the Data](#-step-2-clean-the-data)
- [Step 3: Analyze the Data](#-step-3-analyze-the-data)
- [Capstone: Answer Finance's Challenge](#-capstone-answer-finances-challenge)
- [Prompting Tips](#-prompting-tips)
- [Quick Reference Checklist](#-quick-reference-checklist)

---

## ✈️ The Scenario

You're an analyst on the **Meridian Airport Operations** team. Your team is based in Dallas (DFW) and travels to airport locations across the country for location visits, Go Electric go-lives, training, partner meetings, conferences, and incident response.

Finance has just sent your team this challenge (you'll find it on the **Budget** sheet):

> *Spend **15% less** on travel in FY27 than FY26 actual, while supporting **8 more Go Electric go-lives**.*

Your job is to use Copilot to understand the FY26 travel data, clean it up, and find out **where the money went and where it can be saved**.

---

## 🗂️ Meet Your Data

The workbook has **four sheets**. Each of the first four is set up as an Excel table with the same name as its sheet.

| Sheet / Table | What it holds | Key columns |
|---|---|---|
| **Expenses** | One row per expense line (the main dataset) | `Employee`, `Role`, `Purpose`, `Destination`, `Tier`, `Category`, `ExpenseDate`, `Merchant`, `Amount`, `NightlyRate`, `HotelCap`, `DaysBookedAhead`, `ExceptionReason`, `Receipt`, `DaysToSubmit`, `Status` |
| **Trips** | One row per trip, with the trip total | `TripID`, `Employee`, `Purpose`, `Destination`, `Tier`, `TripStart`, `TripEnd`, `Nights`, `TripTotal` |
| **Budget** | Monthly budget compared with actual spend, plus Finance's FY27 target | `Month`, `Budget`, `Actual` |
| **Team** | Who's on the team | `Employee`, `Role`, `Home Base` |

> 💡 **Tip:** Copilot works with the data you're looking at. **Click inside the table you're asking about** before you send a prompt.

---

## ✅ Before You Start

- [ ] Save **your own copy** of the workbook to **OneDrive or SharePoint**, and make sure **AutoSave is on**.
- [ ] Open the **Expenses** sheet and click anywhere inside the table.
- [ ] Remember **Ctrl + Z** (undo). Copilot can change your data, so undo is your safety net.

---

## 🧭 How to Use This Handout

1. Open **Copilot** from the **Home** tab in Excel.
2. Copy a prompt from the steps below. Each code block has a copy button in GitHub.
3. Paste it into Copilot and send it.
4. **Review every result before you keep it.** Copilot is your assistant. You're still the analyst.

> ✏️ **Make it your own:** Once a prompt works, change the column, employee, city, or month and try again.

---

## 🔍 Step 1: Summarize the Data

**Goal:** Understand what's in the dataset *before* you change anything.
**Sheet:** Start on **Expenses**.

### 1.1 Get the big picture

```
Summarize this data. What is it about, how many rows and columns does it have, and what does each column contain?
```

```
Describe each column in this table, including its data type (text, number, date) and an example value.
```

```
What date range does ExpenseDate cover?
```

### 1.2 Find the key numbers

```
What is the total, average, minimum, and maximum Amount?
```

```
How many unique employees, destinations, and merchants are in this table?
```

```
Show the total Amount by Category, sorted from highest to lowest.
```

```
How many expense lines are there for each Purpose?
```

### 1.3 Understand the business rules

```
What are the different values in Tier, and what HotelCap goes with each tier?
```

```
List the different values in ExceptionReason and how many times each one appears.
```

```
What are the different values in Status and Receipt, and how many rows have each?
```

### 1.4 Spot potential problems early

```
Which columns have blank cells, and how many blanks does each one have?
```

```
Are there any rows that look like duplicates, apart from the LineID?
```

```
Are there any values that look unusual or out of place in this data?
```

### 1.5 Check the other sheets

Click inside the **Trips** table, then:

```
Summarize this table. How many trips are there, and what is the average TripTotal?
```

Click inside the **Budget** table, then:

```
Summarize this table. In how many months was Actual higher than Budget?
```

> 📝 **Write it down:** Keep a short list of what Copilot finds. That's your to-do list for Step 2.

---

## 🧹 Step 2: Clean the Data

**Goal:** Make the data accurate and consistent so you can trust your analysis.
**Sheet:** **Expenses**

> ⚠️ **Review before you keep.** Cleaning prompts change your data. Check the result, and use **Ctrl + Z** if something looks wrong.

### 2.1 Find duplicates

```
Highlight rows that have the same TripID, Employee, Category, ExpenseDate, Merchant, and Amount.
```

```
Add a column called PossibleDuplicate that shows "Yes" when another row has the same TripID, ExpenseDate, Merchant, and Amount.
```

> 🤔 **Think about it:** Why didn't a simple "find duplicate rows" prompt catch these? *(Hint: look at `LineID`.)*

### 2.2 Understand the blanks

Not every blank is a problem. Before you delete or fill anything, find out *why* a cell is empty.

```
Why are NightlyRate, HotelCap, and DaysBookedAhead blank for most rows? Which Category has values in these columns?
```

```
Which rows have a blank SubmittedDate? What is their Status?
```

```
Highlight rows where Receipt is "N".
```

> 🤔 **Think about it:** Should you fill the blanks in `HotelCap` with 0? What would that do to your analysis?

### 2.3 Make values easier to work with

```
Add a column called CategoryGroup that shortens Category. Group both car rental categories as "Car rental" and keep the other categories as they are.
```

```
Add a column called ExpenseMonth that shows the month and year from ExpenseDate.
```

```
Add a column called TripMonth that shows the month and year from TripStart.
```

### 2.4 Flag policy issues

```
Add a column called OverHotelCap that shows "Yes" when NightlyRate is higher than HotelCap.
```

```
Add a column called MissingException that shows "Yes" when NightlyRate is higher than HotelCap and ExceptionReason is blank.
```

```
Highlight rows where Category is "Car rental — other company" and ExceptionReason is blank.
```

```
Add a column called LateSubmission that shows "Yes" when DaysToSubmit is more than 30.
```

### 2.5 Flag outliers

```
Highlight Amount values that are much higher or lower than the rest for their Category.
```

### 2.6 Check your work

```
Summarize this table again. How many rows are flagged as possible duplicates, over the hotel cap, missing an exception reason, or submitted late?
```

> 💡 **Tip:** Flagging is safer than deleting. A flag column lets you filter the problem rows in or out, and you never lose the original data.

---

## 📈 Step 3: Analyze the Data

**Goal:** Turn clean data into answers, trends, and visuals.

### 3.1 Calculate

On the **Expenses** sheet:

```
Add a column called OverCapCost that calculates (NightlyRate minus HotelCap) multiplied by Nights, only when NightlyRate is higher than HotelCap. Otherwise show 0.
```

On the **Trips** sheet:

```
Add a column called CostPerNight that divides TripTotal by Nights.
```

On the **Budget** sheet:

```
Add a column called Variance that calculates Actual minus Budget, and another column that shows the variance as a percentage of Budget.
```

### 3.2 Sort, filter, and highlight

```
Show only the Expenses rows where Purpose is "Go-live support" and Category is "Hotel".
```

```
Sort the Trips table by TripTotal from highest to lowest.
```

```
Highlight the 10 most expensive trips in the Trips table.
```

### 3.3 Summarize with PivotTables

```
Create a PivotTable that shows total Amount by Category and Purpose.
```

```
Create a PivotTable that shows total Amount by Employee, sorted from highest to lowest.
```

```
Create a PivotTable that shows total Amount and the number of trips by Destination.
```

```
Create a PivotTable that shows total Amount by Role and Category.
```

### 3.4 Find trends and patterns

```
Show data insights for this table.
```

```
What trends do you see in total Amount by month?
```

```
Which months had the highest and lowest travel spend? What was different about them?
```

```
Is there a relationship between DaysBookedAhead and NightlyRate for hotel stays?
```

### 3.5 Compare and rank

```
Which 5 destinations have the highest total spend?
```

```
Which Purpose has the highest average TripTotal per trip?
```

```
Compare the average hotel NightlyRate by Tier. Which tier goes over the HotelCap most often?
```

```
What percentage of total Amount does each Category make up?
```

### 3.6 Visualize

```
Create a column chart comparing Budget and Actual by Month.
```

```
Create a chart showing total Amount by Category.
```

```
Create a line chart showing total Amount by month for each Purpose.
```

### 3.7 Ask "what if" and "why"

```
If hotel stays had been booked at or below the HotelCap, how much would we have saved?
```

```
Why was travel spend over budget in April 2026? Which trips, employees, or categories contributed most?
```

```
If DaysToSubmit had been 30 days or less for every expense, how many expense lines would have been affected?
```

---

## 🏆 Capstone: Answer Finance's Challenge

Put it all together. Finance wants **15% less travel spend in FY27 than FY26 actual**, with **8 more Go Electric go-lives**.

```
What was total FY26 travel spend, and what would 15% less than that be?
```

```
What is the average cost of a Go-live support trip? Estimate the cost of 8 more go-live trips.
```

```
Based on this data, suggest 3 ways the team could reduce travel spend by 15% in FY27 while supporting 8 more go-lives. Show the estimated saving for each.
```

```
Write a short summary of the key findings and recommendations that I could send to Finance.
```

> 🤔 **Think about it:** Do you agree with Copilot's recommendations? Which ones are realistic, and which would hurt the business? **You** make the final call.

---

## 💡 Prompting Tips

| Tip | ❌ Instead of… | ✅ Try… |
|---|---|---|
| **Use the real column names** | "Add up the costs" | "Show total `Amount` by `Category`" |
| **Be specific** | "Show me trends" | "Show the monthly trend in `Amount` for `Go-live support`" |
| **Ask one thing at a time** | "Clean, sort and chart this" | One prompt per task |
| **Spell out the rule** | "Flag bad hotels" | "Show 'Yes' when `NightlyRate` is higher than `HotelCap`" |
| **Follow up** | Starting over | "Now break that down by `Tier`" |
| **Ask it to explain** | Guessing at a formula | "Explain how this formula works" |

### 🧩 A simple prompt formula

```
[Action] + [Column/Data] + [Condition or Detail] + [Output]
```

**Example:**

> *Create* **(action)** a PivotTable of `Amount` **(data)** by `Destination` for Go-live support trips **(detail)**, sorted highest to lowest **(output)**.

---

## 📋 Quick Reference Checklist

| Step | Ask yourself | Done? |
|---|---|---|
| **1. Summarize** | Do I know what's in each sheet, the date range, and the business rules (tiers, caps, exceptions)? | ☐ |
| **2. Clean** | Did I flag duplicates, missing receipts, late submissions, and policy issues? | ☐ |
| **2. Check** | Did I tell the difference between *expected* blanks and real problems? | ☐ |
| **3. Analyze** | Did I calculate, summarize, find trends, and visualize? | ☐ |
| **Capstone** | Can I explain to Finance where to save 15%? | ☐ |
| **Review** | Did I check Copilot's results before trusting them? | ☐ |

---

> 🚀 **Remember:** *Summarize it. Clean it. Then make it talk.*
>
> Copilot works fast, but you still check the results.
