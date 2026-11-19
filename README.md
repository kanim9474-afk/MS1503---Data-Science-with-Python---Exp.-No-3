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

# Step 1: Create a sample retail dataset
data = {
    "Order_ID": [101, 102, 103, 104, 105, 105, 106, 107],
    "Product": ["Laptop", "Tablet", "Phone", "Printer", "Monitor", "Monitor", "Tablet", "Laptop"],
    "Region": ["East", "West", "North", "South", "East", "East", "West", None],
    "Sales": [55000, 32000, None, 18000, 24000, 24000, 32000, 55000],
    "Discount": [5, None, 10, 8, 5, 5, None, 8],
    "Profit": [8000, 5000, 4000, None, 3000, 3000, 5000, 8000]
}

df = pd.DataFrame(data)

print("---- Original Retail Dataset ----")
display(df)
print("\nDataset Shape:", df.shape)

# Step 2: Check for missing values
print("\nMissing Values per Column:\n", df.isnull().sum())

# Step 3: Fill missing numeric values with the column mean
df["Sales"].fillna(df["Sales"].mean(), inplace=True)
df["Discount"].fillna(df["Discount"].mean(), inplace=True)
df["Profit"].fillna(df["Profit"].mean(), inplace=True)

# Step 4: Fill missing Region with mode (most frequent value)
df["Region"].fillna(df["Region"].mode()[0], inplace=True)

# Step 5: Remove duplicate records
df.drop_duplicates(inplace=True)

print("\n---- Cleaned Retail Dataset ----")
display(df)
print("\nDataset Shape after Cleaning:", df.shape)

# Step 6: Display summary statistics
print("\nSummary Statistics:\n", df.describe()) 


## Output
<img width="455" height="365" alt="image" src="https://github.com/user-attachments/assets/daa36fa7-c1e7-4e60-a90b-974cc76d173b" />
<img width="557" height="648" alt="image" src="https://github.com/user-attachments/assets/390467f2-6783-4afb-8f3b-07c602c59a40" />



## Result  
The program successfully creates a retail dataset, identifies missing entries and duplicate rows, imputes missing values using mean and mode strategies, removes   duplicates, and outputs a clean dataset ready for downstream analysis.  

