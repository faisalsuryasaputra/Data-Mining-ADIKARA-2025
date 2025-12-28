# Data-Mining-ADIKARA-2025

### Indonesian Credit Default Prediction (ADIKARA 2025)
This repository contains a machine learning implementation for predicting credit default status in the microfinance and MSME (Micro, Small, and Medium Enterprises) sector in Indonesia, using the dataset from ADIKARA 2025 – Indonesian Credit Score, organized by PRODIGI: Digital Talent Centre.

### Background
The microfinance and MSME sector plays a crucial role in Indonesia’s economic growth, as the majority of businesses operate at small and medium scales. In recent years, the rapid adoption of financial technology (fintech) has significantly expanded access to digital financing, enabling many business owners—especially those previously underserved by traditional financial institutions—to obtain working capital and trade financing.
However, this rapid growth also introduces new challenges, particularly related to credit risk management and default rates. Variations in business sectors, borrowers’ backgrounds, collateral types, and regional characteristics contribute to differing levels of credit risk. Therefore, data-driven analysis and artificial intelligence are increasingly important to identify risk patterns and support sustainable financing growth.

### Project Objectives
Develop a binary classification model to predict credit default status
(0 = non-default, 1 = default).
Optimize model performance using Macro-averaged F1 Score as the primary evaluation metric.
Analyze the impact of borrower, business, and regional characteristics on credit risk.

### Approach
This project includes the following stages:
Data preprocessing and feature engineering
Exploratory Data Analysis (EDA)
Machine learning model training and evaluation
Model optimization based on Macro F1-Score
Generation of Kaggle-compatible submission files

### Evaluation Metric
Models are evaluated using Macro-averaged F1 Score, which calculates the F1-score for each class independently and then averages them. This metric assigns equal importance to each class and is suitable for handling potential class imbalance in credit default data.
