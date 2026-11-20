# E-Commerce Sales & Customer Behavior Analysis

An end-to-end analysis of the Olist Brazilian e-commerce marketplace using **Excel, SQL, and Python**, finishing with machine learning models for customer segmentation and review prediction.

> **Status:** 🚧 In progress. Update this line as you go (e.g. "Phase 2 of 4 complete").

---

## Table of Contents
1. [Business Problem](#business-problem)
2. [Dataset](#dataset)
3. [Tools & Skills](#tools--skills)
4. [Project Structure](#project-structure)
5. [Approach](#approach)
6. [Key Findings](#key-findings)
7. [Recommendations](#recommendations)
8. [How to Run](#how-to-run)
9. [Limitations & Assumptions](#limitations--assumptions)
10. [Next Steps](#next-steps)

---

## Business Problem

Leadership at an online marketplace wants to understand:

- What drives revenue, and when does it peak?
- Which product categories and regions perform best?
- Why do some customers leave bad reviews?
- Which customers are worth retaining?

This project answers those questions using the company's order, product, payment, and review data.

## Dataset

**Source:** [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) on Kaggle.

- ~100,000 orders placed between 2016 and 2018
- 9 related tables: orders, order items, customers, products, sellers, payments, reviews, geolocation, category translation

The raw data is **not included** in this repo because of its size. See [How to Run](#how-to-run) to download it.

## Tools & Skills

| Area | Tools | Skills practiced |
|---|---|---|
| Excel | Pivot tables, slicers, charts | Data cleaning, `XLOOKUP`, `SUMIFS`, `COUNTIFS`, dashboards |
| SQL | SQLite / PostgreSQL | Joins, CTEs, subqueries, window functions |
| Python | pandas, matplotlib, seaborn | Data wrangling, EDA, visualization |
| Data Science | scikit-learn, statsmodels | Clustering, classification, model evaluation, forecasting |

## Project Structure

```
olist-ecommerce-analysis/
├── data/
│   ├── raw/                  # original Kaggle CSVs (not tracked)
│   └── processed/            # cleaned and merged files
├── 01_excel/                 # dashboard and cleaning notes
├── 02_sql/                   # schema, queries, business questions
├── 03_python/                # cleaning and EDA notebooks
├── 04_data_science/          # RFM, review prediction, forecasting
├── reports/
│   ├── figures/              # exported charts
│   └── summary.md            # 1-page summary for managers
├── src/                      # reusable helper functions
├── requirements.txt
└── README.md
```

## Approach

### Phase 1: Excel
Cleaned a sample of the data and built pivot tables for revenue by month, category, and state, combined into a one-page dashboard with slicers.

### Phase 2: SQL
Loaded all tables into a database and wrote queries to answer business questions, including:
- Month-over-month revenue growth
- Top 3 products per category
- Average delivery time by state
- Repeat purchase rate
- Relationship between late deliveries and review scores

### Phase 3: Python (EDA)
Merged the tables with pandas, handled missing values and outliers, and explored distributions, correlations, and trends with visualizations.

### Phase 4: Data Science
- **Customer segmentation:** RFM analysis (Recency, Frequency, Monetary) with K-Means clustering
- **Review prediction:** Classification models (logistic regression, random forest) to predict 1-2 star reviews
- **Evaluation:** Train/test split, cross-validation, precision/recall, confusion matrix, feature importance
- **Stretch:** Monthly sales forecasting

## Key Findings

> Fill this in as you complete each phase. Lead with numbers and keep each point to one or two sentences.

1. **Revenue:** _e.g. "Revenue peaked in November 2017, driven by [category]."_
2. **Categories:** _e.g. "The top 10 categories account for X% of total revenue."_
3. **Delivery:** _e.g. "Orders delivered late received an average review score of X vs. Y for on-time orders."_
4. **Retention:** _e.g. "Only X% of customers placed more than one order."_
5. **Segments:** _e.g. "RFM clustering revealed N segments; the 'at risk' group makes up X% of customers."_
6. **Model performance:** _e.g. "The random forest predicted bad reviews with X% recall; delivery delay was the most important feature."_

Add your best 2-3 charts here:

```
![Monthly revenue](reports/figures/monthly_revenue.png)
![Customer segments](reports/figures/rfm_segments.png)
```

## Recommendations

> Write these as actions a manager could take, tied to your findings.

1. _e.g. "Improve delivery performance in [states] to reduce 1-2 star reviews."_
2. _e.g. "Launch a re-engagement campaign for the 'at risk' segment."_
3. _e.g. "Increase inventory and promotion for [category] ahead of the seasonal peak."_

## How to Run

**1. Clone the repo**
```bash
git clone https://github.com/<your-username>/olist-ecommerce-analysis.git
cd olist-ecommerce-analysis
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the data**
Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) and place the CSV files in `data/raw/`.

**4. Run in order**
1. Open `01_excel/olist_dashboard.xlsx`
2. Run the SQL scripts in `02_sql/` (start with `00_schema_and_load.sql`)
3. Run the notebooks in `03_python/`, then `04_data_science/`

## Limitations & Assumptions

> Document your decisions. This shows good analytical practice.

- _e.g. "Orders with status 'canceled' or 'unavailable' were excluded from revenue calculations."_
- _e.g. "Customers are identified by `customer_unique_id`, not `customer_id`."_
- _e.g. "Data covers 2016-2018 only, so findings may not reflect current behavior."_
- _e.g. "Review data is limited to customers who chose to leave a review."_

## Next Steps

- Add a Tableau or Power BI dashboard
- Try gradient boosting (XGBoost / LightGBM) for review prediction
- Add text analysis of review comments (NLP)

---

**Author:** Burak Colak · [LinkedIn](https://www.linkedin.com/in/burak-colak00/)
· [Portfolio](https://burakcolak00.github.io/Portfolio/)
