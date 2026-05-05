# Bank Marketing — Term Deposit Subscription Prediction
### Applied Machine Learning and Predictive Modelling 1 — FS26

---

## Authors

| Name              | Role       | Sections                                      |
|:------------------|:-----------|:----------------------------------------------|
| Hanieh Jebeli     | Student 1  | Data cleaning, EDA, Linear Model, Poisson GLM |
| Enerel Khuyag     | Student 2  | Binomial GLM, GAM                             |
| Aurelio Wyrsch    | Student 3  | SVM, Neural Network, Conclusions              |

---

## Project Description

This project analyses **45,211 real phone marketing calls** made by a Portuguese
bank between 2008 and 2010. Our goal is to predict whether a customer will
subscribe to a term deposit — and understand what drives that decision.

**Research question:**
> *"Can we predict which bank customers will subscribe to a term deposit
> before we call them — and what drives their decision?"*

**Data source:** UCI Machine Learning Repository — Bank Marketing Dataset
https://archive.ics.uci.edu/dataset/222/bank+marketing

---

## Dataset Description

File: `data/bank-full.csv` (semicolon-separated, 45,211 rows x 17 columns)

| Variable      | Type        | Description                                                      |
|:--------------|:------------|:-----------------------------------------------------------------|
| `age`         | Continuous  | Client age in years                                              |
| `job`         | Categorical | Type of job (12 levels: admin, blue-collar, management, etc.)    |
| `marital`     | Categorical | Marital status (married, single, divorced)                       |
| `education`   | Categorical | Education level (primary, secondary, tertiary, unknown)          |
| `default`     | Binary      | Has credit in default? (yes/no)                                  |
| `balance`     | Continuous  | Average yearly balance in euros                                  |
| `housing`     | Binary      | Has housing loan? (yes/no)                                       |
| `loan`        | Binary      | Has personal loan? (yes/no)                                      |
| `contact`     | Categorical | Contact type (cellular, telephone, unknown)                      |
| `day`         | Continuous  | Last contact day of month                                        |
| `month`       | Categorical | Last contact month (jan-dec)                                     |
| `duration`    | Continuous  | Last call duration in seconds                                    |
| `campaign`    | Count       | Number of contacts during this campaign                          |
| `pdays`       | Continuous  | Days since last contact (-1 = never contacted)                   |
| `previous`    | Count       | Number of contacts before this campaign                          |
| `poutcome`    | Categorical | Outcome of previous campaign (success, failure, other, unknown)  |
| `y`           | Binary      | **Target** — subscribed to term deposit? (yes/no)                |

---

## Variable Types — Course Requirements

| Required type       | Variable(s)                        | Status |
|:--------------------|:-----------------------------------|:-------|
| Continuous          | age, balance, duration, pdays      | OK     |
| Count               | campaign, previous                 | OK     |
| Categorical 3+levels| job (12), education (4), month (12)| OK     |
| Binary              | default, housing, loan, y          | OK     |

---

## Folder Structure

```
Jebeli_Khuyag_Wyrsch_MATRICULATION/
│
├── data/
│   ├── bank-full.csv              # Raw data
│   └── bank_clean.rds             # Cleaned data saved by Hanieh's Rmd
│
├── code/
│   ├── 01_Hanieh_cleaning_LM_Poisson.Rmd   # Hanieh — run FIRST
│   ├── 02_Enerel_binomial_GAM.Rmd           # Enerel — run second
│   ├── 03_Aurelio_SVM_NN_conclusions.Rmd    # Aurelio — run third
│   └── main_report.Rmd                      # Final combined report
│
├── models/
│   ├── lm_fit.rds                 # Saved by Hanieh
│   ├── poisson_fit.rds            # Saved by Hanieh
│   ├── binomial_fit.rds           # Saved by Enerel
│   ├── gam_fit.rds                # Saved by Enerel
│   ├── svm_fit.rds                # Saved by Aurelio
│   └── nn_fit.rds                 # Saved by Aurelio
│
├── output/
│   └── main_report.html           # Final compiled report
│
├── .gitignore
└── README.md
```

---

## How to Run

### Step 1 — Install R packages (run once in RStudio console)

```r
install.packages(c(
  "tidyverse", "ggplot2", "GGally", "mgcv",
  "e1071", "nnet", "caret", "pROC",
  "knitr", "broom", "gridExtra", "scales"
))
```

### Step 2 — Download the data

Go to: https://archive.ics.uci.edu/dataset/222/bank+marketing
Download `bank.zip` → unzip → place `bank-full.csv` in the `data/` folder.

### Step 3 — Knit in order

```
1. code/01_Hanieh_cleaning_LM_Poisson.Rmd   → saves data/bank_clean.rds
2. code/02_Enerel_binomial_GAM.Rmd           → loads bank_clean.rds
3. code/03_Aurelio_SVM_NN_conclusions.Rmd    → loads bank_clean.rds
4. code/main_report.Rmd                      → final combined document
```

### Step 4 — Load shared objects in Rmd

```r
# At the top of Enerel's and Aurelio's Rmd:
bank_clean <- readRDS("../data/bank_clean.rds")

# Load a model from a teammate:
lm_fit <- readRDS("../models/lm_fit.rds")
```

---

## Git Workflow

```bash
git clone https://github.com/HaniehJebeli/AML.git
git checkout -b Hanieh    # or Enerel / Aurelio

git add code/01_Hanieh_cleaning_LM_Poisson.Rmd
git commit -m "feat: data cleaning and LM section"
git push origin Hanieh
```

---

## Submission

**Deadline:** June 12, 2026 at 17:00 — uploaded to ILIAS
**Zip name:** `Jebeli_Khuyag_Wyrsch_MATRICULATION.zip`
**Zip contents:** data/bank-full.csv, code/main_report.Rmd, output/main_report.html, README.md
