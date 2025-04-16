# Dynamic Product Price Adjustment Script

## Project Overview

This Python script reads product and sales data from CSV files, applies specific business pricing rules, and generates an updated price list. It helps automate dynamic pricing decisions based on stock and sales performance.

## Input Files

1. **`products.csv`**  
   Contains the product catalog with pricing, cost, and stock details.
   | sku | name | current_price | cost_price | stock |
   |-----|------|----------------|------------|--------|
   | A123 | Item A | 649.99 | 500.00 | 150 |

2. **`sales.csv`**  
   Contains sales quantities in the last 30 days.
   | sku | quantity_sold |
   |-----|----------------|
   | A123 | 10 |

##  Pricing Rules Applied

The following rules are evaluated in order of priority:

1. **Rule 1 – Low Stock, High Demand:**  
   If `stock < 20` and `quantity_sold > 30`, increase price by 15%.

2. **Rule 2 – Dead Stock:**  
   If `stock > 200` and `quantity_sold == 0`, decrease price by 30%.

3. **Rule 3 – Overstocked Inventory:**  
   If `stock > 100` and `quantity_sold < 20`, decrease price by 10%.

4. **Rule 4 – Minimum Profit Guarantee:**  
   Ensure new price is at least 20% above cost price.  
   If not, set `new_price = cost_price * 1.2`.

5. **Rounding:**  
   Final price is rounded to 2 decimal places.

##  Output File

- **`updated_prices.csv`**  
  Contains:
  - `sku`
  - `old_price` (with INR)
  - `new_price` (with INR)

## Libraries Used

- `pandas`: for data manipulation
- `os` *(optional)*: for file checks (not used here, but can be helpful)

##  How to Run

1. Make sure you have Python and Jupyter Notebook installed.
2. Place `products.csv`, `sales.csv`, and the Jupyter Notebook in the same folder.
3. Run all cells in the notebook.
4. The final `updated_prices.csv` will be generated in the same folder.

##  Example Output

| sku  | old_price | new_price |
|------|-----------|-----------|
| A123 | 649.99 INR | 600.00 INR |

##  Deliverables

- `pricing_script.ipynb` – Jupyter notebook with the full implementation.
- `updated_prices.csv` – Final output file.
- `README.md` – This instruction and documentation file.



