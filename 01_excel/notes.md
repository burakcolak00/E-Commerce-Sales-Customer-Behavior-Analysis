# Olist Excel Dashboard - Cleaning Notes

## Data Cleaning Steps

1. **Loaded raw CSVs** from Kaggle Olist dataset (9 files)
2. **Converted date columns** to datetime format across orders, payments, and reviews tables
3. **Handled missing values** - checked and documented null counts per column
4. **Merged core datasets** - order_items + payments + customers into analysis-ready table
5. **Standardized categories** - mapped product_category_name to English names via translation file

## Key Findings

- ~100k orders across ~5k customers
- Revenue concentrated in São Paulo and Rio de Janeiro states
- Most common product categories: electronics, home goods, clothing
- Order delivery times vary significantly by region

## Next Steps

- Excel pivot tables for monthly revenue trends
- Customer segmentation charts
- Geographic distribution visualization