# SWYNEX Data Modeling and DAX – Netflix Customer Churn

## Overview
A Power BI star-schema model built on Netflix customer churn data (5,000 customers).

## Data Model
- **Fact table:** Fact_Customers
- **Dimension tables:** Dim_Subscription, Dim_Region, Dim_Device, Dim_Genre, Dim_Payment
- **Relationships:** One-to-many, single direction (dimension → fact)

## DAX Measures
| Measure | Purpose |
|---|---|
| Total Customers | Distinct count of customers |
| Churned Customers | Customers with churned = 1 |
| Churn Rate % | Churned / Total customers |
| Monthly Revenue | Sum of monthly fees |
| Revenue at Risk | Fees from churned customers |
| Avg Watch Hours | Average watch hours |
| Overall Churn Rate % | Churn rate ignoring filters |
| Churn vs Overall (pp) | Segment churn minus overall churn |

## Dashboard
Cards, charts by subscription and region, a device table, and slicers for genre and payment method.

## Key Insights
- Overall churn rate is about 50%
- Basic plan has the highest churn
- (add one more insight from your dashboard)

## Tools
Power BI Desktop, DAX, Power Query
