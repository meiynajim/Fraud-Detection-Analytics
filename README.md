## Capstone Project: Insurance Fraud Detection Analytics 

This capstone project have two parts with two separated notebooks:

- **❏  Part 1: Initial Report and Exploratory Data Analysis (this notebook)**

- ❏  Part 2: Predictive Modeling (second notebook)


***

### ❏ Part 1: Initial Report and Exploratory Data Analysis

### Section 1. Problem statement

### Section 2. Datasets & Environment you want to use


### Section 3. Initial Exploratory Data Analysis
#### 3.1.	Exploratory Data Review
#### 3.2.	Variable Review and Visualization
#####  3.2.1. Target Variable / Label
#####  3.2.2. Continuous Variables
#####  3.2.3. Categorical Variables
     
#### 3.3 EDA Summary

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

### Key Insights
 - Fraud prevalence: Overall fraud is rare (~6%), but concentrated in specific demographics and policy/vehicle types.
 - Demographics: Younger drivers (18–25 years, 13–15% fraud), males (6.29%), and widowed policyholders (8.57%) show elevated risk compared to other groups.
 - Vehicle Category: Utility vehicles (11.25%) are riskiest, while Sport vehicles (1.57%) are lowest.
 - Policy Type: Complex policies such as Sport - Collision (13.79%), Utility - All Perils (12.06%), and Sedan - All Perils (10.05%) stand out as high-risk.
 - Seasonality: Fraud risk spikes in March (7.5%) and August (7.45%), with the lowest in November (3.83%).
 - Location & Evidence: Fraud is more common in rural areas (8.32%) and when no police report or witness is filed, suggesting external verification reduces fraud.
 - High-risk combinations: Profiles such as young male + Utility vehicle + All Perils policy represent strong predictive signals for modeling.

   
### Section 4. Data Preprocessing / Preparation
#### 4.1 Data Cleaning 
#### 4.2 Feature Engineering - grouping by similar fraud risk/rate
#### 4.3 Encoding
#### 4.4 Initial Correlation Analysis Review and Quick Feature Selection
#### 4.5 Data splitting into train and test sets	
#### 4.6 Data Propressing / Preparation Summary
#### 1.  Data Cleaning:
   - Some minor data cleaning was performed given there were no obvious missing values but some zero and none values
   - There were 15K unique PolicyNumbers,  which were not included as it is not meaningful for  this analysis
   - 'RepNumber','Deductible' data fields were dropped from this analysis due to insignificant contribution to fraud detection
     
#### 2. Feature engineering: 8 data fields were regrouped based on similar fraud risk for better stability (avoids inflated fraud % from tiny sample sizes), interpretability (easier to explain risk by broad categories), and model performance (reduces dimensionality and prevents overfitting to rare categories).

#### 3. Encoding: Data was encoded for correlation review and modeling

#### 4. Initial Correlation Review and Quick Feature Selection: 20 binary variables were selected from around 100 binary variables for baseline models  

#### 5. Data Propressing / Preparation:  data was split into train and test sets for modeling


### Section 5. Initial Baseline Model
#### 5.1 Logistic Regression
#### 5.2 RandomForest Classifier
#### 5.3 Initial Baseline Model Summary

#### 1. Baseline Model Performance Comparison: 
- Both Logistic Regression and RandomForest mode performance were not desirable due to extremely imbalanced target / label
#### 2. To address the imbalanced target data concern, there are two ways in testing:
- Upscale the Minority Class    (where FraudFound ==1)    
- Downsample the Majority Class (where FraudFound ==0)

***
### ❏ Next Steps 

Part 2: Predictive Modeling (Tentative)

#### Section 1. Feature Engineering & Selection
#### Section 2. Modeling: training, testing, and evaluation
1.	Baseline Models + More ML Models
2.  Model Optimization: model tuning, testing, and validation to ensure generalizability
 - The dataset is extremely imbalanced so the model performance is poor. To address the imbalanced target data concern, there are two ways:
    1) Upscale the Minority Class    (where FraudFound ==1)    
    2) Downsample the Majority Class (where FraudFound ==0)
 - Utilize Hyperparameter tuning and grid search to improve model performance
   
#### Section 3. Summary

#### Section 4.  Next Steps and Recommendations
1. Data Expansion: Investigate outliers, duplicates, and potential sampling biases
2. Multicollinearity Review: Use techniques like PCA or VIF to manage highly correlated features
3. Feature Engineering: Create meaningful features, composite features, and/or interaction terms.
•	e.g.: Consider combining variables into interaction terms and review if the joint effect seems significant or not.
4. Feature Selection: Rank feature importance via statistical or model-based methods
5. Predictive Modeling: Train models using logistic regression, decision trees, or ensemble methods to predict coupon acceptance with the main impactful variables which could be used to verify hypotheses around variable impact
6. Model Optimization: model tuning, testing, and validation to ensure generalizability

***
