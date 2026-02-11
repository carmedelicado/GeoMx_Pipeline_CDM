# GeoMx_Pipeline_CDM

A robust spatial transcriptomics pipeline for GeoMx DSP data integration, leveraging GeoMxTools for data orchestration and standR for advanced preprocessing (QC, filtration, normalization, and batch effect correction) and downstream analysis (DE Analysis, GSEA, cell-type deconvolution, and Differential Proportion Analysis).

## Table of Contents

1. [Pipeline Structure](#pipeline-structure)
2. [Development Framework](#development-framework)
3. [Dataset Description](#dataset-description)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Output](#output)
7. [Citation](#citation)
8. [License](#license)

## GeoMx DSP Spatial Transcriptomics Pipeline

**Author:** Carme Delicado Mercader

**Date:** 11-Feb-2026 

**Project:** Implementation of a bioinformatics pipeline for GeoMx™ DSP data analysis.

Welcome to my Master's thesis repository. This project was developed with the aim of sharing the pipeline and all the documentation involved in the final thesis for the Master's in Bioinformatics at UNIR.

**University:** Universidad Internacional de la Rioja

**Developed at:** Statistics and Bioinformatics Unit (UEB) in Vall d'Hebron Research Institute (VHIR)

**Tutor:** Mireia Ferrer Almirall (UEB) and Maria Belén LLedo Bosch (UNIR)

**Main Technologies:** NanoString GeoMx™ DSP, R, standR, GeoMxTools, Rmarkdown

This repository provides a modular and reproducible pipeline designed to transform raw GeoMx™ Digital Spatial Profiling (DSP) data into meaningful biological insights. 

While the workflow is versatile and applicable to any GeoMx transcriptomics study, it is implemented here using a Tumor Microenvironment (TME) dataset as a case study, focusing on immune infiltration and therapeutic response.


## Pipeline Structure

The proposed pipeline consists of two main phases:

  - Preprocessing: data loading, quality control (QC) and filtering, dimensionality reduction, normalization, and batch effect correction.

  - Downstream analysis: differential expression (DE) analysis, gene set enrichment analysis (GSEA), cell-type deconvolution, and differential proportion analysis.

All steps are implemented in a single R Markdown document named PIPELINE.Rmd.


## Development Framework

The development of this pipeline is based on two established tools for the analysis of GeoMx DSP data: GeoMxTools and StandR.

GeoMxTools, the official pipeline developed by NanoString, is used for data loading and initial visualization. This package operates primarily with the NanoStringGeoMxSet object, which is specifically designed to handle GeoMx DSP data structures.

Subsequently, the remaining steps of the pipeline are implemented using StandR, a workflow developed in 2023 that incorporates more robust and updated statistical methodologies. StandR operates on the SpatialExperiment object class, which facilitates interoperability with other Bioconductor packages and simplifies the integration of additional downstream analyses.

The official workflow vignettes for both tools can be found at the following links:

GeoMxTools:
https://bioconductor.org/packages/devel/workflows/vignettes/GeoMxWorkflows/inst/doc/GeomxTools_RNA-NGS_Analysis.html#8_Visualizing_DE_Genes

StandR:
https://davislaboratory.github.io/GeoMXAnalysisWorkflow/articles/GeoMXAnalysisWorkflow.html


# Dataset Description

The dataset used in this study originates from a spatial transcriptomic analysis of recurrent glioblastoma (GBM) samples generated using GeoMx™ Digital Spatial Profiling (DSP).

The cohort consists of tumor tissue samples from recurrent GBM patients, including both those treated with neoadjuvant nivolumab—an immune checkpoint inhibitor targeting PD-1—and untreated controls. Tumor regions were selected based on high densities of SOX2⁺ tumor cells and IBA1⁺ tumor-associated macrophages (TAMs), representing the two most abundant cell populations in GBM. GeoMx DSP was used to generate targeted spatial transcriptomic profiles of these segmented regions, which were subsequently filtered and processed for downstream analysis.

The deposited files include normalized and batch‑corrected expression matrices, metadata for all regions of interest (AOIs), and probe‑to‑gene mappings. Raw Digital Count Conversion (DCC) files are not included in this repository due to their large size, but they can be downloaded in Zenodo and is publicly available via DOI: https://doi.org/10.5281/zenodo.16839828

This dataset supports the findings of the associated peer-reviewed study “Spatial transcriptomic analysis reveals lack of response to PD-1 blockade in recurrent glioblastoma” published in Acta Neuropathologica (2025), DOI: https://doi.org/10.1007/s00401-025-02937-9


## Installation 

This pipeline requires R (>=4.3) and the following packages:

**Install BiocManager if not present**
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

**Core Bioconductor packages**
BiocManager::install(c(
    "GeoMxTools", "StandR", "SpatialExperiment",
    "SpatialDecon", "DESeq2", "limma", "edgeR"
))

**CRAN packages**
install.packages(c(
    "tidyverse", "dplyr", "ggplot2", "networkD3",
    "ggforce", "ggalluvial", "ggrepel", "R.utils",
    "knitr", "DT", "readxl", "writexl"
))

Load libraries in R session

## Usage

  1. Clone the repository:

git clone https://github.com/username/GeoMx_Pipeline_CDM.git


  2. Open PIPELINE.Rmd in RStudio.

  3. Follow the instructions in the R Markdown to run preprocessing and downstream analyses.

  4. Ensure that your dataset files are organized in the correct folders as described in the pipeline.

## Output

The pipeline generates:

  - QC and FIltered expression matrices
  - Normalized and batch-corrected expression matrices
  - Differential expression (DE) analysis results
  - Gene set enrichment analysis (GSEA) results
  - Cell-type deconvolution results
  - Differential proportion analysis results
  - Figures and plots summarizing the results

## Citation

If you use this pipeline or dataset, please cite:

Delicado Mercader, C. Desarrollo de un pipeline bioinformático para el análisis de datos GeoMx™ Digital Spatial Profiler. GitHub repository, available at: https://github.com/carmedelicado/GeoMx_Pipeline_CDM. Accessed on [Date].

## License

This project is licensed under the MIT License - see the LICENSE file for details.
