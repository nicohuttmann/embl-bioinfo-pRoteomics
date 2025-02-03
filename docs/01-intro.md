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

Here is an example with the `install_github()` function from the `devtools` package. This package is not requi

```r
devtools::install_github("nicohuttmann/PELSA")
```


# The tidyverse

You may have already installed the [tidyverse](https://www.tidyverse.org/) in the previous chapter. It is a collection of many R packages made for data science. I see it as a high level dialect - which allows you to do the same as base R 

>"The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures."




# Coding style 

Okay, we nearly made it to our project. Only took us 5+ introductory chapters. Only this one more. I promise.

First of all, I am sorry that I will use the word 'I' in this chapter. I do not like that. However, I believe it is important to understand where certain ideas or nuances come from. Especially if different approaches lead to the same result and especially at the early stages of learning something like programming. 

One decision which you may have already guessed is that I am a follower of the tidyverse and try to use it instead of the base R solutions wherever possible. Still, it is not almighty and sometimes you will need other solutions. For example dividing two data frames through each other would require the tidyverse functions `pivot_longer`, `inner_join`, `mutate` and `pivot_wider`. The elegant base R solution is having the data frames as matrices, put them in a list and which allows us to use mathematical operators in combinations with the `with` function. 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> tidyverse solution </button> <div id="button1" class="collapse">  

```r
"hi"
```
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> base R solution </button> <div id="button2" class="collapse">  

```r
"yed"
```
</div>

## Coding style

![](https://upload.wikimedia.org/wikipedia/en/b/b9/MagrittePipe.jpg)

Well, what is this?! It is not a pipe. But this `%>%` is. Or is it?^[You can read the history to this picture when you are done with a section and really bored: http://adolfoalvarez.cl/blog/2021-09-16-plumbers-chains-and-famous-painters-the-history-of-the-pipe-operator-in-r/]

We previously learned that "Everything that happens is a function call." and in order for the result of the function to 'exist', we need to assign it as an object. Fine. Works. But what happens if we need to do multiple operations on the same object to get our result?

Let's consider the generic example of a vector that contains letters which we would like to count and represent in a barplot. This is the first exercise in this book^[I call it an exercise, because I am not sure if it is well explained and therefore the 'exercise' is to understand what I intend to show you here :)]. You can simply copy the code by marking it or pressing this helpful button in the top right corner of the code chunk and paste it into your R script. Then just run the lines of code and have a look at what they produce. 


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

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button3" aria-expanded="false" aria-controls="button3"> Making of </button> <div id="button3" class="collapse">  

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
  # Make all letter upper case
  toupper() %>% 
  # Remove dublicated letters 
  unique() %>% 
  # Make new vector with letter as name and decresing numbers from 26 to 1 as content
  setNames(26:1, .) %>% 
  # Reorder the vector so that the solution is not immediately obvious to you guys 
  `[`(., order(names(.)))


random_letters <- rep(names(letters_freq), letters_freq)

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

For a probably better explanation of pipes or more in-depth explanation, please have a look at the [corresponding chapter](https://r4ds.had.co.nz/pipes.html) in [R for Data Science](https://r4ds.had.co.nz/) or the [chapter](https://r4ds.hadley.nz/workflow-style.html#sec-pipes) in its second edition, [R for Data Science (2e)](https://r4ds.hadley.nz).



Using the `%>%` pipe operator is only one part of the [Style guide](https://r4ds.hadley.nz/workflow-style.html) but will have a big impact on the legibility of your code. I visually prefer the [old version](http://adv-r.had.co.nz/Style.html) and suggest reading one of the two. If you are at the beginning of your coding career, not all recommendations will be immediately obvious, but you will remember them later on. 





## Data organization wihtin R

And for the last part


## Summary




# (PART\*) Group work project {-}

# Getting started


# Data import


















# (APPENDIX) 

# Version control with GitHub

>Excuse me, do you have a moment to talk about version control?^[https://peerj.com/preprints/3159v2/]

There is a lot to say about GitHub and why one may use it. An extensive discussion on this topic and basically everything you will learn in this chapter can be found in [Happy Git and GitHub for the useR](https://happygitwithr.com/big-picture.html).

This chapter will introduce the basics on how to collaborate with other people using GitHub, which is probably the reason why you are reading this in the first place. 


## Headstart into Git and GitHub with RStudio

The following post provides a quick introduction on how to set up Git and GitHub and connect your GitHub account with RStudio: https://www.bioinformatics.babraham.ac.uk/training/RStudio_GitHub/Initial_setup.html.

Once this is done, you should be able to connect and download online GitHub repositories and are able to start collaborating on projects immediately.



## Basic GitHub routine


Open your Git terminal in R and start with these lines of code.


Add files:


```bash
git add .
```

Commit changes: 


```bash
git commit -m "Add important changes"
```

Push your commits:


```bash
git push
```
...


## Common problems

The following should provide a summary of common problems encountered when using Git. It also serves as a reminder for myself.

### Too large files


Original post of the answer: https://stackoverflow.com/a/17890278.

1. Download the BFG Repo-Cleaner jar file "bfg-x.xx.x.jar" (e.g. "bfg-1.14.0.jar") from https://rtyley.github.io/bfg-repo-cleaner/.

2. Place the file in the directory of your R project, the same of the .git folder.

3. Open the terminal in this folder (e.g. via RStudio > Git > Shell...)

4. Type in the terminal:


```bash
java -jar bfg.jar --strip-blobs-bigger-than 100M
```

The file name "bfg.jar" must match the name of your jar file and the file size limit can be changed (e.g. 50M for 50 )

5. If you do not encouter an error, type:


```bash
git gc --prune=now --aggressive
```

to clean the dead data.


If you encounter the following error `Warning : no large blobs matching criteria found in packfiles - does the repo need to be packed?`, refer to this post https://stackoverflow.com/q/61769785 and type `git gc` prior to step 4.


### .gitignore does not instantly work

Just do:

```bash
git rm -r --cached .
git add .
git commit -m "Drop files from .gitignore"
```


