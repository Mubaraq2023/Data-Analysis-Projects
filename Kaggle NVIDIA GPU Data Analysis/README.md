# NVIDIA GPU Synthetic Sales Analysis

Exploratory data analysis of a synthetic NVIDIA GPU sales dataset, uncovering trends in revenue, pricing, customer segments and inventory health.

## Overview

This project analyzes a synthetic dataset of NVIDIA GPU sales transactions to answer practical business questions about pricing, revenue and customer behavior. It covers data cleaning, exploratory data analysis (EDA) and a set of business-focused investigations, such as which GPU family drives the most revenue, which sales channel gives the best return and whether bundles or longer warranties are worth offering.

The notebook is written for anyone who wants a worked example of an end-to-end EDA workflow on sales data — from loading and validating a raw CSV to producing a summary dashboard of key metrics.

## Key Features

- **Data cleaning**: handles missing values, checks for duplicate records and fixes column data types (dates, categories, strings).
- **Data validation**: cross-checks that `price_premium_pct` and `revenue_usd` match their expected calculated values.
- **Univariate & bivariate analysis**: distribution plots for units sold, revenue and customer satisfaction; relationships between stock status, pricing and satisfaction.
- **Business question deep-dives**, including:
  - Which GPU family drives the most sales volume and revenue
  - Which sales channel gives the best revenue-per-unit return
  - Whether pricing above MSRP hurts customer satisfaction
  - Which customer segment is most valuable, and what they buy
  - The most valuable GPU models within each GPU family
  - Whether bundle add-ons are worth offering
  - Seasonal trends in monthly unit sales
  - Regional differences in pricing power
  - Whether warranty length affects price premium
- **Correlation heatmap** across all numeric fields.
- **Mini dashboard**: a single 2x2 summary figure combining the most important charts.

## Tech Stack / Dependencies

- **Language**: Python 3
- **Environment**: Jupyter Notebook

Libraries used:
- `pandas` - Data Loading, Cleaning and Aggregation
- `numpy` — Numerical Operations
- `matplotlib` — Visualization
- `seaborn` — Statistical Visualization

## Installation / Setup

1. Clone or download this repository.
2. Make sure you have Python 3.9 or later installed.
3. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

4. Place the dataset CSV file (see [Dataset](#dataset) below) in the same directory as the notebook.
5. Launch Jupyter and open the notebook:

   ```bash
   jupyter notebook nvidia_gpu_synthetic_dataset.ipynb
   ```

6. Run all cells in order, from top to bottom.

## Dataset

The dataset contains synthetic GPU sales records with fields such as `sale_id`, `sale_date`, `gpu_model`, `gpu_family`, `launch_year`, `region`, `sales_channel`, `customer_segment`, `units_sold`, `msrp_usd`, `avg_street_price_usd`, `price_premium_pct`, `stock_status`, `customer_satisfaction_score`, `warranty_months`, `bundle_addon`, and `revenue_usd`.

## Usage

Once the dataset is in place, running the notebook produces the full analysis. A few representative snippets:

Load and inspect the data:

```python
df = pd.read_csv("nvidia_gpu_sales_synthetic_2026.csv")
df.head(4)
df.info()
```

Clean missing values and fix data types:

```python
df["bundle_addon"] = df["bundle_addon"].fillna("No bundle")
df["sale_date"] = pd.to_datetime(df["sale_date"], errors="coerce")

categorical_cols = ["gpu_model", "gpu_family", "region", "sales_channel", "customer_segment", "bundle_addon"]
df[categorical_cols] = df[categorical_cols].astype("category")
```

Answer a business question, e.g. which GPU family drives the most revenue:

```python
gpu_fam_rev = df.groupby("gpu_family", observed=True)["revenue_usd"].mean().sort_values(ascending=False)
gpu_fam_rev
```

Generate the summary dashboard (final cell of the notebook), which combines four key charts — sales volume distribution, price premium vs. satisfaction, revenue by customer segment and monthly sales trend into a single figure.

## Project Structure

```
.
├── nvidia_gpu_synthetic_dataset.ipynb   # Main analysis notebook
└── nvidia_gpu_sales_synthetic_2026.csv  # Dataset (not included - add separately)
```

The notebook is organized into the following sections:

1. Import Dependencies
2. Load Dataset
3. Basic Data Understanding
4. Data Cleaning
5. Data Analysis (univariate and bivariate)
6. Business Questions (9 targeted analyses)
7. Mini Dashboard (summary visualization)

## Contributing

This is a personal/portfolio-style analysis project. Suggestions and improvements are welcome:

1. Fork the repository.
2. Create a new branch for your change.
3. Make your edits to the notebook.
4. Submit a pull request describing what you changed and why.
