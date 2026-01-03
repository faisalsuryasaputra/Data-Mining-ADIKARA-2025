# 🇮🇩 Indonesian Credit Default Prediction (ADIKARA 2025)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange?logo=scikit-learn&logoColor=white)
![Status](https://img.shields.io/badge/Competition-ADIKARA%202025-red)

> **A Machine Learning project dedicated to predicting credit default risk within Indonesia's MSME & Micro sectors.**

## 📌 Background

The Micro, Small, and Medium Enterprises (MSME) sector plays a vital role in Indonesia's economic growth. The adoption of financial technology (*fintech*) has expanded access to digital financing but has also introduced new challenges regarding credit risk management.

Due to variations in borrower backgrounds, collateral types, and regional characteristics, risk levels vary significantly. This project aims to build a binary classification model to identify risk patterns and accurately predict customer default status.

## 🎯 Project Objectives

1.  **Risk Classification:** Predict customer status: `0` (Non-default/Safe) or `1` (Default/Risk).
2.  **Metric Optimization:** Utilize **Macro-averaged F1 Score** as the primary evaluation metric to effectively handle class imbalance.
3.  **Factor Analysis:** Identify the borrower and business characteristics that most significantly influence credit risk.

## 🛠️ Methodology & Workflow

The technical approach implemented in this repository covers the following *end-to-end* steps:

### 1. Data Preprocessing & Cleaning
* **Handling Missing Values:** Imputing empty values and handling *infinite* values to maintain model stability.
* **Datetime Extraction:** Extracting temporal features (`Year`, `Month`) from the `tanggal_pencairan` (disbursement date) column to capture seasonal patterns.

### 2. Feature Engineering
Creating new derived features to enrich customer financial information:
* `bunga_nominal`: Difference between total repayment and principal loan amount.
* `bunga_persen`: Percentage of interest relative to the principal.
* `cicilan_harian`: Estimated daily burden (`total_pengembalian` / `durasi_hari`).
* `ratio_lender`: Proportion of repayment allocated to the lender.

### 3. Encoding
Converting categorical variables into numerical format using **Label Encoding**:
* `provinsi` (province), `jenis_pinjaman` (loan type), `status_peminjam` (borrower status), `sektor_usaha` (business sector), `pendidikan` (education), `jenis_jaminan` (collateral type).

### 4. Modeling
The algorithm used is the **Random Forest Classifier**, specifically configured to handle imbalanced data:
* **Algorithm:** Random Forest
* **Class Weight:** `balanced` (Assigns higher weight to the minority/default class).
* **Estimators:** 200 trees.
* **Max Depth:** 15 (To prevent overfitting).

## 📊 Model Evaluation

The model is evaluated using the **Macro F1-Score**. This metric was chosen because it calculates the harmonic mean of *Precision* and *Recall* for each class independently. This provides a fair performance overview, ensuring the model is not biased towards the majority class ("Non-default") despite the "Default" class being significantly smaller.

## 📂 Repository Structure

```text
├── notebooks/          # Jupyter Notebooks for exploration and training
├── submission/         # Prediction results (CSV)
├── README.md           # Project Documentation
└── requirements.txt    # Library dependencies
