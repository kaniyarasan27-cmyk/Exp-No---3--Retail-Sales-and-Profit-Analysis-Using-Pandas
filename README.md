-Exp-No---3--Retail-Sales-and-Profit-Analysis-Using-Pandas




Aim:



To create a sample retail dataset, identify and handle missing values and duplicates using Pandas.




Algorithm:





1. Import the Pandas library.
2. Create a DataFrame with columns – Order_ID, Product, Region, Sales, Discount, and Profit.
3. Introduce some missing and duplicate rows manually.
4. Use isnull() and sum() to check missing values.
5. Replace missing values using fillna() and mean().
6. Remove duplicates using drop_duplicates().
7. Display the cleaned dataset with its shape.


Program:

# Cleaning and Preparing Retail Data using default values

import pandas as pd

# Step 1: Create a sample retail dataset

data = {
    "Order_ID": [101, 102, 103, 104, 105, 105, 106, 107],

    "Product": ["Laptop", "Tablet", "Phone", "Printer",
                "Monitor", "Monitor", "Tablet", "Laptop"],

    "Region": ["East", "West", "North", "South",
               "East", "East", "West", None],

    "Sales": [55000, 32000, None, 18000,
              24000, 24000, 32000, 55000],

    "Discount": [5, None, 10, 8, 5, 5, None, 8],

    "Profit": [8000, 5000, 4000, None,
               3000, 3000, 5000, 8000]
}

df = pd.DataFrame(data)

print("---- Original Retail Dataset ----")
print(df)

print("\nDataset Shape:", df.shape)

# Step 2: Check for missing values
print("\nMissing Values per Column:\n", df.isnull().sum())

# Step 3: Fill missing numeric values with column mean
df["Sales"].fillna(df["Sales"].mean(), inplace=True)

df["Discount"].fillna(df["Discount"].mean(), inplace=True)

df["Profit"].fillna(df["Profit"].mean(), inplace=True)

# Step 4: Fill missing Region with mode (most frequent value)
df["Region"].fillna(df["Region"].mode()[0], inplace=True)

# Step 5: Remove duplicate records
df.drop_duplicates(inplace=True)

print("\n---- Cleaned Retail Dataset ----")
print(df)

print("\nDataset Shape after Cleaning:", df.shape)

# Step 6: Display summary statistics
print("\nSummary Statistics:\n", df.describe())



Output:




---- Original Retail Dataset ----
   Order_ID  Product Region    Sales  Discount  Profit
0       101   Laptop   East  55000.0       5.0  8000.0
1       102   Tablet   West  32000.0       NaN  5000.0
2       103    Phone  North      NaN      10.0  4000.0
3       104  Printer  South  18000.0       8.0     NaN
4       105  Monitor   East  24000.0       5.0  3000.0
5       105  Monitor   East  24000.0       5.0  3000.0
6       106   Tablet   West  32000.0       NaN  5000.0
7       107   Laptop   None  55000.0       8.0  8000.0

Dataset Shape: (8, 6)

Missing Values per Column:
 Order_ID    0
Product     0
Region      1
Sales       1
Discount    2
Profit      1
dtype: int64

---- Cleaned Retail Dataset ----
   Order_ID  Product Region         Sales   Discount       Profit
0       101   Laptop   East  55000.000000   5.000000  8000.000000
1       102   Tablet   West  32000.000000   6.833333  5000.000000
2       103    Phone  North  34285.714286  10.000000  4000.000000
3       104  Printer  South  18000.000000   8.000000  5142.857143
4       105  Monitor   East  24000.000000   5.000000  3000.000000
6       106   Tablet   West  32000.000000   6.833333  5000.000000
7       107   Laptop   East  55000.000000   8.000000  8000.000000

Dataset Shape after Cleaning: (7, 6)

Summary Statistics:
          Order_ID         Sales   Discount       Profit
count    7.000000      7.000000   7.000000     7.000000
mean   104.000000  35755.102041   7.095238  5448.979592
std      2.160247  14285.884353   1.779141  1897.776306
min    101.000000  18000.000000   5.000000  3000.000000
25%    102.500000  28000.000000   5.916667  4500.000000
50%    104.000000  32000.000000   6.833333  5000.000000
75%    105.500000  44642.857143   8.000000  6571.428571
max    107.000000  55000.000000  10.000000  8000.000000
/tmp/ipykernel_2548/462258403.py:36: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.



The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df["Sales"].fillna(df["Sales"].mean(), inplace=True)


  
/tmp/ipykernel_2548/462258403.py:38: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.


The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df["Discount"].fillna(df["Discount"].mean(), inplace=True)
/tmp/ipykernel_2548/462258403.py:40: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.


The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df["Profit"].fillna(df["Profit"].mean(), inplace=True)




  
/tmp/ipykernel_2548/462258403.py:43: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.



The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df["Region"].fillna(df["Region"].mode()[0], inplace=True)






  Result:

  
          The program successfully created a retail dataset, identified and handled missing values.
