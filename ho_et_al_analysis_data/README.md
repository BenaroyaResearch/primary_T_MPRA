# Ho et al. MPRA analysis

Hello! Welcome to the MPRA analysis code for Ho et al. 2025

This folder contains data necessary for the MPRA analysis in Ho et al. 2025. There are 9 steps to this analysis which must be done in order. The CRISPR and V2G analyses are separate. 

Order of operations:
### 1. eliminate_SNP.rmd 
This .Rmd eliminates a SNP which appeared in the results which should not have been there because it is not associated with any disease

### 2. mpra_tf_annotations.Rmd
This code incorporates data two TF binding site programs, motifbreakR and Ananastra, to create columns for the MPRA big tables.

### 3. tcell_mpra_big_table.Rmd 
This code takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. I incorporated human genome liftover data to have seperate hg19 and 38 tables. This code creates the big table for the primary T-cell MPRA. To create all the plots in the other code files below this you need this table.

### 4. jurkat_mpra_big_table.Rmd 
Use this to create a big table for the jurkat MPRA. This code takes the basic MPRA information and contextualize it with linkage disequillirium, epigenetic and transcription factor binding data. I incorporated human genome liftover data to have seperate hg19 and 38 tables. To create all the plots in the other code files below this you need this table.

### 5. mpra_DHS_grid_search.Rmd
This code contains the grid search which is used to estimate the cut-offs for high activity variants (p-CREs) and allelic-specific expression variants (emVars). This code will analyse the enrichment for DHS sites for high activity variants and create Supp. figure 2 c & d and supp. tables 32 & 33
If you're doing your own MPRA use this to calibrate the variant category filter aka. the mpra_sig column (made in mpra_big_table.Rmd). My code will have the variant category filters for Ho et al., but you can calculate your own!
### 6. UK_biobank_finemapping_enrichment.Rmd
This code calculates the enrichments for MPRA emVars for variants fine-mapped in UK BioBank (UKBB) fine-mapping data (Supp. figure 5.). The steps to this analysis include:
- Import the UKBB data and merge with MPRA data. 
- Create a table with MPRA variants and the UKBB data for the paper.
- Create the enrichment plots for MPRA emVars in UKBB data. 

### 7. mpra_plots.Rmd
This code creates plots for MPRA analysis. Many plots are based on the previously published Jurkat analysis (from Mouri, K., Guo, M.H., de Boer, C.G. et al. Prioritization of autoimmune disease-associated genetic variants that perturb regulatory element activity in T cells. Nat Genet 54, 603–612 (2022).) as well as some plots of our own. The analyses include Figure 1 b-f, supplementary figures 3 & 4. There will also be some data generated in this code that will end up as supplementary tables 3, 4, 8, and 34. 

Plots include:
- Comparisons between the Jurkat and primary T-cell data using venn diagrams, tables and plotting allelic bias
- Enrichments for epigenetic data including DHS, ATAC-seq, caQTL, histone marks, etc.
- Enrichment for MPRA emVars for PICS fine-mapping variants
- An initial motifbreakR analysis simply describing the enrichment for transcription factor binding sites)

### 8. motifbeakr_enrichment_analysis.Rmd
This code is used to calculate the TF motif enrichments for MPRA variants and create the relevant plots. (Figure 2, Supp. figure 6). This code contains the transcription factor binding analysis of the MPRA data. The steps to this analysis include:
- Create a Granges bed file of the variants mpra tested in the MPRA
- Run motifbreakR function to generate TF binding data on the MPRA variants
- Merge motifbreakr and MPRA data
- Run t-test of primary T cell MPRA expression of variants which do and do not bind to each tf 
- Repeat step 4 with jurkat mpra expression data
- Run t-test analysis for variants fine mapped to each disease
- Merge the primary tcell and unstimulated jurkat data
- Compare the results of jurkat and primary T cells

