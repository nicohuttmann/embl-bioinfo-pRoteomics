--- 
title: "Data Analysis in R"
author: "Nico Hüttmann"
date: "2025-02-05"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
# url: your book url like https://bookdown.org/yihui/bookdown
# cover-image: path to the social sharing image like images/cover.jpg
description: |
  This is a minimal example of using the bookdown package to write a book.
  The HTML output format for this example is bookdown::bs4_book,
  set in the _output.yml file.
biblio-style: apalike
csl: chicago-fullnote-bibliography.csl
---



# Preface {-}

Hi friends, and welcome to __Introduction to Data Analysis and Visualization in R__. This document contains all explanations and other material for our group project and was produced in RStudio using an R Markdown document which was then 'knitted' into an html file. We'll maybe get there later.^[I am sitting on a train to Munich right now, because I overcommited to a birthday party without knowing where it happens - similar to hosting this group work, but this time coffee was involved. I just recorded the first three videos for this tutorial. You don't need to watch these videos. They are meant to go back to, if you are unsure how to navigate RStudio. It is simple to transfer code, but which buttons to click is a bit more tedious. Feel free to skip through them.]

This book will live in a [Github repository](https://github.com/nicohuttmann/embl-bioinfo-pRoteomics) and will be updated during the course. In the end, you can download the final project alongside additional material like the PowerPoint presentation that will guide us through the sections, other code, the raw data and maybe other stuff. Everything you see during the course will be available to you afterwards.


## Group work structure {-}

You can go through our project individually or in groups. In any case, I do recommend putting the code down in an R script by yourself no matter how. For each step, the problem we are facing will be will be described alongside the final goal. Then, you can either figure out the code entirely on your own, use a hint, or copy the complete code snippet into your document and then run it. The latter option comes close to how many problems in coding are being solved - define the problem, google it, find the answer on StackOverflow and copy it into your script. Yay, you're becoming a data scientist!

The first chapters of this document under __R Basics__ (on the left) will provide a short introduction to coding in R. Parts of it reference the book [R for Data Science (2e)](https://r4ds.hadley.nz). It is a great resource for everyone from beginner to expert. I recommend it no matter what, but if you are relatively new to R in this course, go through it over these days and use the opportunity to discuss concepts from the book in the group setting. The first 2.5 h session on Tuesday should suffice to get everyone on the same page and ready to start exploring some real data in the __Group Work Project__.

::: {.rmdnote}

The game plan for now is:

__Tuesday__\
12:30 - 15:00 R Basics\
15:30 - 17:00 Getting started with the project

__Wednesday__\
16:30 - 17:30 Pick up the project and see if everything still works^[why is there only one hour on Wednesday?]

__Thursdays__\
9:00 - 12:00 Finish data analysis\
13:00 - 16:00 Try out data visualizations and reporting 

__Friday__\
9:00 - 11:30 Prepare the presentation and breakfast

:::


## Motivation {-}

Breakfast on Friday, isn't this motivation enough? Well, no. We're about to spend 13.5 h on this project together while our precious research is waiting for us. 

For the one's of you who are required to use R for your project, I believe there is already plenty of motivation. This course will give you the opportunity to see some actual R code^[I actually wrote most of the code for a package that will be published, and simply used this course to formalize some parts of it.], not just some random examples. You may even use this code once if you are remotely interested in anything regarding protein-protein, protein-nucleic acid, protein-metabolite, or protein-drug interactions on a proteome-wide scale. 

For the one's who do not need R in their projects yet, you could see it as a very fast automation for all your excel tasks. Or GraphPad Prism. Or maybe you want to make a simple website. Or you wanna put it on your CV.^[Thanks Avalon for sharing your motivation for the Python course.]




<!-- ## Blocks -->

<!-- ## Equations -->

<!-- Here is an equation. -->

<!-- \begin{equation}  -->
<!--   f\left(k\right) = \binom{n}{k} p^k\left(1-p\right)^{n-k} -->
<!--   (\#eq:binom) -->
<!-- \end{equation}  -->

<!-- You may refer to using `\@ref(eq:binom)`, like see Equation \@ref(eq:binom). -->


<!-- ## Theorems and proofs -->

<!-- Labeled theorems can be referenced in text using `\@ref(thm:tri)`, for example, check out this smart theorem \@ref(thm:tri). -->

<!-- ::: {.theorem #tri} -->
<!-- For a right triangle, if $c$ denotes the *length* of the hypotenuse -->
<!-- and $a$ and $b$ denote the lengths of the **other** two sides, we have -->
<!-- $$a^2 + b^2 = c^2$$ -->
<!-- ::: -->

<!-- Read more here <https://bookdown.org/yihui/bookdown/markdown-extensions-by-bookdown.html>. -->

<!-- ## Callout blocks -->


<!-- The `bs4_book` theme also includes special callout blocks, like this `.rmdnote`. -->

<!-- ::: {.rmdnote} -->
<!-- You can use **markdown** inside a block. -->

<!-- ```{r collapse=TRUE} -->
<!-- head(beaver1, n = 5) -->
<!-- ``` -->

<!-- ::: -->

<!-- It is up to the user to define the appearance of these blocks for LaTeX output.  -->

<!-- You may also use: `.rmdcaution`, `.rmdimportant`, `.rmdtip`, or `.rmdwarning` as the block name. -->


<!-- The R Markdown Cookbook provides more help on how to use custom blocks to design your own callouts: https://bookdown.org/yihui/rmarkdown-cookbook/custom-blocks.html -->






<!-- This is an introduction to R -->

<!-- ```{r } -->
<!-- 1 + 4 -->
<!-- ``` -->

<!-- ```{r} -->
<!-- b <- 5 -->
<!-- ``` -->

<!-- ```{r} -->
<!-- sqrt(4) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- ?round -->

<!-- round(2.576, digits = 2) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- library(tidyverse) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- mice_pheno <- read_csv(file= url("https://raw.githubusercontent.com/genomicsclass/dagdata/master/inst/extdata/mice_pheno.csv")) -->

<!-- mice_pheno$Bodyweight <- as.numeric(mice_pheno$Bodyweight) -->
<!-- ``` -->


<!-- ```{r} -->
<!-- head(mice_pheno) -->

<!-- dim(mice_pheno) -->

<!-- str(mice_pheno) -->
<!-- ``` -->


<!-- ```{r} -->
<!-- mice_pheno[1:2, 3] -->
<!-- ``` -->


<!-- ```{r} -->
<!-- print(names(PlantGrowth)) -->
<!-- PlantGrowth$weight -->

<!-- PlantGrowth[, "weight"] -->
<!-- ``` -->


<!-- ```{r} -->
<!-- table(mice_pheno$Sex) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- mice_female <- mice_pheno %>%  -->
<!--   filter() -->
<!-- ``` -->



<!-- ```{r} -->
<!-- mice_pheno %>%  -->
<!--   ggplot(aes(x = Diet, y = Bodyweight, fill = Sex)) +  -->
<!--   geom_boxplot() -->
<!--   ggforce::geom_sina() -->
<!-- ``` -->


<!-- kjdslkfjdsj -->
<!-- ```{r} -->
<!-- mice_pheno %>%  -->
<!--   mutate(rep = row_number(), .by = c("Sex", "Diet")) %>%  -->
<!--   pivot_wider(id_cols = c("Sex", "rep"),  -->
<!--               names_from = "Diet",  -->
<!--               values_from = "Bodyweight") -->
<!-- ``` -->

::: {.rmdnote}



:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> Hint </button> <div id="button1" class="collapse">  
\
 
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> Code </button> <div id="button2" class="collapse">  
\



We can do the same in a condensed way.

</div>

