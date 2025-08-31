# Cancer Mortality Prediction Model

## Model Overview

This project implements a machine learning model to predict cancer patient mortality using the SEER (Surveillance, Epidemiology, and End Results) dataset. The model compares **Logistic Regression** and **XGBoost** algorithms to identify the best performing approach for mortality risk prediction.

**Dataset:** 1,278,767 cancer patient records (2004-2015)  
**Best Model:** XGBoost with **88.58% ROC AUC**  
**Target:** Binary classification (vital_status: 0=alive, 1=dead)

## Required Imports

The model uses the following Python libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import RobustScaler, OneHotEncoder, PolynomialFeatures
from sklearn.compose import ColumnTransformer
from sklearn.model_selection import train_test_split
from sklearn.feature_selection import SelectKBest, f_classif
from sklearn.metrics import classification_report, roc_auc_score, confusion_matrix, fbeta_score, roc_curve
from sklearn.linear_model import LogisticRegression
from imblearn.over_sampling import SMOTE
from imblearn.under_sampling import RandomUnderSampler
from imblearn.pipeline import Pipeline as ImbPipeline
from xgboost import XGBClassifier
```

## Model Features

The model uses 11 key features from the SEER dataset:

**Numeric Features:**
- `age`: Patient age at diagnosis
- `tumor_size`: Size of the tumor
- `risk_score`: Engineered clinical risk score

**Categorical Features:**
- `sex`: Patient gender
- `race`: Patient race/ethnicity
- `marital`: Marital status
- `grade`: Tumor grade/differentiation
- `ajcc_stage`: AJCC cancer staging (I, II, III, IV)
- `extension`: Tumor extension
- `lymph_nodes`: Lymph node involvement
- `mets`: Metastasis status

## Model Implementation Steps

### 1. Data Preprocessing
**Purpose:** Clean and prepare the raw SEER data for machine learning

- **Data Loading:** Load 1.2M+ patient records from cancer_dataset.csv
- **Missing Value Handling:** Fill numeric missing values with median
- **Data Type Conversion:** Convert age and tumor_size to numeric format
- **Feature Selection:** Select 11 most relevant clinical features
- **Target Distribution:** 717,663 dead (1) vs 561,104 alive (0) patients

### 2. Feature Engineering
**Purpose:** Create meaningful clinical risk indicators

- **Risk Score Calculation:** Advanced clinical risk scoring based on:
  - AJCC Stage (IV=3.0, III=2.5, II=2.0, I=0.5 points)
  - Age groups (80+=1.5, 70+=1.0, 60+=0.5 points)
  - Lymph node involvement (+1.0 point)
  - Metastasis presence (+1.5 points)
- **Categorical Encoding:** One-hot encoding for categorical variables
- **Numeric Scaling:** RobustScaler for numeric features

### 3. Data Splitting & Preprocessing Pipeline
**Purpose:** Prepare data for training and evaluation

- **Train-Test Split:** 80% training (1,023,013) / 20% testing (255,754)
- **Stratified Sampling:** Maintain target distribution across splits
- **ColumnTransformer Pipeline:** 
  - RobustScaler for numeric features
  - OneHotEncoder for categorical features
- **Final Feature Space:** 470 features after encoding

### 4. Model Training & Comparison
**Purpose:** Train and compare two different algorithms

**Logistic Regression:**
- Linear baseline model with interpretability
- Parameters: `max_iter=1000, class_weight='balanced'`
- Performance: 87.47% ROC AUC

**XGBoost Classifier:**
- Ensemble method for complex pattern recognition
- Parameters: `n_estimators=200, learning_rate=0.1, max_depth=6`
- Performance: 88.58% ROC AUC (**Best Model**)

### 5. Model Evaluation
**Purpose:** Assess model performance using clinical-relevant metrics

**Primary Metrics:**
- **ROC AUC:** Overall discriminative ability (0.8858 for XGBoost)
- **F1-Score:** Balance of precision and recall (0.8213 for XGBoost)
- **F2-Score:** Emphasizes recall for medical diagnosis (0.8129 for XGBoost)

**Clinical Metrics:**
- **Sensitivity/Recall:** Ability to identify high-risk patients
- **Specificity:** Ability to correctly identify low-risk patients
- **Confusion Matrix:** Detailed classification performance

### 6. Feature Importance Analysis
**Purpose:** Understand which clinical factors drive predictions

**Top Contributing Features:**
1. `ajcc_stage_IV`: Most important predictor (9.99% importance)
2. `risk_score`: Engineered clinical score (6.41% importance)
3. `mets_98`: Metastasis indicators
4. Age and tumor characteristics

**Clinical Insights:**
- AJCC Stage IV is the strongest mortality predictor
- Engineered risk score effectively captures clinical complexity
- Metastasis status significantly impacts survival prediction

## Model Performance Results

### Final Model Comparison

| Model | ROC AUC | F1 Score | F2 Score |
|-------|---------|----------|----------|
| Logistic Regression | 0.8747 | 0.8061 | 0.7831 |
| **XGBoost (Best)** | **0.8858** | **0.8213** | **0.8129** |

### Why These Metrics Matter

- **ROC AUC (0.8858):** Excellent discriminative ability - the model correctly ranks a random deceased patient higher than a random alive patient 88.58% of the time
- **F1-Score (0.8213):** Strong balance between precision (avoiding false alarms) and recall (catching high-risk patients)
- **F2-Score (0.8129):** Emphasizes recall, which is crucial in medical diagnosis to minimize missed high-risk cases

### Clinical Significance

The XGBoost model achieves **88.58% ROC AUC**, exceeding the target accuracy of 75-85% and demonstrating strong predictive capability for clinical decision support. The model effectively identifies high-risk patients while maintaining reasonable specificity to avoid unnecessary interventions.

## Key Findings

1. **XGBoost outperforms Logistic Regression** across all evaluation metrics
2. **AJCC Stage IV** is the strongest predictor of mortality risk
3. **Engineered risk score** effectively captures clinical complexity
4. **Model achieves clinical-grade performance** suitable for healthcare applications
5. **Feature importance analysis** provides interpretable insights for clinicians

## Usage

To run the model:
1. Install required dependencies: `pip install -r requirements.txt`
2. Open and run `mortality_predict.ipynb`
3. The notebook will automatically load data, train models, and display results

## Model Interpretability

The model provides feature importance rankings to help clinicians understand which factors most influence mortality predictions, making it suitable for clinical decision support while maintaining transparency in the prediction process.
