# (PART\*) Group Work Project {-}




# Getting started

## What's our project?

PELSA

[A peptide-centric local stability assay enables proteome-scale identification of the protein targets and binding regions of diverse ligands](https://www.nature.com/articles/s41592-024-02553-7)

![](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41592-024-02553-7/MediaObjects/41592_2024_2553_Fig1_HTML.png?as=webp){width=100%}


[Data availability ](https://www.nature.com/articles/s41592-024-02553-7#data-availability)

[PXD034606](https://proteomecentral.proteomexchange.org/cgi/GetDataset?ID=PXD034606)

[PRIDE project URI](https://ftp.pride.ebi.ac.uk/pride/data/archive/2024/11/PXD034606/)

[PELSA_staurosporine_K562_peptides.csv](https://ftp.pride.ebi.ac.uk/pride/data/archive/2024/11/PXD034606/PELSA_staurosporine_K562_peptides.csv)





## Import your data

https://r4ds.had.co.nz/data-import.html#compared-to-base-r

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> Hint </button> <div id="button1" class="collapse">  


</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> Code </button> <div id="button2" class="collapse">  
\

![](https://raw.githubusercontent.com/tidyverse/vroom/main/img/taylor.gif)

```r
# Comment 1
data_raw <- vroom::vroom("Data/report.tsv")

# Comment 2
data_raw <- arrow::read_parquet("Data/report.parquet")
```


</div>



## Understand your data 

Okay, we got our data



```r
names()
```


```r
str(t1)
```



## Tidy up your data 


```r
# Check input
  if (all(c(Q.Value, 
            PG.Q.Value, 
            Lib.Q.Value, 
            Lib.PG.Q.Value, 
            protein.q, 
            gg.q) == 0)) 
    stop("All your q-value cutoffs are 1, please change them according to your study.")
  
  
  # Filter precursors by proteotypicity
  if (proteotypic.only) 
    data_raw_filtered <- data_raw %>% 
      filter(Proteotypic != 0)
  else 
    data_raw_filtered <- data_raw
  
  # Filter precursors by Q-values
  data_raw_filtered <- data_raw_filtered %>% 
    filter(Q.Value <= Q.Value, 
           PG.Q.Value <= PG.Q.Value, 
           Lib.Q.Value <= Lib.Q.Value, 
           Lib.PG.Q.Value <= Lib.PG.Q.Value)
  
  # Extract quantitative data
  
  # Rename runs 
  data_raw_filtered <- data_raw_filtered %>% 
    mutate(Run = setNames(names(sample_names), unname(sample_names))[Run]) %>% 
    arrange(Run)
  
  # Summarise precursors to modified peptides 
  data_quant <- data_raw_filtered %>%  
    summarise(!!quant_column := sum(!!rlang::sym(quant_column)), 
              .by = c("Run", peptide.id)) 
  
  # Add group information 
  data_quant <- data_quant %>% 
    mutate(Group = setNames(sample_groups, names(sample_names))[Run], 
           .after = "Run") %>% 
    mutate(n = sum(!!rlang::sym(quant_column) > 0), .by = c(peptide.id, "Group")) %>% 
    mutate(p = n / max(n), .by = "Group") %>% 
    filter(all(p >= min_val_per_group), .by = peptide.id) %>% ##### Check this 
    mutate(n_peptide = length(Run), .by = peptide.id) %>% 
    filter(n_peptide == max(n_peptide)) %>% 
    pivot_wider(id_cols = "Run", 
                names_from = peptide.id, 
                values_from = quant_column)
  
  
  
  
```




# Limma analysis



# Reporting results 

This chapter serves the purpose to help us explore the different things we do with our results. 





# More data exploration 











