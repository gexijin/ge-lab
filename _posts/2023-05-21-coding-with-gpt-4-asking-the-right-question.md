---
layout: post
title: "Coding with GPT-4: asking the right question"
date: 2023-05-21 15:06:27 +0000
---

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG1.png)

Using [Nicola Rennie](https://twitter.com/nrennie35)'s [ggflowchart](https://github.com/cran/ggflowchart) package, I created a flowchart like this one. But the colors are assigned randomly. I wanted to specify the colors for the three categories. Here is how I did it with GPT-4. I am too lazy to goofy (google) around these days.

My original code:

ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +

ggplot2::theme(legend.position = "bottom")

# Round 1: Initial attempt failed.

Me: In the Status column I have three categories: 'Error', 'Done', or 'To do'. Can I specify which color to use? I want to use red, green, and white, respectively?

GPT-4:

ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +

scale_color_manual(values=c("Error" = "red", "Done" = "green", "To do" = "white")) +

ggplot2::theme(legend.position = "bottom")

# Round 2: Trying to let GPT-4 fix it without luck.

Me: That didn't work.

GPT-4: I apologize if there was any confusion. Let's correct that. Here's how you should modify your ggplot2 command to specify custom colors for your categories. It's important to remember that the variable inside aes() representing color should be a factor.

node_data$Status <- as.factor(node_data$Status)

ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +

scale_color_manual(values=c("Error" = "red", "Done" = "green", "To do" = "white")) +

ggplot2::theme(legend.position = "bottom")

This did not solve the issue either.

# Round 3: Maybe there is something wrong with my data?

Me: Still no luck. Give me an example using the Iris dataset. Color the three species with specified colors.

GPT-4:

library(ggplot2)

custom_colors <- c("setosa" = "red", "versicolor" = "green", "virginica" = "blue")

ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +

geom_point() +

scale_color_manual(values = custom_colors) +

theme(legend.position = "bottom")

This code works. The colors are changed for the data points.

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG2.png)

But why it does not work on my data? I realized that I was trying to change the background color, instead of the color of data points. To test this idea, I tried on the Iris data first.

# Round 3: Maybe I should specify the color for the background?

Me: Change shape by Species. Make the specified color as fill colors.

GPT-4:

library(ggplot2)

custom_colors <- c("setosa" = "red", "versicolor" = "green", "virginica" = "blue")

ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +

geom_point() +

scale_color_manual(values = custom_colors) +

theme(legend.position = "bottom")

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG3.png)

Aha! It turns out that I should have used the scale_fill_manual() functions! I didn't know that function. My initial question was not specific enough.

Now all I have to do is to take the code I got in the first round, and change the scale_color_manual to scale_fill_manual.

ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +

scale_fill_manual(values=c("Error" = "red", "Done" = "green", "To do" = "white")) +

ggplot2::theme(legend.position = "bottom")

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG4.png)

This gives me exactly what I wanted! I was not asking the right question at the very beginning due to my ignorance.
