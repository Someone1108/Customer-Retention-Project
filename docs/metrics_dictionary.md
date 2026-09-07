# Metrics Dictionary

This document defines the main metrics used in the Customer Retention Command Center.

The purpose of this file is to make the project easier to understand for future readers, dashboard users, and interviewers.

## Total Customers

**Definition:**  
The total number of customer records in the dataset.

**Formula:**  
`COUNT(customerid)`

**Business meaning:**  
Shows the size of the customer base included in the analysis.

**Current value:**  
`7,043`

## Churned Customers

**Definition:**  
The number of customers who left the company.

**Formula:**  
`SUM(churn_value)`

**Business meaning:**  
Shows how many customers were lost in the dataset.

**Current value:**  
`1,869`

## Churn Rate

**Definition:**  
The percentage of customers who churned.

**Formula:**  
`SUM(churn_value) / COUNT(customerid)`

**Business meaning:**  
Shows how large the churn problem is relative to the full customer base.

**Current value:**  
Approximately `26.5%`

## Monthly Recurring Revenue

**Definition:**  
The total monthly charges across all customers.

**Formula:**  
`SUM(monthly_charges)`

**Business meaning:**  
Estimates the monthly revenue represented by the customers in the dataset.

## Monthly Revenue at Risk

**Definition:**  
The monthly charges associated with churned customers.

**Formula:**  
`SUM(revenue_at_risk)`

In the current version:

`revenue_at_risk = monthly_charges if is_churned = true, otherwise 0`

**Business meaning:**  
Estimates monthly revenue associated with customers who have already churned.

**Important note:**  
This is a first version of revenue at risk. Later, we may expand it to include non-churned customers with high churn scores.

## Average Monthly Charge

**Definition:**  
The average monthly amount charged per customer.

**Formula:**  
`AVG(monthly_charges)`

**Business meaning:**  
Shows the typical monthly customer value.

## Total Charges

**Definition:**  
The total amount charged to a customer over their tenure.

**Business meaning:**  
Helps understand historical customer value.

**Data quality note:**  
There were 11 missing `total_charges` values. These customers all had `tenure_months = 0`, so the missing values were filled with `0`.

## CLTV

**Definition:**  
Customer Lifetime Value.

**Business meaning:**  
Represents the estimated long-term value of a customer.

**Important note:**  
This value is provided by the source dataset. This project did not calculate CLTV from scratch.

## Churn Score

**Definition:**  
A customer churn-risk score provided by the source dataset.

**Business meaning:**  
Higher values indicate customers who appear more likely to churn.

**Important note:**  
This project did not create the churn score model. It uses the churn score as an existing risk indicator.

## Retention Priority

**Definition:**  
A future scoring method used to rank customers for retention outreach.

**Possible inputs:**

- Churn score
- Monthly charges
- CLTV
- Tenure months
- Contract type
- Payment method

**Business meaning:**  
Helps the retention team decide which customers to contact first.

**Current status:**  
Not finalized yet. Notebook 05 currently sorts high-priority customers by churn score, monthly charges, and CLTV.

## Key Dataset Notes

- `churn_value = 1` means the customer churned.
- `churn_value = 0` means the customer did not churn.
- `churn_label = Yes` matches `churn_value = 1`.
- `churn_label = No` matches `churn_value = 0`.
- `churn_reason` is only available for customers who churned.
- `dim_churn_reason` includes a `Not churned` category so non-churned customers can still connect to the churn reason dimension.

## Your Notes

Use this section to add your own plain-English explanations.

Questions to answer later:

- Which metric best explains the size of the churn problem?
- Which metric best explains the revenue impact?
- Which metric would you show first to a retention manager?
- How would you explain churn rate in an interview?
