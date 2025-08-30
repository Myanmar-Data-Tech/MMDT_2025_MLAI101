# Binary Classification  Customers’ Purchase on Online Shopping

## Project Overview
The project focuses on binary classification to predict whether an online shopper will make a purchase or not during their visit to an e-commerce website.

## Problem Statement
In the rapidly evolving world of e-commerce, understanding customer behavior is crucial for optimizing user experience and increasing conversion rates. One of the biggest challenges for online retailers is that a large percentage of website visits end without a purchase, resulting in lost revenue and missed opportunities for targeted marketing.
This project aims to address that challenge by developing a machine learning model capable of predicting, in real-time, whether an online shopper is likely to complete a purchase during their session.

## Objectives
- Preprocess the dataset and extract meaningful features.
- Implement and evaluate multiple classification models.
- Optimize models through hyperparameter tuning, StratifiedKFold.
- Analyze feature importance.
- Visualize model performance using confusion matrices and ROC-AUC curves.

## Dataset and Feature Description
- **Source**: UCI Machine Learning Repository
- **Size**: 12,330 shopping sessions from different users over 1 year
- **Features**: 18 columns (10 numerical, 8 categorical)

- **Administrative**: Number of pages viewed in the administrative category.
- **Administrative_Duration**: Time spent on administrative pages (in seconds).
- **Informational**: Number of pages viewed in the informational category.
- **Informational_Duration**: Time spent on informational pages (in seconds).
- **ProductRelated**: Number of pages viewed in the product-related category.
- **ProductRelated_Duration**: Time spent on product-related pages (in seconds).
- **BounceRates**: Percentage of visitors who leave the site after viewing only one page.
- **ExitRates**: Percentage of visitors who exit from specific pages.
- **PageValues**: Average value of the pages viewed before completing a transaction.
- **SpecialDay**: Indicator of whether the session occurred on a special shopping day (e.g., holidays).
- **Month**: Month of the session (e.g., Jan, Feb, Mar, etc.).
- **OperatingSystems**: Operating system used by the visitor (e.g., Windows, macOS, Linux).
- **Browser**: Browser used by the visitor (e.g., Chrome, Firefox, Safari).
- **Region**: Geographical region of the visitor (e.g., North America, Europe, Asia).
- **TrafficType**: Type of traffic (e.g., direct, referral, organic search).
- **VisitorType**: Type of visitor (e.g., Returning_Visitor, New_Visitor, Other).
- **Weekend**: Indicator of whether the session occurred on a weekend (True/False).
- **Revenue**: Target variable indicating whether a purchase was made during the session (True/False).


## Machine Learning Models Used
1. **Logistic Regression**
2. **K-Nearest Neighbors (KNN)**
3. **Support Vector Machine (SVM)**
4. **Decision Tree**
5. **Random Forest**

## Evaluation Metrics
- **Precision**: Ability to correctly identify positive predictions (how many predicted positives are actually true).
- **Recall**: Ability to correctly identify positive cases (sensitivity).
- **F1-score**: Harmonic mean of precision and recall, balancing both.
 
## Solution Methodology
### 1. Dataset Preprocessing
- Loaded the dataset (in .csv format).
- Checked null values and the data types of the features.
- Scaled numeric feature values using **StandardScaler**.

### 2. Model Implementation
- Implemented models using **scikit-learn**.
- Evaluated models on an **70-30 train-test split**.

### 3. Feature Importance Analysis
- Extracted feature importance scores using **Random Forest**.

### 4. Hyperparameter Tuning
- Optimized hyperparameters using **RandomizedSearchCV**.
- Used **StratifiedKFold cross-validation** to evaluate parameter combinations.


### 5. Visualization
- Plotted confusion matrices, ROC curves, and feature importance charts.

## Simulation Results
### Feature Importance
The most significant features were:
1. **PageValues**
2. **TotalPageDuration**
3. **ExitRates**
4. **TotalPageViews**
5. **BounceRates**
6. **Month**
7. **Region**
8. **TrafficType**
9. **Browser**
10. **OperationgSystems**


### Model Performance of all the models(Order by F1-Score)
| Model                  | Precision | Recall |  F1-Score | ROC-AUC | Accuracy |
|------------------------|-----------|--------|-----------|---------|----------|
| Random Forest     	 | 0.73   	 | 0.57   | 0.64      | 0.91    | 0.90     |
| Decision Tree 		 | 0.51      | 0.53   | 0.52      | 0.72    | 0.85     |
| Support Vector Machine | 0.72      | 0.39   | 0.50      | 0.88    | 0.88     |
| K-Nearest Neighbors    | 0.71      | 0.38   | 0.50      | 0.79    | 0.88     |
| Logistic Regression    | 0.71      | 0.34   | 0.46      | 0.89    | 0.88     |

### Radmon Forest Model Performance Metrics have best performance using best parameters 
					Test Data								Train Data
Performance			Precision 	Recall	F1-score	Precision 	Recall	F1-score
Original			0.71		0.54	0.61		-			-		-
SMOTE				0.59		0.69	0.64		-			-		-
K-Fold CV			0.72		0.50	0.59		0.74		0.57	0.64
SMOTE & K-Fold CV	0.61		0.70	0.65		0.62		0.74	0.67
Best Parameters		0.72		0.58	0.64		-			-		-



## Conclusion
- **Random Forest achieved the highest precision (72%), recall (58%), F1-score (64%) and ROC-AUC (92%)**.
- **PageValues, TotalPageDuration, ExitRates, TotalPageViews, BounceRates, Month, Region, TrafficType, Browser, OperationgSystems were the most important features**.
- Hyperparameter tuning slightly improved model precision, recall and F1-score.
- Visualization using confusion matrices and ROC curves provided deeper insights into model performance.

## References
Dataset Source: Online Shoppers Purchasing Intention Dataset [Dataset]. (2025). UCI Machine Learning Repository.

## Supplementary Material
- Full Python code and dataset available in files.

## Contribution
- **Ma May Mon Thant** – Analysis, Random Forest, KNN, Preparing Presentation.
- **Ko Myint Myat Aung Zaw** – Decision Tree, SVM.
- **Ma Nilar Win** – Preparing Readme, Logistics Regression, Preparing Presentation.


This README provides an overview of the project, methodologies, and results. For implementation details, refer to the full project report and code files.