# 🛍️ Customer Conversion Prediction — Retail Web Session Intelligence (RWSI)

This project aims to predict **customer conversion likelihood** (whether a visitor makes a purchase) using behavioral and session-based data from a retail website.  
By analyzing the **Retail Web Session Intelligence (RWSI)** dataset, we explore patterns in user engagement, browsing behavior, and contextual factors to improve marketing efficiency and customer targeting.

---

## 🎯 Objectives
- Understand the key factors driving customer conversions.
- Handle missing values and categorical variables effectively.
- Address multicollinearity and outliers.
- Compare preprocessing approaches:
  - **Standardization (StandardScaler)**
- Apply **feature selection using VIF (Variance Inflation Factor)**.
- Handle **class imbalance using SMOTE**.
- Compare model performance of:
  - Logistic Regression  
  - Random Forest  
  - XGBoost (with hyperparameter tuning)

---

##  Dataset Description
**Dataset:** Retail Web Session Intelligence (RWSI)

Each record represents an anonymized customer session on a retail website.  
Key features include:

| Feature | Description |
|----------|-------------|
| `SessionID` | Unique session identifier |
| `AdClicks` | Number of ads clicked during the session |
| `InfoSectionCount` | Count of product info sections viewed |
| `InfoSectionTime` | Time spent reading product information |
| `HelpPageVisits` | Visits to help or FAQ pages |
| `HelpPageTime` | Time spent on help pages |
| `ItemBrowseCount` | Number of items browsed |
| `ItemBrowseTime` | Time spent browsing items |
| `SessionExitRatio` | Ratio of exits before purchase |
| `ExitRateFirstPage` | If user left on first page |
| `PageEngagementScore` | Overall engagement metric |
| `HolidayProximityIndex` | Closeness to a holiday (affects buying intent) |
| `VisitMonth` | Month of the visit |
| `UserPlatformID` | Platform used (web/mobile) |
| `TrafficSourceCode` | Source of traffic (ad, organic, referral, etc.) |
| `IsWeekendVisit` | Whether the visit occurred on weekend |
| `Conversion` | Target variable (1 = Purchase, 0 = No Purchase) |

---

##  Data Preprocessing Steps

### 1 Handling Missing Values
- Missing categorical values were replaced with `"Unknown"` to avoid dropping valuable records.
- Numerical features were imputed using **median** values.

### 2 Encoding
- Applied **Label Encoding** for binary features.
- Used **One-Hot Encoding** for categorical variables with multiple categories.



### 3 Feature Scaling
Two scaling techniques were compared:
- **Standardization (StandardScaler):** centers data to mean 0 and variance 1.  
- **Normalization (MinMaxScaler):** rescales values to range [0, 1].

### 4 Multicollinearity Check (VIF)
- Used **Variance Inflation Factor (VIF)** to detect correlated features.  
- Features with **VIF > 10** were candidates for removal.  
- No features were dropped as all VIF values were within acceptable range.

### 5 Class Imbalance Handling
- Applied **SMOTE (Synthetic Minority Oversampling Technique)** to balance conversion (1) and non-conversion (0) samples.

---

## 🤖 Models Implemented

| Model | Description | Notes |
|--------|--------------|-------|
| **Logistic Regression** | Interpretable linear model | Best with StandardScaler |
| **Random Forest** | Ensemble of decision trees | Better recall than Logistic Regression |
| **XGBoost** | Gradient boosting ensemble | Highest ROC-AUC after hyperparameter tuning |

---

## ⚙️ XGBoost Hyperparameter Tuning
Grid Search with 5-fold cross-validation was used to find the best parameters:


---

## 📊 Model Evaluation Metrics

| Model | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-Score (Class 1) | ROC-AUC |
|--------|-----------|--------------------|------------------|--------------------|----------|
| **Logistic Regression** | 0.86 | 0.53 | 0.70 | 0.61 | **0.861** |
| **Random Forest** | 0.88 | 0.62 | 0.64 | 0.63 | **0.895** |
| **XGBoost** | 0.90 | 0.75 | 0.54 | 0.62 | **0.915** |

---



---

## 📈 Confusion Matrix (XGBoost)

| Actual / Predicted | 0 | 1 |
|---------------------|---|---|
| **0** | 2014 | 70 |
| **1** | 177 | 205 |

---

## 🧠 Insights from EDA
- **Weekend visits** were slightly more likely to result in conversions.  
- **Higher `PageEngagementScore`** strongly correlated with conversion.  
- **`SessionExitRatio`** and **`ExitRateFirstPage`** negatively impacted purchase likelihood.  
- **Holiday proximity** boosted conversion probability.  
- **Multicollinearity handling (VIF)** helped make feature relationships more stable and interpretable.

---

## 🧰 Tech Stack
- **Python**
- **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**
- **Scikit-learn** (Logistic Regression, Random Forest, SMOTE)
- **XGBoost**
- **Statsmodels** (for VIF analysis)




Standardization improved performance for Logistic Regression.
Random Forest balanced precision and recall well.
SMOTE successfully addressed class imbalance, improving recall and F1-score.
XGBoost achieved the best overall ROC-AUC (0.915) with tuned parameters.
🧑‍💻 Author

Aryan Tyagi
📧 Email: at9120140@gmail.com

🔗 GitHub: https://github.com/aryantyagi0
