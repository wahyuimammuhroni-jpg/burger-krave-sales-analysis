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
Three-Month Revenue Forecast
