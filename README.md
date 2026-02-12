Epigenetic Profiling: Methylation Landscape Analysis (WGBS)
Project Overview

This repository contains a reproducible bioinformatics pipeline for the re-analysis of Whole Genome Bisulfite Sequencing (WGBS) data. The project focuses on dissecting the epigenetic landscape of Arabidopsis thaliana, specifically identifying Differentially Methylated Regions (DMRs) and analyzing global methylation shifts between Wild Type (WT) and Epigenetic Mutants.

Unlike standard pipelines that rely solely on fractional methylation differences, this workflow integrates Dispersion Shrinkage for Sequencing data (DSS). This statistical framework uses Beta-binomial models with spatial smoothing to account for biological variance and sequencing depth, ensuring robust detection of epigenetic regulatory events.

📂 Repository Structure

data/
→ Raw coverage files and Bismark reports (excluded)

figures/
→ methylation_density.png
→ dmr_heatmap.png

results/
→ Significant_DMRs.csv

scripts/
→ WGBS_Analysis.R

README.md
LICENSE

🔬 Methodology & Workflow
1️⃣ Data Pre-processing

• Trimming – Trim Galore! (Adapter removal & quality control)
• Alignment – Bismark (v0.22.3) mapping to TAIR10 reference genome
• Methylation Calling – Extraction of cytosine methylation in CpG, CHG, and CHH contexts

2️⃣ Statistical Analysis (R / Bioconductor)

• Quality Control – Dynamic filtering of PCR duplicates (>99.9th percentile) and low-coverage bases (<10x)
• Modeling – methylKit and DSS packages used for differential methylation testing
• Smoothing – Spatial correlation filters applied to detect regional methylation changes rather than isolated loci

📊 Key Results
1️⃣ Global Methylation Shift

Distribution of fractional methylation levels (0 = unmethylated, 1 = fully methylated).
The bimodal peaks characteristic of plant genomes confirm high-quality methylation calling.
A distinct hypomethylation shift is observed in mutant lines compared to Wild Type.

2️⃣ Differentially Methylated Regions (DMRs)

Hierarchical clustering of the top 50 most variable methylation regions reveals a distinct epigenetic signature separating Control and Mutant groups.

🧬 Data Availability

Final Output: Significant_DMRs.csv

Contains:
• Chromosome
• Start
• End
• Methylation Difference (LogFC)
• FDR-corrected P-values (q-values)

💻 Usage

To replicate the analysis:

Install required R packages

Load coverage files

Perform filtering

Run DSS-based differential methylation testing

Export significant DMRs

📦 Dependencies

• R (>= 4.0.0)
• methylKit
• DSS
• genomation
• ggplot2

👨‍💻 Author

Anant Kaushal
Computational Epigenetics Researcher
Specializing in Plant Genomics & Transcriptional Regulation
© 2026 Anant Kaushal. Licensed under MIT.
