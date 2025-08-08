# Numerical Analysis

## What is Numerical Analysis?

Refers to using mathematical techniques and algorithms to analyze, interpret, and extract insights from numerical.

It involves working with data that has numbers as opposed to Categorical / text data such as e.g. Names, gender, yes/ no answer and many more.

An example of the numerical data used in Numerical analysis is Age, prices.

In Numerical analysis these numbers are used to perform:

- **Descriptive Statistics**  
  Which Summarizes and describes numerical data e.g. mean, mode, max, min, etc.

- **Inferential Statistics**  
  Makes predictions or inferences about a population based on a sample.

- **Numerical Computations**  
  Solving mathematical models using: Interpolation, Numerical integration, Root-finding algorithms, Matrix operations.

- **Regression Analysis**  
  Used to model the relationship between variables.

- **Data Cleaning and Transformation**  
  Handling: Missing values, outliers e.g. Filling in missing exam scores with the mean or median.

- **Correlation and Covariance**  
  Measures the relationship between numerical variables:  
  Correlation: Strength and direction (e.g., Pearson correlation)  
  Covariance: Direction of relationship.  
  Example: Correlation between number of study hours and performance.

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
