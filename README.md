# Simple KPI Tracking Sheet

**Track:** Data Analytics · **Level 1 · Task 10** · **Tools:** Excel / Google Sheets

## Objective
Turn raw transactional order data into a small set of business-ready KPIs that update automatically when new rows are added.

## What's inside
`KPI_Tracking_Sheet.xlsx`

| Tab | Purpose |
|---|---|
| **KPI Summary** | One-page KPI dashboard (the deliverable) |
| **Data** | Raw order lines, Superstore-style (Order ID, Date, Segment, Region, Category, Product, Sales, Quantity, Discount, Profit) |
| **Lists** | Small helper table (product → total sales) used to find the top product |

## KPIs (kept to 5 for a first version)
| KPI | Formula approach |
|---|---|
| Total Revenue | `SUMIFS` on Sales |
| Units Sold | `SUMIFS` on Quantity |
| Average Order Value | Total Revenue ÷ unique Order IDs (`SUMPRODUCT/COUNTIF`) |
| Top Product | `INDEX/MATCH` on the max of per-product `SUMIFS` totals |
| Profit Margin | Total Profit ÷ Total Revenue |

## Why it updates automatically
All formulas reference `Data!$J$2:$J$5000` etc., so any new row added below the data (up to row 5000) is picked up instantly — no manual totals. Numbers are formatted consistently (currency, percentage, thousands separators).

## How to use with the original dataset
Paste the Sample Superstore columns into the **Data** tab in the same column order. If a brand-new product appears, add its name at the bottom of `Lists!A` (formula in column B is pre-filled for 20 spare rows).

## Approach & outcome
1. Chose a handful of KPIs a small retail owner would check weekly.
2. Used `SUMIFS`-style aggregation instead of manual totals.
3. Verified results against an independent calculation of the data (revenue, units, AOV all matched).

## Interview notes
- **Which KPIs matter for a small retail business?** Revenue, units, average order value, margin, and best-sellers — they cover volume, basket size, profitability, and what to stock.
- **Keeping it accurate as data grows?** Use ranges larger than the data (or Tables), formula-driven totals only, and a data-check cell (row count / date range) to spot missing loads.

*Note: sample data in this file is Superstore-style generated data; swap in the original dataset as described above.*
