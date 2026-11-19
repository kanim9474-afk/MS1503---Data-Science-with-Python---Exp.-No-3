# Experiment 3 : Retail Sales and Profit Analysis Using Pandas

## Aim
To create a sample retail dataset, identify and handle missing values (`NaN`/`None`) and duplicate records, and compute summary statistics using Pandas in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data cleaning and analysis.
3. **Initialize Raw Retail Dataset**: Create a Python dictionary `data` containing retail records (`Order_ID`, `Product`, `Region`, `Sales`, `Discount`, `Profit`) with deliberate missing (`None`) entries and duplicate rows.
4. **Construct DataFrame & Inspect**:
   * Convert `data` into a Pandas DataFrame `df` using `pd.DataFrame(data)`.
   * Print the original dataset and its initial dimensions (`df.shape`).
5. **Detect Missing Values**:
   * Count missing entries per column using `df.isnull().sum()`.
6. **Impute Missing Values**:
   * Replace missing numerical values in `Sales`, `Discount`, and `Profit` with their respective column means using `.fillna(df[col].mean())`.
   * Replace missing categorical values in `Region` with the column mode (most frequent category) using `.fillna(df["Region"].mode()[0])`.
7. **Remove Duplicate Records**:
   * Drop exact duplicate rows from `df` using `df.drop_duplicates()`.
8. **Display Cleaned Dataset & Summary Statistics**:
   * Print the cleaned DataFrame, updated dimensions (`df.shape`), and descriptive statistical metrics (`df.describe()`).
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation & Inspection** | `pd.DataFrame()` | Converts a Python dictionary into a labeled 2D tabular DataFrame |
| | `df.shape` | Returns the `(rows, columns)` dimensions before and after cleaning |
| | `df.isnull().sum()` | Counts the number of missing (`NaN`/`None`) values in each column |
| **Missing Value Imputation** | `df[col].fillna()` | Replaces missing values with a specified replacement value |
| | `df[col].mean()` | Calculates the arithmetic mean for numerical column imputation |
| | `df[col].mode()[0]` | Retrieves the most frequent category for categorical column imputation |
| **Deduplication & Summary** | `df.drop_duplicates()` | Identifies and removes duplicate rows from the DataFrame |
| | `df.describe()` | Generates count, mean, standard deviation, min, quartiles, and max for numerical features |

## Program

#Cleaning and Preparing Retail Data using Pandas

#Step 1: Create a sample retail dataset

#Step 2: Check for missing values

#Step 3: Fill missing numeric values with column mean

#Step 4: Fill missing Region with mode (most frequent value)

#Step 5: Remove duplicate records

#Step 6: Display summary statistics



## Output
import nbformat as nbf 
import subprocess 
import sys 

nb = nbf.v4.new_notebook() 

cells = [ 
    nbf.v4.new_markdown_cell("""# Customer Data Exploration Using Pandas   

## Aim  
To create a sample customer dataset and perform data exploration and basic analytics using Pandas functions.  

## Algorithm  
1. Import the Pandas library.  
2. Create a customer dataset using a Python dictionary.  
3. Convert the dictionary into a Pandas DataFrame.  
4. Display the dataset, its shape, columns, and data types.  
5. Perform exploratory functions: `head()`, `tail()`, `info()`, `describe()`.  
6. Use filtering, sorting, and grouping operations to analyze customer insights.  
7. Find statistics such as average income, highest spending score, and region-wise averages."""),  
    
    nbf.v4.new_code_cell("""# Customer Data Exploration using Pandas (Default Values)  
import pandas as pd  

# Step 1: Create a sample customer dataset  
data = {  
    "Customer_ID": [101, 102, 103, 104, 105, 106, 107, 108],  
    "Customer_Name": ["Anita", "Rajesh", "Priya", "Vikram", "Divya", "Manoj", "Sita", "Amit"],  
    "Region": ["North", "South", "East", "West", "North", "South", "East", "West"],  
    "Age": [25, 32, 41, 29, 35, 45, 28, 40],  
    "Annual_Income": [55000, 72000, 61000, 48000, 85000, 90000, 64000, 58000],  
    "Spending_Score": [78, 62, 45, 88, 92, 55, 70, 60],  
    "Loyalty_Years": [2, 5, 4, 3, 6, 7, 3, 4]  
}

# Step 2: Convert to a Pandas DataFrame  
df = pd.DataFrame(data)  
print("---- CUSTOMER DATASET ----")  
print(df)"""),  

    nbf.v4.new_code_cell("""# Step 3: Basic exploration
print("Shape of Dataset:", df.shape)  
print("Columns:", df.columns.tolist())  

print("\\n---- Dataset Info ----")  
print(df.info())  

print("\\n---- Summary Statistics ----")  
print(df.describe())"""),  

    nbf.v4.new_code_cell("""# Step 4: Display first and last few records
print("First 3 Records:\\n", df.head(3))  
print("\\nLast 3 Records:\\n", df.tail(3))"""),  

    nbf.v4.new_code_cell("""# Step 5: Sort customers by Annual Income (descending)
print("Customers Sorted by Annual Income:\\n", df.sort_values(by="Annual_Income", ascending=False))"""),  

    nbf.v4.new_code_cell("""# Step 6: Filter high-income customers (Income > 70000)
print("High Income Customers (Income > 70000):\\n", df[df["Annual_Income"] > 70000][["Customer_Name", "Annual_Income"]])"""),  

    nbf.v4.new_code_cell("""# Step 7: Group customers by Region and find average Income and Spending Score
print("Region-wise Average Income and Spending Score:")  
print(df.groupby("Region")[["Annual_Income", "Spending_Score"]].mean())  

# Step 8: Count number of customers in each Region  
print("\\nCustomer Count per Region:")  
print(df["Region"].value_counts())"""),  

    nbf.v4.new_code_cell("""# Step 9: Identify customer with maximum Spending Score
max_spender = df.loc[df["Spending_Score"].idxmax()]  
print("Top Spender Details:\\n", max_spender)  

# Step 10: Compute overall averages    
print("\\nAverage Annual Income:", df["Annual_Income"].mean())  
print("Average Spending Score:", df["Spending_Score"].mean())"""),  

    nbf.v4.new_markdown_cell("""## Result
The program successfully created a customer dataset using Pandas and performed data exploration and basic analytics.""")  
]

nb['cells'] = cells  

filename = "customer_data_exploration_pandas.ipynb"  
with open(filename, 'w', encoding='utf-8') as f:  
    nbf.write(nb, f)   

# Execute the notebook using jupyter nbconvert so outputs are pre-populated  
subprocess.run([sys.executable, "-m", "jupyter", "nbconvert", "--to", "notebook", "--execute", "--inplace", filename], check=True)  
print("Successfully generated and executed:", filename)  

## Result  
The program successfully creates a retail dataset, identifies missing entries and duplicate rows, imputes missing values using mean and mode strategies, removes   duplicates, and outputs a clean dataset ready for downstream analysis.  

