# Cardiovascular Disease Prediction
### Applied Machine Learning and Predictive Modelling 1 — FS26

---

## Authors

| Name              | Sections |
|-------------------|----------|
| Hanieh Jebeli     | Data cleaning, EDA, Linear Model, Poisson GLM |
| Enerel Khuyag     | Binomial GLM, GAM |
| Aurelio Wyrsch    | SVM, Neural Network, Conclusions |al Network, Conclusions |

---

## Project Description

This project analyses a clinical dataset of **70,000 patient records** to predict
the presence of cardiovascular disease using routine medical measurements.

**Research question:**
 *Which patient characteristics are most associated with cardiovascular disease,
 and can we predict its presence from routine clinical measurements?*

**Data source:** Kaggle — Sulianova Cardiovascular Disease Dataset (2019)
https://www.kaggle.com/datasets/sulianova/cardiovascular-disease-dataset

---

## Dataset Description

File: `data/cardio_train.csv` (semicolon-separated, 70,000 rows x 13 columns)

| Variable      | Type        | Description                                        |
|:--------------|:------------|:---------------------------------------------------|
| `id`          | Integer     | Patient ID — dropped in analysis                   |
| `age`         | Integer     | Age in days — converted to years                   |
| `gender`      | Binary      | 1 = Female, 2 = Male                               |
| `height`      | Integer     | Height in cm                                       |
| `weight`      | Float       | Weight in kg                                       |
| `ap_hi`       | Integer     | Systolic blood pressure (mmHg)                     |
| `ap_lo`       | Integer     | Diastolic blood pressure (mmHg)                    |
| `cholesterol` | Categorical | 1 = Normal, 2 = Above normal, 3 = Well above normal|
| `gluc`        | Categorical | 1 = Normal, 2 = Above normal, 3 = Well above normal|
| `smoke`       | Binary      | 0 = No, 1 = Yes                                    |
| `alco`        | Binary      | 0 = No, 1 = Yes                                    |
| `active`      | Binary      | 0 = No, 1 = Yes                                    |
| `cardio`      | Binary      | **Target** — 0 = No disease, 1 = Disease           |o` | Binary | **Target** — 0 = No disease, 1 = Disease |

---

## Folder Structure

```

├── data/
│   ├── cardio_train.csv          # Raw data (not on Git — share via Drive)
│   └── cardio_clean.rds          # Cleaned data saved by Hanieh's Rmd
│
├── code/
│   ├── 01_Hanieh_cleaning_LM_Poisson.Rmd   # Hanieh — run this FIRST
│   ├── 02_Enerel_binomial_GAM.Rmd           # Enerel — run second
│   ├── 03_Aurelio_SVM_NN_conclusions.Rmd    # Aurelio — run third
│   └── main_report.Rmd                      # Final combined report
│
├── models/
│   ├── lm_fit.rds                # Saved by Hanieh
│   ├── poisson_fit.rds           # Saved by Hanieh
│   ├── binomial_fit.rds          # Saved by Enerel
│   ├── gam_fit.rds               # Saved by Enerel
│   ├── svm_fit.rds               # Saved by Aurelio
│   └── nn_fit.rds                # Saved by Aurelio
│
├── output/
│   └── main_report.html          # Final compiled report
│
├── .gitignore
└── README.md
```

---

## How to Run

### Step 1 — Install required R packages (run once in RStudio console)

```r
install.packages(c(
  "tidyverse", "ggplot2", "GGally", "mgcv",
  "e1071", "nnet", "caret", "pROC",
  "knitr", "broom", "gridExtra", "scales"
))
```

### Step 2 — Place raw data

Put `cardio_train.csv` in the `data/` folder.
(Shared separately — not on GitHub due to file size.)

### Step 3 — Knit in order

```
1. code/01_Hanieh_cleaning_LM_Poisson.Rmd   → generates data/cardio_clean.rds
2. code/02_Enerel_binomial_GAM.Rmd           → loads cardio_clean.rds
3. code/03_Aurelio_SVM_NN_conclusions.Rmd   → loads cardio_clean.rds
4. code/main_report.Rmd                      → final combined document
```




