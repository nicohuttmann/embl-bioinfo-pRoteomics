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

We have some pretty nice data frames by now. Let's check them and start to attack our biggest enemy in data science, missing values. There are many approaches to handle missing values, the simplest one to remove all data with missing values. In our case, all peptides with missing values.^[Depending on the data, you may loose too much, but for the beginning this is fine and only with better understanding of the data would we try and include more peptides with missing values.]

In principle, both data frames `data_peptides_o` and `data_peptides_v` could be used for this task. We will use `data_peptides_v` for now. First we need to identify the form of our missing values, they can be `NA`s or 0s. Let's count them with the `dplyr::summarise()` function in combination with `dplyr::across()`. 

::: {.rmdnote}

Read into how you can use `dplyr::across()` to target multiple columns at a time and 1. count `NA`s and 2. 0s. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button32" aria-expanded="false" aria-controls="button32"> Hint - summarise across </button> <div id="button32" class="collapse">  
\
`dplyr::across()` allows us to specify the column we want to modify similar to the `dplyr::select()` function with `dplyr::where()` and a function like `is.numeric()`. The second part of the `dplyr::across()` function needs a function which will be applied to each column separately. In our case, this function should count the number of `NA`s or 0s.
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button33" aria-expanded="false" aria-controls="button33"> Hint - 0 </button> <div id="button33" class="collapse">  
\
`NA`s and regular values, including 0, sometimes behave different. We need to take this into account when counting the 0s in our data. 
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button34" aria-expanded="false" aria-controls="button34"> Code </button> <div id="button34" class="collapse">  
\


```r
data_peptides_v %>% 
  summarise(across(where(is.numeric), \(x) sum(is.na(x))))
# Optionally we can directly View the output of this computation
# %>% View()
```
The first thing we see is that yes, we do have `NA`s in our data. But these numbers are not very telling. We can replace `sum()` with `mean()` to get the fraction of `NA`s in our data. 

```r
data_peptides_v %>% 
  summarise(across(where(is.numeric), \(x) mean(is.na(x))))
```
When counting the number of 0s in our data, this is how I would intuitively do it.

```r
data_peptides_v %>% 
  summarise(across(where(is.numeric), \(x) mean(x == 0)))
```
However, this will fail due to the `NA`s in our data. One quick and dirty workaround would be to temporarily set all `NA`s to 1.^[I only do this to show you how mutate across works.]

```r
data_peptides_v %>% 
  # First we replace all NAs by 1 with the combination of mutate and across
  mutate(across(where(is.numeric), \(x) ifelse(is.na(x), 1, x))) %>% 
  # then we can count the 0s without any trouble
  summarise(across(where(is.numeric), \(x) mean(x == 0)))
```
Now we first transformed all `NA`s to 0s, and then continued with our computation. in addition to mutate across, we also used the function `ifelse()` which is very helpful, when you want to do different operations on you values depending on the value itself. Here, we test for each value of `x` if it is an `NA` by `is.na(x)` and return 1 if the statement is true or the value itself if not.^[This is reflected by having `x` twice in `ifelse()`, in the test statement and the return condition.]

Besides this, we have an answer to our initial question, we only have missing values in form of `NA`s. 
</div>

Now to actually dealing with the data. We already said that we want to simply exclude peptides with missing values. Above, we counted the number of `NA`s per sample. Now, we need to do the same but for each peptide individually. 

::: {.rmdnote}

Count the number of missing values per peptide/row using mutate and the `dplyr::c_across()` function to add a column `f_values`^[fraction of values] to `data_peptides_v`. Assign the new data frame to `data_peptides_v_c`^[c for complete]. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button35" aria-expanded="false" aria-controls="button35"> Hint </button> <div id="button35" class="collapse">  
\
Wasn't this description quite detailed. Anyway, `dplyr::c_across()` work similar to the `dplyr::select()` function. And you have to make sure, to mutate row-wise.
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button36" aria-expanded="false" aria-controls="button36"> Code </button> <div id="button36" class="collapse">  
\
Let's fist count the number of missing values per peptide

```r
data_peptides_v %>% 
  mutate(f_values = mean(is.na(c_across(where(is.numeric)))), 
         .by = "Modified.Sequence", .after = 1) # .after and .before define the position of the new column
# %>% View()
```
We can also visualize the distribution.

```r
data_peptides_v %>% 
  mutate(f_values = mean(is.na(c_across(where(is.numeric)))), 
         .by = "Modified.Sequence", .after = 1) %>% 
  pull(f_values) %>% 
  table() %>% 
  barplot()
```
Inverting to counting values looks actually better here. We can achive this by invering the logical statement with `!`.