### 9. mpra_supplementary_tables
Finally using all the tables which are relevant to the MPRA data created so far, I put the tables into the final format which appears in the paper's supplementary tables (not including anything having to do with CRISPR or V2G).

# Session info

Here is the session info for my R session when I ran all of this code: 

R version 4.3.1 (2023-06-16)
Platform: aarch64-apple-darwin20 (64-bit)
Running under: macOS 15.2

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib 
LAPACK: /Library/Frameworks/R.framework/Versions/4.3-arm64/Resources/lib/libRlapack.dylib;  LAPACK version 3.11.0

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

time zone: US/Pacific
tzcode source: internal

attached base packages:
[1] grid      stats4    stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] biomaRt_2.58.0                           ggvenn_0.1.10                            gt_0.11.0                               
 [4] pegas_1.3                                ape_5.8                                  R.utils_2.12.3                          
 [7] R.oo_1.26.0                              R.methodsS3_1.8.2                        BSgenome.Hsapiens.UCSC.hg19_1.4.3       
[10] SNPlocs.Hsapiens.dbSNP144.GRCh37_0.99.20 TxDb.Hsapiens.UCSC.hg19.knownGene_3.2.2  GenomicFeatures_1.54.1                  
[13] AnnotationDbi_1.62.2                     Biobase_2.60.0                           filelock_1.0.3                          
[16] reshape2_1.4.4                           clusterProfiler_4.8.2                    ChIPseeker_1.36.0                       
[19] pheatmap_1.0.12                          gridExtra_2.3                            ggdendro_0.2.0                          
[22] BSgenome.Hsapiens.UCSC.hg38_1.4.5        motifbreakR_2.14.2                       MotifDb_1.44.0                          
[25] rjson_0.2.21                             dendextend_1.17.1                        cluster_2.1.6                           
[28] rsample_1.2.1                            SNPlocs.Hsapiens.dbSNP155.GRCh38_0.99.24 BSgenome_1.70.1                         
[31] rtracklayer_1.62.0                       BiocIO_1.12.0                            Biostrings_2.68.1                       
[34] XVector_0.40.0                           ggrepel_0.9.5                            pals_1.9                                
[37] viridis_0.6.5                            viridisLite_0.4.2                        GenomicRanges_1.52.1                    
[40] GenomeInfoDb_1.36.4                      IRanges_2.34.1                           S4Vectors_0.38.2                        
[43] BiocGenerics_0.46.0                      rmarkdown_2.27                           RColorBrewer_1.1-3                      
[46] data.table_1.15.4                        readxl_1.4.3                             lubridate_1.9.3                         
[49] forcats_1.0.0                            stringr_1.5.1                            dplyr_1.1.4                             
[52] purrr_1.0.2                              readr_2.1.5                              tidyr_1.3.1                             
[55] tibble_3.2.1                             ggplot2_3.5.1                            tidyverse_2.0.0                         
[58] openxlsx_4.2.7.1                        

