# Burger Krave Sales Performance Analysis

An end-to-end sales analysis project developed using **Microsoft Excel and Power Query** to evaluate Burger Krave's sales performance, product performance, branch contribution, customer behavior, profitability, and short-term revenue outlook.

The project combines data preparation, relational data analysis, interactive dashboard development, and three-month revenue forecasting.

---

## Project Overview

Burger Krave operates across multiple branches and offers a variety of burger products across different categories and sizes.

This project analyzes transaction data throughout **2024** to understand overall business performance, identify top-performing products and branches, evaluate customer characteristics, and monitor monthly sales trends.

The analysis was developed in Microsoft Excel using **Power Query, PivotTables, PivotCharts, formulas, slicers, and forecasting tools**.

---

## Business Objectives

The project aims to answer several business questions:

- How did overall sales perform throughout 2024?
- Which burger products generated the highest revenue?
- Which branches contributed the most to total revenue?
- How is sales performance distributed across branch locations?
- What are the purchasing preferences of male and female customers?
- How are customers distributed across age groups?
- How did monthly revenue and product sales develop throughout the year?
- What could revenue performance look like over the next three months?

---

## Dataset

The analysis uses four related datasets.

| Dataset | Description |
|---|---|
| `transaction_order_detail` | Transaction date, order ID, branch, customer, burger, price, quantity, and transaction time |
| `master_customer` | Customer ID, customer name, gender, birth date, and account opening date |
| `master_cabang` | Branch ID, location, province, and branch name |
| `master_burger` | Burger ID, burger type, burger name, category, size, price, and production cost |

### Data Model

```text
                     master_customer
                           │
                      customer_id
                           │
                           ▼
master_cabang ───► transaction_order_detail ◄─── master_burger
   branch_id                                        burger_id
