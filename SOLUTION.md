# Solution Notes (summary)

Data cleaning
- Strip whitespace from column names and month strings.
- Fix typos (e.g., 'Marcrh' -> 'March', 'November ' -> 'November').
- Create a Date column from Year + Month for time-series analysis.
- Convert required columns to numeric.

Missing values
- For time-series CPI indices, use forward-fill or a short-window moving average for imputation.
- Document the method in your README (which method you used and why).

Analysis performed
1. Year-on-Year (Y-o-Y) change:
   - For the General index (Rural+Urban), compute percent change versus the same month in the previous year:
     YOY_pct = (index_t / index_t-12 - 1) * 100.
   - Plot monthly YOY_pct and compute average YOY_pct per year to identify the year with highest inflation.

2. 12-month period ending May 2023:
   - Filter data for Jun 2022 - May 2023 for Rural+Urban.
   - Compute month-on-month % change for the Food and beverages index.
   - Identify highest and lowest month-on-month % values.
   - For food subcategories, compute absolute change = (value_end - value_start) over the period to find largest contributor.

Files included
- analysis_script.py - runnable script that reproduces the above steps using pandas and matplotlib.
- results/ - contains yoy_general_ru.png and food_abs_changes_jun22_may23.csv.

How to run locally
# Ensure you have Python3 and pandas installed
python3 analysis_script.py
# Results (PNGs & CSVs) will be created in the results/ folder
