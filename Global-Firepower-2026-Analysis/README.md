# Global Firepower 2026 Analysis

A data analytics portfolio project analyzing the **2026 Global Firepower dataset across 145 countries**. The project builds a reproducible data-preparation pipeline, creates eight analysis-ready datasets, combines them into a master analytical dataset, and performs exploratory analysis around five business questions.

## Project Objective

The objective is to examine how defense spending, manpower, military technology, logistics infrastructure, geography, and natural-resource endowments are associated with the Global Firepower Power Index.

The project is designed as an end-to-end data analytics workflow:

```text
Global Firepower Source Data
        ↓
Data Collection
        ↓
Cleaning & Standardization
        ↓
Unit Transformation
        ↓
Validation
        ↓
8 Analysis-Ready Datasets
        ↓
Master Analytical Dataset
        ↓
Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
5 Business Questions
        ↓
Findings & Insights
```

## Dataset Scope

The analysis covers **145 countries** and uses eight analytical domains:

| Dataset | Main content |
|---|---|
| Manpower | Population and military manpower indicators, Power Index and overall rank |
| Finance | Defense budget, external debt, PPP and foreign-exchange reserves |
| Airforce | Aircraft inventory and aircraft categories |
| Army | Tanks, armored vehicles, artillery and rocket systems |
| Navy | Fleet strength and naval indicators |
| Logistics | Airports, ports/terminals, railways, roads and related infrastructure |
| Geography | Land area, coastline, borders and waterways |
| Natural Resources | Oil, natural gas and coal indicators |

## Project Structure

```text
Global-Firepower-2026-Analysis/
│
├── notebooks/
│   ├── Global_Fire_Power_2026_Data_Pipeline.ipynb
│   └── Global_Firepower_2026_EDA.ipynb
│
├── data/
│   ├── df_manpower_2026.pkl
│   ├── df_finance_2026.pkl
│   ├── df_airforce_2026.pkl
│   ├── df_army_2026.pkl
│   ├── df_navy_2026.pkl
│   ├── df_logistics_2026.pkl
│   ├── df_geography_2026.pkl
│   └── df_nat_resources_2026.pkl
│
├── report/
│   └── Global_Firepower_Analysis_2026_Report.docx
│
├── requirements.txt
├── README.md
└── .gitignore
```

## Notebooks

### 1. Data Pipeline

`Global_Fire_Power_2026_Data_Pipeline.ipynb`

This notebook handles the preparation stage:

- Defines source URLs
- Collects Global Firepower data
- Cleans raw tables
- Standardizes column names
- Converts source units into analysis-friendly units
- Validates row counts and country uniqueness
- Checks missingness and country-set consistency
- Exports eight analysis-ready `.pkl` datasets

### 2. Exploratory Data Analysis

`Global_Firepower_2026_EDA.ipynb`

This notebook:

- Loads the eight prepared datasets
- Builds the master analytical dataset
- Performs data understanding and validation
- Engineers analytical features
- Creates visualizations
- Answers five business questions
- Summarizes findings and analytical insights

## Five Business Questions

### Q1. How is defense spending associated with military power?

Defense budget is compared with the Global Firepower Power Index using visualization and Pearson correlation.

**2026 result:** Pearson correlation = **-0.302**

### Q2. Where does military-power rank differ from defense-spending rank?

A **Budget–Power Rank Gap** is calculated as:

```text
Budget Rank − Overall Power Rank
```

The largest positive gap in the executed analysis was **Argentina: 62 ranks**.

### Q3. How does military technology intensity relate to military power?

Aircraft intensity is measured as:

```text
Total Aircraft / Active Personnel × 100,000
```

**2026 result:** Pearson correlation = **-0.352**

### Q4. How does logistics infrastructure relate to military power?

A project-defined logistics score combines max-normalized:

- Serviceable airports
- Major ports/terminals
- Railway length
- Roadway length

using equal weighting.

**2026 result:** Pearson correlation = **-0.341**

