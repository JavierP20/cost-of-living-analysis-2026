# Cost of Living Analysis 2026

## Project Overview

This project analyzes how everyday costs have changed over time in the United States, focusing on inflation, gas prices, wages, and purchasing power.

The goal is to determine whether income growth has kept pace with rising consumer costs and to identify the areas where households may be feeling the most financial pressure.

## Main Question

Has income kept up with the rising cost of living in the United States?

## Key Questions

- How have gas prices changed over time?
- How has inflation affected the purchasing power of the dollar?
- Have wages kept pace with inflation?
- Which cost categories have increased the most?
- Are recent price increases part of a long-term trend or short-term spike?

## Tools Used

- Power BI
- Python
- Excel
- SQL
- GitHub

## Data Sources

This project uses public economic datasets from FRED:

- Consumer Price Index for All Urban Consumers: All Items in U.S. City Average
- U.S. Regular All Formulations Gas Price
- Average Hourly Earnings of Production and Nonsupervisory Employees, Total Private
  
## Data Pipeline

This project follows a simple data pipeline:

1. Raw public datasets were downloaded from FRED and stored in `data/raw/`.
2. Python was used to clean, standardize, and merge the datasets in `notebooks/data_cleaning.ipynb`.
3. Weekly gas price data was converted into monthly averages to match CPI and wage data.
4. Year-over-year percent changes and inflation-adjusted wage metrics were calculated.
5. Cleaned datasets were exported to `data/cleaned/`.
6. The analysis-ready dataset will be used to build the Power BI dashboard.
## Dashboard Pages

1. Executive Summary
2. Gas Prices Over Time
3. Wages vs Inflation
4. Purchasing Power

## Repository Structure

```text
cost-of-living-analysis-2026/
│
├── data/          # Raw and cleaned datasets
├── exports/       # Dashboard PDFs, screenshots, and final outputs
├── notebooks/     # Python notebooks for cleaning and analysis
├── powerbi/       # Power BI dashboard file
├── README.md      # Project overview
└── project_notes.md
```
## Current Status

Data collection and cleaning are complete. The project now includes raw datasets, a Python cleaning notebook, and cleaned CSV files ready for Power BI dashboard development.

## Key Findings

_To be completed after dashboard analysis._

## Dashboard Preview

_To be added after dashboard creation._

