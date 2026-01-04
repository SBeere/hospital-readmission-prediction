# Hospital Readmission Risk Prediction

## Overview
This project uses machine learning to predict 30-day hospital readmissions using the Diabetes 130-US Hospitals dataset (1999–2008).  
The goal is to identify patients at high risk of readmission so that healthcare providers can intervene earlier.

## Business Problem
Hospital readmissions are costly and are used as a quality metric by insurers and regulators.  
Accurately identifying high-risk patients can help reduce avoidable readmissions and improve patient outcomes.

## Dataset
- Source: UCI Machine Learning Repository
- Dataset: Diabetes 130-US Hospitals for Years 1999–2008
- Records: ~100,000 hospital encounters
- Target variable: `readmitted` (converted to binary: readmitted within 30 days vs not)

## Project Structure
hospital-readmission-prediction/
├── data/
│ ├── raw/ # Original dataset
│ └── processed/ # Cleaned dataset
├── notebooks/
│ ├── 01_data_cleaning.ipynb
│ ├── 02_eda.ipynb
│ └── 03_modeling.ipynb
├── reports/
│ └── figures/
├── README.md
├── requirements.txt
└── .gitignore

## Approach
1. Data cleaning and preprocessing
2. Exploratory data analysis (EDA)
3. Feature engineering
4. Model training and comparison
5. Evaluation using recall, ROC-AUC, and confusion matrices

## Models Used
- Logistic Regression
- Random Forest Classifier

## Key Considerations
- Class imbalance in readmission outcomes
- Emphasis on recall to reduce false negatives
- Model interpretability and ethical use in healthcare

## Next Steps
- Hyperparameter tuning
- Additional feature engineering
- Model explainability (SHAP)
- Deployment as a simple risk-scoring tool
