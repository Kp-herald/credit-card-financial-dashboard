# Credit Card Financial Analytics Dashboard — SQL & Power BI

An interactive **Credit Card Financial Analytics Dashboard** built using **SQL and Power BI** to analyze customer behavior, transaction patterns, revenue performance, and customer demographics.

The project follows an end-to-end analytics workflow where raw customer and transaction data is analyzed and prepared using **SQL**, then transformed into an interactive dashboard using **Power BI and DAX**.

---

## Project Overview

This project analyzes credit card transactions and customer information to identify:

* Revenue and transaction performance
* Customer spending behavior
* Card category performance
* Transaction type trends
* Customer demographics
* Income and salary segments
* Expenditure patterns
* Customer job and education segments
* Quarterly and weekly revenue trends

The dashboard provides an interactive way to explore these metrics using filters and cross-highlighting.

---

## Analytics Workflow

```text
Raw CSV Data
     ↓
SQL
     ↓
Data Analysis & Preparation
     ↓
Power BI
     ↓
Power Query / Data Modeling
     ↓
DAX Measures & Calculated Columns
     ↓
Interactive Dashboard
```

---

## Project Structure

```text
credit-card-financial-dashboard/
│
├── credit_card.csv
├── cust_detail.csv
│
├── SQL/
│   └── credit_card_analysis.sql
│
├── Credit_Card_Dashboard.pbix
│
├── SCREENSHOT/
│   ├── Credit_Card_Customer_Report.png
│   └── Credit_Card_Transaction_Report.png
│
└── README.md
```

---

## Tools & Technologies

| Tool / Technology | Purpose                                            |
| ----------------- | -------------------------------------------------- |
| **SQL**           | Data querying, analysis, filtering and aggregation |
| **Power BI**      | Dashboard development and visualization            |
| **DAX**           | Measures and calculated columns                    |
| **Power Query**   | Data transformation and shaping                    |
| **CSV**           | Raw customer and transaction data                  |

---

# SQL Analysis

SQL was used to work with the raw credit card datasets and analyze important business metrics before visualization.

Key analysis areas included:

* Total revenue
* Transaction amount
* Transaction count
* Interest earned
* Revenue by card category
* Revenue by transaction type
* Revenue by expenditure type
* Revenue by customer job
* Revenue by education level
* Revenue by salary group
* Customer demographic analysis
* Quarterly and weekly performance

Example SQL analysis areas:

```sql
-- Total Revenue
SELECT
    SUM(Revenue) AS Total_Revenue
FROM credit_card;
```

```sql
-- Revenue by Card Category
SELECT
    Card_Category,
    SUM(Revenue) AS Total_Revenue
FROM credit_card
GROUP BY Card_Category
ORDER BY Total_Revenue DESC;
```

```sql
-- Revenue by Transaction Type
SELECT
    Use_Chip,
    SUM(Revenue) AS Total_Revenue,
    COUNT(*) AS Transaction_Count
FROM credit_card
GROUP BY Use_Chip
ORDER BY Total_Revenue DESC;
```

> The SQL analysis was used to understand the dataset and derive business insights before presenting them through Power BI.

---

# Power BI Dashboard

The Power BI report contains two main pages.

## Page 1 — Credit Card Transaction Report

This page focuses on **transaction behavior and revenue performance**.

### KPI Cards

* **Total Revenue:** 55.3M
* **Total Interest:** 7.8M
* **Transaction Amount:** 45M
* **Transaction Count:** 656K

### Visualizations

* Revenue by Use Chip Type
* Quarterly Revenue and Transaction Count
* Revenue by Card Category
* Revenue by Expenditure Type
* Revenue by Education Level
* Revenue by Customer Job
* Card Category performance table

### Filters / Slicers

* Week Start Date
* Quarter
* Gender
* Card Category
* Salary Group

---

# Page 2 — Credit Card Customer Report

This page focuses on **customer demographics and revenue contribution**.

### KPI Cards

* **Total Revenue:** 55.3M
* **Total Interest:** 7.8M
* **Total Income:** 576M
* **Customer Satisfaction Score:** 3.19

### Visualizations

