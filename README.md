# Retail Credit Risk & Predictive Default Scoring Engine

An end-to-end machine learning project for retail credit-risk assessment and predictive default scoring using the Home Credit Default Risk dataset.

## Overview

This project develops a borrower-level credit-risk modeling pipeline using demographic, financial, employment and credit-related attributes.

Two classification approaches are compared:

- Logistic Regression as an interpretable baseline
- XGBoost for nonlinear relationships and feature interactions

The project focuses on predictive discrimination, threshold analysis, borrower risk segmentation and model feature importance.

## Project Pipeline

Raw Credit Data
↓
Data Quality Analysis
↓
Feature Engineering
↓
Missing Value Handling
↓
Categorical Encoding
↓
Class Imbalance Handling
↓
Logistic Regression / XGBoost
↓
Model Evaluation
↓
Threshold Analysis
↓
Predictive Risk Scoring
↓
Risk Segmentation

## Dataset

This project uses the Home Credit Default Risk dataset.

The dataset contains borrower application information and a binary target indicating whether an applicant experienced payment difficulties.

The raw dataset is not included in this repository because of its large size.

See `data/README.md` for dataset setup instructions.

## Feature Engineering

Key engineered features include:

- Credit-to-Income Ratio
- Annuity-to-Income Ratio
- Age in Years

Exploratory analysis was performed to examine the relationship between these variables and observed default rates.

## Models

### Logistic Regression

Used as an interpretable baseline classification model.

### XGBoost

Used to capture nonlinear relationships and interactions between borrower characteristics.

## Results

Evaluation was performed on a held-out test set.

| Model | ROC-AUC | PR-AUC | KS |
|---|---:|---:|---:|
| Logistic Regression | 0.7485 | 0.2200 | 0.3777 |
| XGBoost | **0.7610** | **0.2446** | **0.3932** |

## Threshold Analysis

Classification thresholds were evaluated using a validation set to study the trade-off between false positives and false negatives.

At the 0.50 threshold, XGBoost achieved:

- Precision: 17.21%
- Recall: 66.97%
- F1 Score: 27.38%

## Predictive Risk Scoring

The model generates borrower-level predictive outputs including:

- Model-predicted risk
- Risk score
- Risk band

The current score is intended for predictive ranking and risk segmentation. It should not be interpreted as a calibrated Probability of Default for real-world lending without additional calibration and validation.

## Feature Importance

XGBoost feature importance was used to identify important transformed predictors.

Important contributors included:

- EXT_SOURCE_2
- EXT_SOURCE_3
- EXT_SOURCE_1
- Education-related variables
- Income type
- Age
- Contract type
- Selected document and ownership indicators

Feature importance indicates contribution to model predictions and does not establish causality.

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- SHAP
- Google Colab

## Repository Structure

```text
Retail-Credit-Risk-Predictive-Scoring/
│
├── credit_risk_predictive_scoring.ipynb
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── README.md
│
└── results/
    ├── model_comparison.csv
    ├── threshold_analysis.csv
    └── feature_importance.csv