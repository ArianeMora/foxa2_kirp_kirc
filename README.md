# Data and code to test whether FOXA2 is changed in KIRP patients with low FH

## Datasets

RNA count data were downloaded from TCGA (https://www.cancer.gov/about-nci/organization/ccg/research/structural-genomics/tcga)
using scidat (https://github.com/ArianeMora/scidat) for patients with kidney cancers (rna_df.csv in data folder.)

## Processing

The kidney cancer patient count data were split into KIRC and KIRP, and only the tumour data was used for this analysis, 
see notebook FOXA2.ipynb in the code folder. Samples were split by their expression of FH in their tumour samples, 
with several annotations used to separate patients for completeness:  

1. Low-High: Comparing the bottom 25% (< Q1) of patients by FH vs “high” FH (i.e. top 25%, > Q3): p.adj 0.00004  
2. Low-Normal: Comparing the bottom 25% of patients by FH to the patients with “normal” range FH (between Q1 and Q3): p.adj 0.053   
3. Outlier-High: Comparing outlier FH to “high” (i.e. top 25%): p.adj 0.067    
4. Outlier-Normal: Comparing the outlier FH (Q1 – 1.5*IQR) to all “normal” FH patients: p.adj 0.169


We did the same for KIRC patients – we don’t see FOXA2 as expected

1. Comparing the bottom 25% of patients by FH vs the top 25% of patients with FH: 0.14   
2. Comparing the bottom 25% of patients by FH to the patients with “normal” range FH:  0.25  
3. Comparing the outlier FH to all “normal” FH patients: 0.31  
4. Comparing outlier FH to “high” (i.e. top 25%): 0.32  

Each of these groups were used to also perform DE analysis between the two groups, see respective RMD files in code for details.

### References

If you use this work please cite TCGA:
```
Creighton, C. J., Morgan, M., Gunaratne, P. H., Wheeler, D. A., Gibbs, R. A., Gordon Robertson, A., Chu, A., Beroukhim, R., Cibulskis, K., Signoretti, S., Vandin Hsin-Ta Wu, F., Raphael, B. J., Verhaak, R. G. W., Tamboli, P., Torres-Garcia, W., Akbani, R., Weinstein, J. N., Reuter, V., Hsieh, J. J., … University of North Carolina at Chapel Hill. (2013). Comprehensive molecular characterization of clear cell renal cell carcinoma. Nature, 499(7456), Article 7456. https://doi.org/10.1038/nature12222
```
