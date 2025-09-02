# Deliverable 1: Data Preparation

This guide provides a step-by-step walkthrough for the data preparation phase of the assignment. The goal is to load, clean, and perform an initial analysis of the two South African datasets: `education.csv` and `labour.csv`.

---

### 1. Load Data and Required Libraries

First, we need to import the necessary Python libraries. We'll use `pandas` for data manipulation and `matplotlib` with `seaborn` for our initial visualizations.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

Next, we load the two CSV files into pandas DataFrames. A `try-except` block is used to handle potential `FileNotFoundError` gracefully.

```python
try:
    edu_df = pd.read_csv("education.csv")
    labour_df = pd.read_csv("labour.csv")
    print("Files loaded successfully!")
except FileNotFoundError as e:
    print(f"Error loading files: {e}")
```

---

### 2. Initial Inspection and Cleaning

Before cleaning, it's crucial to understand the structure of our data.

*   **Get a summary:** Use `df.info()` to see the number of rows, columns, and data types.
*   **Filter for South Africa:** The assignment requires us to focus on South African data. We'll filter both DataFrames to only include rows where the `REF_AREA_LABEL` is "South Africa."
*   **Select and Rename Columns:** To make the data easier to work with, we'll select only the columns we need and rename them to be more intuitive.

```python
# Filter for South Africa
edu_sa = edu_df[edu_df["REF_AREA_LABEL"] == "South Africa"].copy()
labour_sa = labour_df[labour_df["REF_AREA_LABEL"] == "South Africa"].copy()

# Define a clear mapping for columns to keep and their new names
columns_to_keep = {
    "TIME_PERIOD": "Year",
    "INDICATOR_LABEL": "Indicator",
    "SEX_LABEL": "Sex",
    "AGE_LABEL": "Age",
    "OBS_VALUE": "Value"
}

# Apply the selection and renaming
edu_clean = edu_sa[list(columns_to_keep.keys())].rename(columns=columns_to_keep)
labour_clean = labour_sa[list(columns_to_keep.keys())].rename(columns=columns_to_keep)
```

---

### 3. Handle Missing Values

A critical step in data preparation is to check for and handle missing data.

```python
print("---"Missing values in cleaned Education data"---")
print(edu_clean.isnull().sum())

print("\n---"Missing values in cleaned Labour data"---")
print(labour_clean.isnull().sum())
```
In this specific dataset for South Africa, no missing values were found in the `Value` column. However, if there were, we would need to handle them. A common strategy for time-series data is **forward-fill**, which propagates the last valid observation forward.

```python
# Example of forward-filling if NaNs were present:
# edu_clean['Value'].fillna(method='ffill', inplace=True)
```

---

### 4. Generate Insights and Descriptive Statistics

Finally, we can generate some initial insights.

*   **Descriptive Statistics:** The `.describe()` method provides a quick summary of the central tendency, dispersion, and shape of the dataset’s distribution.
*   **Visual Inspection:** A histogram is an excellent way to visualize the distribution of our key values. This helps us understand the spread and frequency of the data points.

```python
print("\n---"Descriptive Statistics for Education Data"---")
print(edu_clean.describe())

print("\n---"Descriptive Statistics for Labour Data"---")
print(labour_clean.describe())

# Create histograms to visualize the distribution of values
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
sns.histplot(edu_clean['Value'], kde=True)
plt.title('Distribution of Education Attainment (%)')

plt.subplot(1, 2, 2)
sns.histplot(labour_clean['Value'], kde=True)
plt.title('Distribution of Labour Force Participation (%)')

plt.tight_layout()
plt.show()
```
By following these steps, you will have a clean, well-understood dataset ready for the subsequent stages of analysis, fully meeting the requirements for this deliverable.

```