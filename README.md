# PROJECT-REPORT-FOR-LOAN-DEFAULT-PREDICTION-
This is a project report explaining project methodology and
1. INTRODUCTION
This is a project report explaining project methodology and results, this report focuses on predicting loan repayment outcomes using historical client and loan application data. The target variable is “Good and Bad Flag”, which indicates whether a client repaid their loan as expected (good) or defaulted (bad).
The goal is to:
1. Perform data cleaning and exploratory data analysis (EDA).
2. Apply feature engineering for better predictive power.
3. Train and evaluate multiple machine learning models.
4. Build an interactive Power BI dashboard for business insights.
5. Deploy the best-performing model using Streamlit app for demonstration.

2. METHODOLOGY
2.1. DATA PREPARATION
•	Merging datasets: Three raw datasets were provided, cleaned individually, and merged on “Customer Id” and related keys.
•	Cleaning steps: For the cleaning, the following steps were meticulously implemented.
1)	Removed duplicate rows (Dataset 2).
2)	Handled missing values:
a)	Categorical: filled with most frequent class or domain-driven replacements (e.g., “employment_status_clients” → “unemployed”).
b)	Numerical: filled with median values to reduce sensitivity to outliers.
c)	Standardized column formats (dates converted to “datetime”, categorical to lowercase strings).
3)	Encoded “Good_Bad_Flag” as binary (1 = bad, 0 = good).

2.2. EXPLORATORY DATA ANALYSIS (EDA)
•	Descriptive statistics: Summary of numerical/categorical columns.
•	Univariate analysis: Distribution plots for numerical features (e.g., loan amount, total due). Skewness identified in several monetary columns.
•	Bivariate/Multivariate analysis:
1)	Correlations: strong correlation was observed between “loan_amount” and “total_due”.
2)	Relationship with target: I noticed that clients with higher outstanding balances were more likely to default.
3)	Target balance: the dataset exhibited mild imbalance (\~70% good vs. 30% bad).

2.3. FEATURE ENGINEERING
1) Date features: Extracted year, month, day from “Approved date” and “Creation date”.
2) Duration feature: Created “loan_frequency = (Loan Number / Term Days)” as well as "repayment_ratio = (Loan Amount / Total Due)".
3) Categorical encoding:	Ordinal encoding for “education_level” and “employment_status_clients”.
4) Numerical Scaling: StandardScaler applied to continuous features (loan amounts, balances).
5)	Feature selection:
a)	Variance threshold used to remove low-variance columns.
b)	Correlation analysis removed highly correlated (>0.9) redundant features.
c)	Recursive Feature Elimination (RFE) narrowed down the most predictive features.


2.4. MODELING
Five machine learning models were trained:
1)	Logistic Regression
2)	Random Forest Classifier
3)	Gradient Boosting (XGBoost)
4)	Support Vector Classifier (SVC)
5)	K-Nearest Neighbors (KNN)
•	Training/Test Split: 80/20 stratified split.
•	Imbalance Handling: Used SMOTE to oversample minority (bad loans).

2.5. EVALUATION METRICS
1)	The models were evaluated on:
2)	Accuracy: overall correctness.
3)	Precision/Recall/F1-score: handling of minority class.
4)	ROC-AUC: probability discrimination ability.
5)	Confusion Matrix: classification trade-offs.

 2.6. RESULTS

MODEL	ACCURACY	PRESCISION	RECALL	F1-SCORE	ROC-AUC

RANDOM FOREST	0.926160	0.920536	0.995283	0.956451	0.969966

GRADIENT BOOSTING	0.853143	0.850475	0.994609	0.916913	0.869923

K-NEAREST NEIGHBORS	0.827615	0.854760	0.949798	0.899777	0.771342

SUPPORT VECTOR MACHINE	0.821576	0.820343	1.000000	0.901306	0.763297

LOGISTIC REGRESSION	0.816909	0.818610	0.995957	0.898617	0.657490


•	Best Model: Random Forest achieved the best performance with 92% accuracy and 0.96 ROC-AUC. Gradient Boosting was close behind.

2.7. DASHBOARD (POWER BI)
A Power BI dashboard was built to help stakeholders explore:
1)	Loan portfolio distribution by employment status, education, and region.
2)	Default rates across loan amounts, durations, and approval dates.
3)	KPI cards: default rate (%), total loans approved, average loan amount.

2.8. DEPLOYMENT
The final Random Forest model was exported as a “.pkl” file and deployed via Streamlit:
1)	Input modes: Batch scoring (CSV upload) or single input (form).
2)	Outputs: Predicted label (Good/Bad), default probability, and customizable threshold.
3)	Hosted on Streamlit Cloud for easy access.

2.9. CONCLUSION
•	Data cleaning and feature engineering significantly improved model performance.
•	Random Forest proved most effective, offering both high predictive power and interpretability.
•	The Power BI dashboard enables actionable insights for loan officers and managers.
•	Streamlit deployment allows real-time scoring, bridging the gap between data science and decision making.
FUTURE WORK:
•	I’ll try to integrate real-time API for live loan scoring.
•	Use advanced ensemble models (e.g., LightGBM, CatBoost).
•	Expand feature set with external credit bureau or financial behavior data.

 results, this report focuses on predicting loan repayment outcomes using historical client and loan application data. 
