# Numerical Analysis

## Overview
This section builds on the data preparation phase and applies mathematical and statistical techniques to analyze the South African education and labour datasets.

## Steps Performed

1. **Load and Prepare Data**
   - Imported pandas, numpy, matplotlib, seaborn.
   - Loaded education and labour datasets.
   - Filtered for South Africa and selected relevant columns (Year, Indicator, Sex, Age, Value).

2. **Descriptive Statistics**
   - Calculated mean, median, mode, min, max, and standard deviation for key numerical columns.
   - Compared statistics across different groups (by Sex, Age, Indicator).

3. **Grouped Analysis**
   - Grouped data by Sex and Age to analyze differences and trends.

4. **Year Matching and Correlation**
   - Merged datasets by Year to enable direct comparison.
   - Calculated correlation between education attainment and labour force participation (yearly averages).

5. **Visualization**
   - Plotted histograms for distributiongits.
   - Created scatter plots for relationships.
   - Used boxplots to compare groups.

## Why Year Matching?
Year matching is performed in this deliverable to enable meaningful comparison and correlation analysis between the two datasets. This allows us to explore relationships and trends over time.

## Next Steps
- Use insights from numerical analysis for further statistical modeling or database integration in subsequent deliverables.

---

NumPy is a powerful Python library used in numerical analysis to perform fast and efficient mathematical operations on large sets of numerical data.

- NumPy provides fast functions for basic statistics on numerical data.
- NumPy helps in detecting and handling missing or invalid values.
- Assess relationships between two numerical datasets i.e. Checking how two features move together.
- While NumPy doesn’t plot data, it helps prepare time series for trend analysis. i.e. Detecting changes and patterns over time.

---

## Why do we Reshape arrays?

We often reshape arrays to match the structure required by mathematical operations or machine learning models. NumPy expects data in specific formats, especially when working with vectors, matrices, or multi-dimensional arrays.

## How do we Reshape arrays?

You reshape arrays using the `reshape()` method:  
`array.reshape(new_shape)`.

## What operations can be performed on reshaped arrays?

- After reshaping, you can perform arithmetic operations.
- Enable operations like dot products, transposes, and solving equations.
- Some plots (like heatmaps or matrix plots) need reshaped data.
