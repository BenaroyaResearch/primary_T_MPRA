
Here are the motifbreakR results for the MPRA library. You need to add the RNA-seq data by downloading from online.

# Download RNA-seq data 

Import dice gene expression data for primary CD4 tcells from this site:

https://dice-database.org/downloads

Download this file:

CD4_NAIVE_TPM.csv

Download the jurkat data from this site:

https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE145453

Resting Jurkat GSM4318505, GSM4318506

Stimulated Jurkat GSM4318507, GSM4318508

Stimulated + chemokine Jurkat GSM4318509, GSM4318510

Download this file:

GSE145453_norm_counts_TPM_GRCh38.p13_NCBI.tsv

The annotate file in the GEO data set Human.GRCh38.p13.annot.tsv did not have that many genes so I am going to use an online tool to convert the gene IDs to genes

https://www.syngoportal.org/convert

This takes a long time but the results will be worth it. Use NCBI entrez Gene 
