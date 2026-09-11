# Sales Analysis with Python — 2019 E-commerce Data
It is never too late to be what you might have been – George Eliot

My first end-to-end data analysis project: cleaning, exploration, visualization,
and statistical testing on ~186,000 sales records covering 12 months.

## Dataset

- **Source:** 12 monthly CSV files (one per month of 2019)
- **Rows:** ~186,000 orders
- **Raw columns:** Order ID, Product, Quantity Ordered, Price Each, Order Date, Purchase Address

## Tools

Python 3 · pandas · matplotlib · scipy · Jupyter / Google Colab

## Project Workflow

1. **Merge** 12 monthly CSVs into one DataFrame
2. **Clean** — drop blank rows, remove repeated header rows, fix dtypes, parse datetime
3. **Augment** — add Month, Hour, Sales, and City columns
4. **Explore** — answer six business questions
5. **Test** — apply statistical tests (Chi-square, correlation, ANOVA) instead of eyeballing charts

## Key Findings

| # | Question | Method | Result |
|---|----------|--------|--------|
| 1 | Best month for sales? | Group-by sum | **December** ($4.61M) |
| 2 | Which city sold the most? | Group-by sum | **San Francisco, CA** |
| 3 | Best time to advertise? | Chi-square + hourly counts | **19:00 (7 PM)**; χ² = 58,878, p ≈ 0 |
| 4 | Price vs. quantity? | Pearson / Spearman | Weak negative: r = −0.15, ρ = −0.34, p ≈ 0 |
| 5 | Do cities differ in avg order value? | One-way ANOVA | **No** — F = 0.43, p = 0.92 |

### Main insight

Cities differ in **total sales** because of **order volume**, not because their
average order value is different. Per-order value is statistically
indistinguishable across cities (ANOVA, p = 0.92).

## Files

- `sales_analysis.ipynb` — full analysis notebook
- `requirements.txt` — Python dependencies
- `.gitignore` — ignore rules

## Limitation

Price–quantity relationship is weak;quantity is dominated by 1-unit orders,
so correlations have little predictive value.

Large sample size (n ≈ 186k) inflates p-values; effect sizes are reported
where relevant.

City extraction relies on comma-separated address format (works for this
dataset, not generalizable).
## How to Run

```bash
pip install -r requirements.txt
jupyter notebook sales_analysis.ipynb