loaded via a namespace (and not attached):
  [1] fs_1.6.4                    ProtGenerics_1.34.0         matrixStats_1.3.0           bitops_1.0-8               
  [5] enrichplot_1.20.3           DirichletMultinomial_1.44.0 TFBSTools_1.38.0            HDO.db_0.99.1              
  [9] httr_1.4.7                  tools_4.3.1                 backports_1.5.0             utf8_1.2.4                 
 [13] R6_2.5.1                    lazyeval_0.2.2              Gviz_1.46.1                 withr_3.0.1                
 [17] prettyunits_1.2.0           cli_3.6.3                   scatterpie_0.2.3            Rsamtools_2.18.0           
 [21] yulab.utils_0.1.5           gson_0.1.0                  foreign_0.8-87              DOSE_3.26.2                
 [25] dichromat_2.0-0.1           parallelly_1.38.0           plotrix_3.8-4               maps_3.4.2.1               
 [29] rstudioapi_0.16.0           RSQLite_2.3.7               generics_0.1.3              gridGraphics_0.5-1         
 [33] gtools_3.9.5                zip_2.3.1                   GO.db_3.17.0                Matrix_1.6-5               
 [37] interp_1.1-6                fansi_1.0.6                 abind_1.4-5                 lifecycle_1.0.4            
 [41] yaml_2.3.10                 SummarizedExperiment_1.30.2 gplots_3.1.3.1              qvalue_2.32.0              
 [45] SparseArray_1.2.3           BiocFileCache_2.10.1        blob_1.2.4                  crayon_1.5.3               
 [49] lattice_0.22-6              cowplot_1.1.3               annotate_1.78.0             KEGGREST_1.40.1            
 [53] mapproj_1.2.11              pillar_1.9.0                knitr_1.48                  fgsea_1.26.0               
 [57] boot_1.3-30                 codetools_0.2-20            fastmatch_1.1-4             glue_1.7.0                 
 [61] downloader_0.4              ggfun_0.1.5                 treeio_1.24.3               vctrs_0.6.5                
 [65] png_0.1-8                   cellranger_1.1.0            gtable_0.3.5                poweRlaw_0.80.0            
 [69] cachem_1.1.0                xfun_0.46                   S4Arrays_1.2.0              tidygraph_1.3.1            
 [73] pracma_2.4.4                nlme_3.1-166                ggtree_3.8.2                bit64_4.0.5                
 [77] progress_1.2.3              KernSmooth_2.23-24          rpart_4.1.23                splitstackshape_1.4.8      
 [81] colorspace_2.1-1            seqLogo_1.68.0              DBI_1.2.3                   Hmisc_5.1-3                
 [85] nnet_7.3-19                 ade4_1.7-22                 motifStack_1.44.1           tidyselect_1.2.1           
 [89] bit_4.0.5                   compiler_4.3.1              curl_5.2.1                  htmlTable_2.4.3            
 [93] xml2_1.3.6                  DelayedArray_0.26.7         shadowtext_0.1.4            checkmate_2.3.2            
 [97] scales_1.3.0                caTools_1.18.2              rappdirs_0.3.3              digest_0.6.36              
[101] htmltools_0.5.8.1           pkgconfig_2.0.3             jpeg_0.1-10                 base64enc_0.1-3            
[105] MatrixGenerics_1.12.3       dbplyr_2.5.0                fastmap_1.2.0               ensembldb_2.26.0           
[109] rlang_1.1.4                 htmlwidgets_1.6.4           farver_2.1.2                jsonlite_1.8.8             
[113] BiocParallel_1.34.2         GOSemSim_2.26.1             VariantAnnotation_1.48.1    RCurl_1.98-1.16            
[117] magrittr_2.0.3              Formula_1.2-5               GenomeInfoDbData_1.2.10     ggplotify_0.1.2            
[121] patchwork_1.2.0             munsell_0.5.1               Rcpp_1.0.13                 furrr_0.3.1                
[125] stringi_1.8.4               ggraph_2.2.1                zlibbioc_1.46.0             MASS_7.3-60.0.1            
[129] plyr_1.8.9                  parallel_4.3.1              listenv_0.9.1               deldir_2.0-4               
[133] CNEr_1.36.0                 splines_4.3.1               graphlayouts_1.1.1          hms_1.1.3                  
[137] igraph_2.0.3                TFMPvalue_0.0.9             XML_3.99-0.17               evaluate_0.24.0            
[141] latticeExtra_0.6-30         biovizBase_1.50.0           tzdb_0.4.0                  tweenr_2.0.3               
[145] polyclip_1.10-7             future_1.34.0               ggforce_0.4.2               xtable_1.8-4               
[149] restfulr_0.0.15             AnnotationFilter_1.26.0     tidytree_0.4.6              aplot_0.2.3                
[153] memoise_2.0.1               GenomicAlignments_1.38.0    timechange_0.3.0            globals_0.16.3   








