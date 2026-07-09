# Task 1 — Data Cleaning and Preprocessing

## Dataset
**UCI Adult Income Dataset**
- Source: UCI Machine Learning Repository (US Census Bureau, 1994)
- Raw data: 32,561 rows × 15 columns
- Target column: `income` — whether a person earns <=50K or >50K per year

## What this task covers
- Detecting and handling missing values
- Removing duplicate rows
- Fixing inconsistent text formatting
- Outlier detection and capping using IQR method
- Feature engineering — creating new useful columns
- Data visualization — missing values heatmap, outlier box plots, distribution charts

## Problems found in raw data

| Problem | Details |
|---------|---------|
| Missing values | 4,262 missing across workclass, occupation, native_country |
| Duplicates | 24 duplicate rows |
| Inconsistent text | Missing values written as ' ?' instead of NaN |
| Outliers | Extreme values in age, hours_per_week, capital_gain |

## Steps performed

1. Loaded dataset with correct column names (no header in raw file)
2. Treated ' ?' as missing values at load time using `na_values`
3. Removed 24 duplicate rows using `drop_duplicates()`
4. Filled missing numeric columns with **median**
5. Filled missing categorical columns with **mode**
6. Stripped whitespace from all text columns using `str.strip()`
7. Detected and capped outliers using IQR method (`clip()`)
8. Validated data ranges (age: 17–90, hours: 1–99)
9. Created 3 new features: `age_group`, `capital_net`, `is_high_earner`

## Results

| Metric | Before | After |
|--------|--------|-------|
| Total rows | 32,561 | 32,521 |
| Missing values | 4,262 | 0 |
| Duplicate rows | 24 | 0 |
| New features | 0 | 3 |

## Files

```
task1/
├── task01_cleaning.py        # main cleaning script
├── adult_data.csv            # raw dataset
├── adult_income_cleaned.csv  # cleaned output (used in Task 2)
└── charts/
    ├── 01_missing_values.png
    ├── 02_outliers.png
    ├── 03_age_distribution.png
    ├── 04_income.png
    ├── 05_education_vs_income.png
    ├── 06_hours_per_week.png
    ├── 07_workclass_vs_income.png
    ├── 08_age_group_vs_income.png
    └── 09_correlation.png
```

## How to run

```bash
pip install pandas numpy matplotlib seaborn
python task01_cleaning.py
```

## Tools used
Python 3.12 · pandas · numpy · matplotlib · seaborn
