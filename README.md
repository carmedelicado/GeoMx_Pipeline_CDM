# GeoMx_Pipeline_CDM

A robust spatial transcriptomics pipeline for GeoMx DSP data integration, leveraging GeoMxTools for data orchestration and standR for advanced preprocessing (QC, filtration, normalization, and batch effect correction) and downstream analysis (DE Analysis, GSEA, cell-type deconvolution, and Differential Proportion Analysis).

# GeoMx DSP Spatial Transcriptomics Pipeline

**Author:** Carme Delicado Mercader
**Date:** 11-Feb-2026 
**Project:** Implementation of a hybrid bioinformatics pipeline for GeoMx™ DSP data analysis.

Welcome to my Master's thesis repository. This project was developed as to share de pipeline developed for the final thesis at the Master’s in Bioinformatics of UNIR.

University: Universidad Internacional de la Rioja
**Developed at:** Statistics and Bioinformatics Unit (UEB) in Vall d'Hebron Research Institute (VHIR)
**Tutor:** Mireia Ferrer Almirall (UEB) and Maria Belén LLedo Bosch (UNIR)
**Main Technologies:** NanoString GeoMx™ DSP, R, standR, GeoMxTools, Rmarkdown

This repository provides a modular and reproducible pipeline designed to transform raw GeoMx™ Digital Spatial Profiling (DSP) data into meaningful biological insights. 

While the workflow is versatile and applicable to any GeoMx transcriptomics study, it is implemented here using a Tumor Microenvironment (TME) dataset as a case study, focusing on immune infiltration and therapeutic response (e.g., Nivolumab).

## Pipeline Structure

The proposed pipeline consists of two main phases.

  - Preprocessing: data loading, QC and filtering, dimensional reduction, normalization and batch effect correction.
  - Downstream Analysis: DE Analysis, GSEA, cell-type deconvolution, and Differential Proportion Analysis

These have been coded in a unique RMarkdown document.


Methodology & Highlights

Hybrid Orchestration: Seamless transition from NanoStringGeoMxSet to SpatialExperiment for maximum interoperability.Advanced Normalization: Implementation of TMM (Trimmed Mean of M-values) to stabilize variance across heterogeneous AOIs.In-depth Deconvolution: Use of the safeTME matrix to specifically isolate immune and stromal signals, bypassing common biases found in cancerous cells.Proportion Testing: Statistical validation of cell-type shifts using the Arc-sine (asin) transformation to identify "ineffective infiltration" patterns.RequirementsThe pipeline is developed in R (v4.3+). Key dependencies include:GeoMxTools & NanoStringNCToolsstandR (for robust preprocessing)SpatialDecon (for cell typing)speckle (for propeller proportion testing)limma & edgeR (for statistical modeling)ggplot2 & pheatmap (for visualization)Usage1. Reproduce this projectClone the repository: git clone https://github.com/tu-usuario/GeoMx_TME_Pipeline.gitInput Data: Place your .dcc, .pkc, and Annotation.xlsx files in the data/ folder.Run the analysis: Execute the RMarkdown files in the analysis/ folder sequentially.2. Custom Data AnalysisThe pipeline is parameterized to handle different ROI selection strategies (e.g., Iba1+ for myeloid, Sox2+ for tumor). To adapt it to your data, update the design_matrix in the 3.0_batch_correction.Rmd file.AbstractThis work implements a specialized bioinformatics pipeline for GeoMx™ DSP data to evaluate the immune-tumor interface. By leveraging the standR framework, the pipeline achieves superior batch correction and normalization compared to standard workflows. Applying this to a cohort of primary and recurrent tumors, we identified a state of ineffective immune infiltration: despite high lymphocyte presence in tumor niches (Sox2+), no significant transcriptomic shifts were observed post-treatment, suggesting a suppressed immune state.LicenseCode: MIT LicenseContent: CC BY-NC-SA 4.0ContactLidia Getino-Álvarez [Tu LinkedIn / Email Profesional]
