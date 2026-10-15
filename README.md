# ☕ Café Sales Analysis

A data cleaning and analysis project in Python. It takes a messy café sales dataset, cleans it, and turns it into business insights about products, locations and monthly revenue.

## Objective

- Clean a real-world style "dirty" dataset with invalid and missing values
- Find which products and locations generate the most revenue
- Track monthly revenue trends and product growth
- Suggest business actions based on the findings

## Dataset

**File:** `dirty_cafe_sales.csv`
**Source:** [add dataset link here]

Each row is one café transaction with these columns:

| Column | Description |
|---|---|
| Transaction ID | Unique ID for each sale |
| Item | Product sold (coffee, tea, salad, etc.) |
| Quantity | Number of units bought |
| Price Per Unit | Price of one unit |
| Total Spent | Total amount of the transaction |
| Payment Method | Cash, card or digital wallet |
| Location | In-store or takeaway |
| Transaction Date | Date of the sale |

The raw data contains invalid values such as `ERROR`, `UNKNOWN`, blanks and wrong data types.

## Tools Used

- Python
- Pandas
- NumPy
- VS Code

## Project Workflow

### 1. Data Inspection
- Checked structure, data types and missing values with `head()`, `info()`, `isna()` and `describe()`

### 2. Data Cleaning
- Standardized column names (lowercase, no spaces)
- Cleaned text values in `item`, `payment_method` and `location`
- Replaced fake missing values (`ERROR`, `UNKNOWN`, `N/A`, blanks) with proper `NaN`
- Converted quantity, price and total to numeric, and transaction date to datetime
- Filled missing quantity and price with the median, and missing payment method and location with labels

### 3. Analysis
- Created a `revenue` column (quantity × price per unit)
- Revenue by item and by location
- Monthly revenue share and month-over-month % change
- Revenue share of each item, overall and by month
- Average monthly growth of each item

## Key Insights

**Top 5 items by revenue**

| Item | Revenue |
|---|---|
| Salad | 16,959 |
| Sandwich | 13,538 |
| Smoothie | 13,218 |
| Juice | 10,542 |
| Cake | 10,401 |

**Items with the fewest transactions:** tea (1,089), cookie (1,092), smoothie (1,096)

**Monthly revenue is flat:** each month brings in about 7–8% of yearly revenue, so there is no clear growth over the year.

**Average monthly growth by item**

| Item | Avg. monthly change |
|---|---|
| Smoothie | +4.57% |
| Coffee | +3.21% |
| Cookie | +1.51% |
| Tea | +1.09% |
| Juice | +1.04% |
| Cake | −0.23% |
| Salad | −0.35% |
| Sandwich | −2.06% |

Salad and sandwich are the top two revenue items, but their monthly revenue is slightly declining, which is worth monitoring.

## Recommendations

- **Combo offers** to boost low-selling items, e.g. salad + tea, salad + smoothie, sandwich + tea + cookie
- **Customer feedback** on salad and sandwich to understand what changes customers want and protect the top revenue items
- **Growth plan:** monthly revenue should be increasing, so promotions or new products could help drive growth

## Limitations and Next Steps

- Missing prices and quantities were filled with the median. A better approach is to recover them using `total_spent = quantity × price_per_unit` and each item's fixed menu price.
- Rows with a missing item or date are left out of item and monthly breakdowns.
- Each transaction contains one item, so combo offers should be tested before rollout. The data cannot show which items are bought together.
- Next step: add charts with Matplotlib or Seaborn to visualize the trends.

## How to Run

1. Clone this repository
2. Install the libraries:
   ```bash
   pip install pandas numpy
   ```
3. Keep `dirty_cafe_sales.csv` in the same folder as the script
4. Run:
   ```bash
   python cafe_sales_analysis.py
   ```

## Project Structure

```
├── cafe_sales_analysis.py   # cleaning + analysis script
├── dirty_cafe_sales.csv     # raw dataset
└── README.md                # project overview
```

