# Hey there! Welcome to our DVA Assignment repo 👋

We’re super excited about the datasets we picked for this project. Honestly, we think they’re a great combo and they let us tell a pretty cool story for our assignment.

Let us walk you through why we chose them and how we’re planning to tackle the whole thing.

---

### 1. Why We Picked These Datasets (aka "The Story")

So, here’s what we’re working with:

1. **Educational Attainment:** `Educational attainment, at least Bachelor's or equivalent, population 25+, total (%) (cumulative)`
2. **Labor Force Participation:** `Labor force participation rate, total (% of total population ages 15+) (modeled ILO estimate)`

We thought it’d be interesting to see if more people getting degrees in South Africa actually means more people joining the workforce. Our main question is:

**"As higher education levels go up, does the labor force participation rate change too?"**

Our group’s hypothesis: If more people have degrees, maybe more people get into the formal workforce. We’re gonna test this with real data!

---

### 2. What’s Up With The Data?

We checked out the World Bank datasets and here’s what we found:

- **Labor Force Participation Rate:** This one’s got data for almost every year (like 1990 to 2023). Super consistent!
- **Educational Attainment (Bachelor’s):** Not so much. It’s only available for certain years (think 1996, 2001, 2007, 2011, 2016, etc.) because it comes from big surveys or censuses.

Honestly, this is part of the fun! Figuring out how to compare these two is a big part of our project.

---

## How We’re Tackling the Assignment

We’ve got enough data to do everything the rubric asks for. Here’s our plan:

**1. Data Preparation (15 marks)**
- First, we’ll load both datasets.
- We noticed one is yearly and the other is kinda random. So, we’ve got a missing values problem to solve!
- Two ways we can handle this:
    - **Option A (Matching Years):** Only use years where we have *both* education and labor force data. Fewer data points, but super accurate.
    - **Option B (Interpolation):** Fill in the gaps for education data (like forward-fill in Pandas, so 2001’s value stays until 2007, etc.).
- We’ll also do some basic stats (mean, median, etc.) for both datasets.

**2. Numerical Analysis (20 marks)**
- We’ll use NumPy to check the **correlation** between the two datasets. We’ll do this for both matched years and interpolated data, then compare.
- We’ll also look at how things change between years (percentage change and all that).
- Finally, we’ll explain what our findings mean (like, “Hey, we found a strong positive correlation!”).

**3. Visualisation (20 marks)**
- We’re planning a cool **line chart** with two y-axes: one for labor participation, one for education, and years on the x-axis.
- Also, a **scatter plot** to show the correlation (education on x, labor force on y, each dot is a year).

**4. Database Integration (20 marks)**
- We’ll set up a simple SQLite database with two tables: `EducationData` and `LaborForceData`, both using `Year` as a key.
- Then we’ll write some SQL `JOIN` queries to pull data for years where both have info. Gotta show off those database skills!

---

## Wrapping Up

We really think these datasets are a great match for this assignment. They’re relevant, let us tell a clear story, and give us a real-world data cleaning challenge (which is kinda fun, honestly).

Thanks for checking out our repo! Wish us luck 😄