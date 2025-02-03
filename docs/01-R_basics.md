# (PART\*) R Basics {-} 




# R and RStudio

>"R is ‘GNU S’, a freely available language and environment for statistical computing and graphics which provides a wide variety of statistical and graphical techniques: linear and nonlinear modelling, statistical tests, time series analysis, classification, clustering, etc."

This is the description of R on the R website. 

## Install the R language

Download the most recent release of R for your platform from https://cloud.r-project.org/. Install it like any other program. It is important to install R before RStudio.


## Install RStudio

RStudio is an integrated development environment (IDE) for R. Other IDEs do exist, but RStudio is the software of choice by far. Like, by far. Download the desktop version of RStudio from https://www.rstudio.com/products/rstudio/. This is the program in which you will interact with the R language and conduct all your analyses.

# How does R work?

> “To understand computations in R, two slogans are helpful:
Everything that exists is an object.
Everything that happens is a function call." — John Chambers^[[Chambers, 2007](https://books.google.de/books?id=kxxjDAAAQBAJ&pg=PA4&lpg=PA4&dq=%22Everything+that+exists+in+R+is+an+object%22&source=bl&ots=c6AiUD6NXp&sig=NiI4WlvJBolTQ3jSVisPIBcm-fU&hl=en&sa=X&redir_esc=y#v=onepage&q=%22Everything%20that%20exists%20in%20R%20is%20an%20object%22&f=false)]

Ok, cool. So what now? Well, this statement tells us that everything in our R code falls into two categories, either it is an object or it is a function (which will most likely take an object as input and give back a modified object in return).

## Objects 

