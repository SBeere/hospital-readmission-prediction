# Hospital Readmission Risk Prediction

## Overview
This project applies machine learning to predict whether a patient will be readmitted to the hospital within 30 days of discharge.  
Thirty-day readmissions are a key healthcare quality metric and are associated with increased costs and reimbursement penalties.

The goal of this project is to build and evaluate predictive models that can support **risk stratification** and **post-discharge intervention planning**.

---

## Business Problem
Hospital readmissions are costly and often preventable. Identifying patients at high risk of readmission enables healthcare providers and payers to:
- Prioritize follow-up care
- Allocate care management resources
- Reduce avoidable readmissions and associated penalties

This project frames readmission prediction as a **binary classification problem** focused on clinical usefulness rather than pure accuracy.

---

## Dataset
- **Source:** UCI Machine Learning Repository  
- **Dataset:** Diabetes 130-US Hospitals for Years 1999–2008  
- **Records:** ~100,000 inpatient encounters  
- **Target Variable:** 30-day readmission (`readmitted_binary`)
  - `1` = readmitted within 30 days  
  - `0` = not readmitted within 30 days  

The dataset contains patient demographics, utilization history, diagnoses, and hospital encounter information.

---

## Project Structure
hospital-readmission-prediction/
├── data/
│ ├── raw/ # Original dataset
│ └── processed/ # Cleaned dataset used for modeling
├── notebooks/
│ ├── 01_data_cleaning.ipynb
│ ├── 02_eda.ipynb
│ └── 03_modeling.ipynb
├── reports/
│ └── figures/
├── README.md
├── requirements.txt
└── .gitignore


---

## Exploratory Data Analysis (EDA)
Key findings from exploratory analysis include:
- Readmission rates vary across age groups but show no single dominant demographic driver.
- Prior inpatient utilization and clinical complexity are strongly associated with readmission risk.
- Length of stay alone is a weak predictor but contributes signal when combined with other features.

These findings reinforce that readmission risk is **multifactorial** rather than driven by a single variable.

---

## Modeling Approach
Two supervised classification models were evaluated:

- **Logistic Regression**
  - Used as an interpretable baseline model
  - Class weighting applied to address outcome imbalance

- **Random Forest Classifier**
  - Used to capture nonlinear relationships and feature interactions
  - Provided modest improvement in predictive performance

### Preprocessing
- Categorical features were one-hot encoded
- Numeric features were passed through without scaling
- Train/test split preserved class imbalance via stratification

---

## Model Evaluation
Models were evaluated using:
- **Recall (Sensitivity)** for 30-day readmission
- **ROC-AUC** for overall discrimination
- **Precision** to assess false-positive tradeoffs

Accuracy was not emphasized due to class imbalance.

### Results Summary
- Logistic Regression achieved an ROC-AUC of approximately **0.64**
- Random Forest achieved an ROC-AUC of approximately **0.66**
- Both models demonstrated modest but meaningful predictive signal, which is typical for readmission prediction using administrative data

---

## Feature Insights
Feature importance analysis from the Random Forest model indicated that readmission risk is primarily driven by:
- Prior inpatient utilization
- Number of diagnoses (clinical complexity)
- Length of hospital stay
- Patterns of healthcare usage rather than isolated demographic factors

These findings align with clinical expectations and support the use of the model as a **risk stratification tool**.

---

## Practical Implications
In a real healthcare setting, this model could be used to:
- Flag high-risk patients at discharge
- Prioritize care coordination or follow-up outreach
- Support population health and utilization management efforts

The model is intended to **support decision-making**, not replace clinical judgment.

---

## Limitations & Next Steps
- The dataset does not include social determinants of health or post-discharge behavior.
- Feature scaling and hyperparameter tuning may improve performance.
- Model explainability techniques (e.g., SHAP values) would be required prior to deployment.

---

## Technologies Used
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebooks
- Git & GitHub

