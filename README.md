# A-GEO-dataset-analysis.
A project I undertook to learn R and bioinformatics.
# Transcriptomic Analysis of Influenza Infection (GSE68849)
This repository contains the bioinformatic workflow for analyzing differential gene expression in Influenza-treated human samples using Illumina Microarray data.

## Overview
This project analyses the public GEO dataset GSE68849 (10 samples, Illumina
HumanHT-12 V4.0 expression beadchip, GPL10558). The data come from primary
human plasmacytoid dendritic cells (pDCs) from donors, either exposed to
influenza A for 8 hours ex vivo (5 samples) or left as controls (5 samples).
Differentially expressed genes are identified with limma in R.

## Preprocessing:
The submitters quantile-normalised the data with Illumina
GenomeStudio (as stated in the GEO record). Expression values were
[log2-transformed in R / used as provided]. Sample information was matched
to the expression matrix.

## Limitations:
- Small sample size (5 vs 5).
   
## Workflow & Methodology
1. **Data Retrieval:** Programmatic fetching of `ExpressionSet` objects via `GEOquery`.
2. **Preprocessing:** Variance stabilization via Log2 transformation and phenotype-expression matrix harmonization.
3. **Differential Expression Analysis:** Linear modeling using the `limma` package (Empirical Bayes method).
4. **Visualization:** Volcano plots (`EnhancedVolcano`) and styled summary tables (`kableExtra`).

## Prerequisites
To reproduce this analysis, you will need R and the following packages:
- `GEOquery`, `limma` (Bioconductor)
- `dplyr`, `tibble`
- `EnhancedVolcano`, `kableExtra`

This is the result table of the project. 
<img width="1200" height="960" alt="Influenza A Gene Expression Change" src="https://github.com/user-attachments/assets/eaf39bb3-bb5b-49e0-b5c5-5f412a2ea0a9" />
Result shows the increase of the IFNA family. IFNA gene family is produces potent antiviral and immunomodulatory proteins that body cells secrete in response to viral infections, cancer, and immune system signals. Here the samples has Influenza A virus. This is explains the accuracy of our table.

About the Author

**Alperen Korkmaz**  
*Undergraduate Student | BSc Biology (4rd Year), Gazi University*

I am a Biology undergraduate student with a strong focus on bioinformatics, computational biology, and data science. I am passionate about bridging the gap between molecular biology and computational solutions, specifically in transcriptomic data analysis, variant calling workflows, and evolutionary genetics. I actively build analytical pipelines using R and Linux environments.

This repository serves as a portfolio piece demonstrating my proficiency in processing and visualizing high-throughput genomic data. 

**Let's Connect:**
- **Email:** [alperen57korkmaz@gmail.com]
- **LinkedIn:** [https://www.linkedin.com/in/alperen-korkmaz-ba4b32322/]
- **Project Report:** [https://alperen-korkmaz-57.github.io/A-GEO-dataset-analysis./]
