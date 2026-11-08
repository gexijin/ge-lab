---
layout: post
title: "Coding with GPT-4: Asking the Right Question"
date: 2023-05-21 15:06:27 +0000
---

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG1.png)

Using [Nicola Rennie](https://twitter.com/nrennie35)'s [ggflowchart](https://github.com/nrennie/ggflowchart) package, I created a flowchart like this one. But the colors were assigned automatically, and I wanted to specify the colors for the three categories. Here is how I did it with GPT-4. I am too lazy to goofy (google) around these days.

My original code:

```r
ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +
  ggplot2::theme(legend.position = "bottom")
```

## Round 1: The initial attempt fails

**Me:** In the Status column I have three categories: 'Error', 'Done', or 'To do'. Can I specify which color to use? I want to use red, green, and white, respectively?

**GPT-4:**

```r
ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +
  scale_color_manual(values=c("Error" = "red", "Done" = "green", "To do" = "white")) +
  ggplot2::theme(legend.position = "bottom")
```

## Round 2: Letting GPT-4 fix it, without luck

**Me:** That didn't work.

**GPT-4:** I apologize if there was any confusion. Let's correct that. Here's how you should modify your ggplot2 command to specify custom colors for your categories. It's important to remember that the variable inside aes() representing color should be a factor.

```r
node_data$Status <- as.factor(node_data$Status)

ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +
  scale_color_manual(values=c("Error" = "red", "Done" = "green", "To do" = "white")) +
  ggplot2::theme(legend.position = "bottom")
```

This didn't solve the issue either.

## Round 3: Is something wrong with my data?

**Me:** Still no luck. Give me an example using the Iris dataset. Color the three species with specified colors.

**GPT-4:**

```r
library(ggplot2)

custom_colors <- c("setosa" = "red", "versicolor" = "green", "virginica" = "blue")

ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point() +
  scale_color_manual(values = custom_colors) +
  theme(legend.position = "bottom")
```

This code works: the data points change color.

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG2.png)

So why doesn't it work on my data? I realized I was trying to change the fill (background) color of the boxes, not the color of points or lines. To test this idea, I tried it on the Iris data first.

## Round 4: Should I specify the fill color instead?

**Me:** Change shape by Species. Make the specified color as fill colors.

**GPT-4:**

```r
library(ggplot2)

custom_colors <- c("setosa" = "red", "versicolor" = "green", "virginica" = "blue")

ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point() +
  scale_color_manual(values = custom_colors) +
  theme(legend.position = "bottom")
```

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG3.png)

Aha! It turns out I should have used the `scale_fill_manual()` function, which I didn't know about. My initial question was not specific enough.

Now all I had to do was take the code from the first round and change `scale_color_manual` to `scale_fill_manual`:

```r
ggflowchart::ggflowchart(graph_data, node_data, fill = Status) +
  scale_fill_manual(values=c("Error" = "red", "Done" = "green", "To do" = "white")) +
  ggplot2::theme(legend.position = "bottom")
```

![]({{ site.baseurl }}/assets/uploads/2023/05/052123_1701_CodingwithG4.png)

This gave me exactly what I wanted! Out of ignorance, I wasn't asking the right question at the very beginning.
