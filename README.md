# 🤖 Machine Learning Projects

# 🧠📊 Machine Learning Projects Portfolio

This repository contains three fundamental machine learning projects covering:

- 🔢 Linear Regression: Brain Mass Prediction
- ❤️ Logistic Regression: Credit Card Deliquency, Employee Wellness Prediction
- 🛍️ K-Means Clustering: Mall Customers Segmentation, Credit Card Data

Each project demonstrates data preprocessing, modeling, evaluation, and insights tailored for real-world applications.

---

## 🔢 Brain Weight Prediction using Linear Regression

### 📋 Project Overview

This project uses Linear Regression to predict brain mass based on head size, age, and gender. It serves as an introduction to regression modeling, exploring how physiological features relate to brain weight.

### 🗂️ Dataset Description

The dataset is compiled from a medical study with the following features:

| Feature     | Type       | Description                           |
|-------------|------------|---------------------------------------|
| Gender      | Categorical| Male / Female                         |
| AgeGroup    | Categorical| Age category (e.g., 20–30, 30–40)     |
| Head Size   | Continuous | Head circumference (cm³)              |
| Brain Weight| Continuous | Brain mass (grams)                    |

### ⚙️ Methodology

- Encoded categorical variables (Gender, AgeGroup)
- Performed correlation analysis
- Built a Linear Regression model
- Evaluated with MAE, MSE, RMSE, and R²

### 📈 Results

| Metric        | Value       |
|---------------|-------------|
| MAE           | ~30 g       |
| MSE           | ~1700       |
| RMSE          | ~41.23 g    |
| R² Score      | ~0.85       |

### 🔍 Insights

- Head size had a strong positive correlation with brain weight.
- Age group showed moderate influence.
- The model explains ~85% of variance.

---
## 🛍️ Customer Segmentation using K-Means Clustering

### 📋 Project Overview

K-Means clustering is applied to identify customer segments based on Annual Income and Spending Score. Useful for targeted marketing strategies.

### 🗂️ Dataset Description

**File:** `Mall_Customers.csv`  
**Size:** 200 records  
**Source:** Kaggle

| Column               | Type      | Description                                  |
|----------------------|-----------|----------------------------------------------|
| CustomerID           | Integer   | Unique customer ID                           |
| Gender               | Categorical | Male/Female                               |
| Age                  | Integer   | Age of customer                              |
| Annual Income (k$)   | Integer   | Annual income in $1000s                      |
| Spending Score (1–100)| Integer  | Mall-assigned spending score                 |

### ⚙️ Methodology

- Selected features: `Annual Income` and `Spending Score`
- Scaled features using StandardScaler
- Used the elbow method to determine optimal `k=5`
- Applied K-Means clustering
- Interpreted clusters by centers

### 📊 Cluster Centers (k=5)

| Cluster | Income (k$) | Spending Score |
|---------|-------------|----------------|
| 0       | 55.30       | 49.52          |
| 1       | 86.54       | 82.13          |
| 2       | 25.73       | 79.36          |
| 3       | 88.20       | 17.11          |
| 4       | 26.30       | 20.91          |

### 🔍 Interpretation

- **Cluster 1**: High income & high spending → Premium segment
- **Cluster 2**: Low income & high spending → Impulse buyers
- **Cluster 3**: High income & low spending → Frugal rich
- **Cluster 4**: Low income & low spending → Budget group
- **Cluster 0**: Average income & spending → Regulars

### 📈 Evaluation

- Used Elbow Method and Silhouette Score (~0.56) for quality
- Clusters are interpretable and useful for campaign targeting

---

### 🏦 Customer Delinquency Risk Prediction – Geldium
<img width="698" height="392" alt="image" src="https://github.com/user-attachments/assets/f908328f-3793-41f4-ae3d-15dac30723de" />

**Goal:**  
Help a fictional fintech company **Geldium** identify **high-risk customers** likely to become **delinquent on their payments**, and understand *why* they are risky.

**Highlights:**

- 🔍 Framed as a **binary classification** task:
  - Predict whether a customer is **High_Risk** based on recent and historical payment patterns.
- 📊 Performed **EDA** to understand:
  - Late/missed payment patterns  
  - Relationship between credit score, utilisation and risk  
- 🧮 Feature engineering:
  - Created a `High_Risk_Customer` label  
  - Encoded categorical features like employment status  
  - Built a feature set from income, credit score, utilisation, debt-to-income ratio, tenure, etc.
- 🤖 Models:
  - **Logistic Regression** (interpretable baseline)  
  - **Random Forest Classifier** (non-linear benchmark)
- 📏 Evaluation:
  - Accuracy, Precision, Recall, F1, ROC–AUC  
  - Feature importance comparison  
- 🏆 Final Choice:
  - **Optimised Logistic Regression** chosen for its balance of **performance + interpretability + ease of deployment**.
- ⚖️ Extra:
  - Designed a **fairness monitoring framework** concept (age groups, income bands, credit tiers).

**Main file:**  
`Forage.ipynb`

---

### 🧠Employee Wellness Prediction – Mental Health Treatment Classifier
<img width="723" height="677" alt="image" src="https://github.com/user-attachments/assets/51e75d09-0193-4013-9c87-8a8c39f5a1dd" />

**Goal:**  
Enable a tech company to **identify employees who may need mental health treatment** using HR and survey data, and highlight factors driving mental health risks.

**Highlights:**

- 🎯 Framed as a **binary classification** problem:
  - Predict whether an employee needs **treatment** (`Yes` / `No`).
- 🧹 Data cleaning:
  - Fixed inconsistent `Age` values and created age bins  
  - Normalised messy `Gender` entries (e.g. “M”, “male”, “femail”, etc.)  
  - Mapped `Country` into broader **regions**  
  - Dropped sparse / non-informative columns (e.g. long free-text comments)
- 🔡 Encoded:
  - Binary questions (Yes/No)  
  - Ordinal scales (e.g. consequences, ease of leave)  
  - Employer support and anonymity awareness  
- 📊 EDA:
  - Analysed how **family history, work interference, benefits, leave policy, supervisor/coworker support** relate to treatment.
- 🤖 Models:
  - **Logistic Regression**  
  - **Random Forest Classifier**  
  - **XGBoost Classifier**
- 📏 Evaluation:
  - Train/test evaluation + **Stratified Cross-Validation**  
  - Accuracy, Precision, Recall, F1-score, ROC–AUC, confusion matrix.
- 💡 Insights:
  - Key drivers: family history, work interference, perceived consequences, quality of benefits & wellness programs.
  - These insights can help HR teams design **better wellness initiatives**.

**Main file:**  
`Final_Hackathon.ipynb`

---

## 🧱 Tech Stack

- 🐍 **Python**
- 📓 **Jupyter Notebook**
- 📊 **Pandas, NumPy** – data manipulation
- 📈 **Matplotlib, Seaborn** – data visualisation
- 🤖 **Scikit-learn, XGBoost** – machine learning models
- 🧮 **Stats & ML concepts** – EDA, feature engineering, model comparison, metrics

---

