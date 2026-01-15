<font size="+2.5" color='#27408B'><b> Capstone Project: Fraud Detection Analytics </b> </font>


This capstone project has a lifecycle analytics process with two phases in two separated notebooks:

<font size="+1.8" color='#27408B'><b> ❏  Phase 1: Exploratory Data Analysis (first notebook: Fraud Detection Analytics Phase 1 Exploratory Data Analysis.ipynb) </b> </font>
 - Data Input: carclaims.csv (raw data: https://www.kaggle.com/code/rashmiek99/vehicle-insurance-fraud-detection)
 - Data Output: df_cleaned (cleaned for modeling in Phase 2)

<font size="+1.8" color='#27408B'><b> ❏  Phase 2: Predictive Analytics (second notebook: Fraud Detection Analytics Phase 2 Predictive Analytics.ipynb) </b> </font>
 - Data Input: df_cleaned (cleaned from Phase 1)
 - Model Output: Predictive Analytics and Fraud Detection Insights
   

<img width="1446" height="1070" alt="image" src="https://github.com/user-attachments/assets/58946f64-e946-46f3-bcad-2e0a3a7132f4" />


***
<font size="+2" color='#27408B'><b> CONTENT </b> </font>

<font size="+2" color='#27408B'><b> ❏ Phase 1: Exploratory Data Analysis </b> </font>

### Section 1. Problem Statement
### Section 2. Datasets & Environment
### Section 3. Exploratory Data Analysis (EDA)
#### 3.1.	Initial Exploratory Data Review
#### 3.2.	Individual Variable Review and Visualization
#####  3.2.1. Target Variable / Label
#####  3.2.2. Continuous Variables
#####  3.2.3. Categorical Variables
#### 3.3 Data Cleaning
 Based on the data review:
 - 3.3.1. Data Fields Deleting:
    - PolicyNumber is not meaningful so dropped from this analysis
    - Age is dropped due to AgeOfPolicyholder capturing better data quality
    - Deductible is dropped due to very poor data quality
 - 3.3.2. Imputation: There are a few columns with value of 0 which was replaced by the most frequent values
     
### Exploratory Data Analysis Summary

#### 1. Overall Fraud Rate: The target variable / label shows only 6% of Claims are detected as Fraud which dataset is extremely imbalanced
  - Fraud cases: 923 (5.99%)
  - Non-fraud cases: 14,497 (94.01%) ➡️ Fraud is relatively rare, but patterns emerge across certain categories.

#### 2. Temporal Patterns
  - Months: Fraud peaks in March (7.5%), August (7.45%), and May (7.23%); lowest in November (3.83%).
  - Days of Week: Higher fraud on weekends (Saturday 6.66%, Sunday 6.99%) compared to weekdays.
  - Claim Timing: Mismatches between accident and claim dates show elevated fraud risk.

#### 3. Vehicle & Policy Features
  - Vehicle Category: Utility (11.25%) → highest fraud risk; Sedan (8.22%) → moderate risk; Sport (1.57%) → lowest risk.
  - Policy Type: Sport-Collision (13.79%), Utility-All Perils (12.06%), Sedan-All Perils (10.05%) → high risk; Sedan-Liability (0.72%) → very low risk.
  - Base Policy: All Perils (10.16%) shows higher fraud than Collision (7.29%) or Liability (0.72%).
  - Vehicle Price: Fraud is higher in low (<20k, 9.4%) and high (>69k, 8.7%) price ranges.

#### 4. Demographics
  - Sex: Males (6.29%) show higher fraud than females (4.34%).
  - Marital Status: Widows (8.57%) and divorced (3.95%) show elevated risk compared to married/single (~6%).
  - Age of Policy Holder: Younger policyholders are disproportionately associated with fraud.
    - 18–25 years → highest fraud (13–15%) vs. Older groups (41–65) → lower fraud (~5%).

#### 5. Claim & Accident Details
  - Fault: Policy Holder at fault → 7.89% fraud; Third Party at fault → 0.88%.
  - Accident Area: Rural (8.32%) vs. Urban (5.72%).
  - Police Report Filed: Fraud lower when reports are filed (3.74% vs. 6.05%).
  - Witness Present: Fraud lower when witnesses are present (3.45% vs. 6.0%).
    ➡️ Lack of external verification (no police report, no witness) correlates with higher fraud.

#### Key Insights
 - Fraud prevalence: Overall fraud is rare (~6%), but concentrated in specific demographics and policy/vehicle types.
 - Demographics: Younger drivers (18–25 years, 13–15% fraud), males (6.29%), and widowed policyholders (8.57%) show elevated risk compared to other groups.
 - Vehicle Category: Utility vehicles (11.25%) are riskiest, while Sport vehicles (1.57%) are lowest.
 - Policy Type: Complex policies such as Sport - Collision (13.79%), Utility - All Perils (12.06%), and Sedan - All Perils (10.05%) stand out as high-risk.
 - Seasonality: Fraud risk spikes in March (7.5%) and August (7.45%), with the lowest in November (3.83%).
 - Location & Evidence: Fraud is more common in rural areas (8.32%) and when no police report or witness is filed, suggesting external verification reduces fraud.
 - High-risk combinations: Profiles such as young male + Utility vehicle + All Perils policy represent strong predictive signals for modeling.

***

***

<font size="+2" color='#27408B'><b> ❏ Phase 2: Predictive Analytics </b> </font>


### Section 4.Feature Engineering
#### 4.1. Grouping by similar fraud risk/rate
#### 4.2. Creating indicator for very high or low fraud risk/rate
#### Feature Engineering Summary: 
 - 4 raw data fields were created by regrouping similar fraud risk
 - 5 indicators were created for high/low fraud risk
 - Benefits:
       - Stability (avoids inflated fraud % from tiny sample sizes),
       - Interpretability (easier to explain risk by broad categories)
       - Model performance (reduces dimensionality and prevents overfitting to rare categories)

### Section 5. Data Preprocessing
#### 5.1. Encoding
 - Data encoding for modeling
 - Correlation review
 - Initial Correlation Review and Quick Feature Selection: 
        - 20 binary variables highly corrected with target were selected from around 100 binary variables
 - Scaling - no need in this dataset and use case
   
#### 5.2. Splitting into train and test sets for modeling
#### 5.3. Upsampling to address the imbalanced data
 - The dataset is extremely imbalanced so the model performance is poor. To address the imbalanced target data concern, The following two methods were applied and the upscale one was better so included in this analytics:
    1) Upscale the Minority Class    (where FraudFound ==1) -- this was included in this notebook   
    2) Downsample the Majority Class (where FraudFound ==0) --> this was tested but not included in this notebook due to space concern

