# Regression Analysis – GDT500 (Group 4)

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![R ≥ 4.0](https://img.shields.io/badge/R-≥%204.0-blue.svg)
![Quarto ≥ 1.4](https://img.shields.io/badge/Quarto-≥%201.4-orange.svg)
![GitHub stars](https://img.shields.io/github/stars/DrKangMunir/regression-analysis-assignment?style=social)
![GitHub forks](https://img.shields.io/github/forks/DrKangMunir/regression-analysis-assignment?style=social)

Reproducible multiple **logistic** and multiple **linear** regression analyses using simulated public health data for the GDT500 Multivariable Analysis course (DrPH, Universiti Sains Malaysia).[file:2][file:3]


---

<details>
<summary>📑 Table of Contents</summary>

- [Overview](#overview)
- [Contributors](#contributors)
- [Folder Structure](#folder-structure)
- [Published Analysis in Posit-Connect](#published-analysis-in-posit-connect)
- [Installation](#installation)
- [Usage](#usage)
- [Data](#data)
- [List of Analyses](#list-of-analyses)
- [Results](#results)
- [Contributing](#contributing)
- [Disclaimer](#disclaimer)
- [License](#license)
- [Version History](#version-history)

</details>

---

## Overview

- Examines how work-related and lifestyle factors relate to **quality of life (continuous)** and **depression (binary)** outcomes using multiple linear and multiple logistic regression on simulated data.
- Uses **R**, **Quarto**, and **tidyverse-based workflows** to demonstrate data simulation, EDA, model building, interaction terms, diagnostics, and interpretation.
- Exploratory Data Analysis (EDA) involves summarizing and visualizing datasets to understand distributions, relationships, and potential issues before modeling.
- Status: Stable teaching example for the GDT500 Regression Analysis group assignment (Group 4).

---

## Contributors


| Name                                | Student ID | Role                      |
|-------------------------------------|------------|---------------------------|
| Dr. Nazirul Munir Bin Abu Hassan    | 23202537   | Analysis & Documentation  |
| Dr. Nurfarihah Zulkifli             | 23202679   | Data Simulation           |
| Dr. Khairunnisa Binti Ariffin       | 23202532   | Model Diagnostics         |
| Dr. Sanggary Marimuthu              | 23202894   | Visualization & Reporting |


---

## Folder Structure

Layout within this repository:

- `Multiple-Linear-Regression/` – multiple linear regression (MLR) component  
  - `Group4_MLR.qmd`  – MLR analysis document  
  - `Group4_MLR.html` – rendered HTML report for MLR  
  - `data/` – simulated QoL dataset and generation script  
    - `simulated_qol_data.csv`  
    - `data_generation_qol.R`  

- `Multiple-Logistic-Regression/` – multiple logistic regression (MLogR) component  
  - `Group4_MLogR.qmd`  – MLogR analysis document  
  - `Group4_MLogR.html` – rendered HTML report for MLogR  
  - `data/` – simulated depression dataset and generation script  
    - `simulated_depression_data.csv`  
    - `data_generation_depression.R`  

- `README.md` – this overview file


```
├── Multiple-Linear-Regression/
│   ├── Group4_MLR.qmd
│   ├── Group4_MLR.html
│   └── data/
│       ├── simulated_qol_data.csv
│       └── data_generation_qol.R
├── Multiple-Logistic-Regression/
│   ├── Group4_MLogR.qmd
│   ├── Group4_MLogR.html
│   └── data/
│       ├── simulated_depression_data.csv
│       └── data_generation_depression.R
└── README.md
```

---

## Published Analysis in Posit-Connect

- [Linear Regression Analysis](https://posit-connect.kk.usm.my/content/2987b23e-f1f1-47ef-a116-90260349bf05)  
- [Logistic Regression Analysis](https://posit-connect.kk.usm.my/content/b9144dca-f26c-4d55-91ca-6085d73494db)
 
---

## Installation

### Prerequisites

- R (≥ 4.0.0) and RStudio (recommended)  
- Quarto or R Markdown  
- Required R packages:  
  `tidyverse`, `dplyr`, `tibble`, `modelr`,  
  `ggplot2`, `GGally`, `patchwork`, `corrplot`,  
  `broom`, `broom.helpers`, `performance`, `car`, `lmtest`, `mfp`,  
  `gtsummary`, `gt`, `knitr`,  
  `summarytools`, `labelled`, `DT`,  
  `caret`, `ResourceSelection`, `pROC`

### Setup

```bash
git clone https://github.com/DrKangMunir/regression-analysis-assignment.git
cd regression-analysis-assignment
```

Then in R:

```r
install.packages(c(
  "tidyverse", "dplyr", "tibble", "modelr",
  "ggplot2", "GGally", "patchwork", "corrplot",
  "broom", "broom.helpers", "performance", "car", "lmtest", "mfp",
  "gtsummary", "gt", "knitr",
  "summarytools", "labelled", "DT",
  "caret", "ResourceSelection", "pROC"
))
```

---

## Usage

### 1. Multiple Logistic Regression (Part 1)

From the repository root:

```bash
cd Multiple-Logistic-Regression

# Quarto
quarto render Group4_MLogR.qmd
```

This generates `Group4_MLogR.html` with the simulated depression dataset, EDA, multiple logistic regression models, diagnostics, and interpretation.

### 2. Multiple Linear Regression (Part 2)

```bash
cd Multiple-Linear-Regression

# Quarto
quarto render Group4_MLR.qmd
```

This generates `Group4_MLR.html` with the simulated QoL dataset, EDA, multiple linear regression models, diagnostics, and interpretation.

---

## Data

All datasets are **fully simulated** for educational purposes and contain no real participant data.

### Multiple Logistic Regression

- Source: `Multiple-Logistic-Regression/data/simulated_depression_data.csv`  
- Variables:  
  - `depression` – binary outcome  
  - `years_working` – continuous predictor  
  - `phys_activity` – continuous predictor  
  - `obesity` – binary obesity status
  - `phys_activity x obesity` - interaction term between physical activity and obesity
- Generated with fixed random seeds (`set.seed()`) in `data_generation_depression.R` or in Part A of the analysis document.

### Multiple Linear Regression

- Source: `Multiple-Linear-Regression/data/simulated_qol_data.csv`  
- Variables:  
  - `qol` – continuous quality of life score  
  - `years_working` – continuous predictor  
  - `phys_activity` – continuous predictor
  - `obesity` – binary obesity status
  - `phys_activity x obesity` - interaction term between physical activity and obesity
- Generated with fixed seeds in `data_generation_qol.R` or in Part A of the MLR analysis document.

A more detailed data dictionary can be included in each HTML report or a separate markdown file if required.

---

## List of Analyses

### Multiple Logistic Regression – Depression

- **Part A: Dataset and variable creation**  
  - Simulate a 200-observation dataset (depression, years of working, physical activity, obesity) with a prespecified interaction between physical activity and obesity.
  - Recode, factor-label, and document variables for transparent analysis.

- **Part B: Exploratory data analysis**  
  - Descriptive statistics for all variables using tabular summaries.
  - Histograms, boxplots, and bar plots (including depression by obesity) to explore distributions and group differences.

- **Part C: Regression modeling**  
  - Univariable logistic regression for each predictor with ORs and 95% CIs. 
  - Multivariable models:  
    - Main-effects model (years working, physical activity, obesity).  
    - Interaction model (physical activity × obesity) with interpretation of effect modification.
  - Model comparison using likelihood ratio tests and ANOVA for nested models.

- **Part D: Model checking and diagnostics**  
  - Assess linearity of the logit using fractional polynomials (mfp) for continuous predictors.
  - Evaluate independence and multicollinearity (correlation matrix, standard errors, VIF).
  - Assess goodness-of-fit (Hosmer–Lemeshow test, classification table, sensitivity/specificity, predictive values, ROC curve/AUC).
  - Influence diagnostics: Cook’s distance, leverage, DFBETAs, standardized residuals; identification and removal of influential observations; refitting and comparing models (coefficients, diagnostics, calibration plot).

- **Part E: Presentation and interpretation**  
  - Final regression table with adjusted ORs, CIs, p-values and Tjur’s R².
  - Final model equation, interpretation of main effects and interaction, model comparison, practical significance, and model assumptions. 
  - Prediction section with fitted probabilities for existing and new patients, interaction plots, and probability heatmaps.

### Multiple Linear Regression – Quality of Life

- **Part A: Research question, data simulation, and preparation**  
  - Research question on association between physical activity, obesity, years of working, and quality of life among adults.  
  - Simulate QoL data with specified coefficients for main effects and interaction (physical activity × obesity), plus random error and truncation to 0–100. 
  - Data preparation: structure checking, labeling of variables, and dataset summary.

- **Part B: Exploratory data analysis**  
  - Descriptive statistics for QoL and predictors (means, SDs, ranges, IQRs, proportions).
  - Histograms for continuous variables; boxplots by obesity status for QoL and predictors.  
  - Scatterplots of QoL vs predictors (including colour-coded plots by obesity to visualize interaction).
  - Correlation matrix and correlation plots for continuous variables.

- **Part C: Regression modeling**  
  - Univariable linear regression models for years of working, physical activity, and obesity with beta estimates and 95% CIs.  
  - Handling potential confounders by sequential model building.
  - Multivariable models:  
    - Model 1: main-effects-only model (years of working, physical activity, obesity).  
    - Model 2: full model with physical activity × obesity interaction. 
  - Model comparison based on fit statistics and change in coefficients.

- **Part D: Model checking and influential analysis**  
  - Assumption checks: linearity, normality of residuals (Q–Q plot), homoscedasticity (scale–location), and independence of residuals.  
  - Influence diagnostics: Cook’s distance, leverage, DFBETAs; identification of influential observations. 
  - Remedial measures: remove influential observations, refit the model, and compare estimates and diagnostics before and after removal.

- **Part E: Results and prediction**  
  - Final multivariable regression table with adjusted betas, SEs, CIs, t-statistics, and p-values. 
  - Final model equation and interaction plot illustrating effect modification by obesity. 
  - Narrative interpretation of main effects, interaction, model fit, practical significance, and robustness.  
  - Prediction section with new data simulation, fitted values, and visualization of predicted QoL across predictor ranges.

---

## Results

- **Logistic regression:** Odds ratios, ROC curves, calibration, diagnostics, and interpretation in `Group4_MLogR.html`. 
- **Linear regression:** Coefficient estimates, assumption checks, influence analysis, and interpretation in `Group4_MLR.html`. 

Key learning outcomes:

- Demonstrates reproducible regression workflows in R, from simulation to reporting.
- Shows how to specify, fit, check, and interpret multiple regression models with main effects and interaction terms in public health contexts.

---

## Contributing

This repository is part of a course assignment; external contributions are not accepted

For corrections or suggestions, please contact the group members or instructor with the relevant file name and section.

---

## Disclaimer

- This repository was developed as part of the **GDT500 Multivariable Analysis course**.  
- All datasets included are **simulated** and contain no real participant information.  

- Development of code and data generation was supported by **Microsoft Copilot**, an AI companion.  
- Copilot assisted with structuring code, automating simulations, and refining documentation; however, all analytical choices, interpretations, and conclusions remain the sole responsibility of the authors.  

- The materials provided here are intended exclusively for **educational and demonstration purposes**.  
- They should **not** be applied to clinical practice, policy decisions, or any real‑world patient data analysis.

---

## License

This project is licensed under the **MIT License**.  
See the top-level `LICENSE` file for full details.

## Version History

- v1.0.0 (2026-01-05): Initial release with complete linear and logistic regression analyses.
