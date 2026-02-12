# Epigenetic Profiling: Methylation Landscape Analysis

## 🧬 Project Overview
This repository contains a bioinformatics pipeline for processing **Whole Genome Bisulfite Sequencing (WGBS)** data. 
It focuses on identifying **Differentially Methylated Regions (DMRs)** and analyzing the global methylation shift between Wild Type and Epigenetic Mutants.

This workflow replicates standard high-resolution epigenetic analysis pipelines, specifically utilizing count-based statistical modeling to account for biological variance and sequencing depth.

## 📊 Key Results

### 1. Global Methylation Shift
![Methylation Density](figures/methylation_density.png)
*Figure 1: Distribution of Fractional Methylation levels (0 = Unmethylated, 1 = Fully Methylated). The bimodal peaks confirm high-quality methylation calling. Note the shift in the mutant lines (Red), indicating global hypomethylation.*

### 2. Differentially Methylated Regions (DMRs)
![DMR Heatmap](figures/dmr_heatmap.png)
*Figure 2: Hierarchical clustering of the top 50 most variable methylation regions. The heatmap reveals a distinct epigenetic signature separating the Control and Stress/Mutant groups.*

## 📂 Data & Output
- **Full Results:** [Significant_DMRs.csv](figures/Significant_DMRs.csv) (Contains LogFC, methylation differences, and P-values for all significant genomic regions).

## 🛠️ Methodology
### 1. Data Pre-processing & Alignment
* **Quality Control:** Raw fastq reads were trimmed using `Trim Galore!` to remove adapter sequences and low-quality bases.
* **Alignment:** Bisulfite-converted reads were mapped to the *Arabidopsis thaliana* reference genome (TAIR10) using **Bismark** (v0.22.3).
* **Methylation Calling:** Cytosine methylation states were extracted for all three sequence contexts characteristic of plants: **CpG, CHG, and CHH**.

### 2. Differential Methylation Analysis (R/Bioconductor)
* **Package:** Analysis was performed using **methylKit** and **DSS** (Dispersion Shrinkage for Sequencing data), which are optimized for count-based WGBS data.
* **Filtering:** To ensure high confidence, bases with low coverage (<10x) or extremely high coverage (>99.9th percentile, indicating PCR bias) were discarded.
* **DMR Identification:** Differentially Methylated Regions (DMRs) were identified using the DSS `callDMR` function, applying a smoothing filter to account for spatial correlation of methylation sites.
* **Annotation:** Significant DMRs were annotated to genomic features (Promoters, Exons, Introns, Transposable Elements) using `genomation`.

## 👨‍💻 Author
**Anant Kaushal**
*Computational Epigenetics Researcher*