```r
data_peptides_v %>% 
  # mean(is.na(... -> mean(!is.na(...
  mutate(f_values = mean(!is.na(c_across(where(is.numeric)))), 
         .by = "Modified.Sequence", .after = 1) %>% 
  pull(f_values) %>% 
  table() %>% 
  barplot()
```
And now we filter the table.

```r
data_peptides_v %>% 
  mutate(f_values = mean(!is.na(c_across(where(is.numeric)))), 
         .by = "Modified.Sequence", .after = 1) %>% 
  filter(f_values == 1) # Here we could adjust the threshold 
# 1 means no NAs
```
Mutating and filtering can also be combined. 

```r
data_peptides_v_c <- data_peptides_v %>% 
  filter(mean(!is.na(c_across(where(is.numeric)))) == 1, 
         .by = "Modified.Sequence")
```

You could finally compare the number of peptides in `data_peptides_v` and `data_peptides_v_c` to see how many peptides were filtered out.  
</div>


### (Optional) Normalize the data 

We were already working with a column named `Precursor.Normalised`, which suggests this data is somehow normalized, but sometimes renormalizing makes sense and in general there are enough cases where normalization is essential. In general, we want to eliminate systematic factor between our samples. This means when dividing all peptide values of one sample by the ones of another sample, the median factor should be one. This is based on the assumption that the bulk of our data does not change between conditions. 

We will use the `limma` function `limma::normalizeBetweenArrays()` to normalize our data. You could try and figure out how to use it, however, it took me quite some time and involves a couple of uncommon functions to get the data into the right shape. Basically the `limma::normalizeBetweenArrays()` accepts a matrix with variables/peptides as rows. So let's simply have a look at the code. 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button37" aria-expanded="false" aria-controls="button37"> Code </button> <div id="button37" class="collapse">  
\


```r
# We assign a new object 
data_norm <- data_peptides_v_c %>% 
  # Column_to_rownames allows us to make a matrix from our tibble 
  # and store the character column 'Modified.Sequence' as rownames
  tibble::column_to_rownames(var = "Modified.Sequence") %>%
  # Normalization with the scale-method = median-normalization
  limma::normalizeBetweenArrays(method = "scale") %>%
  # The following lines revert the matrix to a tibble
  as.data.frame() %>%
  tibble::rownames_to_column(var = "Modified.Sequence") %>%
  tibble::as_tibble()
```

If this failed, it's on me! I forgot to remove the column with additional information about our peptides. This is a quick way to do so. 


```r
data_norm <- data_peptides_v_c %>% 
  # Only keep the first id column and all numeric columns 
  select(c(1, where(is.numeric))) %>% 
  tibble::column_to_rownames(var = "Modified.Sequence") %>%
  limma::normalizeBetweenArrays(method = "scale") %>%
  as.data.frame() %>%
  tibble::rownames_to_column(var = "Modified.Sequence") %>%
  tibble::as_tibble()
```

