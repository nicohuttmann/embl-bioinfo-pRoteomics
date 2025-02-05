# (PART\*) Group Work Project {-}




# Our project

We will work with mass spectrometry (MS) data obtained from a new proteomics method called PELSA ([A peptide-centric local stability assay enables proteome-scale identification of the protein targets and binding regions of diverse ligands](https://www.nature.com/articles/s41592-024-02553-7)). The PELSA method combines a short tryptic digestion of the proteins of interest with liquid chromatography-tandem MS (LC-MS/MS) analysis. Doing this under differential conditions like a drug treatment of the cells or a specific ligand like metabolites or nucleic acids is called limited proteolysis and identifies which sides of the proteins are shielded from digestion by Trypsin through stabilization of the protein-ligand complex (see __Fig.1a__). 

![](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41592-024-02553-7/MediaObjects/41592_2024_2553_Fig1_HTML.png?as=webp){width=100%}

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> Fig. 1 caption </button> <div id="button1" class="collapse">  
\
a, Workflow of PELSA. E/S ratio (wt/wt). b, Volcano plot visualization of all peptides from a PELSA analysis of BT474 lysates exposed to 100 nM lapatinib. c, Volcano plot as in b but on the protein level. d, Local stability profiles to reveal ligand-binding regions. The upper and lower boundaries of the gray-shaded area represent log2FCs of 0.3 and −0.3, respectively. The x axis represents the protein sequence from the N-terminal to the C-terminal. e, Local affinity profiles to reveal the local binding affinity of a ligand. Heatmap representation of log2 peptide fold changes of ERBB2 with increasing lapatinib concentrations (0, 0.1, 1, 10 and 100 μM). f, Complex structure of mTOR, rapamycin and FKBP1A (PDB 1FAP). g, Volcano plot visualizations of all proteins from a PELSA analysis or a published LiP–MS analysis9 of HeLa lysates exposed to 2 μM rapamycin. h, Local stability profiles of mTOR for 2 μM rapamycin treatment. b, c and g, P values, a two-sided empirical Bayes t-test (four lysate replicates), no adjustment. In all local stability plots, for peptides with |log2FC| > 0.3, only those that passed the significance cutoff (−log10P > 2, two-sided empirical Bayes t-test) were retained to ensure the reliable differences in peptide abundance. Schematics in a created using BioRender.com.
</div>

\
LC-MS/MS then measures the abundance of individual peptides which we can use to quantitatively compare different conditions represented by a volcano plot as in __Fig. 2a__.

![](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41592-024-02553-7/MediaObjects/41592_2024_2553_Fig2_HTML.png?as=webp){width=100%}
<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> Fig. 2 caption </button> <div id="button2" class="collapse">  
\
a, Volcano plot visualization of all proteins from PELSA analyses of K562 (left) and HeLa (right) lysates exposed to 20 μM staurosporine (four lysate replicates); P values, two-sided empirical Bayes t-test without adjustment. The lower boundary of the red shadow denotes the threshold of −log10P, above which over 80% of the stabilized proteins (log2FC < 0) are protein kinases; this threshold corresponds to −log10P > 3.09 in the PELSA K562 dataset and −log10P > 3.77 in the PELSA HeLa dataset. b, TPR evaluation for the selected assays in staurosporine target identification. The labeled points represent the numbers of identified candidate targets and kinase targets in each assay (TPR up to 80%). LiP-Quant is also labeled at the kinase target number of 20 (TPR = 40%). The gray line (slope 1) and black dashed line (slope 0.8) represent 100 and 80% of the candidate targets are kinase targets, respectively. c, Comparison of protein sequence coverage between LiP-Quant HeLa and PELSA HeLa analyses for the whole quantified proteome (n = 5,601 versus n = 6,840 proteins) and identified kinase targets (n = 24 versus n = 108 kinase targets). d, Fold changes of kinase targets (n = 17) identified by both LiP-Quant (TPR cutoff of 40%) and PELSA (HeLa). c,d, P values, two-sided Wilcoxon rank sum test, no adjustment; box plots show the median (line, value labeled), upper and lower quartiles (box) ±1.5× interquartile range (whiskers); outliers are not shown. e, Fold changes of the kinases quantified in PELSA (K562), iTSA and mTSA datasets. f, Melting temperatures of identified kinase targets and all quantified kinases in two PELSA datasets and the TPP dataset. Some PELSA kinase targets lack TPP-reported melting temperature values. g, Density plots showing −log10P distributions of peptides with tryptic cleavage sites located within or outside the kinase domains (KD) in HeLa and K562 PELSA analyses. The dashed lines indicate −log10P cutoffs defined in a. The doughnut charts show the locations of the kinase peptides that passed −log10P cutoffs. P values are determined as in a. b–f, Kinase targets refer to protein kinases that are identified as staurosporine-binding proteins; quantified kinases refer to all protein kinases in the dataset including protein kinases that are not identified as staurosporine-binding proteins. LiP-Quant, TPP, iTSA and mTSA datasets were retrieved from the literature4,9,17,19; LiP-Quant dataset was acquired from HeLa cell lysates, while TPP, iTSA and mTSA datasets were obtained from K562 cell lysates.
</div>

\

::: {.rmdnote}

Nowadays, all proteomics publications are accompanied by their raw MS data. Try and find the data in this publication for __Fig. 2a__. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button3" aria-expanded="false" aria-controls="button3"> Solution </button> <div id="button3" class="collapse">  
\
The data can be found following the path below:

[Data availability ](https://www.nature.com/articles/s41592-024-02553-7#data-availability)

[PXD034606](https://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD034606)

[PRIDE project URI](https://ftp.pride.ebi.ac.uk/pride/data/archive/2024/11/PXD034606/)

[PELSA_staurosporine_K562_peptides.csv](https://ftp.pride.ebi.ac.uk/pride/data/archive/2024/11/PXD034606/PELSA_staurosporine_K562_peptides.csv)

</div>

\
Great, this data already looks quite clean. That's why we will work with 'rawer' data in this course.

# Working with data 

Finally, it's happening. We are beginning to work with real data and you can apply all your new knowledge right away. 

## Prepare your project 

Let's start with opening a fresh R project, making a nice folder structure and opening our first __script__. Which kind of script is up to you, both __R__ and __R Markdown__ work equally well, try and find your preference here. 

::: {.rmdnote}

Start your project as described above and save your first script under a name like 'R_group_project' in the Scripts folder. Choose a name you like.

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button4" aria-expanded="false" aria-controls="button4"> Hint </button> <div id="button4" class="collapse">  
\
You can choose what kind of script you want to have by clicking File -> New File -> R Script/R Markdown.../etc.

To save it, press the blue button on top of the script that says Save current document.

</div>

\
Having our first script ready to code, let's make it nicer. I would suggest to briefly describe what the script contains and start loading the first packages.


```r
# 
# R Group Project
# Analysis of LC-MS/MS PELSA data to identify kinases 
# 

# Load libraries
library(tidyverse)

```

Leave an empty lines on top, it will look more professional. You can then also use the `#` or multiple `##`s in R scripts as comments^[text which is not evaluated as code] or as headings in your R Markdown script. 

## Import your data

By now, you should have a link to the datasets in Slack. If not, please complain. There should be two files called report.tsv and report.parquet. Both are output files from the [DIA-NN](https://github.com/vdemichev/DiaNN) software, a tool that analyzes mass spectrometry data and outputs a table of all identified ions.^[Each ion, also called precursor, represents a peptide and its charge state. Each peptide can have multiple cahrge states and was originally derived from a protein by proteolytic cleavage. All this data stems from multiple samples and replicates which are combined in one table.]

::: {.rmdnote}

Download both files and place them in your R project. Then, try and figure out which functions you need to read both files and store them as objects `data_raw`. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button5" aria-expanded="false" aria-controls="button5"> Hint </button> <div id="button5" class="collapse">  
\
Google :)

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button6" aria-expanded="false" aria-controls="button6"> Another hint </button> <div id="button6" class="collapse">  
\
Google 'import R tsv', or 'import R parquet'.

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button7" aria-expanded="false" aria-controls="button7"> Code </button> <div id="button7" class="collapse">  
\
![](https://raw.githubusercontent.com/tidyverse/vroom/main/img/taylor.gif)

This wasn't me, I swear. It was [them](https://vroom.r-lib.org/). In all seriousness, there are many ways to import your data from [base R](https://r4ds.had.co.nz/data-import.html#compared-to-base-r) solutions, to [canonical tidyverse functions](https://r4ds.hadley.nz/data-import.html), that cover different data types to this one, `vroom`. It made my life much, much easier as it automatically understands the file format. 


```r
# Simply this
data_raw <- vroom::vroom("Data/report.tsv")
```

All other functions to read files begin with `read.` or `read_`. Type them in and press Tab.

Another file format I would like to introduce you to is .parquet, from [Apache Arrow](https://arrow.apache.org/) with the accompanying [Arrow R Package](https://arrow.apache.org/docs/r/). This one is not compatible with `vroom` and needs its own function. 


```r
data_raw <- arrow::read_parquet("Data/report.parquet")
```

The same data is a tenth of the size and therefore reads and writes much faster. It is also more convenient as .csv files due to the clear format of the columns. I'm only afraid it doesn't work with Excel. 

</div>


<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button8" aria-expanded="false" aria-controls="button8"> Additional info </button> <div id="button8" class="collapse">  
\
Both functions also work with URLs. Try it out:^[I am not sure how they behave with OwnCloud.]

```r
data_raw <- vroom::vroom("https://www.owncloud.de/bioinfo/R/dataset.tsv")
```

</div>

\
We will continue with the data from the .parquet file, so you can delete the other object. 


## Understand your data 

Okay, we got our data in R. For now, this is already better than Excel. Try and open the .tsv file in Excel. But we need to view it. How do we do this again?

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button9" aria-expanded="false" aria-controls="button9"> View solution </button> <div id="button9" class="collapse">  
\
Same as for the lists, either click on the object in your Global Environment in the top rigth or type in:

```r
View(data_raw, title = "wow, we can add a title")
```
</div>

\
Great, we have a first impression of our data by scrolling through its columns. Since understanding data you did not generate yourself is hard, we can discuss this more together. If you want to give it a try, here are some [DIA-NN basics](https://github.com/vdemichev/DiaNN?tab=readme-ov-file#basics-of-dia-data-analysis) and more importantly the [Main output reference](https://github.com/vdemichev/DiaNN?tab=readme-ov-file#main-output-reference). This explains all column names, have a look at it. 

Once we have an idea what we are looking at, let's see if R provides us with some more summary functions. 

::: {.rmdnote}

Which summary functions did we use in the Intro to R on Monday?

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button10" aria-expanded="false" aria-controls="button10"> Hint </button> <div id="button10" class="collapse">  
\
Google gave me this nice resource https://www.r-bloggers.com/2018/11/explore-your-dataset-in-r/.
</div>


<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button11" aria-expanded="false" aria-controls="button11"> Code </button> <div id="button11" class="collapse">  
\
Here are a couple of examples to get an overview of the structure of an R data object. 

```r
# Column names
names(data_raw)
# or 
colnames(data_raw)
```


```r
# Print the top of the data
head(data_raw)
```


```r
# Object structure
str(data_raw)
dim(data_raw)
```


```r
# This my take some time with big data but gives you some statistics
summary(data_raw)
```
</div>

\
Not all of these are necessary, I simply `View()` the data before I start to look at it with more specific questions. 

### Data format 

Having a broad idea of our data, we can start and look for the things we are interested in. Most scientific data follows the structure below.

![](https://r4ds.hadley.nz/images/tidy-1.png){width=100%}

There are variables, in our case precursors (measured peptide ions). Each variable was measured in an observations, our samples. And for each pair, there are values for the different data types. This is called the wide data format. You can read more about this in the [Tidy data](https://r4ds.hadley.nz/data-tidy.html#sec-tidy-data) section. Check if this applies to our data! 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button12" aria-expanded="false" aria-controls="button12"> base R solution </button> <div id="button12" class="collapse">  
\
The column `Runs` contains sample names which are the observations of the example above. In addition, we have a column `Precursor.Id`, which are our variables. This means we are not working with data in the wide format, but in the long format. 

The `tidyr` functions `tidyr::pivot_wider()` and `tidyr::pivot_longer()` were mentioned before and will allow as to reshape our data from long to wide and back.
</div>

### Data types

But before we start to do reshape our data, we need to identify and extract the relevant data columns. 

::: {.rmdnote}

Output the data types per each column by combining the two functions `lapply` and `typeof`.

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button13" aria-expanded="false" aria-controls="button13"> Hint </button> <div id="button13" class="collapse">  
\
`?lapply` and `?typeof` will help you understand the individual functions. `lapply` is a useful function when applying the same operation to all elements of a list or vector. In our case, the `data_raw` is a tibble/data frame that can be seen as a list of columns. Therefore, the specified function will be applied to each column. 
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button14" aria-expanded="false" aria-controls="button14"> Code </button> <div id="button14" class="collapse">  
\

```r
# The function FUN will be applied to each column of X
# Notice that we did not add `()` brackets after `typeof`
lapply(X = data_raw, FUN = typeof)
```
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button15" aria-expanded="false" aria-controls="button15"> Tidyverse code </button> <div id="button15" class="collapse">  
\
The `purrr::map` function family replaces base R's `apply` functions and are recommended. 

```r
# map works the same as lapply
map(data_raw, typeof)
# Or 
data_raw %>% 
  map(typeof)
```

[These functions](https://purrr.tidyverse.org/reference/map.html) are very useful once you start working with more than one dataset of data frame at once. 
</div>

\
We can use this opportunity to include some discussions about how to [Control flow](https://adv-r.hadley.nz/control-flow.html) of your code. 

::: {.rmdnote}

Reframe the problem above in a [Loop](https://adv-r.hadley.nz/control-flow.html#loops). 

:::


Now we have an idea which columns in our data contain `character` data, mainly IDs, and `numeric` data, which are our quantitative values and some q-values. 

::: {.rmdnote}

We can combine identifying data types and extracting these columns with a combination of `dplyr::select()` and `dplyr::where()`. 1. Select all `character` columns. 2. Select all `numeric` columns. 3. Combine useful ID columns with all `numeric` columns. This will be helpful for an overview of the data as well.

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button16" aria-expanded="false" aria-controls="button16"> Hint </button> <div id="button16" class="collapse">  
\
You can find explanations for both functions online:
[select](https://dplyr.tidyverse.org/reference/select.html) and [where](https://tidyselect.r-lib.org/reference/where.html)
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button17" aria-expanded="false" aria-controls="button17"> Code 1 </button> <div id="button17" class="collapse">  
\
The `where()` function accepts any kind of function which can be used to test whether a column should be selected or not. 

```r
data_raw %>% 
  select(where(is.character))
```

We could also use the output of the previous `map` function to indicate the columns.


```r
# Create vector of character column names 
names_character <- map_lgl(data_raw, is.character) %>% 
  which() %>% 
  names() 
# Use vector as input for select 
data_raw %>% 
  select(names_character)
```

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button18" aria-expanded="false" aria-controls="button18"> Code 2 </button> <div id="button18" class="collapse">  
\
All numeric data can be found with `is.numeric()`. Again, since we provide a function as an object, and do not want it to do something immediately, we leave out the `()` brackets. 

```r
data_raw %>% 
  select(where(is.numeric))
```
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button19" aria-expanded="false" aria-controls="button19"> Code 3 </button> <div id="button19" class="collapse">  
\

```r
data_raw %>% 
  # Combine the different ways of choosing columns in a vector c()
  select(c("Precursor.Id", where(is.numeric)))
# We could also retain some more information
data_raw %>% 
  select(c("Precursor.Id", "Run", "Protein.Group", "Protein.Names", "Genes"  , where(is.numeric)))
```
But to also provide the most basic use case of `select`, we can simply use the column names as they are or as "strings". Pressing Tab with the cursor in the `select` function can be helpful as well.

```r
data_raw %>% 
  select(c(Precursor.Id, Modified.Sequence, "Run", "Precursor.Charge"))
```
</div>

\
Let's keep the remaining time open to explore other `dplyr` functions. They are described in the [Data transformation](https://r4ds.hadley.nz/data-transform) section and listed in the [Function reference](https://dplyr.tidyverse.org/reference/index.html) but the most useful ones are:

* `dplyr::select()`
* `dplyr::filter()`
* `dplyr::arrange()`
* `dplyr::pull()`
* `dplyr::bind_rows()`

* `dplyr::mutate()`
* `dplyr::summarise()`
* `dplyr::rename()`


* `dplyr::full_join()`
* `dplyr::inner_join()`
* `dplyr::left_join()`
* `dplyr::right_join()`


## Tidy up your data 

With the list of `dplyr` functions above, you have a pretty powerful tool set to manipulate data in which ever way you like. But we also need to know, what we need to do, to get our data analysis-ready. 

Following this, we can start to make our data more legible by removing unnecessary information and making names more meaningful. We will follow a scheme like this: 

1. Filtering identified precursors 
2. Shorten and clean up sample names
3. Remove unnecessary information (select column you need)
4. Sum precursors to modified peptides 
5. Pivot data to a samples x peptides matrix (still a tibble tho) 
6. Count missing values and further filter data 
7. (Optional) Normalize the data 




### Filtering identified precursors 

The [Main output reference](https://github.com/vdemichev/DiaNN?tab=readme-ov-file#main-output-reference) was mentioned before, and at the end it contains a section about __Filtering the main report__. Choose a filtering scheme that you think makes sense (match-between runs (MBR) was used).

::: {.rmdnote}

Choose parameters and threshold to filter the precursors in your data and assign a new object `data_filtered`.

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button20" aria-expanded="false" aria-controls="button20"> Hint </button> <div id="button20" class="collapse">  
\
As the DIA-NN documentation suggest, we could use a threshold of 0.01 for `Lib.Q.Value` and `PG.Q.Value`.

`Lib.Peptidoform.Q.Value` could also be applied retroactively if we find some outliers or weirdly behaving data points. 
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button21" aria-expanded="false" aria-controls="button21"> Code </button> <div id="button21" class="collapse">  
\
The `dplyr::filter()` function allows us to remove rows based on a logical operation that results in one TRUE/FALSE value per row.

```r
data_filtered <- data_raw %>% 
  filter(Lib.Q.Value < 0.01) %>% 
  filter(PG.Q.Value < 0.01)
```

We can do the same in a condensed way.

```r
data_filtered <- data_raw %>% 
  filter(Lib.Q.Value < 0.01, PG.Q.Value < 0.01) 
```
</div>

\
This is a relatively simple way to filter your data. In many cases, there will be further parameters or data-driven schemes (variance, etc.) to fiter your data. 

### Shorten and clean up sample names

The easier your data can be read and understood, the more useful it will be to you and others. You will sometimes spend days, weeks or months with the same dataset. Therefore, you will be very familiar all the sample names, groups, etc. For others to understand it in a meeting or a presentation, it will be very helpful to have all names you use as concise and meaningful as possible. Let's look at the sample names in column `Run`. Currently, they contain the full names of the raw data files that we processed by DIA-NN. Depending on the needed information, we can remove redundant details between the sample names. 

Let's check them first:

```r
# The Run column can also be accessed with the dplyr::pull() function
data_filtered$Run %>% 
  # we only need each name once
  unique()
```

We can see that there is a lot of redundancy in the sample names, as each one describes the whole experimental and MS scheme. Shortening them will make the data more legible. 

::: {.rmdnote}

Modify the `Run` column of the `data_filtered` data frame by shortening the sample names to only the useful parts. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button22" aria-expanded="false" aria-controls="button22"> Hint - modify names </button> <div id="button22" class="collapse">  
\
To figure out how to modify the names, it makes it easier to extract the names and work on this test vector until we can implement the code into our script. 

```r
sample_names <- data_filtered %>% 
  pull(Run) %>% 
  unique()
```
Useful functions for text manipulation can be found in the `stringr` [package](https://stringr.tidyverse.org/). To get a good overview of the functions in a package, the [Reference](https://stringr.tidyverse.org/reference/index.html) nicely lists everything we need to know. For most, if not all functions, there are [base R equivalents](https://stringr.tidyverse.org/articles/from-base.html. For our problem we can start with a simple base R function `substring`. 

```r
sample_names %>% 
  substring(first = 20)
```
You can go from here. 

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button23" aria-expanded="false" aria-controls="button23"> Hint - modify the data frame </button> <div id="button23" class="collapse">  
\
When modifying our data, we either focus on one column or all columns of a certain type. Both can be accomplished with `dplyr::mutate()`. This function assigns the new values to a column with a provided name, if the name is the same as an existing column, it overwrites it.

```r
data_filtered <- data_filtered %>% 
  mutate(Run = substring(text = Run, first = 20))
```
You can see that the mutate function overwrites the Run column as defined by the left side of the `=` sign and uses `Run` in the expression on the right side of the `=` sign. To finish this problem, we still need to adjust the beginning of the desired substring. 

If you do not want to count by yourself, could do some copying and use the `nchar()` function. 

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button24" aria-expanded="false" aria-controls="button24"> Code </button> <div id="button24" class="collapse">  
\
Combining both hints, we can reassign the `data_filtered` object and overwrite the `Run` column.

```r
data_filtered <- data_filtered %>% 
  mutate(Run = substring(text = Run, first = 41))
```
Make sure you are comfortable with how the mutate function works!

A different way would be to remove the redundant part of the string with the `stringr::str_remove()` function.

```r
data_filtered <- data_filtered %>% 
  mutate(Run = stringr::str_remove(
    string = Run, 
    pattern = "EVE_250123_S4504_LKJ_CP_PELSA_K562_Stau_"))
```
The intendation of the code above was changed slightly, otherwise the pattern argument would have reached outside the 80 characters limit and would not look as nice. Synthax-wise, this does not make any difference and the code work just the same.
</div>

\
`View` your data frame and see how it looks much nicer now.

```r
View(data_filtered)
```

### Remove unnecessary information 

After removing all the redundant stuff in our sample names, the next step in our *Tidy Data Campaign* involves removing all information we do not need later. This will help us a lot with getting a better overview of our data and will allow others to look at our dataset without immediately being overwhelmed. 
Again, the [Main output reference](https://github.com/vdemichev/DiaNN?tab=readme-ov-file#main-output-reference) is helpful here and the *Main report* section of the [Output](https://github.com/vdemichev/DiaNN?tab=readme-ov-file#output) chapter gives a short summary. We are primarily interested in information regarding our samples, our features which are the precursors and there further information like the peptide sequence further annotation as well as the normalized quantity.

::: {.rmdnote}

Remove all columns from `data_filtered` that we do not need. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button25" aria-expanded="false" aria-controls="button25"> Hint </button> <div id="button25" class="collapse">  
\
The `dplyr::select()` function will allow us to only retain the column we need. Regarding which columns we need, just take a guess and you'll find out in the solution. 
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button26" aria-expanded="false" aria-controls="button26"> Solution </button> <div id="button26" class="collapse">  
\


```r
data_filtered <- data_filtered %>% 
  select(c("Run",
           "Precursor.Id",
           "Modified.Sequence",
           "Stripped.Sequence",
           "Protein.Group",
           "Protein.Names",
           "Genes",
           "Precursor.Normalised"))
```
This also allowed us to change the order of the columns. There are two more ways to do this.

```r
data_filtered <- data_filtered %>% 
  select(all_of(c("Run",
                  "Precursor.Id",
                  "Modified.Sequence",
                  "Stripped.Sequence",
                  "Protein.Group",
                  "Protein.Names",
                  "Genes",
                  "Precursor.Normalised")))
```
The `dplyr::all_of()` function will check, if all specified column names can be found in the data. The `dplyr::any_of()` function does the same, but does not fail if a column name cannot be found. This makes it a bit more flexible, but the real advantage is that you can use a predifened vector to list the column names.

```r
column_names <- c("Run",
                  "Precursor.Id",
                  "Modified.Sequence",
                  "Stripped.Sequence",
                  "Protein.Group",
                  "Protein.Names",
                  "Genes",
                  "Precursor.Normalised")
data_filtered <- data_filtered %>% 
  select(any_of(column_names))
```
Simply using a vector works as well, but R will complain and we don't want that. And it could lead to confusions in the code, which is the real problem. 

</div>

\
Great, our data should look much better already.^[*whispering* `View()` it.]

### Sum precursors to modified peptides 

The next step is very data-specific, but will allow us to explore the `dplyr::summarise()` function. Our data currently exists on the precursor level.^[Precursor or precursor ion is the mass spec term for an peak in the MS1, which represents the mass-over-charge (m/z) of a particular ion.] As a peptide can have multiple charge states based on its amino acid sequence and the pH of the buffer (e.g. 2+ and 3+), we can combine the quantity of both to represent a truer peptide quantity. Simply summing both values up is the way to go here. 

::: {.rmdnote}

Read into the `dplyr::summarise()` function and sum up the `Precursor.Normalised` column from the precursors to peptides to create `data_peptides`. You will need to identify which column in our data identifies the peptides. In addition, check if `Precursor.Normalised` contains `NA`s, as the `sum()` function is sensitive to them. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button27" aria-expanded="false" aria-controls="button27"> Hint - peptide info </button> <div id="button27" class="collapse">  
\
You will need to summarise precursors to the peptides identified by `Modified.Sequence` and individually for each sample/`Run`.
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button28" aria-expanded="false" aria-controls="button28"> Hint - summarise </button> <div id="button28" class="collapse">  
\
The `dplyr::summarise()` function works the same as `dplyr::mutate()`, the only difference is that the computation in mutate yields an output of the same length as the input and summarise reduces the number of elements of the output by combining them. If used plain, the output will have one row which is the summary of each column. You can specify sub groups to be combined with the `.by` argument.
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button29" aria-expanded="false" aria-controls="button29"> Solution </button> <div id="button29" class="collapse">  
\
We first check if the `Precursor.Normalised` data contains `NA`s.

```r
data_filtered %>% 
  pull(Precursor.Normalised) %>% 
  is.na() %>% 
  # sum will give you the total number of NAs, table or mean work as well 
  sum()
```
Looks good, now we can combine our precursors. 

```r
data_peptides <- data_filtered %>% 
  # It can be useful to indicate the operations we do along the way as names 
  # Precursor.Normalised -> Precursor.Normalised.sum 
  summarise(Precursor.Normalised.sum = sum(Precursor.Normalised), 
            .by = c("Run", "Modified.Sequence"))
```
The new data frame contains `Run` and `Modified.Sequence` as row IDs and the new `Precursor.Normalised.sum` column. If we want to retain the other annotations of our peptides, we can use a function to keep them as well. Since the protein and gene information will be the same for each peptide, we can simply use unique to reduce the multiple entries into one. 
We can do the same in a condensed way.

```r
data_peptides <- data_filtered %>% 
  summarise(Precursor.Normalised.sum = sum(Precursor.Normalised), 
            Stripped.Sequence = unique(Stripped.Sequence), 
            Protein.Group = unique(Protein.Group), 
            Protein.Names = unique(Protein.Names), 
            Genes = unique(Genes), 
            .by = c("Run", "Modified.Sequence"))
```
If there were different informations for each precursor, we could use the `paste(..., collapse = ";")` or `c()` to keep the information
</div>

\
Now our data operates on the 'modified peptides' level^[peptide sequence + specific PTMs], which is what we want to do the differential abundance analysis on. 


### Pivot data to a samples x peptides matrix 

Our data is on a good way to be finally used for the Limma analysis. We can check in on the way by pivoting it into the wide format. This will allow us to inspect the data visually easier. 

::: {.rmdnote}

We came across the `tidyr::pivot_wider()` function before. Use it to spread your data in two ways: 1. `data_peptides_o`^[o for observations as rows] so that peptides become become column names and 2. `data_peptides_v`^[v for variables as rows] so that the sample names become column names. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button30" aria-expanded="false" aria-controls="button30"> Hint </button> <div id="button30" class="collapse">  
\
The `tidyr::pivot_wider()` wider function has three primary arguments which dictate the shape of the resulting data frame. 

```r
pivot_wider(id_cols = c("column that stays as row IDs"), 
            names_from = c("column whose values will be used as column names"), 
            values_from = c("column from which values are used for each cell"))
```

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button31" aria-expanded="false" aria-controls="button31"> Code </button> <div id="button31" class="collapse">  
\
In the first part of the exercise, we want the samples to stay as rows.

```r
data_peptides_o <- data_peptides %>% 
  pivot_wider(id_cols = "Run", 
              names_from = "Modified.Sequence", 
              values_from = "Precursor.Normalised.sum")
```
Great, this is what we want! Now let's do the opposite. 

```r
data_peptides_v <- data_peptides %>% 
  pivot_wider(id_cols = "Modified.Sequence", 
              names_from = "Run", 
              values_from = "Precursor.Normalised.sum")
```
Works as well, but we lost some data. We can fix this by including the column names as `id_cols`. 

```r
data_peptides_v <- data_peptides %>% 
  pivot_wider(id_cols = c("Modified.Sequence", 
                          "Stripped.Sequence",
                          "Protein.Group",
                          "Protein.Names",
                          "Genes"), 
              names_from = "Run", 
              values_from = "Precursor.Normalised.sum")
```
This does not work when retaining the samples as rows.
</div>

### Count missing values and further filter data 

We have some pretty nice data frames by now. Let's check them and start to attack our biggest enemy in data science, missing values. There are many approaches to 

### (Optional) Normalize the data 



## Save your data 

Once your raw data is imported and you have some first data transformation done, we can break up our code into a separate script. 

For this we need to save our `R Environment` to keep all data objects together. Before that, it can be useful to delete intermediate objects and evertyhing you do not need anymore.

```r
# Clean environment
rm(list = c())

# Save RData
save.image("Data/RData/00_Import_data.RData")
```

Now, everything is saved and can be conveniently accessed later again. This is also a nice way to share your data with others. 


<!-- ```{r} -->
<!-- # Check input -->
<!--   if (all(c(Q.Value,  -->
<!--             PG.Q.Value,  -->
<!--             Lib.Q.Value,  -->
<!--             Lib.PG.Q.Value,  -->
<!--             protein.q,  -->
<!--             gg.q) == 0))  -->
<!--     stop("All your q-value cutoffs are 1, please change them according to your study.") -->


<!--   # Filter precursors by proteotypicity -->
<!--   if (proteotypic.only)  -->
<!--     data_raw_filtered <- data_raw %>%  -->
<!--       filter(Proteotypic != 0) -->
<!--   else  -->
<!--     data_raw_filtered <- data_raw -->

<!--   # Filter precursors by Q-values -->
<!--   data_raw_filtered <- data_raw_filtered %>%  -->
<!--     filter(Q.Value <= Q.Value,  -->
<!--            PG.Q.Value <= PG.Q.Value,  -->
<!--            Lib.Q.Value <= Lib.Q.Value,  -->
<!--            Lib.PG.Q.Value <= Lib.PG.Q.Value) -->

<!--   # Extract quantitative data -->

<!--   # Rename runs  -->
<!--   data_raw_filtered <- data_raw_filtered %>%  -->
<!--     mutate(Run = setNames(names(sample_names), unname(sample_names))[Run]) %>%  -->
<!--     arrange(Run) -->

<!--   # Summarise precursors to modified peptides  -->
<!--   data_quant <- data_raw_filtered %>%   -->
<!--     summarise(!!quant_column := sum(!!rlang::sym(quant_column)),  -->
<!--               .by = c("Run", peptide.id))  -->

<!--   # Add group information  -->
<!--   data_quant <- data_quant %>%  -->
<!--     mutate(Group = setNames(sample_groups, names(sample_names))[Run],  -->
<!--            .after = "Run") %>%  -->
<!--     mutate(n = sum(!!rlang::sym(quant_column) > 0), .by = c(peptide.id, "Group")) %>%  -->
<!--     mutate(p = n / max(n), .by = "Group") %>%  -->
<!--     filter(all(p >= min_val_per_group), .by = peptide.id) %>% ##### Check this  -->
<!--     mutate(n_peptide = length(Run), .by = peptide.id) %>%  -->
<!--     filter(n_peptide == max(n_peptide)) %>%  -->
<!--     pivot_wider(id_cols = "Run",  -->
<!--                 names_from = peptide.id,  -->
<!--                 values_from = quant_column) -->




<!-- ``` -->




# Limma analysis

__Coming on Thursday__

<!-- https://kasperdanielhansen.github.io/genbioconductor/html/limma.html -->

<!-- https://www.bioconductor.org/packages/devel/bioc/vignettes/limma/inst/doc/usersguide.pdf -->

<!-- (https://www.bioconductor.org/packages/devel/bioc/vignettes/limma/inst/doc/usersguide.pdf) -->

# Reporting results 

__Coming on Thursday.__
<!-- This chapter serves the purpose to help us explore the different things we do with our results.  -->





# More data exploration 

__Coming on Thursday.__









