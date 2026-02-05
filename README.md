# Epigenetic Profiling: Methylation Landscape Analysis

## 🧬 Project Overview
This repository contains a bioinformatics pipeline for processing **Whole Genome Bisulfite Sequencing (WGBS)** data. 
It focuses on identifying **Differentially Methylated Probes (DMPs)** and analyzing the global methylation shift between Wild Type and Epigenetic Mutants.

This workflow replicates the standard analysis pipeline used in **Lister et al.**, specifically utilizing **SWAN Normalization** to correct for technical noise.

## 📊 Key Results

### 1. Global Methylation Shift
![Methylation Density](figures/methylation_density.png)
*Figure 1: Distribution of Beta values (0 = Unmethylated, 1 = Fully Methylated). The bimodal peaks confirm high-quality methylation calling. Note the shift in the mutant lines (Red), indicating global hypomethylation.*

### 2. Differentially Methylated Regions (DMRs)
![DMR Heatmap](figures/dmr_heatmap.png)
*Figure 2: Hierarchical clustering of the top 50 most variable methylation sites. The heatmap reveals a distinct epigenetic signature separating the Control and Stress/Mutant groups.*

## 📂 Data & Output
- **Full Results:** [Significant_DMPs.csv](figures/Significant_DMPs.csv) (Contains LogFC and P-values for all probes).

## 🛠️ Methodology
- **Package:** `minfi` (Bioconductor)
- **Metric:** Beta Values
- **Normalization:** SWAN (Subset-quantile Within Array Normalization)
- **Statistics:** Linear Models (`limma`) with Empirical Bayes moderation.

## 👨‍💻 Author
**Anant Kaushal**
*Computational Epigenetics Researcher*
