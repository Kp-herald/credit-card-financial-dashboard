# Credit Card Financial Dashboard — Power BI Project
 
A two-page interactive Power BI dashboard built to analyze credit card customer behavior and transaction patterns. The project provides actionable insights across revenue, customer demographics, transaction types, and card categories.
 
---
 ## Project Structure
 
```
credit-card-financial-dashboard/
├── credit_card.csv                        # Transaction-level raw data
├── cust_detail.csv                        # Customer demographics raw data
├── Credit_Card_Dashboard.pbix             # Power BI Dashboard file
├── SCREENSHOT/
│   ├── Credit_Card_Customer_Report.png
│   └── Credit_Card_Transaction_Report.png
└── README.md
```
---

## Dashboard Overview
 
### Page 1 — Credit Card Transaction Report
 
Focuses on **how customers spend** and which card/transaction types drive revenue.
 
**KPI Cards:**
- Total Revenue: **55.3M**
- Total Interest: **7.8M**
- Transaction Amount: **45M**
- Transaction Count: **656K**
**Visuals Included:**
- Revenue by Use Chip Type (Swipe: 35M / Chip: 17M / Online: 3M)
- Quarterly Revenue & Total Transaction Count (Combo Line + Bar Chart)
- Card Category table (Revenue, Interest Earned, Annual Fees)
- Revenue by Expenditure Type (Bills, Entertainment, Fuel, Grocery, Food, Travel)
- Revenue by Education Level
- Revenue by Customer Job
- Revenue by Card Category (Blue: 46M dominant)
**Filters / Slicers:**
- Week Start Date (dropdown)
- Quarter selector (Q1–Q4)
- Gender (F / M)
- Card Category (Silver / Blue / Gold / Platinum)
- Salary Group (Low / Med / High)
---

 ### Page 2 — Credit Card Customer Report
 
Focuses on **who the customers are** and how revenue breaks down by demographics.
 
**KPI Cards:**
- Total Revenue: **55.3M**
- Total Interest: **7.8M**
- Total Income: **576M**
- Customer Satisfaction Score (CSS): **3.19**
**Visuals Included:**
- Revenue vs Gender (Line Chart — Jan to Dec 2023)
- Age Group breakdown (Horizontal Bar Chart)
- Top 5 States by Revenue (TX, NY, CA, FL, NJ)
- Salary Group distribution (High / Med / Low)
- Dependent Count analysis
- Marital Status comparison
- Education Level breakdown
- Customer Job table (Revenue, Transaction Amount, Income)
**Filters / Slicers:**
- Week Start Date (dropdown)
- Quarter selector (Q1–Q4)
- Gender (F / M)
- Card Category (Silver / Blue / Gold / Platinum)
- Transaction Type (Swipe / Online / Chip)
---


## DAX Measures Used
 
```dax
-- Week-over-Week Revenue
WoW Revenue % =
  VAR CurrentWeek = CALCULATE([Total Revenue], FILTER(ALL(credit_card), credit_card[Week_Num2] = MAX(credit_card[Week_Num2])))
  VAR PreviousWeek = CALCULATE([Total Revenue], FILTER(ALL(credit_card), credit_card[Week_Num2] = MAX(credit_card[Week_Num2]) - 1))
  RETURN DIVIDE((CurrentWeek - PreviousWeek), PreviousWeek)
 
-- Age Group Column (Calculated Column)
AgeGroup =
  SWITCH(
    TRUE(),
    cust_detail[Customer_Age] < 30, "< 30",
    cust_detail[Customer_Age] >= 30 && cust_detail[Customer_Age] < 40, "30-40",
    cust_detail[Customer_Age] >= 40 && cust_detail[Customer_Age] < 50, "40-50",
    cust_detail[Customer_Age] >= 50 && cust_detail[Customer_Age] < 60, "50-60",
    "60+"
  )
 
-- Income Group Column (Calculated Column)
IncomeGroup =
  SWITCH(
    TRUE(),
    cust_detail[Income] < 35000, "Low",
    cust_detail[Income] >= 35000 && cust_detail[Income] < 70000, "Med",
    "High"
  )
```
 
---
 
## Dashboard Screenshots

### Transaction Report
![Credit Card Transaction Report](Credit_Card_Transaction_Report.png)
  
### Customer Report
![Credit Card Customer Report](Credit_Card_Customer_Report.png)
 
---
 
## Tools & Technologies
 
- **Power BI Desktop** — Report building and visualization
- **DAX** — Calculated columns and measures
- **Power Query (M)** — Data transformation and shaping
- **CSV / Excel** — Source data
---
 
## Key Insights
 
- **Blue card holders** generate the most revenue at **46M**, far exceeding Silver, Gold, and Platinum combined.
- **Businessmen** are the top revenue-generating customer segment at **17.4M**.
- **Swipe transactions** dominate usage, contributing **35M** vs just **3M** for Online.
- **Bills** are the top expenditure category at **14M**, followed by Entertainment and Fuel.
- **Graduates** account for the highest revenue by education level at **22M**.
- Revenue is relatively stable across quarters, with Q1 and Q3 slightly leading.
- **High salary group** customers contribute the most — **22M** vs **10M** for Low salary group.
---
 
## How to Use
 
1. Open `Credit_Card_Dashboard.pbix` in Power BI Desktop.
2. Use the **Quarter buttons (Q1–Q4)** at the top to filter by quarter.
3. Use the **Week_Start_Date slicer** to drill into specific weeks.
4. Use the **Gender, Card Category, and Transaction Type** slicers for cross-filtering.
5. Hover over any chart for detailed tooltips.
6. Click on any bar/segment to cross-highlight related visuals across the page.
---
 
## Author

**K Pramod Herald**
 
- kpherald7@gmail.com
- [LinkedIn](https://www.linkedin.com/in/k-pramod-herald-92a27b295)
