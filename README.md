# Primary T-cell MPRA project code

In this README, there will be information on each .Rmd which is used to analyze the data of the paper "linking candidate causal autoimmune variants to T-cell networks using genetic and epigenetic screens".

### 20240913_eliminate_SNP.Rmd
  This Rmd eliminates a SNP which appeared in the results which should not have been there.

### 20240913_mpra_merge_creation_FINAL.Rmd
  This Rmd takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. This creates the expanded table which is called mpra merge.

### 20240913_mpra_hg_19_to_38_final.Rmd
   After the MPRA merge table is created, I incorporated human genome liftover data to have seperate hg19, hg38 and hg19 and 38 tables. I have already done this and both columns appear in the final table so you don't need to do this agian.
   
### 20240820_DHS_precision_recall_grid.Rmd
   This Rmd contains the grid search which is used to estimate the cut-offs for high activity variants (p-CREs) and allelic-specific expression variants (emVars).
   
### 20240913_motifbeakr_enrichment_analysis_FINAL.Rmd
   This Rmd contains the transcription factor binding analysis of the MPRA data.

 ### 20240914_tf_columns_mpra_merge.Rmd
    After creating TF data, create the columns which are used in MPRA merge.
   
### 20240914_UK_biobank_finemapping_enrichment.Rmd
    This Rmd contains the enrichments for emVars in UKBB fine-mapping data. 
    
### 20240913_mpra_supplementary_tables.Rmd
    Finally using all the tables which I have created so far, I put the tables into the final format which appears in the paper.


### Raylab Analysis V2G Jupyter Notebook
This Jupyter notebook generates variant-to-gene (V2G) mapping for rsIDs of interest. Key steps include:

Converting rsIDs to variant IDs using genopyc
Mapping variants to genes with the V2G otargen pipeline
Processing T cell expression data from the DICE database
Filtering V2G output based on cell-specific expression
Creating background and foreground datasets for network analysis

Requires Python (pandas, genopyc, polars) and R (otargen, purrr, dplyr, readr) libraries. Outputs include filtered V2G data and gene sets for further analysis.
