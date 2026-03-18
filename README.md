# Introduction to Graphing in R
### Bioinformatics Beginner Lab · ~1.5 hours
 
---
 
## Learning Goals
 
By the end of this activity, you will:
 
- Understand the basic types of graphs (histogram, bar graph, boxplot, scatterplot)
- Learn how to create simple graphs in R using `ggplot2`
- Understand when to use different types of graphs
- Improve graphs to make them clearer and easier to understand
 
> **Note:** All code examples are shown in code blocks. In the Questions section, you will write your own code.
 
---
 
## Part 1: Getting Started with R
 
### Step 1: Load ggplot2
 
Before making graphs, load the package:
 
```r
library(ggplot2)
```
 
**Why?** R does not automatically include advanced graphing tools. `ggplot2` gives us easy and powerful ways to create graphs.
 
---
 
## Part 2: Understanding Data Types
 
Before making graphs, you need to understand the types of data you are working with:
 
| Data Type | Description | Examples |
|-----------|-------------|---------|
| **Numerical** | Numbers | age, height, income |
| **Categorical** | Groups or labels | gender, continent |
 
### Choosing the Right Graph
 
| X Variable | Y Variable | Graph Type |
|------------|------------|------------|
| Numerical | Numerical | Scatterplot |
| Categorical | Numerical | Boxplot |
| Categorical | Categorical | Bar graph |
| Numerical | *(frequency)* | Histogram |
 
> Choosing the right graph depends on your data!
 
---
 
## Part 3: Introduction to ggplot2
 
All graphs in this lab follow this basic structure:
 
```r
ggplot(data, aes(x = variable)) + geom_...
```
 
| Component | Meaning |
|-----------|---------|
| `data` | Your dataset |
| `aes()` | Tells R what variables to use |
| `geom_...` | The type of graph |
 
---
 
## Part 4: Histograms — Numerical Data
 
A histogram shows how values are distributed across a single numerical variable.
 
### Load Data
 
```r
titanicData <- read.csv("DataForLabs/titanic.csv", stringsAsFactors = TRUE)
```
 
### Create a Histogram
 
```r
ggplot(titanicData, aes(x = age)) + geom_histogram()
```
 
**What this shows:** How often different ages appear in the dataset.
 
**Why use a histogram?**
- Helps see patterns (clusters, spread, skewness)
- Useful for understanding distributions
 
---
 
## Part 5: Bar Graphs — Categorical Data
 
A bar graph shows counts for each category.
 
```r
ggplot(titanicData, aes(x = sex)) + geom_bar()
```
 
**What this shows:** The number of passengers by sex.
 
---
 
## Part 6: Boxplots — Categorical + Numerical
 
A boxplot compares a numerical variable across groups.
 
```r
ggplot(titanicData, aes(x = sex, y = age)) + geom_boxplot()
```
 
**What this shows:** Age distribution for each sex.
 
### Key Parts of a Boxplot
 
| Element | Meaning |
|---------|---------|
| Middle line | Median |
| Box | Middle 50% of data (IQR) |
| Whiskers | Spread of remaining data |
 
---
 
## Part 7: Scatterplots — Numerical vs. Numerical
 
A scatterplot shows the relationship between two numerical variables.
 
### Load Data
 
```r
guppyFatherSonData <- read.csv("DataForLabs/chap02e3bGuppyFatherSonAttractiveness.csv")
```
 
### Create a Scatterplot
 
```r
ggplot(guppyFatherSonData, aes(x = fatherOrnamentation, y = sonAttractiveness)) +
  geom_point()
```
 
**What this shows:** The relationship between father ornamentation and son attractiveness.
 
---
 
## Part 8: Improving Your Graphs
 
You can make any graph clearer by adding labels and a cleaner theme:
 
```r
ggplot(data, aes(x = variable)) +
  geom_... +
  xlab("Your X-axis Label") +
  ylab("Your Y-axis Label") +
  theme_classic()
```
 
**What this does:**
- Adds descriptive axis labels
- Removes the default grey background
- Makes graphs easier to read
 
---
 
## Questions / Practice
 
### Question 1 — Comparing Graphs
 
Look at two versions of the following graphs:
- Survivorship vs. sex (Titanic dataset)
- Ear length vs. age
 
Which version communicates the data better? Why?
 
---
 
### Question 2 — Countries Dataset
 
**a) Load the data:**
 
```r
countries <- read.csv("DataForLabs/countries.csv")
```
 
**b)** Why do we need `library(ggplot2)` before making graphs?
 
**c) Create a histogram of measles immunization rates and describe the pattern:**
 
```r
ggplot(countries, aes(x = measles_immunization_oneyearolds)) + geom_histogram()
```
 
**d) Create a bar graph of countries by continent:**
 
```r
ggplot(countries, aes(x = continent)) + geom_bar()
```
 
**e) Create a scatterplot of male vs. female life expectancy:**
 
```r
ggplot(countries, aes(x = life_expectancy_at_birth_male,
                      y = life_expectancy_at_birth_female)) +
  geom_point()
```
 
---
 
### Question 3 — Ecological Footprint
 
```r
ggplot(countries, aes(x = ecological_footprint_2000,
                      y = ecological_footprint_2012)) +
  geom_point() +
  geom_abline(intercept = 0, slope = 1)
```
 
Answer the following:
1. Is there a relationship between the 2000 and 2012 footprints?
2. Does a country's footprint in 2000 predict its footprint in 2012?
3. Are ecological footprints generally increasing or decreasing over time?
 
---
 
### Question 4 — Continent vs. Life Expectancy
 
```r
ggplot(countries, aes(x = continent, y = life_expectancy_at_birth_female)) +
  geom_boxplot()
```
 
Describe the patterns you observe across continents.
 
---
 
### Question 5 — Bat Tongue Dataset
 
**a) Load the data and explore it:**
 
```r
bat_tongues <- read.csv("DataForLabs/BatTongues.csv")
summary(bat_tongues)
```
 
**b) Create a scatterplot and describe the relationship:**
 
```r
ggplot(bat_tongues, aes(x = palate_length, y = tongue_length)) +
  geom_point()
```
 
**c) Find and identify the outlier:**
 
```r
library(dplyr)
filter(bat_tongues, tongue_length > 80)
```
 
---
 
### Question 6 — Reflection
 
Pick one graph you created in this lab.
 
- How could you improve it?
- What labels, themes, or other changes would make it clearer?
 
---
 
*STEM Fellowship · Challenge Based Learning · UBC*






























