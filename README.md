# python
import numpy as np

categories = np.array(["Beverages", "Food", "Electronics", "Clothing", "Household"])
quantity = np.array([120, 250, 60, 150, 200])
unit_price = np.array([10, 5, 200, 25, 15])
profit = np.array([300, 400, 800, 350, 500])

total_sales = quantity * unit_price
overall_sales = np.sum(total_sales)
average_sales = np.mean(total_sales)
median_sales = np.median(total_sales)
std_sales = np.std(total_sales)
profit_margin = (profit / total_sales) * 100
best_category = categories[np.argmax(total_sales)]

print("Total Sales:", total_sales)
print("Overall Sales:", overall_sales)
print("Average Sales:", average_sales)
print("Median Sales:", median_sales)
print("Standard Deviation:", std_sales)
print("Profit Margin (%):", np.round(profit_margin, 2))
print("Best Performing Category:", best_category)
