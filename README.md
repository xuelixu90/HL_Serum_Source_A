# SILAC-Based Proteomic Source Attribution & EV-PC Protein Classification

This repository contains the computational pipeline for quantifying, classifying, and attributing protein sources in extracellular vesicle protein corona (EV–PC) studies using SILAC (Stable Isotope Labeling by Amino Acids in Cell Culture) mass spectrometry data.

---

## 📌 Overview

Extracellular vesicles (EVs) isolated from serum-containing media often adsorb background serum proteins, forming a "protein corona" (PC). This pipeline addresses the critical challenge of distinguishing **producer-cell-derived EV proteins** from **serum-acquired protein corona components**.

---

## 🔗 Example & Interactive Tutorial

We use SILAC proteomic data from differential EV isolation methods (`DGEVPC_B`, `DGEVPC_C`, and `UCEVPC` compared against the `UCEV` reference control) as example datasets.

* **[Using SILAC Pipeline to Analyze EV-PC Proteomic Data and Protein Corona Attribution](reports/SILAC_Interactive_Dashboard.html)**

*(Note: The link above leads to a standalone, interactive HTML report featuring clickable UniProt database links, dynamic search tables, and Plotly interactive distribution plots.)*

---

## ✨ Features & HTML Visualizations

- **🔗 UniProt Integration**: Automatically turns `Majority_protein_IDs` into direct hyperlinks (`https://www.uniprot.org/uniprotkb/[ID]`).
- **📊 Interactive Tables (`DT`)**: Embedded tables with global search, column sorting, pagination, and one-click export to **CSV**, **Excel**, or **Clipboard**.
- **📈 Dynamic Visualizations (`plotly`)**: Interactive bar charts with hover tooltips and zoom functions.
- **🌐 Standalone HTML Export**: Generates self-contained HTML reports that can be shared and opened offline in any web browser.

---

## 🔬 Classification & Methodology Workflow

The algorithm categorizes each detected protein into four analytical cases:

- **Case 1 (High-peptide paired quantitation)**: Valid L/H pairs present in reference and target groups with $\ge 2$ unique peptides.
- **Case 2 (Single-peptide paired candidate)**: Valid L/H pairs present with 1 unique peptide.
- **Case 3 (Acquired-only Level 1)**: Protein absent in reference control, showing Light-dominant signal in target group with $\ge 2$ unique peptides.
- **Case 4 (Acquired-only Level 2)**: Protein absent in reference control, showing Light-dominant signal in target group with 1 unique peptide.

---

## ⚙️ Requirements & Dependencies

Install required R packages before running:

```R
install.packages(c("readxl", "dplyr", "purrr", "tibble", "knitr", "ggplot2", "DT", "plotly", "htmlwidgets", "htmltools"))