Please have a look at the [workflow basics](https://r4ds.hadley.nz/workflow-basics#coding-basics) as a first introduction or recapitulation^[If you are already familiar with all of this, it may help you formalize your problems better by getting familiar with the vocabulary the authors of R use.] into coding in R.

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> Done? </button> <div id="button1" class="collapse">  
\
The most important takeaway from this is that you can assign (create) an object in R with the assignment operator `<-`. And while we are at it, the __c__ombine function `c()`^[which I always called vector, and wondered where the c is coming from...] will be one of the most frequently used functions in R. 

```r
# Assign the vector to an object called numbers
numbers <- c(1, 2, 3)
# Execute the following line to print it to the console
numbers
#> [1] 1 2 3
# Some objects (not this one) need to be forced to show in the console 
print(numbers)
#> [1] 1 2 3
```
This ` c(1, 2, 3) -> numbers` works as well, but please do not ever do this.^[[here](https://stat.ethz.ch/R-manual/R-devel/library/base/html/assignOps.html)'s a list of other assignment operators]
</div>

\
What we have created here is called a vector, and more precisely an atomic vector. This means it its elements are all of the same type. You can read more on this in the [Vectors](https://adv-r.hadley.nz/vectors-chap.html) chapter of [Advanced R](https://adv-r.hadley.nz/) if you have some waiting time or if you are unsure about the behavior of your vectors. Examples would be:

```r
mixed_numbers <- c(0, 1, 2, "three")
mixed_numbers_2 <- c(F, TRUE, 2, 3)
# You don't actually need to assign them
c(F, TRUE, 2, "three")
```

If you are unhappy that the type of your data has changed in the previous example, simply change `c()` to `list()`.^[The `typeof()` function comes in handy if you ever need to test if your code does what you think it does.]

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> I am lazy. </button> <div id="button2" class="collapse">  
\

```r
list(0, 1, 2, "three")
list(F, TRUE, 2, 3)
list("these" = F, "are" = TRUE, "names" = 2, "three")
list("and" = F, "they" = TRUE, "work" = 2, "notemptyanymore" = "for both lists and vectors :)")
```
</div>

\
The other data types can be found in the [Vectors](https://adv-r.hadley.nz/vectors-chap.html) chapter as mentioned previously or will be covered in the project eventually. 

## Functions 

Besides the most basic object in R, a vector, we have also covered two functions as well. The `c()` and the `list()` functions which allow us to create atomic vector and list objects. If you want to understand a function, simply write `?c`^[question mark + function name] and R will prompt you to the documentation of the function in the Help pane on the bottom right.^[Or google the function like a normal human being.]

The number of functions exceeds the number of object types by far, therefore we should see how to use functions properly. Each function 1. has a name, 2. is an object itself and 3. can be evoked by `()` brakets following its name. Let's try this:

```r
sum(1, 2, 3)
#> [1] 6
```
Nice! But bad example. Write the function name `sum` again and wait for a list of options to appear. If this does not happen, you can press Tab. Once you see a list, scroll through it with your arrow buttons and choose a function with Tab or Enter. Once your cursor is in between the brackets of the function, press Tab again. Now, you see the arguments of a function. Arguments are the different inputs for a function and declare precisely which input goes where within the function. Our bad example has a special type of argument `...`, the [(dot-dot-dot)](https://adv-r.hadley.nz/functions.html?q=...#fun-dot-dot-dot), that accepts an undefined number of arguments, in this case multiple numbers.

A better example is the `intersect()` function, which takes two sets in form of atomic vectors `x` and `y` and returns the intersection. 

```r
intersect(x = c(1, 2, 3), 
          y = c(2, 3, 4))
#> [1] 2 3
```

The other [Set Operation](https://stat.ethz.ch/R-manual/R-devel/library/base/html/sets.html) functions will be useful at one point for sure. Another resource worth mentioning is the [R-bloggers website](https://www.r-bloggers.com/2024/11/the-complete-guide-to-using-setdiff-in-r-examples-and-best-practices/).

For a formal description of functions, you can read [function fundamentals](https://adv-r.hadley.nz/functions.html?q=...#function-fundamentals). And now let's see where all these functions come from.


# R packages



>"R packages are collections of functions and data sets developed by the community. They increase the power of R by improving existing base R functionalities, or by adding new ones."^[https://www.datacamp.com/community/tutorials/r-packages-guide] 

Basically, R packages are nothing but collections of functions bundled together in a way that makes sense. Like different cookbooks that only contain recipes for a particular kind of food. They can be installed from many different sources which will be explored below. 

## From CRAN

[The Comprehensive R Archive Network](What are R and CRAN?) (CRAN) package repository features 18,000+ R packages. Here's the list of [Available CRAN Packages By Name](https://cran.r-project.org/web/packages/available_packages_by_name.html). Most general purpose packages can be found here, however due to reasons, some packages are only available from other sources. 

As a first example, we will download the [tidyverse](https://www.tidyverse.org/), a collection of R packages for data science. 

>"The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures."

We can install packages from CRAN with the `install.packages()` function like this:

```r
install.packages("tidyverse")
```

Note, that we can also download more than one package at once using a vector (`c()`) containing all package names:

```r
install.packages(c("BiocManager", "devtools"))
```

`BiocManager` as well as `devtools` will be used in the following to download R packages from other sources.


## From Bioconductor

The [Bioconductor](https://bioconductor.org/) is a collection of R packages for bioinformatics purposes. The first packages we will need from the Bioconductor will be downloaded with the `install()` function from the `BiocManager` package: 

```r
BiocManager::install(c("fgsea",
                       "org.Hs.eg.db",
                       "UniProt.ws"))
```



## From GitHub and others sources

Another important source of R packages is GitHub. GitHub is not just the place where most R packages are being developed before they are put to repositories such as CRAN or Bioconductor, many other packages including the `PELSA` package can be installed from it as well. 

Here is an example with the `install_github()` function from the `devtools` package. This package is not required yet. 

```r
devtools::install_github("nicohuttmann/PELSA")
```


# The tidyverse

You may have already installed the [`tidyverse`](https://www.tidyverse.org/) in the previous chapter. It is a [collection](https://www.tidyverse.org/packages/) of many R packages made for data science. I see it as a high level dialect - which allows you to do the same as base R 

>"The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures."

The tidyverse is extensively described in the [R for Data Science (2e)](https://r4ds.hadley.nz) book^[I'm a fan, if you haven't noticed] as recommended in [Learn the tidyverse](https://www.tidyverse.org/learn/) and individual packages are summarized in some [Posit cheatsheets](https://posit.co/resources/cheatsheets/).

# Coding style 

Okay, we nearly made it to our project. Only took us 5+ introductory chapters. Only this one more. I promise.

First of all, I am sorry that I will use the word 'I' in this chapter. I do not like that. However, I believe it is important to understand where certain ideas or nuances come from. Especially if different approaches lead to the same result and especially at the early stages of learning something like programming. 

One decision which you may have already guessed, is that I am a follower of the tidyverse and try to use it instead of the base R solutions wherever possible.^[base R refers to the functions which are available to you in R without installing any additional package. And little surprisingly, it is a package as well. You could check it's functions by writing `base::`and pressing Tab. _I just found all the basic mathematical operators by doing this and scrolling up. I'm learning so much by doing this!_] Still, it is not almighty and sometimes you will need other solutions. For example dividing two data frames through each other would require the tidyverse functions `pivot_longer`, `inner_join`, `mutate` and `pivot_wider`. The elegant base R solution is having the data as matrices and simply using the mathematical operator `/`. 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button3" aria-expanded="false" aria-controls="button3"> base R solution </button> <div id="button3" class="collapse">  
\

```r
m1 <-  matrix(1:9, nrow = 3)

m2 <-  matrix(1:9, nrow = 3) * 2

m2 / m1
```
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button4" aria-expanded="false" aria-controls="button4"> tidyverse solution </button> <div id="button4" class="collapse">  
\

```r
t1 <- tibble(a = 1:3, b = 4:6, c = 7:9)

t2 <- tibble(a = 1:3, b = 4:6, c = 7:9) %>% 
  mutate(across(everything(), \(x) x * 2))

t2 / t1
```

Damn, while writing this example, I found out that what I was trying to show not to work, did somehow work. But let me explain why I don't like the example. 

The structure of an object in R can be found by using the `class()` function. Just try it.


```r
class(m1)

class(m2)

class(m2 / m1)
```

All objects in the base R example are matrices. Let's check the tidyverse example. 


```r
class(t1)

class(t2)

class(t2 / t1)
```

The output of the divide operation is not a `tibble` ("tbl_df") object anymore, it is a `data.frame`. This is not a big problem for now, and can be solved quite easily with the `tibble::as_tibble()` function:

```r
tibble::as_tibble(t2 / t1)
```

__But is better avoided.__

The real tidyverse solution would work the following. 


```r
# First we add a row column to the tibbles, this brings them closer to real data 
t1_r <- t1 %>% 
  mutate(row = c("1", "2", "3"), 
         .before = 1)

t2_r <- t2 %>% 
    mutate(row = c("1", "2", "3"), 
         .before = 1)

t1_long <- pivot_longer(t1_r, 
                        cols = c("a", "b", "c"), 
                        names_to = "column", 
                        values_to = "number")

t2_long <- pivot_longer(t2_r, 
                        cols = -1, 
                        names_to = "column", 
                        values_to = "number")

# We start with combining the data frames by matching both tibbles by the columns "row" and "column" and choosing a suffing for overlapping column names
full_join(t1_long, t2_long, by = c("row", 
                                   "column"), 
          suffix = c("_1", "_2")) %>% 
  # Then we can divide the values of t2 by t1 and save them in a new column 
  mutate(number = number_2 / number_1) %>% 
  # Now we finally pivot back to the wide data format from the beginning
  pivot_wider(id_cols = "row", 
              names_from = "column", 
              values_from = "number")
```

This seems like a very tideous example in comparison, but also bears it's advantages as we will see later. 

Btw, this is how I would've done the above in a code-condensed form. 


```r
# First we put the tibbles in a list 
list("t1" = t1, "t2" = t2) %>% 
  # map allows us to do the same computation for all objects of the list as defined by the function \(x) x...
  map(\(x) x %>% 
        mutate(row = c("1", "2", "3"), 
               .before = 1) %>% 
        pivot_longer(cols = -1, 
                        names_to = "column", 
                        values_to = "number")) %>% 
  # Once both tibbles are ready to be combined, we can access them via the with function (we may talk about this again, I find it very helpful sometimes)
  with(full_join(t1, t2, by = c("row", 
                                   "column"), 
          suffix = c("_1", "_2"))) %>% 
  # Now we continue as above
  mutate(number = number_2 / number_1) %>% 
  # And back to a wide format tibble 
  pivot_wider(id_cols = "row", 
              names_from = "column", 
              values_from = "number")
```

You do not need to understand all of this immediately, but these are some of the most common operations in omics data science. If you understand the `pivot` functions within this week, you're years ahead compared to my journey in data science :)



</div>

## Coding style

![](https://upload.wikimedia.org/wikipedia/en/b/b9/MagrittePipe.jpg)

Well, what is this?! It is not a pipe. But this `%>%` is. Or is it?^[You can read the history to this picture when you are done with a section and really bored: http://adolfoalvarez.cl/blog/2021-09-16-plumbers-chains-and-famous-painters-the-history-of-the-pipe-operator-in-r/]

We previously learned that "Everything that happens is a function call." and in order for the result of the function to 'exist', we need to assign it as an object. Fine. Works. But what happens if we need to do multiple operations on the same object to get our result?

Let's consider the generic example of a vector that contains letters which we would like to count and represent in a barplot. 


```r
letters_freq <- c("A" = 5, "B" = 18, "C" = 20, "D" = 2,
                  "E" = 24, "F" = 13, "G" = 1, "H" = 25,
                  "I" = 21, "J" = 11, "K" = 19, "L" = 6,
                  "M" = 10, "N" = 14, "O" = 16, "P" = 9,
                  "Q" = 23, "R" = 17, "S" = 8, "T" = 26,
                  "U" = 22, "V" = 7, "W" = 15, "X" = 12,
                  "Y" = 3, "Z" = 4)

random_letters <- rep(names(letters_freq), letters_freq)

```

This is the first exercise in this book^[I call it an exercise, because I am not sure if it is well explained and therefore the 'exercise' is to understand what I intend to show you here :)]. You can simply copy the code by marking it or pressing this helpful button in the top right corner of the code chunk and paste it into your R script. Then just run the lines of code and have a look at what they produce. 




```r
random_letters_table <- table(random_letters)

random_letters_table_sorted <- sort(random_letters_table, decreasing = T)

barplot(random_letters_table_sorted)

```



```r
random_letters <- table(random_letters)

random_letters <- sort(random_letters, decreasing = T)

barplot(random_letters)
```

You saw in the examples above that there are different ways to chain the outputs of the different computations into each other to arrive at the barplot. Let's try and use the ` %>%` operator to simplify this process. within each line


```r
random_letters %>%  
  table() %>% 
  sort(decreasing = T) %>% 
  barplot()
```

The chain begins with an object `random_letters` and is then followed by functions in each subsequent line. The output of the preceeding line is always used as the first argument of the following function.

The above is equivalent to: 

```r
barplot(sort(table(random_letters), decreasing = T))
```

The chain begins with 

But I hope it is obvious why the `%>%` is a useful tool, not just for writing less code but also making the code more legible. Btw, did you find the hidden message in the barplot? If not, try and stretch the 'Plots' window or press 'Zoom' in the 'Plots' panel.

The making of this exercise is an even better example of the utility of the `%>%` :)

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button5" aria-expanded="false" aria-controls="button5"> Making of </button> <div id="button5" class="collapse">  
\
And maybe a nice 

```r
sentence_full <- "The quick brown fox jumps over the lazy dog"
#  Wow I just discovered there's a `sentences` object in R

# Generate the frequency of each individual letter
letters_freq <- sentence_full %>% 
  # Remove spaces
  str_remove_all(" ") %>% 
  # Split the string into individual letters 
  str_split("") %>% 
  # Extract vector from list 
  unlist() %>% 
  # Make all letters upper case
  toupper() %>% 
  # Remove dublicated letters 
  unique() %>% 
  # Make new vector with letter as name and decreasing numbers from 26 to 1 as content
  # Do you see how the . marks the position of the argument coming from the previous line?
  setNames(26:1, .) %>% 
  # Reorder the vector so that the solution is not immediately obvious to you guys 
  # Not this is some weird stuff here, do try this at home
  `[`(., order(names(.)))

# Test if it works
random_letters <- rep(names(letters_freq), letters_freq)


# Now prepare the example for the exercise

# This function copies a vector to the console 
.cat_character_named <- function(...) {
  
  n <- paste0(names(...), '" = "', ..., '"')
  
  cat(paste0('c("', paste(n, collapse = ',\n\t"'), ')'))
  
}

.cat_character_named(random_letters)

letters_freq <- c("A" = 5,
                  "B" = 18,
                  "C" = 20,
                  "D" = 2,
                  "E" = 24,
                  "F" = 13,
                  "G" = 1,
                  "H" = 25,
                  "I" = 21,
                  "J" = 11,
                  "K" = 19,
                  "L" = 6,
                  "M" = 10,
                  "N" = 14,
                  "O" = 16,
                  "P" = 9,
                  "Q" = 23,
                  "R" = 17,
                  "S" = 8,
                  "T" = 26,
                  "U" = 22,
                  "V" = 7,
                  "W" = 15,
                  "X" = 12,
                  "Y" = 3,
                  "Z" = 4)

```
</div>

\
For a probably better explanation of pipes or more in-depth explanation, please have a look at the [corresponding chapter](https://r4ds.had.co.nz/pipes.html) in [R for Data Science](https://r4ds.had.co.nz/) or the [chapter](https://r4ds.hadley.nz/workflow-style.html#sec-pipes) in its second edition, [R for Data Science (2e)](https://r4ds.hadley.nz).

Using the `%>%` pipe operator is only one part of the [Style guide](https://r4ds.hadley.nz/workflow-style.html) but will have a big impact on the legibility of your code. I visually prefer the [old version](http://adv-r.had.co.nz/Style.html) and suggest reading one of the two. If you are at the beginning of your coding career, not all recommendations will be immediately obvious, but you will remember them later on. 


## Data organization wihtin R

And for the last part


## Summary