* Revenue by Gender
* Revenue by Age Group
* Top 5 States by Revenue
* Salary Group distribution
* Dependent Count analysis
* Marital Status comparison
* Education Level breakdown
* Customer Job analysis

### Filters / Slicers

* Week Start Date
* Quarter
* Gender
* Card Category
* Transaction Type

---

# DAX Measures & Calculated Columns

DAX was used in Power BI to create calculated metrics and customer segments.

### Week-over-Week Revenue

```dax
WoW Revenue % =
VAR CurrentWeek =
    CALCULATE(
        [Total Revenue],
        FILTER(
            ALL(credit_card),
            credit_card[Week_Num2] = MAX(credit_card[Week_Num2])
        )
    )
VAR PreviousWeek =
    CALCULATE(
        [Total Revenue],
        FILTER(
            ALL(credit_card),
            credit_card[Week_Num2] = MAX(credit_card[Week_Num2]) - 1
        )
    )
RETURN
    DIVIDE(
        CurrentWeek - PreviousWeek,
        PreviousWeek
    )
```

### Age Group

```dax
AgeGroup =
SWITCH(
    TRUE(),
    cust_detail[Customer_Age] < 30, "< 30",
    cust_detail[Customer_Age] >= 30 &&
        cust_detail[Customer_Age] < 40, "30-40",
    cust_detail[Customer_Age] >= 40 &&
        cust_detail[Customer_Age] < 50, "40-50",
    cust_detail[Customer_Age] >= 50 &&
        cust_detail[Customer_Age] < 60, "50-60",
    "60+"
)
```

### Income Group

```dax
IncomeGroup =
SWITCH(
    TRUE(),
    cust_detail[Income] < 35000, "Low",
    cust_detail[Income] >= 35000 &&
        cust_detail[Income] < 70000, "Med",
    "High"
)
```

---

# Dashboard Screenshots

## Transaction Report

![Credit Card Transaction Report](SCREENSHOT/Credit_Card_Transaction_Report.png)

## Customer Report

![Credit Card Customer Report](SCREENSHOT/Credit_Card_Customer_Report.png)

---

# Key Business Insights

### 1. Blue Card Dominates Revenue

Blue card holders generate approximately **46M in revenue**, making the Blue category the strongest contributor among the card categories.

### 2. Swipe Transactions Lead

Swipe transactions contribute approximately **35M in revenue**, significantly higher than Chip and Online transactions.

### 3. Bills Are the Largest Expenditure Category

Bills generate approximately **14M in revenue**, followed by categories such as Entertainment and Fuel.

### 4. Businessmen Generate High Revenue

Businessmen represent one of the strongest customer job segments, contributing approximately **17.4M in revenue**.

### 5. Graduates Generate the Highest Revenue

Customers with a graduate-level education contribute approximately **22M in revenue**.

### 6. High-Income Customers Contribute More Revenue

The High salary group contributes approximately **22M**, compared with approximately **10M** from the Low salary group.

### 7. Revenue Remains Relatively Stable

Revenue performance remains relatively consistent across quarters, with some variation between Q1, Q2, Q3, and Q4.

---

# How to Use the Dashboard

1. Open `Credit_Card_Dashboard.pbix` using **Power BI Desktop**.
2. Use the **Quarter** selector to filter dashboard results.
3. Use the **Week Start Date** slicer to analyze specific periods.
4. Apply filters such as **Gender, Card Category, Salary Group, and Transaction Type**.
5. Hover over visualizations to view detailed tooltips.
6. Select any chart element to cross-filter related visuals.
7. Use the dashboard pages to switch between **Transaction Analysis** and **Customer Analysis**.

---

# Skills Demonstrated

This project demonstrates practical experience with:

* SQL
* Data Analysis
* Data Cleaning & Transformation
* Data Aggregation
* Power BI
* DAX
* Power Query
* Data Modeling
* Interactive Dashboard Development
* KPI Development
* Business Intelligence
* Customer & Transaction Analytics
* Business Insights

---

# Author

**K Pramod Herald**

📧 **Email:** [kpherald7@gmail.com](mailto:kpherald7@gmail.com)

🔗 **LinkedIn:** [K Pramod Herald](https://www.linkedin.com/in/k-pramod-herald-92a27b295)
