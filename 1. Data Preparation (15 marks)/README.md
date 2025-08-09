# DVA_Assignment
# Data Preparation

## 1. Load data

### Library needed:
*   Import the pandas library, which is essential for data manipulation.
    ```python
    import pandas as pd
    ```
*   Load your data from a CSV file into a DataFrame.
    ```python
    df = pd.read_csv("actual file name.csv")
    ```

### What to check right away
*   Get a concise summary of the DataFrame, including the number of rows, columns, non-null counts, and data types.
    ```python
    df.info()
    ```
*   View the first 5 rows of the DataFrame to get a quick look at your data.
    ```python
    df.head()
    ```
*   See a list of all column names.
    ```python
    df.columns
    ```
*   Print the full summary of the DataFrame (useful in scripts).
    ```python
    print(df.info())
    ```

---

## 2. Clean data

*   **Rename columns:** Adjust column names to be more descriptive or to remove special characters.
*   **Drop duplicates:** Remove duplicate rows from the DataFrame.
    ```python
    df = df.drop_duplicates()
    ```
*   **Ensure correct data types:** Make sure numerical columns are stored as numbers (integers/floats) and not as text (strings).

---

## 3. Handle missing values

*   Find out the total number of missing values (NaNs) in each column.
    ```python
    print(df.isnull().sum())
    ```
*   Replace missing values in a specific column (e.g., 'gdp_per_capita') with the mean of that column.
    ```python
    df['gdp_per_capita'].fillna(df['gdp_per_capita'].mean(), inplace=True)
    ```
*   Drop rows or columns that have too many missing values. `dropna()` removes rows with any null values by default.
    ```python
    df = df.dropna()
    ```

---

## 4. Generate insights and descriptive statistics

*   Generate descriptive statistics for the numerical columns in your dataset. This includes the mean, count, standard deviation, minimum, maximum, and quartile values (Q1, median/Q2, Q3).
    ```python
    df.describe()
    ```
*   **Create visuals:** Use plotting libraries like Matplotlib or Seaborn to visualize relationships in the data, guided by the story or hypothesis you are exploring.
