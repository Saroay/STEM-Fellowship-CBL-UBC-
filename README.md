# STEM-Fellowship-CBL-UBC
Introduction to Graphing in R (Beginner Lab)

(Bioinformatics Lab Activity ~ 1.5 hours)

Learning Goals

## By the end of this activity, you will:
- Understand basic types of graphs (histogram, bar graph, boxplot, scatterplot)
- Learn how to create simple graphs in R using ggplot2
- Understand when to use different types of graphs
- Improve graphs to make them clearer and easier to understand

** NOTE: All code is given in quotes (except for in the questions segment) ** 
  
## Part 1: Getting Started with R
Step 1: Load ggplot2
Before making graphs, we need to load a package:

"library(ggplot2)"

Why?
R does not automatically include advanced graphing tools. ggplot2 gives us easy and powerful ways to create graphs.

## Part 2: Understanding Data Types (Important!)
Before making graphs, we need to understand types of data:
Numerical data → numbers (e.g., age, height, income)
Categorical data → groups or labels (e.g., gender, continent)

Types of Comparisons: 
Numerical + Numerical → Scatterplot
Categorical + Numerical → Boxplot
Categorical + Categorical → Bar graph
Numerical (single variable) → Histogram (frequency on y-axis)

Choosing the right graph depends on your data!

## Part 3: Introduction to ggplot
All graphs in this lab follow this structure:
" ggplot(data, aes(x=variable)) + geom_... "

data = your dataset
aes() = tells R what variables to use
geom_... = type of graph

## Part 4: Histograms (Numerical Data)
A histogram shows how values are distributed. 

First Load Data
"titanicData <- read.csv("DataForLabs/titanic.csv", stringsAsFactors = TRUE)"

Create Histogram
"ggplot(titanicData, aes(x=age)) + geom_histogram()"

What this shows:
How often different ages appear in the dataset

Why use a histogram?
Helps see patterns (clusters, spread, skewness)
Useful for understanding distributions

## Part 5: Bar Graphs (Categorical Data)
A bar graph shows counts for categories.
"ggplot(titanicData, aes(x=sex)) + geom_bar()"

What this shows:
Number of passengers by sex

## Part 6: Boxplots (Categorical + Numerical)
A boxplot compares a numerical variable across groups.
"ggplot(titanicData, aes(x=sex, y=age)) + geom_boxplot()"

What this shows:
Age distribution for each sex

Key parts:
Middle line = median
Box = middle 50% of data
Lines = spread of data

## Part 7: Scatterplots (Numerical vs Numerical)
A scatterplot shows relationships between two variables.

Load Data
"guppyFatherSonData <- read.csv("DataForLabs/chap02e3bGuppyFatherSonAttractiveness.csv")"

Create Scatterplot
"ggplot(guppyFatherSonData, aes(x=fatherOrnamentation, y=sonAttractiveness)) +
geom_point()"
  
What this shows:
Relationship between two numerical variables

## Part 8: Improving Your Graphs
You can make graphs clearer by adding:
"+ xlab("X-axis label") +
  ylab("Y-axis label") +
  theme_classic()"
  
This:
Adds better labels
Removes grey background
Makes graphs easier to read

------------------------------------------------------------------------------------------------------------------------------

### Questions / Practice

## 1. Comparing Graphs
  Look at two versions of graphs:
  Survivorship vs sex (Titanic)
  Ear length vs age
  Which version communicates better? Why?

## 2. Countries Dataset
  a. Load data
  countries <- read.csv("DataForLabs/countries.csv")
  
  b. Why do we need library(ggplot2)?
  
  c. Histogram
  ggplot(countries, aes(x=measles_immunization_oneyearolds)) + geom_histogram()
  
  Describe the pattern
  
  d. Bar Graph
  ggplot(countries, aes(x=continent)) + geom_bar()
  
  e. Scatterplot
  ggplot(countries, aes(x=life_expectancy_at_birth_male,
                        y=life_expectancy_at_birth_female)) + geom_point()

## 3. Ecological Footprint
  ggplot(countries, aes(x=ecological_footprint_2000,
                        y=ecological_footprint_2012)) + geom_point() +
                        geom_abline(intercept=0, slope=1)

  Questions:
  Is there a relationship?
  Does 2000 predict 2012?
  Are values increasing or decreasing?

## 4. Continent vs Life Expectancy
  ggplot(countries, aes(x=continent, y=life_expectancy_at_birth_female)) + geom_boxplot()
  
  Describe patterns

## 5. Bat Tongue Dataset
  a. Load data
  bat_tongues <- read.csv("DataForLabs/BatTongues.csv")
  summary(bat_tongues)
  
  b. Scatterplot
  ggplot(bat_tongues, aes(x=palate_length, y=tongue_length)) +
    geom_point()
  Describe relationship

  c. Find outlier
  library(dplyr)
  filter(bat_tongues, tongue_length > 80)
  
## 6. Reflection Question
  Pick one graph you made:
  How could you improve it?






