You can find an explantion of the normalization method in the [documentation](http://web.mit.edu/~r/current/arch/i386_linux26/lib/R/library/limma/html/normalizebetweenarrays.html).

</div>

\
We can explore the impact of renormalizing our data later by calculating the coefficient of variance (CV) for both group and doing a PCA analysis of both data frames. 

Our data looks pretty good by now and is ready for a Limma analysis to identify which peptides were affected in their abundance by the drug treatment. Now we can simply see how to we can store our data when done working and simply reopen it when sitting down again. 


## Save your data 

Once your raw data is imported and you have some first data transformation done, we could clean up our environment and break up our code into a separate script. 

For this we need to save our `R Environment` to keep all data objects together. Before that, it can be useful to delete intermediate objects and everything you do not need anymore.

```r
# Clean environment
rm(list = c())

# Save RData
save.image("Data/RData/00_Import_data.RData")
```

Now, everything is saved and can be conveniently accessed later again by loading the data into your environment with `load("Data/RData/00_Import_data.RData")`. This is also a nice way to share your data with others. 


# Limma analysis

Here we are, after wrangling two days with our data, making it pretty and tidy without ever seeing a heatmap of it, ready to do a differential abundance analysis with [limma](https://pmc.ncbi.nlm.nih.gov/articles/PMC4402510/). *limma* is a tool originally developed for microarray analysis, which works just as well for proteomics data.^[Yes, proteomics started by borrowing tools from the RNA people..] We will use it to identify, which peptides have a different abundance between the two sample groups. 

## Running limma

You can find the [limma package](https://bioconductor.org/packages/release/bioc/html/limma.html) on Bioconductor. Check out the website and find 1. how to install it, 2. the limma User's Guide and 3. the Reference Manual.^[You can leave out 'A brief introduction to limma'] All Bioconductor package pages are made up this way and allow us to find the relevant information quickly. Except in this case. 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button38" aria-expanded="false" aria-controls="button38"> Code + Links </button> <div id="button38" class="collapse">  
\


```r
# Install BiocManager if not yet installed
if (!require("BiocManager", quietly = TRUE))
  install.packages("BiocManager")
# Install limma
BiocManager::install("limma")
```

[limma User's Guide](https://bioconductor.org/packages/release/bioc/vignettes/limma/inst/doc/usersguide.pdf) and [Reference Manual](https://bioconductor.org/packages/release/bioc/manuals/limma/man/limma.pdf)

</div>

\
Admittedly, this is not very helpful yet. For other packages, you can find a much more concise documentation and commonly one or more workflow descriptions depending on what you want to do. [This guide](https://kasperdanielhansen.github.io/genbioconductor/html/limma.html) seems a bit more practical and can be applied to our data. 

::: {.rmdnote}

Let's make this a real world example! Try and apply a `limma` analysis to your data. Use the explanations in [this guide](https://kasperdanielhansen.github.io/genbioconductor/html/limma.html) and on page 36/37 of the [limma User's Guide](https://bioconductor.org/packages/release/bioc/vignettes/limma/inst/doc/usersguide.pdf). Help for individual functions can be found in the [Reference Manual](https://bioconductor.org/packages/release/bioc/manuals/limma/man/limma.pdf) and with the known `?limma::lmFit`. 

The final goal is to use the `limma::topTable()` function to extract the results. Have fun and good luck!

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button39" aria-expanded="false" aria-controls="button39"> Solution </button> <div id="button39" class="collapse">  
\
Are you sure you want to give up already?

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button40" aria-expanded="false" aria-controls="button40"> No </button> <div id="button40" class="collapse">  
\
Great! Just continue trying out something and it will eventually work. In the worst case, you could use ChatG...NO, please don't do this. 

</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button41" aria-expanded="false" aria-controls="button41"> Yes </button> <div id="button41" class="collapse">  
\
Okay, here we go. Since the analysis involves a couple of steps and I do not like to clutter the environment too much, I propose to keep intermediate steps of the same analysis all in one list. Don't worry, the result will be the same as when you simply do it with multiple R objects. 

```r
limma_list <- list()
```
We will first add our data, which we already very nice prepared. The only thing missing is to take the `log2` of our data, because limma like other statistical tests like a t-test assume normally distributed data. 

```r
## Add base data frame 
limma_list[["data"]] <- data_norm %>% 
  # This works simply with mutate(across(where(is.numeric), log2)) or with the 
  # fast version by pivoting in long format and back after the operation
  tidyr::pivot_longer(-1) %>% 
  # We need to make sure the sample sames stay in the correct order 
  arrange(name) %>% 
  dplyr::mutate(value = log2(value)) %>% 
  tidyr::pivot_wider()
```
It is good practise to save your input data close to your statistical tests. 

The `limma` functions, similar to `limma::normalizeBetweenArrays()`, accept a `matrix` or an `eSet` (expression set), a special type of storing your data. 


```r
## Add eset 
limma_list[["eset"]] <- limma_list[["data"]] %>%
  # We have seen this before, but here is the generalized example by renaming 
  # the first column to "rowname", which is the default column to use as 
  # rownames for column_to_rownames
  dplyr::rename(rowname = 1) %>% 
  tibble::column_to_rownames() %>%
  as.matrix() %>% 
  # Depending on your input data frame, you may need to transpose your data
  # an eset has samples as columns and features/variables as rows
  # t() %>% 
  Biobase::ExpressionSet()
```
The ExpressionSet is an idea to standardize data formats in R, but is practically only used in some packages as input and most people mainly work with `tibble`s.

Next, we need to describe our experimental setup. We can find this information in our sample name `names(limma[["data"]])` and it describes either a 'Control' or the 'Staurosporine' group, we can simply make a vector that describes the sample groups in the order of our samples 

```r
limma_list[["design"]] <- 
  model.matrix(
    ~0+factor(c(rep("Control", 4), rep("Staurosporine", 4)), 
              levels = c("Control", "Staurosporine")))
```
The vector can be made in any way. `c(rep("Control", 4), rep("Staurosporine", 4))` is just one of many ways to accomplish this. `rep(c("Control", "Staurosporine"), each = 4)` would work as well or fully writing all names individually. 

Because the names look weird, we can rename the generated model matrix. Have a look at it and see how they encode the group information in it. 


```r
colnames(limma_list[["design"]]) <- c("Control", "Staurosporine")
```

Now we can start with the first linear model fit `limma::lmFit()`. This needs the eset and the design matrix as input. 


```r
limma_list[["fit"]] <- limma::lmFit(limma_list[["eset"]], limma_list[["design"]])
```

Following this, we need to indicate which comparisons we want to conduct. In the case of more than two groups or a more complex factorial design, we can indicate all interesting difference here. 


```r
limma_list[["contrast.matrix"]] <- limma::makeContrasts(Staurosporine-Control, 
                                                        levels=limma_list[["design"]])
```

Now we compare both of our groups. 


```r
limma_list[["fit2"]] <- limma::contrasts.fit(fit = limma_list[["fit"]], 
                                             contrasts = limma_list[["contrast.matrix"]])
```

And finally compute our statistics. 


```r
limma_list[["fit2_eBayes"]] <- limma::eBayes(limma_list[["fit2"]])
```

The final results can be extracted with `limma::topTable()`. 

```r
limma::topTable(limma_list[["fit2_eBayes"]]) # %>% View()
```

Great, we go our first results. Let's explore how we can further work with them. 

</div>

</div>


## Filtering the limma output

The `limma::topTable()` should have given you a preview of your results. But I recommend using a different functions for this, the `biobroom::tidy.MArrayLM()` function which outputs a nice `tibble`. [biobroom](https://bioconductor.org/packages/release/bioc/html/biobroom.html) is again a Bioconductor function and it helps you with "[...] methods for converting standard objects constructed by bioinformatics packages, especially those in Bioconductor, and converting them to tidy data".

::: {.rmdnote}

Try it out and have a look at your results!^[And install biobroom if you do not have it yet. ]

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button42" aria-expanded="false" aria-controls="button42"> Code </button> <div id="button42" class="collapse">  
\


```r
limma_list[["results"]] <- 
  biobroom::tidy.MArrayLM(limma_list[["fit2_eBayes"]])
```

</div>

\
We can `View()` our results and bring the peptides with the lowest p-value to the top by clicking the `p.value` column. Still, there are still some generic terms in this data frame like `gene`. We can modify it to help its legibility. 

::: {.rmdnote}

Repeat the last command but further modify the data frame by renaming the gene column to something like id and arrange the rows by p.value.

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button43" aria-expanded="false" aria-controls="button43"> Code </button> <div id="button43" class="collapse">  
\


```r
limma_list[["results"]] <- biobroom::tidy.MArrayLM(limma_list[["fit2_eBayes"]]) %>% 
  dplyr::rename(id = gene) %>% 
  dplyr::arrange(p.value)
```

</div>

\
Nice, now we can look at the data more closely. A common practise when applying statistical test to many different measurements is a multiple testing correction, as even with a p-value threshold of 0.05, we assume 5% of our hits to be false positives. The most common method in proteomics is the Benjamini-Hochberg correction, which is implemented in the `p.adjust()` function. 

::: {.rmdnote}

Add a `p.adjust` column to your data by applying the `p.adjust()` function to your p-values.^[Bonus if the new column lands right after p.value.] Typing `p.adjust.methods` will tell you about available methods. You can again append the code from above. 

:::


<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button44" aria-expanded="false" aria-controls="button44"> Code </button> <div id="button44" class="collapse">  
\

```r
limma_list[["results"]] <- biobroom::tidy.MArrayLM(limma_list[["fit2_eBayes"]]) %>% 
  dplyr::rename(id = gene) %>% 
  # Rearranging our data by the p-values does not affect the adjustment 
  dplyr::arrange(p.value) %>% 
  # Adjust p-values
  dplyr::mutate(p.adjust = p.adjust(p.value, method = "BH"), 
                .after = "p.value")
```
</div>

\
Nice! Finally, we want to use our adjusted p-values and the effect size/log2 fold-change (FC) termed `estimate` in the table, to threshold our data and define more and less abundant/up- and down-regulated peptides. We can do this with the `dplyr::case_when()` function. Have a look at the code!

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button45" aria-expanded="false" aria-controls="button45"> Code </button> <div id="button45" class="collapse">  
\

```r
limma_list[["results"]] <- biobroom::tidy.MArrayLM(limma_list[["fit2_eBayes"]]) %>% 
  dplyr::rename(id = gene) %>% 
  dplyr::arrange(p.value) %>% 
  # Adjust p-values
  dplyr::mutate(p.adjust = p.adjust(p.value, method = "BH"), 
                .after = "p.value") %>% 
  # Apply thresholds
  dplyr::mutate(regulation = dplyr::case_when(
    p.adjust < 0.01 & 
      estimate >= log10(1.2) ~ "up", 
    p.adjust < 0.01 & 
      estimate <= - log10(1.2) ~ "down", 
    .default = "none"
  ))
```
Each logical statement like `p.adjust < 0.01 & estimate >= log10(1.2)`^[log10(120%) refers to an increase of 20% in peptide abundance.] return if true the values defined after `~`. If none apply, the function will return the `.default` for this element.^[Which is only by chance called "none" here as well.]

</div>

\
The table in `limma_list[["results"]]` contains now all information we need to further plot and report our results. 

## Visualizing the limma results 

The one and only way to represent the data from a differential abundance/expression analysis with two groups is the Volcano plot. Let's try it!

::: {.rmdnote}

Represent the *limma* results `estimate` and the `-log10(p.value)` in a volcano plot and color each point by the type of `regulation`. Use `ggplot2` for this. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button46" aria-expanded="false" aria-controls="button46"> Expanation </button> <div id="button46" class="collapse">  
\
The `ggplot2::ggplot()` function builds the foundation of your plot. You can try this function without any further input. 


```r
ggplot()
```
You should see a blank canvas. We can start to add our data with the `data` argument. 


```r
ggplot(limma_list[["results"]]) 
```
Wow, nothing changed. Next, we need to explain `ggplot` which column of our `data` should be projected on which axis or plot element. This is achieved with the `mapping` argument which takes the above described links between data and plot within the `ggplot2::aes()`^[aesthetics] function. We can define columns like `x = estimate` and even modify them in place like `y = -log10(p.value)`. 


```r
ggplot(limma_list[["results"]], aes(x = estimate, y = -log10(p.value)))
```
Now that the call gets longer, we can make use of the pipe to add our data. 

```r
limma_list[["results"]] %>%
  ggplot(aes(x = estimate, y = -log10(p.value)))
```

Oh, we have some axes now. But `ggplot` still only knows which data should be represented where, hence the axes, but not how. We want the most basic type, points.


```r
limma_list[["results"]] %>%
  ggplot(aes(x = estimate,
             y = -log10(p.value))) +
  # geom_point is only one of many geom_... layers 
  geom_point()
```

Nice, each one of our precious peptides represented as one little ugly point. Let's unravel this. `ggplot2::geom_point()` is called a layer and adds the representation for the defined `mapping` of our data. It is added to the initial plot created by `ggplot2::ggplot()` via a `+`. No `%>%`. Just a `+`. We can further modify this layer by setting a transparency with `alpha` and changing the `shape`, so that the changes are better visible.^[You can find a list of all shapes here: https://ggplot2.tidyverse.org/articles/ggplot2-specs.html#sec:shape-spec] 


```r
limma_list[["results"]] %>%
  ggplot(aes(x = estimate,
             y = -log10(p.value))) +
  # you can check all options in the function documentation 
  geom_point(shape = 16, alpha = 0.5)
```

Further, we can change the `theme` to something like `ggplot2::theme_classic()`.


```r
limma_list[["results"]] %>%
  ggplot(aes(x = estimate,
             y = -log10(p.value))) +
  geom_point(shape = 16, alpha = 0.5) +
  # there are many different theme_... types 
  theme_classic()
```

Looking good! Now let's color our points. If we would like to color our points all in one color, we could simple define this in the `ggplot2::geom_point(color = "grey)` layer. But we want the color to depend on the type of regulation as defined by the thresholds before. For this, we need to add a new variable to the `aes()` mapping and define a manual color scale.


```r
limma_list[["results"]] %>%
  ggplot(aes(x = estimate,
             y = -log10(p.value),
             # Define which column to use
             color = regulation)) +
  geom_point(shape = 16, alpha = 0.5) +
  theme_classic() +
  # Define the values for each data entry
  scale_color_manual(values = c(none = "grey",
                                up = "red",
                                down = "blue"))
```

Finally, we can remove the space between our plotted points and the outer border like this. This is a taste thing. 


```r
limma_list[["results"]] %>%
  ggplot(aes(x = estimate,
             y = -log10(p.value),
             color = regulation)) +
  geom_point(shape = 16, alpha = 0.5) +
  theme_classic() +
  scale_color_manual(values = c(none = "grey",
                                up = "red",
                                down = "blue")) +
  # You can also define the xlim = c(-3, 3) and ylim = c(0, 10) here 
  coord_cartesian(expand = F)
```

Finally, we can save our plot first and print it then separately. 

```r
limma_list[["p"]] <- limma_list[["results"]] %>%
  ggplot(aes(x = estimate,
             y = -log10(p.value),
             color = regulation)) +
  geom_point(shape = 16, alpha = 0.5) +
  theme_classic() +
  scale_color_manual(values = c(none = "grey",
                                up = "red",
                                down = "blue")) +
  coord_cartesian(expand = F)
# Sometimes you may need force this by print(limma_list[["p"]]) 
limma_list[["p"]]
```

</div>

\
Great, this basically covered most parameters you can change for plotting in R with `ggplot2`. It may take some time to get comfortable with all functions and get to know all possibilities, but then there are no limits!

You can find much more information in the [Data visualization](https://r4ds.hadley.nz/data-visualize) chapter or the in depth [Layers](https://r4ds.hadley.nz/layers) chapter. Further readings would be [Fundamentals of Data Visualization](https://clauswilke.com/dataviz/) and the formal description of the system we are using here, [A Layered Grammar of Graphics](https://vita.had.co.nz/papers/layered-grammar.pdf).

## Summary

In this chapter, we applied a package `limma` to analyse our data and represented the results in one plot. `limma` is one of the more complicated packages to use IMO, but still very useful and a good exercise. 

# Reporting results 

Now we have the results of our analysis and the plot in R. But not on the desk of our PI yet. Let's change this. We would need to export our plot and the results table. 

## Export graphics 

The simple and quick way to export your plots is by clicking 'Export' on top of you plots. You can then choose to export and image like a .png or a .pdf file. .pdf files can be very useful, as they can be imported into Adobe Illustrator and font etc. could be further adjusted. Also possible with `ggplot2` for most parts, but still convenient. 

Other ways include functions like the `ggplot2::ggsave()` function, base R solutions like `pdf()` or knitting an R Markdown file. I very much like the last approach for the day to day work and would only put more effort into exporting precise dimension etc. with the `pdf()` or `tiff()` function. For now, and the presentation, you can export them manually as described at the beginning. 

## Exporting data 

To export the data, we want to make sure to include only important information and annotation of the results and the peptides. Then, we need to decide on the output format. Usually we would want either a .csv or a .xlsx file.^[For you and you PI, respectively.]

Let's check the results table `View(limma_list[["results"]])`and decide what to keep and what we may need to add.

My suggestions are to specify `id` to Modified.Sequence or even better Modified.Peptide, `estimate` to log2.FC, keep `p.value`, `p.adjust` and `regulation`, and drop `term`, `statistic`, `lod`. 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button47" aria-expanded="false" aria-controls="button47"> Code </button> <div id="button47" class="collapse">  
\

```r
limma_list[["export"]] <- limma_list[["results"]] %>% 
  rename(Modified.Peptide = id, 
         log2.FC = estimate) %>% 
  select(-c(term, statistic, lod))
```
 
</div>

\
Further, we could add some information we had previously in `data_peptides_v` like the `Protein.Group` and the `Genes`
column. We could do this by joining the `tibble`s together or in a simpler way.


```r
limma_list[["export"]] <- limma_list[["export"]] %>% 
  mutate(Protein.Group = pull(data_peptides_v, Protein.Group, Modified.Sequence)[Modified.Peptide], 
         Genes = pull(data_peptides_v, Genes, Modified.Sequence)[Modified.Peptide], 
         .after = "Modified.Peptide")
```

Now we also have some additional information regarding our peptides which we would need to interpret the results. This data frame can now be exported.


```r
# To a .csv
write.csv(limma_list[["export"]], "Output/limma_results.csv")
# To an .xlsx
openxlsx::write.xlsx(limma_list[["export"]], "Output/limma_results.xlsx")
```

A table and a plot, what more could they ask from us. Oh, there are probably a lot of things which people may want to see things like a principal component analysis (PCA) plot to see how well the samples cluster by group, or an overview of the peptide intensities or CV values, to get insight into the quantitative values. We can explore some of those in the following chapter. 

# More data exploration 

__We'll design this chapter together.__



