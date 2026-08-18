# Heavy/Light Isotope-Based Serum Source Analysis & EV-PC Protein Classification

This repository contains the computational pipeline for quantifying, classifying, and attributing protein sources in extracellular vesicle protein corona (EV–PC) studies using SILAC (Stable Isotope Labeling by Amino Acids in Cell Culture) mass spectrometry data.

---

## 📌 Overview

Extracellular vesicles (EVs) isolated from serum-containing media often adsorb background serum proteins, forming a "protein corona" (PC). This pipeline addresses the critical challenge of distinguishing **producer-cell-derived EV proteins** from **serum-acquired protein corona components**.

---

## 🔗 Example

We use Heavy/Light isotope-based SILAC proteomic data from extracellular vesicle (EV) isolation experiments as example datasets.

[Using Heavy/Light Isotope-Based Analysis to evaluate serum source attribution and EV-PC protein classification](https://htmlpreview.github.io/?https://github.com/xuelixu90/HL_Serum_Source_A/blob/main/Heavy_Light-Isotope-Based_Serum_Source_Analysis.html)

> **Note:** Click the link above to open and explore the interactive report directly in your web browser. It features interactive Plotly charts, dynamic searchable tables, and clickable UniProt accession links.

---

## ✨ Key Features & Interactive Visualizations

- **🔗 UniProt Integration**: Automatically links `Majority_protein_IDs` to the UniProt database (`https://www.uniprot.org/uniprotkb/[ID]`).
- **📊 Interactive Tables (`DT`)**: Searchable, paginated tables supporting one-click exports to **CSV**, **Excel**, or **Clipboard**.
- **📈 Dynamic Visualizations (`plotly`)**: Interactive charts with hover tooltips, pan, and zoom capabilities.
- **🌐 Offline Access**: Generates self-contained HTML reports for sharing and offline browsing.

---

## 🔬 Protein Classification Categories

The workflow automatically classifies detected proteins into the following categories:
- **Case 1 (High-peptide paired quantitation)**: Valid L/H pairs present in reference and target groups with $\ge 2$ unique peptides.
- **Case 2 (Single-peptide paired candidate)**: Valid L/H pairs present with 1 unique peptide.
- **Case 3 (Acquired-only Level 1)**: Protein absent in reference control, showing Light-dominant signal in target group with $\ge 2$ unique peptides.
- **Case 4 (Acquired-only Level 2)**: Protein absent in reference control, showing Light-dominant signal in target group with 1 unique peptide.

---

## ⚙️ Requirements & Installation

Install the necessary R dependencies before rendering:

```R
install.packages(c("readxl", "dplyr", "purrr", "tibble", "knitr", "ggplot2", "DT", "plotly", "htmlwidgets", "htmltools"))
