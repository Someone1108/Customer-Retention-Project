# Customer Retention Project

Hands-on analytics project for building a Customer Retention Command Center using the IBM Telco Customer Churn dataset.

## Project Goal

The project helps a fictional telecommunications retention team understand:

- Which customer groups churn most often
- How much monthly revenue is at risk
- Which contract, service, payment, and customer factors are associated with churn
- Which customers may deserve retention attention first

## Current Progress

Completed so far:

- Created the project folder structure
- Loaded and inspected the raw Telco churn dataset
- Cleaned column names into `snake_case`
- Converted important numeric fields
- Investigated missing `total_charges` values
- Built first star schema CSV outputs
- Added DuckDB SQL analysis notebook starter
- Created Power BI dashboards

## Notebooks

- `notebooks/01_data_inspection.ipynb`
- `notebooks/02_data_cleaning.ipynb`
- `notebooks/03_star_schema_design.ipynb`
- `notebooks/04_build_star_schema.ipynb`
- `notebooks/05_sql_analysis_with_duckdb.ipynb`

## Data Outputs

Raw data:

- `data/raw/Telco_customer_churn.xlsx`

Processed data:

- `data/processed/telco_customer_churn_clean.csv`
- `data/processed/star_schema/dim_customer.csv`
- `data/processed/star_schema/dim_contract.csv`
- `data/processed/star_schema/dim_payment_method.csv`
- `data/processed/star_schema/dim_service.csv`
- `data/processed/star_schema/dim_churn_reason.csv`
- `data/processed/star_schema/fact_customer_snapshot.csv`


