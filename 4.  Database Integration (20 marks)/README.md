# Visualisation Overview

## 1. Create Plots (Bar, Scatter, Box, Histograms, etc.)

We will use different types of plots to represent key variables from our datasets to support the stories and insights being told. Below are the plot types and what they help us uncover:

| Plot Type | Purpose | Example from Data |
|-----------|---------|-------------------|
| Bar Chart | Compare categories | Bachelor's Degree % in 2015 vs. 2020 vs. 2024 |
| Scatter Plot | Show correlation or relationships between two numeric variables | Education level (%) vs. Labor force participation (%) |
| Box Plot | Visualize distribution, median, quartiles, and outliers | Participation rates across different sectors |
| Histogram | Show frequency distribution of a single variable | Distribution of age or participation rates over time |
| Line Plot | Track changes over time | Trend of education growth from 2010 to 2024 |

## 2. Explain Trends and Patterns

Each plot will be accompanied by a short narrative explaining the trends, patterns, and anomalies observed.

### Definitions:

**Trend:** A general direction in which something is developing over time (e.g., "Bachelor's degree attainment has increased steadily from 2010 to 2024").

**Pattern:** A repeating or consistent structure/behavior (e.g., "Each time education levels rise, participation remains flat").

**Anomaly:** An unexpected result that deviates from the trend (e.g., "A sharp drop in participation despite education increase in 2020").

### Example Insights:

- "Despite a 15% increase in tertiary education from 2010 to 2024, labor force participation remains stagnant."
- "Scatter plots show weak or negative correlation between higher education and participation in certain periods."

## 3. Use Colour and Labels Clearly

To ensure clear and accessible visualisations:

| Element | Implementation |
|---------|----------------|
| Axis Labels | Clearly describe x and y axes (e.g., "Year", "Education Attainment (%)") |
| Legends | Show what each color or marker represents (e.g., age group, location, or sector) |
| Titles | Every plot will have a descriptive title (e.g., "Trend in Labor Force Participation (2010–2024)") |
| Colors | Distinct but minimal colors to avoid confusion and emphasize comparisons |

## Story-Based Visualisation Strategy

Below is the breakdown of how we will apply visualisation and analysis to each story theme:

### 1. The Skills Premium Paradox

**Goal:** Show that educational attainment has increased, but labor participation has not kept pace.

**Use:** Line plot for education and participation trends over years.

Scatter plot: Correlation between education growth and labor force participation.
Highlight: 2015, 2020, 2024.

**Analysis:**
- Calculate correlation coefficient.
- Identify gap between expected and actual labor participation ("education dividend").
- Lag analysis: does education from 2015 impact participation in 2018?

### 2. Economic Sector Mismatch

**Goal:** Show misalignment between education output and sector labor demand.

**Use:** Bar plots for sector employment vs. education levels.
Box plots: Compare sector participation distribution.
Scatter plot: Education levels vs. participation rate by sector.

**Analysis:**
- Compare growth in education vs. growth in sector jobs.
- Identify if automation/prioritization affects educated employment.
- Show inverse relationships between high education and low participation in some sectors.

### 3. Urban vs Rural Divide

**Goal:** Explore geographic disparities in education and labor force engagement.

**Use:**
- Side-by-side bar plots: Urban vs. rural degree holders.
- Scatter plot: Education vs. participation, colored by province.

**Analysis:**
- Calculate urban–rural education and participation gaps.
- Compare migration patterns (educated rural youth moving to urban areas).
- Show if education premium varies by location.

### 4. Youth Employment Crisis

**Goal:** Investigate the diminishing returns of education for younger age groups.

**Use:**
- Line plots or bar charts for participation by age group (15–24, 25–34, 35–54).
- Histogram or scatter plot: Participation vs. education level by cohort.

**Analysis:**
- Compare participation across age brackets.
- Determine if youth (especially 25–34) benefit from education in labor outcomes.
- Calculate "youth education penalty" if education doesn't improve youth employment.

## Technical Analysis Techniques

In addition to plotting:

| Technique | Purpose |
|-----------|---------|
| Correlation Coefficient (Pearson) | Measure strength/direction of education vs. participation |
| Inflection Point Detection | Identify years when trend direction changed |
| Lag Analysis | Test delayed effects of education on participation |
| Regression Analysis | Quantify the relationship between education and labor participation |
| Scatter Visualisations | Illustrate positive, negative, or no correlation |