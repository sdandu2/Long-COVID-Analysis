# Long COVID Prediction Model

This project focuses on predicting the likelihood of long COVID outcomes using machine learning. By analyzing patient data and medical history, the model identifies key features contributing to long COVID and provides accurate predictions.

---

## Table of Contents
- [Introduction](#introduction)
- [Pre-Processing and EDA](#pre-processing-and-eda)
- [Feature Selection](#feature-selection)
- [Model Selection](#model-selection)
- [Preliminary Results](#preliminary-results)
- [XGBoost Tuning and Results](#xgboost-tuning-and-results)
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)

---

## Introduction

Long COVID prediction involves identifying patterns in patient data to forecast prolonged symptoms. This project aims to:
- Develop a machine learning model for accurate long COVID prediction.
- Optimize features for better interpretability and prediction accuracy.
- Provide actionable insights for medical professionals.

---

## Pre-Processing and EDA

### Pre-Processing
- Removed duplicates to balance class proportions.
- Cleaned missing values by eliminating incomplete records.

### Exploratory Data Analysis (EDA)
- **Age Distribution**: Age emerged as a key factor in long COVID prediction.
- **Mortality by ICU and Intubation**: Strong correlation identified between mortality rate and ICU/intubation status.
- **Mortality Over Time**: Showed variations in patient outcomes across months.

---

## Feature Selection

### Methods
1. **Correlation Analysis**:
   - Identified redundant and highly correlated features to reduce multicollinearity.
2. **Feature Importance**:
   - Random Forest was used to rank features by their predictive importance.
   - Significant features included `Age`, `Medical Unit`, and `Died`.

### Dimensionality Reduction
- Focused on the top 10 features to simplify the model and enhance interpretability.

### Domain Expertise Integration
- Incorporated clinical knowledge to prioritize features like `Pneumonia`, `Hypertension`, and `ICU`.

---

## Model Selection

### Logistic Regression
- **Pros**:
  - Baseline model for comparison.
  - Simplicity and interpretability.
- **Use Case**:
  - Understanding the impact of individual features.

### Random Forest
- **Pros**:
  - Handles non-linear relationships effectively.
  - Robust to overfitting when tuned.

### XGBoost
- **Pros**:
  - High efficiency with regularization techniques.
  - State-of-the-art performance in structured data problems.

### Voting Classifier
- **Pros**:
  - Combines predictions from multiple models for improved stability.

### Neural Network
- **Pros**:
  - Captures complex non-linear relationships.
  - Effective for highly interactive features.

---

## Preliminary Results

| Model               | Training Accuracy | Test Accuracy | Precision | Recall | F1 Score | AUC    |
|---------------------|-------------------|---------------|-----------|--------|----------|--------|
| Logistic Regression | 0.6207            | 0.6193        | 0.6303    | 0.6509 | 0.6405   | 0.6608 |
| Random Forest       | 0.7492            | 0.5787        | 0.5906    | 0.6235 | 0.6066   | 0.5992 |
| XGBoost             | 0.6546            | 0.6436        | 0.6459    | 0.6994 | 0.6716   | 0.6940 |
| Voting Classifier   | 0.7215            | 0.6216        | 0.6292    | 0.6664 | 0.6473   | 0.6574 |
| Neural Network      | 0.6295            | 0.6285        | 0.6285    | 0.7015 | 0.6629   | 0.6798 |

- **XGBoost** was selected as the best model due to its balanced performance across metrics and superior recall (69.94%).

---

## XGBoost Tuning and Results

### Tuning Parameters
- `max_depth`: Set to 6 to control complexity and prevent overfitting.
- `learning_rate`: Set to 0.01 for gradual learning.
- Regularization (`reg_alpha` = 0.6, `reg_lambda` = 0.6) to stabilize the model.

### Cross-Validation
- Performed 8-fold stratified cross-validation.
- Achieved a mean CV accuracy of 67.03%.

### Test Results
- **Precision**: 65% for positive cases.
- **Recall**: 78% for positive cases.
- **F1 Score**: 0.71.
- **AUC**: 0.72.

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/long-covid-prediction.git
   cd long-covid-prediction
