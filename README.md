# SILAC-Based Proteomic Source Attribution & EV-PC Protein Classification

This repository contains the computational pipeline for quantifying, classifying, and attributing protein sources in extracellular vesicle protein corona (EV–PC) studies using SILAC (Stable Isotope Labeling by Amino Acids in Cell Culture) mass spectrometry data.

---

## 📌 Overview

Extracellular vesicles (EVs) isolated from serum-containing media often adsorb background serum proteins, forming a "protein corona" (PC). This pipeline addresses the critical challenge of distinguishing **producer-cell-derived EV proteins** from **serum-acquired protein corona components**.

By analyzing Light (L) and Heavy (H) SILAC peptide intensities across experimental condition groups (`DGEVPC_B`, `DGEVPC_C`, and `UCEVPC`) against a baseline reference group (`UCEV`), the protocol categorizes detected proteins into rigorous statistical confidence tiers and quantifies net serum-derived contribution.

---

## 🔬 Classification & Methodology Workflow

The algorithm categorizes each detected protein into one of four primary analytical cases:

- **Case 1 (High-peptide paired quantitation)**: Valid L/H pairs present in reference and target groups with $\ge 2$ unique peptides.
- **Case 2 (Single-peptide paired candidate)**: Valid L/H pairs present with 1 unique peptide.
- **Case 3 (Acquired-only Level 1)**: Protein absent in reference control, showing Light-dominant signal in target group with $\ge 2$ unique peptides.
- **Case 4 (Acquired-only Level 2)**: Protein absent in reference control, showing Light-dominant signal in target group with 1 unique peptide.

### Statistical Confidence Tiers
For paired proteins (Case 1 & 2), the pipeline calculates:
1. **Light Fraction Excess ($\Delta r$)**: $r_{\text{target}} - r_{\text{baseline}}$
2. **Dynamic Background Thresholds**: Based on robust median absolute deviation (MAD) standard deviations ($\sigma$) of the baseline control.
3. **Z-Score & 95% Confidence Interval (CI) Separation**: Evaluates statistical separation between target and baseline control.
4. **Serum Fraction & CV Floor**: Estimates serum contribution ratio and filters out noisy candidates with High CV (>0.50).

---

## 📁 Repository Structure

```text
.
├── SILAC_EV_PC_Attribution.Rmd    # Main R Markdown workflow script
├── README.md                       # Project documentation (this file)
└── output/                         # Output directory (configured in script)
    ├── 01_sample_information.csv
    ├── 00_All_Comparisons_Merged_Results.csv
    ├── 00_All_Comparisons_Primary_Serum_Derived_Merged.csv
    ├── 00_Classification_Summary_by_Group.csv
    ├── DGEVPC_B_vs_UCEV/
    │   ├── DGEVPC_B_vs_UCEV_00_All_Results.csv
    │   └── DGEVPC_B_vs_UCEV_01_Merged_Primary_Serum_Derived_Proteins.csv
    ├── DGEVPC_C_vs_UCEV/
    └── UCEVPC_vs_UCEV/
