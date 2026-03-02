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

#project titanic

import pandas as pd
import numpy as np

print("Libraries Imported Successfully\n")

df = pd.read_csv("Titanic-Dataset.csv")

print("Dataset Loaded Successfully\n")

print("Displaying First 10 Rows of the Dataset:\n")
print(df.head(10))

print("\nTotal Rows and Columns in Dataset:")
print(df.shape)

print("\nCreating Series from Columns...\n")

age_series = df["Age"]
fare_series = df["Fare"]
survival_series = df["Survived"]

print("Age Series:\n", age_series.head())
print("\nFare Series:\n", fare_series.head())
print("\nSurvival Series:\n", survival_series.head())

print("\nDataset Information:\n")
df.info()

print("\nStatistical Summary:\n")
print(df.describe())

print("\nMissing Values in Dataset:\n")
print(df.isnull().sum())

df["Age"].fillna(df["Age"].mean(), inplace=True)
df["Embarked"].fillna(df["Embarked"].mode()[0], inplace=True)

print("\nMissing Values After Cleaning:\n")
print(df.isnull().sum())

print("\nDetails of First Passenger using loc:\n")
print(df.loc[0])

print("\nFirst 5 Passengers using iloc:\n")
print(df.iloc[0:5])

print("\nSelected Columns (Age, Fare, Survived):\n")
print(df[["Age", "Fare", "Survived"]].head())

print("\nRenaming Column Sex to Gender\n")
df.rename(columns={"Sex": "Gender"}, inplace=True)

print("\nPivot Table: Survival based on Gender and Class\n")
pivot_table = df.pivot_table(values="Survived", index="Gender", columns="Pclass")
print(pivot_table)

print("\nPassengers Age > 30\n")
print(df[df["Age"] > 30].head())

print("\nPassengers Fare > 50\n")
print(df[df["Fare"] > 50].head())

print("\nFemale Passengers who Survived\n")
print(df[(df["Gender"] == "female") & (df["Survived"] == 1)].head())

print("\nSorting by Fare\n")
print(df.sort_values(by="Fare", ascending=False).head())

print("\nSorting by Age\n")
print(df.sort_values(by="Age").head())

print("\nSurvival Rate by Gender\n")
print(df.groupby("Gender")["Survived"].mean())

print("\nAverage Age by Passenger Class\n")
print(df.groupby("Pclass")["Age"].mean())

print("\nSurvival Count by Embarked Location\n")
print(df.groupby("Embarked")["Survived"].sum())

print("\nCreating Additional DataFrame for Class Information\n")

class_info = pd.DataFrame({
    "Pclass": [1, 2, 3],
    "Class_Type": ["First Class", "Second Class", "Third Class"]
})

merged_df = pd.merge(df, class_info, on="Pclass")

print("\nMerged Dataset Sample\n")
print(merged_df.head())

print("\nAverage Age of Survivors vs Non-Survivors\n")
print(df.groupby("Survived")["Age"].mean())

print("\nHighest Fare Paid:")
print(df["Fare"].max())

print("\nLowest Fare Paid:")
print(df["Fare"].min())

print("\nSurvival Percentage:")
survival_percentage = (df["Survived"].sum() / len(df)) * 100
print(round(survival_percentage, 2), "%")

print("\nProject Analysis Completed Successfully!")
