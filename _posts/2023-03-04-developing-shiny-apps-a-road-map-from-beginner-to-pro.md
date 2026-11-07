---
layout: post
title: "Developing Shiny apps: a road map from beginner to pro"
date: 2023-03-04 19:49:52 +0000
categories: ["Shiny App"]
---

![]({{ site.baseurl }}/assets/uploads/2023/05/050723_1538_DevelopingS1-1.png)

Based on the learning-by-doing strategy, here is how you can learn to develop Shiny apps by working on an example and then enhancing it step by step. The difficulty level increases at every step, like in these video games.

### Step 1. Learn to write clear, organized, readable R code

Always assume that your code will be read and reused by yourself or others in the future. Add comments for readability & maintenance. Follow recommended style guides such as  [Google](https://google.github.io/styleguide/Rguide.html) and [Tidyverse](http://adv-r.had.co.nz/Style.html). See the [iDEP app](https://github.com/gexijin/idepGolem) for some example code written largely by Gavin Doering and Emma Spors.

### Step 2. Develop a simple app with your favorite dataset

1. From RStudio, populate an example app by going to File à New Project à New Directory à Shiny app. You create a folder that holds the shiny app. Store all required data in this folder.
2. Run and then change this app using your data. These [lessons](https://shiny.rstudio.com/tutorial/written-tutorial/lesson1/) are excellent in guiding me. I also use it as a reference regularly. You can read in files and clean the data at the very beginning of the app.R file.
3. Take baby steps. For example, to add a new plot whose color can be changed by a selectInput button, do things in these four steps.

- Add the control widget on the UI and run the app to ensure it appears.
- Write the R code to generate the desired plot with a fixed color (col = "red"). This is best done in a regular R script file (File à New File à R script) so that it can be tested and fixed quickly using data objects already in the environment.
- Add a server function to generate the plot inside Shiny. This is best done by duplicating existing server functions and replacing the core plotting part. Add the plot to the UI. Test so that a plot shows up correctly.
- Put it all together by changing the server function to make colors variable according to user selection by replacing the fixed color with user input, i.e., col = input$select_color.

1. Enhance the app. Make it intuitive to use by OTHER people. Add tabs to organize the app.

### Step 3. Deploy the app to Shinyapps.io

From RStudio, click on the Publish button on the top right of the app. Make sure to upload the necessary data files. Your app should not read files using an absolute path only defined on your laptop (C:/Users/Tom/data.csv).

### Step 4. Publish your code on GitHub

1. Create a GitHub account.
2. Create a repository.
3. Upload your code to GitHub. You can do this on the GitHub website.
4. Edit the readme file to explain the app and link to the deployed URL.
5. Learn to use version control. This is optional, and it will take time to fully realize the benefit of version control. I recommend [GitHub Desktop](https://desktop.github.com/). But you can use [Git from RStudio](https://sites.northwestern.edu/researchcomputing/resources/using-git-and-github-with-r-rstudio/). GitHub helps track all your changes, like Microsoft Word. You can define different branches, each branch can hold different versions. These enable tracking, testing, and collaboration.

### Step 5. Restructure the app with Shiny modules

We divide large Shiny apps into modules so that we can build complex apps using the divide-and-conquer strategy. A Shiny module is a tiny shiny app defined by two functions, server and ui. Different modules can communicate, but they focus on various aspects of the data analysis (e.g., distribution of categorical vs. continuous variables). For more on Shiny modules, see [here](https://shiny.rstudio.com/articles/modules.html) and [here](https://mastering-shiny.org/scaling-modules.html). Run some of the examples before restructuring your app.

Another powerful benefit of Shiny modules is that you can reuse them, even in the same app. For example, in the [iDEP app](https://github.com/gexijin/idepGolem), the [ottoPlots](https://github.com/espors/ottoPlots) module written by former grad student Emma Spors was used over ten times for exporting figures to PDF, and PNG formats.

The price we pay is communication: variables defined in one module are no longer accessible from another. Different modules have their own namespaces. Even in the same module, the input elements should be used in the ui function inside a namespace function, for example, *ns("select_color").*

### Step 6. Turn your shiny app into an R package

The [golem R package](https://engineering-shiny.org/golem.html) provides a toolkit for simplifying the development of large apps as R packages. In addition to the use of Shiny modules to structure the app, we also extract most data analysis steps as functions, which are defined in separate files and called by the server function. Functions are documented following a specified format with the [roxygen2](https://cran.r-project.org/web/packages/roxygen2/vignettes/roxygen2.html) package.

[RTutor](https://github.com/gexijin/RTutor) is a small example of a golem app. It only has one module. You can easily take the skeleton of RTutor and replace the R code with your own and create an R package that can be installed. On the other hand, the [iDEP app](https://github.com/gexijin/idepGolem) is a large app refactored from an [older version](https://github.com/iDEP-SDSU/idep/tree/master/shinyapps/idep96) usingthe golem framework. With 12 modules, it is a complex app. It is still under development.

### Step 7. Debugging, testing, performance

You can add breakpoints anywhere in the Shiny code for debugging using the [browser](https://shiny.rstudio.com/articles/debugging.html)( ) function. You can look at the values of variables and even write scripts based on the environment up to that point. Shiny apps are websites for others to use. Users have no knowledge of how the app is designed. They might interact with the website differently than the developer envisioned or assumed. Developer needs to test the app using a variety of scenarios. Unit tests can be performed on individual functions or modules using the [testthat](https://testthat.r-lib.org/) package. The entire app (system test) can be evaluated using [shinytest2](https://rstudio.github.io/shinytest2/). To see which steps are taking more time to complete, you can trace the sequence of events using the [shinylogs](https://dreamrs.github.io/shinylogs/articles/shinylogs.html) package

Many of these steps will take time to master. You do not need to fully master a step before moving to the next. Steps 5, 6, 7 are more advanced topics that can tackled in the future. The most important thing is keep learning by practicing.

**To learn more:**

- Hadley Wickham, [Mastering Shiny](https://mastering-shiny.org/scaling-modules.html)
- Fay et al., [Engineering Production-Grade Shiny Apps](https://engineering-shiny.org/index.html)