### Q5. How are geography and natural resources associated with military power?

Two project-defined composite measures are analyzed:

- Geography score
- Natural-resource score

**2026 results:**

- Geography vs Power Index: **-0.362**
- Resources vs Power Index: **-0.334**

## Key Analytical Insight

Across the five questions, the analyzed dimensions show **moderate negative associations** with the Power Index. Since a lower Power Index represents a stronger position in the Global Firepower ranking, the direction of these relationships is consistent with higher values of the examined indicators being associated with stronger ranking positions.

These are **associations, not causal effects**. The project does not claim that defense spending, logistics, geography, resources, or aircraft intensity independently causes military strength.

## Important Methodological Notes

### Power Index interpretation

The Global Firepower Power Index is used as the main military-power outcome. **Lower values represent stronger positioning** in the ranking.

### Composite scores

The logistics, geography, and natural-resource scores are **project-defined analytical features**. They use normalization and equal weighting for transparent comparison. They are not official Global Firepower scores.

### Navy fleet tonnage missingness

Fleet-tonnage information is not available for every country in the source. In the 2026 dataset, values are available for **51 of 145 countries**, while the remaining 94 observations are retained as `NaN`.

Missing fleet-tonnage values are **not converted to zero and are not artificially imputed**.

### Correlation

Pearson correlation measures linear association. It does not establish causation and can be affected by skewed distributions and extreme observations.

## Installation

Use Python 3.10 or newer.

Create a virtual environment if desired:

```bash
python -m venv .venv
```

Activate it and install dependencies:

```bash
pip install -r requirements.txt
```

For the data-collection notebook, Selenium requires a working Chrome/Chromium browser environment. `webdriver-manager` is used to manage the Chrome driver.

## Running the Project

### Step 1 — Run the data pipeline

Open:

```text
Global_Fire_Power_2026_Data_Pipeline.ipynb
```

Run the notebook from top to bottom. It prepares and exports the eight 2026 `.pkl` datasets.

### Step 2 — Run the EDA

Place the eight generated `.pkl` files where the EDA notebook expects them and open:

```text
Global_Firepower_2026_EDA.ipynb
```

Run all cells from the beginning to reproduce the master dataset, feature engineering, visualizations, and business-question analysis.

## Outputs

The project produces eight analysis-ready datasets:

```text
df_manpower_2026.pkl
df_finance_2026.pkl
df_airforce_2026.pkl
df_army_2026.pkl
df_navy_2026.pkl
df_logistics_2026.pkl
df_geography_2026.pkl
df_nat_resources_2026.pkl
```

The project also includes the final Word report:

```text
Global_Firepower_Analysis_2026_Report.docx
```

## Limitations

- The analysis is cross-sectional and uses the 2026 dataset rather than a time series.
- Global Firepower indicators should be interpreted within the source's methodology.
- Project-defined composite scores depend on the selected variables and normalization approach.
- Navy fleet tonnage has substantial source missingness.
- Pearson correlation describes linear association and does not establish causality.
- Aircraft intensity measures quantity relative to active personnel and does not directly measure aircraft quality, readiness, training, or combat effectiveness.

## Data Source

Primary source: **Global Firepower**

https://www.globalfirepower.com/

Country listing:

https://www.globalfirepower.com/countries-listing.php

## Reproducibility

The project separates **data preparation** from **exploratory analysis**. This makes the workflow easier to reproduce, validate, and extend to future Global Firepower releases.

The data pipeline creates standardized analytical datasets, while the EDA notebook focuses on analysis and interpretation.

## Portfolio Context

This project was developed as a data analytics portfolio project for the **AICTE Data Analytics with AI internship program (CSRBOX + IBM)**.

---

**Project:** Global Firepower 2026 Analysis  
**Dataset scope:** 145 countries  
**Analysis type:** Data Preparation + Exploratory Data Analysis  
**Primary tools:** Python, Pandas, NumPy, Matplotlib, Seaborn, Selenium
