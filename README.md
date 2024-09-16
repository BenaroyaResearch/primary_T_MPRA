# Primary T-cell screens project code

In this README, there will be information on each analysis code file which is used to analyze the data of the paper "linking candidate causal autoimmune variants to T-cell networks using genetic and epigenetic screens".

### 20240913_eliminate_SNP.Rmd

This .Rmd eliminates a SNP which appeared in the results which should not have been there because it was not even in the sequencing library. 

### 20240913_mpra_merge_creation_FINAL.Rmd

This Rmd takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. This creates the expanded table which is called mpra merge.

### 20240913_mpra_hg_19_to_38_final.Rmd

After the MPRA merge table is created, I incorporated human genome liftover data to have seperate hg19, hg38 and hg19 and 38 tables. I have already done this and both columns appear in the final table so you don't need to do this agian.

### 20240916_mouri_et_al_replication_code_in_line.Rmd

This .Rmd contains code to replicate the MPRA analysis code for the previously published Jurkat T-cell cell line data (from Mouri, K., Guo, M.H., de Boer, C.G. et al. Prioritization of autoimmune disease-associated genetic variants that perturb regulatory element activity in T cells. Nat Genet 54, 603–612 (2022).) as well as some plots of our own. The analyses include: 

Comparisons between the Jurkat and primary T-cell data using venn diagrams, tables and plotting allelic bias

Enrichments for epigenetic data including DHS, ATAC-seq, caQTL, histone marks, etc.

An plot describing the enrichment for MPRA emVars for PICS fine-mapping variants

An initial motifbreakR analysis simply describing the enrichment for transcription factor binding sites)
   
### 20240820_DHS_precision_recall_grid.Rmd

This Rmd contains the grid search which is used to estimate the cut-offs for high activity variants (p-CREs) and allelic-specific expression variants (emVars).
   
### 20240913_motifbeakr_enrichment_analysis_FINAL.Rmd

This Rmd contains the transcription factor binding analysis of the MPRA data. The steps to this analysis include: 

1. Create a Granges bed file of the variants mpra tested in the MPRA

2. Run motifbreakR function to generate TF binding data on the MPRA variants

3. Merge motifbreakr and MPRA data

4. Run t-test of primary T cell MPRA expression of variants which do and do not bind to each tf 

5. Repeat step 4 with jurkat mpra expression data

6. Run t-test analysis for variants fine mapped to each disease

7. Merge the primary tcell and unstimulated jurkat data

8. Compare the results of jurkat and primary T cells


 ### 20240914_tf_columns_mpra_merge.Rmd
  
After creating the TF data in the previous .Rmd, this .Rmd created the columns which are used in MPRA merge. This .Rmd incorporates data two TF binding site programs, motifbreakR and Ananastra.  
   
### 20240914_UK_biobank_finemapping_enrichment.Rmd
  
This Rmd contains the enrichments for MPRA emVars for variants fine-mapped in UK BioBank (UKBB) fine-mapping data. The steps to this analysis include:

Import the UKBB data and merge with MPRA data. 

Create a table with MPRA variants and the UKBB data for the paper.

Create the enrichment plots for MPRA emVars in UKBB data. 
    
### 20240913_mpra_supplementary_tables.Rmd

Finally using all the tables which are relevant to the MPRA data created so far, I put the tables into the final format which appears in the paper. Here are all the tables created in this file:

**NOT THE ORDER IN THE ACTUAL SUPPLEMENTARY TABLES**

1. Tcell MPRA results
 
2. Jurkat MPRA results 
 
3. PICS enrichment all loci
 
4. PICS enrichment emvars loci
 
5. UK biobank enrichment all loci

6. UK biobank enrichment emvars loci

7. tcell motifbreakr mpra combined
 
8. tcell motifbreakr logskew ttest
 
9. jurkat motifbreakr mpra combined

10. jurkat motifbreakr logskew ttest

11. ChromHMM enrich

12. Histone CAGE DHS enr

13. T cell MPRA functional annotations

14. PICS by MPRA

14. UKBB by MPRA

15. Jurkat MPRA functional annotations

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
