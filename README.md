# SILAC-Based Serum Source Attribution and EV-PC Protein Classification

This repository contains the computational pipeline for quantifying, classifying, and attributing protein sources in extracellular vesicle protein corona (EV-PC) studies using SILAC (Stable Isotope Labeling by Amino Acids in Cell Culture) mass spectrometry data.

---

## Overview

Extracellular vesicles (EVs) isolated from serum-containing media often adsorb background serum proteins, forming a "protein corona" (PC). This pipeline addresses the challenge of distinguishing **producer-cell-derived EV proteins** from **serum-acquired protein corona components**.

---

## Example

We use Heavy/Light isotope-based SILAC proteomic data from extracellular vesicle (EV) isolation experiments as example datasets.

[Using Heavy/Light Isotope-Based Analysis to Evaluate Serum Source Attribution and EV-PC Protein Classification](https://htmlpreview.github.io/?https://github.com/xuelixu90/SILAC-SAPC/blob/main/code/Heavy_Light-Isotope-Based_Serum_Source_Analysis_1.html)

> **Note:** Click the link above to view the HTML report in your web browser. The report contains sample metadata, protein classification results, summary tables, top high-confidence serum-derived protein candidates, and static visualizations. Detailed results are exported as CSV files.

---

## Key Features & Report Outputs

- **SILAC-based source attribution**: Uses Heavy/Light intensity measurements to estimate baseline Light fractions in the `UCEV` reference group and evaluate serum-associated protein signals in each target group.
- **Replicate-aware protein classification**: Classifies proteins according to valid Heavy/Light pairs, Light-dominant signals, unique peptide counts, replicate support, background variability, and serum-fraction estimates.
- **Multiple comparison analysis**: Compares `DGEVPC_B`, `DGEVPC_C`, and `UCEVPC` separately against the `UCEV` reference group.
- **Protein annotation retention**: Preserves `Protein IDs`, `Majority protein IDs`, `Protein names`, and `Gene names` in the generated results.
- **CSV result export**: Exports complete protein-level results, primary serum-derived protein lists, merged results across comparisons, classification summaries, and sample metadata.
- **HTML report generation**: Produces an HTML report containing sample metadata, classification summary tables, top high-confidence protein candidate tables, and static `ggplot2` visualizations.

---

## Protein Classification Categories

The workflow automatically classifies detected proteins into the following categories:

- **Case 1 (High-peptide paired quantitation)**: Valid Heavy/Light pairs are present in at least two reference and target replicates, with at least 2 unique peptides in the required number of target replicates.
- **Case 2 (Single-peptide paired candidate)**: Valid Heavy/Light pairs are present in at least two reference and target replicates, with single-peptide support in the target group.
- **Case 3 (Acquired-only Level 1)**: Protein is absent in the reference control and shows a Light-dominant signal in at least two target replicates with high-peptide support.
- **Case 4 (Acquired-only Level 2)**: Protein is absent in the reference control and shows a Light-dominant signal in at least two target replicates with single-peptide support.

---

## Requirements & Installation

Install the necessary R dependencies before rendering:

```r
install.packages(c(
  "readxl",
  "dplyr",
  "purrr",
  "tibble",
  "knitr",
  "ggplot2"
))
