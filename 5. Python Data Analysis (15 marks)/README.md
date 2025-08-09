# Python Data Analysis (15 Marks)

Hey! Here’s my plan for tackling the final analysis part of our project. This is how I’m thinking about approaching it, with examples and prep steps, so when it’s time to actually do it, I’ll be ready to go.

---

## 1. How I’ll Clean & Transform the Data

Once the data is ready from the earlier deliverables, I’ll dig deeper to get new insights. Here’s what I’m planning:

### A. Make a 'Decade' Column
Grouping by decade should make it easier to spot trends over time.
```python
# When I have 'df_combined' with a 'Year' column
# I’ll make a new 'Decade' column
 df_combined['Decade'] = (df_combined['Year'] // 10) * 10
 print(df_combined[['Year', 'Decade']].head())
```

### B. Calculate Year-over-Year % Change
This will show how fast things are changing, not just the actual values.
```python
# I’ll use pandas to get % change
 df_combined['Labor_Force_Change_%'] = df_combined['Labor_Force_Pct'].pct_change() * 100
 df_combined['Education_Change_%'] = df_combined['Education_Pct'].pct_change() * 100
 print(df_combined[['Year', 'Labor_Force_Change_%', 'Education_Change_%']].head())
```

---

## 2. Making the Data Pop (Conditional Formatting)

I want my summary tables to be easy to read and highlight the important stuff. Instead of Excel, I’ll use pandas’ Styler in my notebook.

### Highlighting Max/Min Values
```python
summary_by_decade = df_combined.groupby('Decade').agg({
    'Labor_Force_Pct': 'mean',
    'Education_Pct': 'mean'
}).reset_index()

styled_summary = summary_by_decade.style.highlight_max(
    subset=['Labor_Force_Pct', 'Education_Pct'], color='lightgreen'
).highlight_min(
    subset=['Labor_Force_Pct', 'Education_Pct'], color='salmon'
)
# In my notebook, I’ll just display 'styled_summary' to see the effect.
```

### Color Gradient for Range
```python
styled_gradient = summary_by_decade.style.background_gradient(
    cmap='viridis', subset=['Labor_Force_Pct', 'Education_Pct']
)
# Display 'styled_gradient' in a notebook cell for a nice visual.
```

---

## 3. Charts & What I’ll Look For

This is where I’ll make the final charts that really show what’s going on. I want something that sums up the whole story.

### Bar Chart: Labor Force by Decade
```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
sns.barplot(
    data=summary_by_decade,
    x='Decade',
    y='Labor_Force_Pct'
)
plt.title('Average Labor Force Participation by Decade in South Africa')
plt.ylabel('Average Labor Force Participation (%)')
plt.xlabel('Decade')
plt.show()
```
**What I’ll be looking for:** The chart should show if labor force participation was highest in the 2010s, and if that lines up with a rise in education levels.

---

## My Final Workflow (Step-by-Step)

Here’s the full script I plan to use to get my results:
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# --- PREP (from earlier steps) ---
# 'df_combined' will be my clean DataFrame with 'Year', 'Labor_Force_Pct', and 'Education_Pct'.
data = {
    'Year': range(1995, 2023),
    'Labor_Force_Pct': [50.1, 50.3, 50.5, 51.0, 51.2, 51.8, 52.1, 52.3, 52.0, 52.5, 52.8, 53.1, 53.5, 53.2, 53.0, 52.9, 53.4, 54.0, 54.5, 54.8, 55.1, 55.3, 55.0, 54.7, 54.3, 54.0, 52.0, 52.3],
    'Education_Pct': [3.1, 3.1, 3.1, 3.1, 3.1, 4.2, 4.2, 4.2, 4.2, 4.2, 4.2, 5.5, 5.5, 5.5, 5.5, 5.5, 7.1, 7.1, 7.1, 7.1, 7.1, 8.9, 8.9, 8.9, 8.9, 8.9, 8.9, 8.9]
}
df_combined = pd.DataFrame(data)

# --- ANALYSIS ---
# Step 1: Decade column
 df_combined['Decade'] = (df_combined['Year'] // 10) * 10
# Step 2: Summary table
 summary_table = df_combined.groupby('Decade').agg(
    Avg_Labor_Participation=('Labor_Force_Pct', 'mean'),
    Avg_Education_Level=('Education_Pct', 'mean')
).round(2)
print("--- Summary Table by Decade ---")
print(summary_table)
# Step 3: Conditional formatting
 styled_table = summary_table.style.background_gradient(cmap='Greens', subset=['Avg_Education_Level']).highlight_max(subset=['Avg_Labor_Participation'], color='lightblue')
# Step 4: Final chart
 plt.figure(figsize=(10, 6))
 sns.barplot(data=summary_table.reset_index(), x='Decade', y='Avg_Labor_Participation', color='cornflowerblue')
 plt.title('Average Labor Force Participation by Decade in SA', fontsize=16)
 plt.ylabel('Average Participation Rate (%)', fontsize=12)
 plt.xlabel('Decade', fontsize=12)
 plt.ylim(50, max(summary_table['Avg_Labor_Participation']) * 1.05)
 plt.show()
# Step 5: My conclusion
# "The summary table and chart should make it clear: decades with higher average education also have higher labor force participation. The 2010s should be the peak for both!"
```

---

## What I Expect to Find

Once I run all this, I’m hoping the data will show that more education goes hand-in-hand with more people joining the workforce. I’ll be looking for the 2010s to stand out for both metrics!