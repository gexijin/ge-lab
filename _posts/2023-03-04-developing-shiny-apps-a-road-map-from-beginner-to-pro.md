---
layout: post
title: "Developing Shiny Apps: A Road Map from Beginner to Pro"
date: 2023-03-04 19:49:52 +0000
categories: ["Shiny App"]
---

![]({{ site.baseurl }}/assets/uploads/2023/05/050723_1538_DevelopingS1-1.png)

Following a learning-by-doing strategy, here is how you can learn to develop Shiny apps: start with an example and enhance it step by step. As in a video game, the difficulty increases at every level.

## Step 1. Learn to write clear, organized, readable R code

Always assume that your code will be read and reused, by yourself or others, in the future. Add comments for readability and maintenance. Follow a recommended style guide, such as [Google's](https://google.github.io/styleguide/Rguide.html) or the [tidyverse](https://style.tidyverse.org/) style guide. See the [iDEP app](https://github.com/gexijin/idepGolem) for example code written largely by Gavin Doering and Emma Spors.

## Step 2. Develop a simple app with your favorite dataset

1. In RStudio, create an example app by going to **File → New Project → New Directory → Shiny Application**. This creates a folder that holds the Shiny app. Store all required data in this folder.
2. Run the app, then modify it to use your data. These [lessons](https://shiny.posit.co/r/getstarted/shiny-basics/lesson1/) were an excellent guide for me, and I still use them as a reference regularly. You can read in files and clean the data at the very beginning of the `app.R` file.
3. Take baby steps. For example, to add a new plot whose color can be changed with a `selectInput()` widget, work in these four steps:
   1. Add the control widget to the UI and run the app to make sure it appears.
   2. Write the R code to generate the desired plot with a fixed color (`col = "red"`). This is best done in a regular R script (**File → New File → R Script**) so that it can be tested and fixed quickly using data objects already in the environment.
   3. Add a server function to generate the plot inside Shiny. This is easiest by duplicating an existing server function and replacing the core plotting code. Add the plot to the UI, and test that it shows up correctly.
   4. Put it all together by replacing the fixed color with the user's input, i.e., `col = input$select_color`.
4. Enhance the app. Make it intuitive for OTHER people to use. Add tabs to organize the app.

## Step 3. Deploy the app to shinyapps.io

In RStudio, click the **Publish** button at the top right of the app. Make sure to upload the necessary data files. Your app should not read files using an absolute path that exists only on your laptop (e.g., `C:/Users/Tom/data.csv`).

## Step 4. Publish your code on GitHub

1. Create a GitHub account.
2. Create a repository.
3. Upload your code to GitHub. You can do this on the GitHub website.
4. Edit the README file to explain the app and link to the deployed URL.
5. Learn to use version control. This is optional, and it takes time to fully appreciate its benefits. I recommend [GitHub Desktop](https://desktop.github.com/), but you can also [use Git from RStudio](https://rcdsdocs.it.northwestern.edu/tutorials/r/git-with-r.html). Like Track Changes in Microsoft Word, Git tracks all your changes. You can also create branches, each holding a different version of the code. Together, these enable tracking, testing, and collaboration.

## Step 5. Restructure the app with Shiny modules

We divide large Shiny apps into modules so that we can build complex apps with a divide-and-conquer strategy. A Shiny module is a tiny Shiny app defined by two functions, a UI function and a server function. Modules can communicate with each other, but each focuses on a different aspect of the analysis (e.g., the distribution of categorical vs. continuous variables). For more on Shiny modules, see [here](https://shiny.posit.co/r/articles/improve/modules/) and [here](https://mastering-shiny.org/scaling-modules.html). Run some of the examples before restructuring your app.

Another powerful benefit of Shiny modules is that you can reuse them, even within the same app. For example, in the [iDEP app](https://github.com/gexijin/idepGolem), the [ottoPlots](https://github.com/espors/ottoPlots) module, written by former grad student Emma Spors, is used more than ten times to export figures in PDF and PNG formats.

The price we pay is communication: variables defined in one module are not accessible from another, because each module has its own namespace. Even within a module, input IDs in the UI function must be wrapped in the namespace function, for example, `ns("select_color")`.

## Step 6. Turn your Shiny app into an R package

The [golem](https://engineering-shiny.org/golem.html) R package provides a toolkit that simplifies developing large apps as R packages. Besides using Shiny modules to structure the app, we also extract most data analysis steps into functions, which are defined in separate files and called by the server function. Functions are documented in a standard format using the [roxygen2](https://cran.r-project.org/web/packages/roxygen2/vignettes/roxygen2.html) package.

[RTutor](https://github.com/gexijin/RTutor) is a small example of a golem app with only one module. You can easily take the skeleton of RTutor, replace the R code with your own, and create an installable R package. On the other hand, the [iDEP app](https://github.com/gexijin/idepGolem) is a large app refactored from an [older version](https://github.com/iDEP-SDSU/idep/tree/master/shinyapps/idep96) using the golem framework. With 12 modules, it is a complex app, and it is still under development.

## Step 7. Debugging, testing, and performance

For debugging, you can add a breakpoint anywhere in your Shiny code with the [`browser()`](https://shiny.posit.co/r/articles/improve/debugging/) function. You can then inspect variables and even run code in the environment as it exists at that point.

Shiny apps are websites for others to use. Users know nothing about how the app is designed, and they may interact with it differently than the developer envisioned. Developers need to test the app under a variety of scenarios. Unit tests of individual functions or modules can be written with the [testthat](https://testthat.r-lib.org/) package. The entire app (system test) can be tested with [shinytest2](https://rstudio.github.io/shinytest2/). To see which steps take more time, you can trace the sequence of events with the [shinylogs](https://dreamrs.github.io/shinylogs/articles/shinylogs.html) package.

Many of these steps take time to master. You do not need to fully master one step before moving to the next. Steps 5, 6, and 7 are advanced topics that can be tackled later. The most important thing is to keep learning by practicing.

## To learn more

- Hadley Wickham, [Mastering Shiny](https://mastering-shiny.org/)
- Colin Fay et al., [Engineering Production-Grade Shiny Apps](https://engineering-shiny.org/index.html)
