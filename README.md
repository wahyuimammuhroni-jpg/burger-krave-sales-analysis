# Burger Krave Sales Performance Analysis

An end-to-end sales analytics project developed using **Microsoft Excel, Power Query, and Power Pivot** to analyze Burger Krave's sales performance, profitability, customer behavior, product performance, branch contribution, and short-term revenue outlook.

The project covers the complete analytics workflow from data preparation and relational data modeling to KPI development, interactive dashboard creation, and three-month revenue forecasting.

---

## Project Overview

Burger Krave operates across multiple branches and offers various burger products across different categories and sizes.

This project analyzes transaction data throughout **2024** to understand overall business performance, identify key revenue drivers, evaluate customer characteristics, compare branch performance, and monitor sales trends.

The analysis was developed using:

- Microsoft Excel
- Power Query
- Power Pivot
- Data Model Relationships
- Measures
- PivotTables
- PivotCharts
- Slicers
- Forecasting Tools

---

## Business Objectives

The project aims to answer several business questions:

- How did overall revenue and profitability perform throughout 2024?
- Which burger products generated the highest revenue?
- Which branches contributed the most to total revenue?
- How is sales activity distributed across branch locations?
- What are the purchasing preferences of male and female customers?
- How are customers distributed across different age groups?
- How did monthly revenue and product sales develop throughout the year?
- What is the estimated revenue outlook for the next three months?

---

# Dataset

The analysis uses four related datasets.

| Dataset | Description |
|---|---|
| `transaction_order_detail` | Transaction date, order ID, branch, customer, burger, price, quantity, order time, and completion time |
| `master_customer` | Customer ID, customer name, gender, birth date, and account opening date |
| `master_cabang` | Branch ID, location, province, and branch name |
| `master_burger` | Burger ID, burger type, burger name, category, size, price, and production cost |

The `transaction_order_detail` table serves as the main transaction table, while the remaining tables provide descriptive customer, branch, and product information.

---

# Analysis Workflow

```text
Raw Dataset
    ↓
Power Query
Data Cleaning & Transformation
    ↓
Power Pivot
Data Modeling & Relationships
    ↓
Measures & KPI Development
    ↓
PivotTables & PivotCharts
    ↓
Interactive Dashboard
    ↓
Business Insights
    ↓
Three-Month Revenue Forecast```
```

---

## Data Preparation with Power Query

Power Query was used to prepare and standardize the datasets before analysis.

The preparation process included:

- Standardizing column names
- Assigning appropriate data types
- Validating missing and error values
- Preparing primary and foreign keys
- Structuring transaction and master data
- Preparing analysis-ready tables
- Ensuring consistency between related datasets

![Power Query Data Preparation](images/05_power_query_data_preparation.png)

---

## Power Pivot

### Data Modeling

After data preparation, the cleaned tables were loaded into the Power Pivot Data Model.

The model uses transaction_order_detail as the central transaction table connected to three supporting master tables.

Table Relationships

![Power Pivot Data Modeling](images/06_power_pivot_data_modeling.png)

- `master_customer[customer_id]` → `transaction_order_detail[customer_id]`
- `master_cabang[branch_id]` → `transaction_order_detail[branch_id]`
- `master_burger[burger_id]` → `transaction_order_detail[burger_id]`

### Measures

Several measures were created in Power Pivot to support KPI calculation and dashboard analysis

| Measure              | Analytical Purpose                                 |
| -------------------- | -------------------------------------------------- |
| Revenue Per Trx      | Supports revenue calculation from transaction data |
| Profit               | Measures overall business profit                   |
| Customer Count       | Measures the number of customers                   |
| Profit Margin %      | Evaluates profitability relative to revenue        |
| Avg Completion Order | Measures average order completion performance      |

### DAX Code

```DAX
Revenue Per Trx

Revenue Per Trx :=
SUMX(
    'transaction_order_detail',
    'transaction_order_detail'[quantity]
        * RELATED(master_burger[price])
)
--------------------------------------------------------------------------

Profit

Profit :=
SUMX(
    transaction_order_detail,
    (
        RELATED(master_burger[price])
        - RELATED(master_burger[production_cost])
    )
    * transaction_order_detail[quantity]
)
--------------------------------------------------------------------------

Customer Count

Customer Count :=
DISTINCTCOUNT(
    transaction_order_detail[customer_id]
)
--------------------------------------------------------------------------

Profit Margin %

Profit Margin % :=
DIVIDE(
    [Profit],
    [Revenue Per Trx],
    0
)
--------------------------------------------------------------------------

Avg Completion Order

Avg Completion Order :=
AVERAGEX(
    FILTER(
        transaction_order_detail,
        NOT(ISBLANK(transaction_order_detail[order_time]))
            && NOT(ISBLANK(transaction_order_detail[completion_time]))
    ),
    MOD(
        transaction_order_detail[completion_time]
            - transaction_order_detail[order_time],
        1
    ) * 1440
)```
```

---

## Dashboard Overview

An interactive Excel dashboard was developed to summarize the main business indicators and provide multiple perspectives on sales performance.

The dashboard includes interactive filters for:

- Transaction Period
- Burger Category
- Burger Name
- Branch Name

Executive KPIs

| KPI             |         Result |
| --------------- | -------------: |
| Total Revenue   | 28,263,267,000 |
| Total Customers |         48,780 |
| Total Orders    |        500,000 |
| Total Quantity  |        879,145 |
| Total Profit    | 16,195,231,700 |
| Profit Margin   |         57.30% |

![Dashboard Overview](images/01.dashboard_overview.png)
