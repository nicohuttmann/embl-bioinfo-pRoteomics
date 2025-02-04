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

By now, you should have a link to the datasets in Slack. If not, please complain. There should be two files called report.tsv and report.parquet. Both are output files from the [DIA-NN](https://github.com/vdemichev/DiaNN) software, a tool that analyzes mass spectrometry data and outputs a table of all identified ions.^[Each ion, also called precursor, represents a peptide and its charge states. Each peptide can have multiple cahrge states and was originally derived from a protein by proteolytic cleavage. All this data stems from multiple samples and replicates which are combined in one table.]

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
Let's keep the remaining time open to explore other `dplyr` functions. They are listed in the [Function reference](https://dplyr.tidyverse.org/reference/index.html) but the most useful ones are:
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

__Coming on Wednesday__

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

__Coming on Wednesday__

# Reporting results 

__Coming on Thursday.__
<!-- This chapter serves the purpose to help us explore the different things we do with our results.  -->





# More data exploration 

__Coming on Thursday.__









