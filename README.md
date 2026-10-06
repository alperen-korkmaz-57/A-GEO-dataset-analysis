# Influenza A exposure in plasmacytoid dendritic cells (GSE68849)

A learning project on differential expression analysis of a public microarray dataset in R.

## Overview

This project analyses the public GEO dataset GSE68849 (10 samples, Illumina HumanHT-12 V4.0 expression beadchip, GPL10558). The data come from primary human plasmacytoid dendritic cells (pDCs) from five donors, either exposed to influenza A for 8 hours ex vivo or left as controls (5 vs 5; the samples are paired by donor). Differentially expressed genes are identified with limma in R.

## Workflow & Methodology

1. **Data retrieval:** `ExpressionSet` object downloaded with `GEOquery`.
2. **Preprocessing:** The submitters quantile-normalised the data with Illumina GenomeStudio (as stated in the GEO record). Expression values were used on the log2 scale (log2-transformed in R if they were on a raw scale). Probes mapping to the same gene were averaged.
3. **Quality control:** Boxplots of expression per sample and PCA.
4. **Differential expression analysis:** Linear model with `limma` (empirical Bayes), including donor as a blocking factor. P-values were adjusted with the Benjamini-Hochberg method.
5. **Visualisation:** Volcano plot (`EnhancedVolcano`) and summary tables (`knitr`).

## Results

Using thresholds of adjusted p < 0.05 and |log2 fold change| > 1, 202 genes were upregulated and 137 downregulated in influenza A-exposed pDCs compared with controls (3,413 genes had adjusted p < 0.05 regardless of fold change). The model accounted for pairing by donor.

Top 10 genes by adjusted p-value:

| Gene    | log2 fold change | Adjusted p-value |
|---------|------------------|------------------|
| IFNA7   | 7.19             | 2.3e-11          |
| IFNA2   | 7.36             | 2.3e-11          |
| IFNA21  | 6.99             | 2.3e-11          |
| IFNA10  | 7.39             | 4.1e-11          |
| IFNA14  | 6.69             | 9.9e-11          |
| IFNW1   | 6.28             | 1.7e-10          |
| IFNA5   | 6.77             | 2.1e-10          |
| IFNA16  | 7.21             | 3.5e-10          |
| IFNA4   | 3.42             | 1.2e-9           |
| RNF144B | 3.36             | 1.3e-9           |

Nine of the ten most significant genes are type I interferon genes (IFNA family and IFNW1). Plasmacytoid dendritic cells are major producers of type I interferons, so this agrees with known biology and works as a sanity check. It does not by itself validate the analysis.

<img width="1200" height="960" alt="image" src="https://github.com/user-attachments/assets/cf61274d-f8e4-482b-bcbc-a2102cbe262e" />

## Limitations

- Small sample size (5 vs 5).
- In the PCA, control and influenza-exposed samples separate only partially, which may reflect donor-to-donor variability.
- IFNA genes are very similar in sequence, so probes may cross-hybridise. The IFNA hits should not be read as independent evidence for each gene.
- Probes of the same gene were averaged, which is a simplification.
- Only differential expression was performed; no pathway or GO enrichment yet.

## How to run

Install the required packages in R:

```r
install.packages(c("tidyverse", "knitr"))
BiocManager::install(c("GEOquery", "limma", "Biobase", "EnhancedVolcano"))
```

Open `Influenza_A_analysis.qmd` in RStudio and render it with Quarto. The data are downloaded automatically from GEO, so an internet connection is needed.

**Alperen Korkmaz**  
*Undergraduate Student | BSc Biology , Gazi University*

I am learning bioinformatics by working through datasets in R and on the Linux command line.

This repository is a learning project on differential expression analysis of a
public GEO dataset. See "Limitations" for what is not covered yet. Feedback is
welcome.

**Let's Connect:**
- **Email:** [alperen57korkmaz@gmail.com]
- **LinkedIn:** [https://www.linkedin.com/in/alperen-korkmaz-ba4b32322/]
- **Rendered report:** [https://alperen-korkmaz-57.github.io/A-GEO-dataset-analysis/]
