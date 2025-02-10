# Ho et al. MPRA analysis

Hello! Welcome to the MPRA analysis code for Ho et al. 2025

This folder contains data necessary for the MPRA analysis in Ho et al. 2025. There are 9 steps to this analysis which must be done in order. The CRISPR and V2G analyses are separate (steps 10 and 11)

Order of operations:

### 1. eliminate_SNP.rmd 

Use this to eliminate a SNP which isn't associated with any diseases in the study (I already elimianted this SNP from the jurkat and t-cell files)

### 2. mpra_tf_annotations.Rmd

Use this to make some columns for the MPRA big table. This code incorporates data two TF binding site programs, motifbreakR and Ananastra. 
### 3. tcell_mpra_big_table.Rmd 

Use this to create a big table for the primary t-cell MPRA. This code takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. I incorporated human genome liftover data to have seperate hg19 and 38 tables. To create all the plots in the other code files below this you need this table.
### 4. jurkat_mpra_big_table.Rmd 

Use this to create a big table for the jurkat MPRA. To create all the plots in the other code files below this you need this table.

### 5. mpra_DHS_grid_search.Rmd

This code will analyse the enrichment for DHS sites for high activity variants and is used to estimate the cut-offs for high activity variants (p-CREs) and allelic-specific expression variants (emVars). It will create Supp. figure 2 c & d and supp. tables 32 & 33. If you're doing your own MPRA use this to calibrate the variant category filter aka. the mpra_sig column (made in mpra_big_table.Rmd). My code will have the variant category filters for Ho et al., but you can calculate your own!

### 6. UK_biobank_finemapping_enrichment.Rmd

Use this to create the UKBB finemapping emVar enrichment plots in Supp. figure 5.

### 7. mpra_plots.Rmd

Use this to create most of the MPRA plots (figure 1 b-f, supp. figure 3 & 4)

### 8. motifbeakr_enrichment_analysis.Rmd

This code is used to calculate the TF motif enrichments for MPRA variants and create the relevant plots. (Figure 2, Supp. figure 6)

### 9. mpra_supplementary_tables

Finally using all the tables which are relevant to the MPRA data created so far, I put the tables into the final format which appears in the paper's supplementary tables (not including anything having to do with CRISPR or V2G)

### 10. Raylab Analysis V2G Jupyter Notebook

This Jupyter notebook generates variant-to-gene (V2G) mapping for rsIDs of interest. Key steps include:

Converting rsIDs to variant IDs using genopyc
Mapping variants to genes with the V2G otargen pipeline
Processing T cell expression data from the DICE database
Filtering V2G output based on cell-specific expression
Creating background and foreground datasets for network analysis

Requires Python (pandas, genopyc, polars) and R (otargen, purrr, dplyr, readr) libraries. Outputs include filtered V2G data and gene sets for further analysis.

### 11. CRISPR_screen_analysis.Rmd

This markdown file uses Seurat and SCEPTRE to analyze single-cell CRISPR screen data.
