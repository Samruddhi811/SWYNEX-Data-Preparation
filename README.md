# SWYNEX Interactive Dashboard: Netflix Customer Churn Analysis

An interactive Power BI dashboard that helps business users understand **who is leaving Netflix, where, and why**, so retention teams can act on it.

Built as part of the **SWYNEX Technologies** Data Analytics Internship (Task 3), on top of the Netflix churn project prepared in earlier tasks.

---

## 1. Project Overview

Customer churn (customers cancelling their subscription) directly reduces revenue. This project cleans and models a Netflix customer dataset, defines business KPIs with DAX, and presents them in an interactive dashboard where users can slice churn by subscription plan, region, device, favourite genre and payment method.

## 2. Business Questions Answered

- What is the overall churn rate?
- Which subscription plan loses the most customers?
- Which regions have the highest churn?
- How does churn differ by device, and how does it compare with the overall average?
- Does watch time relate to churn?
- How much monthly revenue is at risk because of churn?
- Do favourite genre or payment method influence churn?

## 3. Tools Used

| Tool | Purpose |
|---|---|
| Power BI Desktop | Report building and visuals |
| Power Query | Data cleaning and transformation |
| DAX | KPI measures |
| GitHub | Version control and submission |

## 4. Project Workflow (from scratch)

### Step 1: Data preparation (Power Query)
1. Imported the raw Netflix customer CSV into Power BI (Get Data → Text/CSV).
2. Checked data types, removed duplicates and handled null or blank values.
3. Standardised text columns (trimmed spaces, consistent casing).
4. Split the data into a fact table and dimension tables.

### Step 2: Data model (star schema)

```
Dim_Device ─────┐
Dim_Genre ──────┤
Dim_Payment ────┼──► Fact_Customers
Dim_Region ─────┤
Dim_Subscription┘
```

| Table | Type | Contains |
|---|---|---|
| `Fact_Customers` | Fact | One row per customer: churn flag, watch hours, monthly revenue, keys to all dimensions |
| `Dim_Device` | Dimension | Desktop, Laptop, Mobile, Tablet, TV |
| `Dim_Genre` | Dimension | Favourite genre (Action, Comedy, Documentary, Drama, Horror, Romance, ...) |
| `Dim_Payment` | Dimension | Credit Card, Crypto, Debit Card, Gift Card, PayPal, ... |
| `Dim_Region` | Dimension | North America, South America, Europe, Africa, Oceania, Asia |
| `Dim_Subscription` | Dimension | Basic, Standard, Premium |
| `_Measures` | Measure table | All DAX measures, kept in one place |

Each dimension has a one-to-many relationship to `Fact_Customers` (single direction filter).

### Step 3: DAX measures (`_Measures` table)

| Measure | Meaning |
|---|---|
| Total Customers | Number of customers in the current filter |
| Churned Customers | Customers who churned |
| Churn Rate % | Churned Customers ÷ Total Customers |
| Overall Churn Rate | Churn rate across the whole dataset, ignoring slicers (benchmark) |
| Churn vs Overall (pp) | Churn Rate % minus Overall Churn Rate, in percentage points |
| Avg Watch Hours | Average watch hours per customer |
| Monthly Revenue | Sum of monthly revenue |
| Revenue at Risk | Monthly revenue lost or at risk from churned customers |


### Step 4: Dashboard design
- **Page 1:** overview (add a one-line description of your Page 1 here).
- **Page 2:** churn deep-dive, described below.

## 5. Dashboard Features

**Visuals**
- **Churn Rate by Subscription** (column chart): compares Basic, Standard and Premium.
- **Churn Rate by Region** (bar chart): compares the six regions.
- **Table by Device**: churn rate, average watch hours and churn vs overall (pp) per device.

**Slicers (interactive filters)**
- Favourite Genre
- Payment Method

Clicking any bar, slicer value or table row cross-filters the other visuals, so a user can answer questions such as "What is churn for Debit Card payers in Europe?"

## 6. Key Insights

> Check these against your dashboard with **all slicers cleared** before publishing. The values below were read from Page 2 while the Payment Method slicer was filtered to Debit Card, so they may change.

- **Basic plan churn is far higher** (about 0.60) than Standard (about 0.33) and Premium (about 0.34).
- **North America has the highest regional churn** (about 0.49) and Asia the lowest (about 0.37).
- **Desktop users churn least** (about 0.33) and also watch the most (about 14 hrs on average). TV and Mobile users churn most (about 0.46 to 0.48) with lower watch hours.
- Lower watch hours appear alongside higher churn, which suggests engagement is an early warning signal.

## 7. Recommendations

1. Offer upgrade incentives or trial benefits to Basic plan users to reduce their churn.
2. Run region-specific retention campaigns, starting with North America and South America.
3. Improve the TV and Mobile experience, and nudge low-watch-time users with personalised recommendations.
4. Track Revenue at Risk monthly so retention spending can be prioritised.

## 8. Repository Structure

```
SWYNEX-Interactive-Dashboard/
├── Netflix_Churn_Dashboard.pbix
├── data/
│   └── netflix_customers.csv
├── screenshots/
│   ├── page1.png
│   └── page2.png
├── docs/
│   └── dax_measures.md
└── README.md
```

## 9. How to Use

1. Download `Netflix_Churn_Dashboard.pbix`.
2. Open it in **Power BI Desktop** (free from Microsoft).
3. Use the slicers and click on charts to explore the data.
4. Use **Ctrl + click** to select multiple values in a visual.

## 10. Screenshots
1]  <img width="1920" height="1080" alt="Dashboard2" src="https://github.com/user-attachments/assets/3670eea3-3ab8-488b-a36f-51337ad28617" />

2]  <img width="1920" height="1080" alt="Dashboard1" src="https://github.com/user-attachments/assets/610e2249-4071-48e2-bb49-a3b71bf422e0" />


## 11. What I Learned

- Building a star schema with fact and dimension tables.
- Writing DAX measures for churn rate, benchmarks and revenue at risk.
- Designing interactive visuals and slicers for non-technical users.
- Turning data into business recommendations.

## 12. Author

**[Your Name]**
Data Analytics Intern, SWYNEX Technologies
LinkedIn: www.linkedin.com/in/samruddhi-shelke-051bb9443
GitHub: https://github.com/Samruddhi811

