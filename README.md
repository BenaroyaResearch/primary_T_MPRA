# Primary T-cell screens project code

In this README, there will be information on each analysis code file which is used to analyze the data of the paper "linking candidate causal autoimmune variants to T-cell networks using genetic and epigenetic screens".

### 20250204_eliminate_SNP.Rmd

This .Rmd eliminates a SNP which appeared in the results which should not have been there because it is not associated with any disease

###  20250204_mpra_tf_annotations.Rmd

This code incorporates data two TF binding site programs, motifbreakR and Ananastra, to create columns for the MPRA big tables.

### 20250204_tcell_mpra_big_table.Rmd

This code takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. I incorporated human genome liftover data to have seperate hg19 and 38 tables. This code creates the big table for the primary T-cell MPRA. 

### 20250204_jurkat_mpra_big_table.Rmd

This code takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. I incorporated human genome liftover data to have seperate hg19 and 38 tables. This code creates the big table for the jurkat MPRA. 

### 20241113_DHS_precision_recall_grid.Rmd

This code contains the grid search which is used to estimate the cut-offs for high activity variants (p-CREs) and allelic-specific expression variants (emVars).

### 20250204_mpra_plots.Rmd

This code creates plots for MPRA analysis. Many plots are based on the previously published Jurkat analysis (from Mouri, K., Guo, M.H., de Boer, C.G. et al. Prioritization of autoimmune disease-associated genetic variants that perturb regulatory element activity in T cells. Nat Genet 54, 603–612 (2022).) as well as some plots of our own. The analyses include Figure 1 b-f, supplementary figures 3 & 4. There will also be some data generated in this code that will end up as supplementary tables 3, 4, 8, and 34. 

Plots include:

Comparisons between the Jurkat and primary T-cell data using venn diagrams, tables and plotting allelic bias

Enrichments for epigenetic data including DHS, ATAC-seq, caQTL, histone marks, etc.

Enrichment for MPRA emVars for PICS fine-mapping variants

An initial motifbreakR analysis simply describing the enrichment for transcription factor binding sites)

### 20250204_UK_biobank_finemapping_enrichment.Rmd
  
This code calculates the enrichments for MPRA emVars for variants fine-mapped in UK BioBank (UKBB) fine-mapping data. The steps to this analysis include:

Import the UKBB data and merge with MPRA data. 

Create a table with MPRA variants and the UKBB data for the paper.

Create the enrichment plots for MPRA emVars in UKBB data. 
   
### 20250204_motifbeakr_enrichment_analysis.Rmd

This code contains the transcription factor binding analysis of the MPRA data. The steps to this analysis include: 

1. Create a Granges bed file of the variants mpra tested in the MPRA

2. Run motifbreakR function to generate TF binding data on the MPRA variants

3. Merge motifbreakr and MPRA data

4. Run t-test of primary T cell MPRA expression of variants which do and do not bind to each tf 

5. Repeat step 4 with jurkat mpra expression data

6. Run t-test analysis for variants fine mapped to each disease

7. Merge the primary tcell and unstimulated jurkat data

8. Compare the results of jurkat and primary T cells
    
### 20250204_mpra_supplementary_tables.Rmd

Finally using all the tables which are relevant to the MPRA data created so far, I put the tables into the final format which appears in the paper. 

### Raylab Analysis V2G Jupyter Notebook

This Jupyter notebook generates variant-to-gene (V2G) mapping for rsIDs of interest. Key steps include:

Converting rsIDs to variant IDs using genopyc
Mapping variants to genes with the V2G otargen pipeline
Processing T cell expression data from the DICE database
Filtering V2G output based on cell-specific expression
Creating background and foreground datasets for network analysis

Requires Python (pandas, genopyc, polars) and R (otargen, purrr, dplyr, readr) libraries. Outputs include filtered V2G data and gene sets for further analysis.

### CRISPR_screen_analysis.Rmd

This markdown file uses Seurat and SCEPTRE to analyze single-cell CRISPR screen data.
