---
layout: post
title: "Exploratory Data Analysis, Automated!"
date: 2023-11-03 20:52:33 +0000
---

Exploratory data analysis (EDA) is an essential first step in any data science project—think of it as the annual check-up for your data. I have long believed that EDA can be automated, as the tasks are very general. While there are existing R packages for EDA, such as [DataExplorer](https://cran.r-project.org/web/packages/DataExplorer/vignettes/dataexplorer-intro.html), [summarytools](https://cran.r-project.org/web/packages/summarytools/vignettes/introduction.html), [tableone](https://cran.r-project.org/web/packages/tableone/vignettes/introduction.html), and [GGally](https://github.com/ggobi/ggally), I have not found what I was looking for. Leveraging GPT-4, I was able to create an EDA script in just a few hours.

The result is an R Markdown template for EDA, designed to work with any dataset. The concept is straightforward: you provide a dataset containing numerical and categorical variables, and the template automatically generates a detailed [EDA report like this](https://htmlpreview.github.io/?https://github.com/gexijin/inspect/blob/main/inst/example_report.html).

Here's what the template does:

- Starts with a data summary.
- Checks for missing values and outliers.
- Plots the distribution of numerical variables using histograms and QQ plots. When skewness is excessive, it recommends a log transformation.
- Shows the distribution of categorical variables.
- Provides a general overview of the data with a heatmap and a correlation plot.
- Plots the correlation matrix (corrplot).
- Uses scatter plots to examine correlations between numerical variables.
- Uses violin plots and ANOVA to study differences between groups defined by categorical variables.
- Tests whether categorical variables are independent of each other, using Chi-squared tests and bar plots.

To use the R Markdown file, just get a copy from my [GitHub repository](https://github.com/gexijin/inspect/blob/main/inst/eda.Rmd). Replace the demo data file with your own, specify a target variable, and render the report.

If that sounds like too much work, simply upload your data file to [RTutor.ai](https://RTutor.ai) and click the **EDA** tab. A comprehensive report will be generated in 2 minutes. The template was originally written for RTutor.

![]({{ site.baseurl }}/assets/uploads/2023/11/110623_1418_Exploratory1.png)
