# CA4---RDBMS-Linear-Regression-Project
Part B

LINK TO GITHUB 

https://github.com/GraceReilly/CA4---RDBMS-Linear-Regression-Project.git


----------------------------------------------------------------------------






---
title: 2022 - MSc - Data Analytics for Immersive Environments - CA4 - RDBMS & Linear Regression Project Database design, SQL, and Linear Regression
output:
  pdf_document: default
  html_document: default
date: "2023-01-02"
---

# **Part B - Linear Regression Analysis**

## Student Name - Grace Reilly / Student ID - D00232395

## Contents :

-   A: Introduction
-   B: Histogram of average monthly hours of gaming and average age
-   C: Confidence Interval
-   D: Sharpio-Wilk Test
-   E: Pearson Correlation Coefficient
-   F: Average Linear Regression of average monthly hours gaming on age
-   G: References

### A: Introduction

-   The two columns chosen to perform linear regression are age and avg_monthly_hrs_gaming as they have a relationship that can be quantified using linear equation. It can be assumed that as age increases, the avg_monthly_hrs gaming may also increase or decrease.

### B: Histogram of average monthly hours of gaming and average age

```{r echo=FALSE, warning=FALSE}
library(readxl)
library(ggplot2)
# read in the data from the Excel file
data <- read_excel("C:/Users/iviic/OneDrive/Desktop/CA1/amalgamated_game_survey_250_2022 (1).xlsx")

# select a random sample of 200 records
set.seed(123)
sample <- data[sample(nrow(data), 200), ]

ggplot(data = sample, aes(x = age, fill = "Age")) +
geom_histogram(bins = 30) +
labs(x = "Age", y = "Frequency", title = "Histogram of age")

ggplot(data = sample, aes(x = avg_monthly_hrs_gaming, fill = "Average monthly hours spent gaming")) +
geom_histogram(bins = 30) +
labs(x = "Average monthly hours spent gaming", y = "Frequency", title = "Histogram of average monthly hours spent gaming")
```

### C: Confidence interval of average monthly hours gaming on age

-   The confidence interval for the coefficient suggests that the relationship between the two variables is not highly significant within this sample.

```{r echo=FALSE, warning=FALSE}
# read in the data from the CSV file
data <- read_excel("C:/Users/iviic/OneDrive/Desktop/CA1/amalgamated_game_survey_250_2022 (1).xlsx")

# select a random sample of 200 records
set.seed(123)
sample <- data[sample(nrow(data), 200), ]

# perform linear regression on age and avg_monthly_hrs_gaming
model <- lm(avg_monthly_hrs_gaming ~ age, data = sample)

# calculate the confidence intervals for age and avg_monthly_hrs_gaming
confint(model, level = 0.95)


```