### Section 6. Feature Selection
 - Feature Importance Ranking
 - Correlation Review
   
### Section 7. Modeling & Tunning
 - Modeling on 5-fold CV, model testing and tuning to ensure generalizability
   - Logistic Regression   
   - Decision Tree 
   - Random Forest  
   - Gradient Boosting
   - XGBoost
   - Deep Learning / Deep Neural Networks

 - Hyperparameter tuning and grid search to improve model performance

### Section 8. Model Evaluation
  - Performance Metrices (Accuracy, Precision, Recall, F1, ROC-AUC)
  - Explainability
    
### Section 9. Model Deployment and Monitoring

### Executive Summary for Predictive Analytics

 - **Tuned Deep Neural Network (DNN) achieved the highest accuracy (93.39%)** and recall, which is critical for fraud detection because recall measures how many fraudulent cases we catch.
 - **XGBoost (91.89%)** and **Gradient Boosting (91.21%)** also performed strongly, offering a good balance of accuracy and ROC-AUC.
 - **Logistic Regression (90.01%) is competitive and highly interpretable**, which is important for compliance and audit trails.
 - **Decision Tree and Random Forest have lower accuracy (~77%) but very high precision (>92%)**, meaning they **minimize false positives—valuable when false alerts are costly**.

### Key Fraud Detection Insights

**1. Recall is King in Fraud Detection**

 - Missing a fraudulent transaction (false negative) is far more costly than flagging a legitimate one.
 - DNN’s recall (93.39%) makes it the best candidate for fraud detection because it catches the most fraud cases.


**2. Precision Trade-off**

 - High precision reduces false positives (legitimate transactions flagged as fraud).
 - Tree-based models have precision >92%, which is good for minimizing customer friction.
 - DNN has slightly lower precision (89%), so expect more false alerts—but this is acceptable in fraud prevention where catching fraud is priority.


**3. ROC-AUC Analysis**

 - XGBoost (0.824) and Gradient Boosting & Random Forest (0.812) lead in ROC-AUC, meaning they rank transactions well by fraud likelihood.
 - DNN’s ROC-AUC (0.803) is slightly lower, so probability calibration may need improvement for threshold tuning.

### Business Impact

 - **DNN** ensures maximum fraud detection coverage, reducing financial losses.
 - **XGBoost** offers strong performance and better probability ranking, useful for risk scoring and prioritization.
 - **Logistic Regression** provides interpretability for regulatory compliance and audit reporting.


### Recommended Strategy

 - **Primary Model**: Deploy Tuned DNN for real-time fraud detection where recall is critical.
 - **Secondary Model**: Use XGBoost for risk scoring and threshold-based alerts.
 - **Hybrid Approach**: Combine DNN for detection and XGBoost for ranking severity.
 - **Explainability**: Implement SHAP or LIME for transparency in fraud decisions.
   
### A Few Recommended Future Work
1. Data Expansion: incorporating more relevant data sources
2. Investigation: outliers and potential sampling biases
3. Multicollinearity Review: Use techniques like PCA or VIF to manage highly correlated features
4. Feature Engineering: Create meaningful features, composite features, and/or interaction terms.
	e.g.: Consider combining variables into interaction terms and review if the joint effect seems significant or not.

***
