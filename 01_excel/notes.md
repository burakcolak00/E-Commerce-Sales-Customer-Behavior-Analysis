# Phase 1: Excel Notes

## Goal
Explore the Olist data in Excel, build a revenue-by-month analysis, and start a dashboard.

## Data Overview

| Table | What one row represents | Key columns | Links to |
|---|---|---|---|
| `orders` | One customer order | `order_id`, `customer_id`, `order_status`, `order_purchase_timestamp` | `order_items.order_id`, `customers.customer_id` |
| `order_items` | One item inside an order (an order can have several rows) | `order_id`, `product_id`, `price`, `freight_value` | `orders.order_id`, `products.product_id` |
| `customers` | One customer record per order | `customer_id`, `customer_unique_id`, `customer_state` | `orders.customer_id` |

**Row counts (verify against your files):** orders ≈ 99k, order_items ≈ 113k, customers ≈ 99k.

**Things I noticed**
- One order can have multiple items, so revenue must be summed from `order_items`, not `orders`.
- `customer_id` is unique per order. `customer_unique_id` identifies the real person, which matters for repeat-purchase analysis later.
- Some delivery date columns in `orders` have blanks (orders not yet delivered or canceled).

## Steps Taken

1. Imported `order_items` and `orders` into the workbook with **Data → Get Data → From Text/CSV**. Raw CSVs in `data/raw/` were not modified.
2. Added a `purchase_date` column to `order_items` using a lookup on `order_id` (`VLOOKUP` / `XLOOKUP`) against `orders`.
3. Excel stored the timestamps as serial numbers, so I formatted the column as a date.
4. Added a `month` column with `=TEXT([@purchase_date], "yyyy-mm")`.
5. Built a pivot table: `month` in Rows, *Sum of price* in Values, sorted A to Z.
6. Created a line chart: **Monthly Revenue (2016-2018)**, x-axis = Month, y-axis = Revenue (BRL).

## Mistakes and Lessons

- **First attempt used `MONTH()` only**, which returned 1-12. That merged the same month from different years and gave a misleading chart (a fake "drop" in months 9-12). Using `yyyy-mm` fixed it.
- **Pivot rows were unsorted** at first, which made the line zigzag. Sorting Row Labels A to Z fixed it.
- Check for partial periods before drawing conclusions from a trend.

## Findings

- Total revenue (item prices only, excluding freight): **BRL 13,591,643.70**
- Revenue grew steadily through 2017, from about BRL 120k in January to a peak of about **BRL 1.01M in November 2017** (likely Black Friday).
- In 2018, monthly revenue stayed high at roughly BRL 850k-1M.
- Late 2016 (Sep-Dec) and September 2018 are near zero because the dataset only partially covers those months. These are data coverage limits, not real drops.

## Assumptions and Limitations

- Revenue = sum of `price` in `order_items`. Freight (`freight_value`) is excluded.
- Orders with every status are included for now, including canceled ones. **To do:** filter by `order_status` and compare.
- Partial months at the start and end of the dataset were left in the pivot but not used for conclusions.

## Next Steps

- [ ] Revenue by product category (needs `products` and the category translation table)
- [ ] Revenue by customer state (needs `customers`)
- [ ] Exclude canceled/unavailable orders and compare totals
- [ ] Add slicers and combine pivots into a one-page `dashboard` sheet
- [ ] Answer: top 10 categories by revenue, and which months peak
