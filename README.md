# Healthcare Analytics Pipeline — BRFSS 2015 Heart Disease Dataset

A structured, multi-stage healthcare data analytics pipeline built on the **BRFSS 2015 Heart Disease Health Indicators dataset**. The project moves from domain research through data cleaning, feature engineering, and exploratory data analysis, with a strong emphasis on reproducibility, explainability, and machine-readable outputs that feed downstream reporting.

## Overview

This pipeline is organized as a sequence of Jupyter notebooks, each building on the outputs of the last. Every reported statistic is sourced programmatically from JSON logs rather than typed by hand, ensuring that final documentation always reflects the actual computed results.

## Pipeline Stages

1. **Domain Research**
   A healthcare analytics research report establishing market context, key drivers, and challenges in the space, produced as both Markdown and PDF.

2. **Data Cleaning & Feature Engineering**
   Raw BRFSS survey data is audited and cleaned — duplicate flagging, BMI winsorization, and correction of logically inconsistent responses — then enriched with 12 derived features spanning clinical, mental/physical health, and demographic dimensions.

3. **Exploratory Data Analysis & Visualization**
   A fully executed EDA notebook covering univariate and bivariate analysis, a correlation heatmap, demographic prevalence breakdowns, and comorbidity dose-response analysis. Produces seven saved figures and a 12-slide presentation deck.

## Key Findings

- **Comorbidity_Count** is the strongest predictor of heart disease in this dataset, showing a clear dose-response relationship across 0–4 comorbidities.
- The rule-based **HighRisk_Profile_Flag** achieves meaningful lift over baseline prevalence.
- Heart disease risk accelerates notably after **age 60**.

## Repository Structure

```
v2/
├── 01_Domain_Research/
├── 02_Data_Cleaning_Feature_Engineering.ipynb
├── 03_EDA_Visualization.ipynb
├── data/
│   └── heart_disease_cleaned.csv
├── docs/
│   └── eda_findings_log.json      # Machine-readable stats log driving report generation
├── figures/                        # Generated EDA visualizations
└── reports/
    ├── Healthcare_Analytics_Research_Report.pdf
    ├── EDA_Presentation.pdf
    └── EDA_Report.docx
```

## Tools & Stack

- **Language/Environment:** Python, Jupyter (`nbformat`, `nbconvert`)
- **Data:** BRFSS 2015 Heart Disease Health Indicators dataset
- **Documentation:** `python-docx`, `pptxgenjs`, LibreOffice, pandoc + xelatex
- **Visualization:** Standard Python plotting libraries

## Design Principles

- **Reproducibility first** — all statistics in written reports are pulled from JSON logs, never manually transcribed.
- **Explicit, readable code** — plain loops and named variables over dense/vectorized one-liners; each code cell is preceded by a markdown explanation distinguishing the *why* (logic) from the *how* (implementation).
- **Visual QA** — generated presentations and reports are visually verified (e.g., rasterized contact sheets) before being finalized.

## Known Issues

- The data cleaning notebook currently **drops duplicates outright**, whereas other stages use a flag-and-preserve approach. This is a known architectural inconsistency flagged for future correction.

## Status

Domain research, data cleaning/feature engineering, and EDA/visualization stages are complete. A predictive modeling and/or final reporting stage may follow.
