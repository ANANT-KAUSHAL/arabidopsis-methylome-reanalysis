Epigenetic Profiling: Methylation Landscape Analysis (WGBS)
 Project Overview

This repository contains a reproducible bioinformatics pipeline for re-analysis of Whole Genome Bisulfite Sequencing (WGBS) data in Arabidopsis thaliana. The workflow identifies Differentially Methylated Regions (DMRs) and characterizes genome-wide methylation shifts between Wild Type (WT) and Epigenetic Mutants.

The statistical framework integrates DSS (Dispersion Shrinkage for Sequencing data) using Beta-binomial modeling with spatial smoothing to ensure biologically robust DMR detection.
data/        # Raw coverage files (excluded)
figures/     # Generated plots
results/     # Significant_DMRs.csv
scripts/     # WGBS_Analysis.R
Methodology

Pre-processing

Trim Galore! – Adapter trimming

Bismark (v0.22.3) – Alignment to TAIR10

Cytosine methylation extraction (CpG, CHG, CHH)

Statistical Analysis

Coverage filtering (min 10x)

PCR bias filtering (>99.9 percentile)

Differential methylation testing via DSS

Spatial smoothing for regional DMR detection

Key Results
1. Global Methylation Landscape

Distribution of fractional methylation levels (0–1 scale).
Bimodal peaks validate plant methylome quality. Mutant samples show a global hypomethylation shift compared to WT.

2️. Differentially Methylated Regions (DMRs)

Hierarchical clustering of top 50 variable regions reveals distinct epigenetic separation between WT and Mutant lines.

Output

results/Significant_DMRs.csv
Contains:

Chromosome

Start

End

LogFC (Methylation difference)

FDR-adjusted q-values
scripts/WGBS_Analysis.R
Required packages:

methylKit

DSS

genomation

ggplot2

👨‍💻 Author

Anant Kaushal
Computational Epigenetics | Plant Genomics | Epigenomic Regulation

💻 Reproducibility

Main script:
