# Retail Sales Data Cleaning & Insights Pipeline

**A real-world case study: turning a messy, raw retail sales export into a clean, analysis-ready dataset — and the business insights hidden inside it.**

Built with **Python, Pandas, NumPy, and Matplotlib.**

---

## The Problem

Small retail and e-commerce businesses almost never have clean data. Sales exports from POS systems, Shopify, or manually maintained spreadsheets are full of:

- Inconsistent date formats (`2026-06-02`, `06/10/2026`, `17-Nov-2025`, all in the same column)
- Currency symbols and thousands separators mixed into numeric fields (`"Rs. 9,830"`, `"PKR 8,478"`, `"1599"`)
- Inconsistent category/region spelling and casing (`Electronics`, `electronics`, `ELECTRONICS`, `Electronic`)
- Missing values in critical fields (dates, prices, quantities, customer names)
- Duplicate rows from repeated exports or merged sheets
- Data-entry outliers (a quantity of `500` typed instead of `5`)
- Returns recorded as negative quantities, mixed in with regular sales

This project simulates exactly that scenario with a realistic 2,500+ row raw sales export, then builds a repeatable pipeline that cleans it, documents every fix, and turns it into decision-ready charts.

## What This Project Demonstrates

| Skill | Where |
|---|---|
| Data cleaning with Pandas & NumPy | `scripts/02_clean_data.py` |
| Handling messy real-world data (dates, currency text, typos, duplicates, outliers) | `scripts/02_clean_data.py` |
| Business analysis & KPI calculation | `scripts/03_analysis_and_visuals.py` |
| Data visualization with Matplotlib | `scripts/03_analysis_and_visuals.py`, `visuals/` |
| Turning technical work into a client-facing deliverable | `DATA_QUALITY_REPORT.md` |

## Results

- **2,537 → 2,452 rows** after removing 37 exact duplicates and 48 rows with unparseable dates
- **10 categories of data-quality issues** found, logged, and fixed — see [`DATA_QUALITY_REPORT.md`](DATA_QUALITY_REPORT.md)
- **PKR 21.4M** in completed revenue recovered and correctly calculated from previously unusable text fields
- 6 client-ready charts generated automatically from the cleaned data

### Before vs. After Cleaning

![Before vs after cleaning](visuals/06_before_after_cleaning.png)

### Monthly Revenue Trend

![Monthly revenue trend](visuals/01_monthly_revenue_trend.png)

### Revenue by Category

![Revenue by category](visuals/02_revenue_by_category.png)

More charts (revenue by region, top products, order status breakdown) are in the [`visuals/`](visuals) folder.

## Project Structure

```
retail-data-cleaning-pipeline/
├── data/
│   ├── raw/raw_sales_export.csv          # messy "client" export
│   └── cleaned/cleaned_sales_data.csv    # analysis-ready output
├── scripts/
│   ├── 01_generate_raw_data.py           # builds the sample messy dataset
│   ├── 02_clean_data.py                  # the cleaning pipeline
│   └── 03_analysis_and_visuals.py        # KPIs + matplotlib charts
├── visuals/                              # 6 generated PNG charts
├── DATA_QUALITY_REPORT.md                # auto-generated fix log
├── requirements.txt
└── README.md
```

## How to Run

```bash
pip install -r requirements.txt

python scripts/01_generate_raw_data.py       # generates data/raw/raw_sales_export.csv
python scripts/02_clean_data.py              # generates data/cleaned/cleaned_sales_data.csv + report
python scripts/03_analysis_and_visuals.py    # generates all 6 charts in visuals/
```

## Adapting This for a Real Client

The `02_clean_data.py` pipeline is written so each cleaning step is isolated and reusable:
swap in a client's actual export, adjust the `category_map` / `region_map` dictionaries to their
real category names, and the same pipeline produces the same before/after report — a ready-made
proof-of-work document for a data-cleaning engagement.

## Tech Stack

- **Pandas** — data loading, cleaning, grouping, feature engineering
- **NumPy** — numeric coercion, outlier detection (IQR method), vectorized calculations
- **Matplotlib** — all charts, styled for a clean client-facing look

---

*This is a portfolio project built with a synthetic dataset designed to realistically mimic messy client data. No real customer data is used.*
