---
title: ReadMe

---

________________________________________
## Employee Turnover Prediction with Machine Learning
This project aims to predict employee attrition (whether an employee left the company or not) using machine learning models such as K-Nearest Neighbors (KNN) , Support Vector Machine (SVM), Logistic Regression and Naïve Bayes Classifier.The dataset comes from Zenodo's 2024 HR Analytics Dataset.
________________________________________
### Project Overview
Employee attrition is one of the major challenges faced by many organizations. Identifying employees at risk of leaving allows companies to take proactive measures in improving job satisfaction and retention.

In this project:
•	We preprocess the HR dataset (handling duplicates, encoding categorical features, scaling, etc.)
•	We train classification models (KNN, SVM, Logistic Regression, Naive Bayes)
•	We evaluate models using confusion matrix, classification report, and accuracy metrics (precision, recall, AUC score)

________________________________________
### Dataset
- Source: Zenodo HR Analytics Dataset
- Size: 14,999 observations
•	Target Variable: left
        0 → Employee stayed
        1 → Employee left
- Features (18 total):
- Continuous features: satisfaction_level, last_evaluation, average_montly_hours, time_spend_company
- Categorical: department (nominal), salary (ordinal)
- Binary: Work_accident, promotion_last_5years
________________________________________
### Data Preprocessing
•	Checked and removed duplicate rows
•	Applied one-hot encoding for sales (department)
•	Applied label encoding for salary (ordinal: low < medium < high)
•	Scaled features using MinMaxScaler (important for KNN and SVM)
•	Split dataset into training (80%) and testing (20%) sets
________________________________________
### Models Implementation Process 
![model_implementation](https://hackmd.io/_uploads/SyhH6Bb9xg.jpg)

________________________________________
### Visualizations
•	Heatmap-style Confusion Matrix 
•	Classification Reports
•   Precision - Recall Comparison Curve 
•   ROC Curve Comparison 

________________________________________
# Requirements
•	Python 3.8+
•	pandas
•	numpy
•	scikit-learn
•	seaborn
•	matplotlib
Install them using:
pip install pandas numpy scikit-learn seaborn matplotlib
________________________________________
### Future Work
•    Plan to extend this project by collecting key features (e.g., satisfaction level,
number of projects, working hours, tenure, work accidents, promotions,
department, salary, left) from Myanmar employees
•    Collect data anonymously from employees via Google Forms, without including
any personally identifiable information (PII)
•    Experiment with other models like Random Forest and XGBoost
	
________________________________________
### License
This project is licensed under the MIT License.
________________________________________

