# 💳👩🏻‍💻Customer Delinquency Risk Prediction – Geldium (Gen-AI Data Analytics)
<img width="698" height="392" alt="image" src="https://github.com/user-attachments/assets/abd0e8d0-00ce-44a8-a0b9-00dbbedf6f3c" />


This repository contains my end-to-end **Machine Learning Project** from the
📽️**Tata/Forage “Gen-AI Data Analytics” virtual experience**.

The goal is to help a fictional fintech company **Geldium** identify **high-risk
customers** who are likely to become **delinquent on their payments**, and to
understand *why* they are risky so that business teams can design proactive
interventions.

>👾 **Tech stack:** Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn  

> 📁**Main file:** `Forage.ipynb`


---

## 🧩 Problem Statement

Geldium provides consumer credit products and wants to:

1. **Predict** which customers are likely to miss several upcoming payments.
2. **Explain** the drivers of delinquency in a way that is transparent and
   regulator-friendly.
3. **Balance** model performance with fairness, interpretability and ease of
   deployment.

Using a historical payment dataset, the task is to build and compare ML models
that classify customers into:

- `High_Risk_Customer` – customers with **3+ recent late/missed payments**  
- `Low_Risk_Customer` – everyone else

and then recommend the best model & pipeline for production.


---

## 📂 Dataset

Synthetic customer-level dataset (`Forage_Deliquency.xlsx`, provided by Forage)
containing **several thousand anonymised customers** with features such as:

- `Age`
- `Income`
- `Credit_Score`
- `Credit_Utilization`
- `Loan_Balance`
- `Missed_Payments` (historical)
- `Late_Missed_Count` (recent 6-month window)
- `Employment_Status` (encoded into `Employment_Status_Encoded`)
- Derived features: `Debt_to_Income_Ratio`, `Account_Tenure`, etc.

---
## 🔍 Exploratory Data Analysis (EDA)

The notebook first focuses on **understanding the data and its quality**.

### 1️⃣ Structure & Data Quality

- ✅ Inspected **shape, dtypes, summary statistics and value ranges**.  
- 🔎 Identified **missing values** in numeric features such as `Income`, `Loan_Balance` and occasionally `Credit_Score`.  
- 📊 Created a **missing-data table** with counts and percentages to decide how each column should be treated.

### 2️⃣ Handling Missing Data

- 🧹 For `Income`, `Loan_Balance`, `Credit_Score` → **imputed with median values** to keep the distribution robust to outliers.  
- ✔️ Verified that the total number of missing values after treatment is **zero**.

### 3️⃣ Behaviour & Risk Patterns

Multiple visualisations are created to understand delinquency drivers:
- 📈 **Distribution of** Late_Missed_Count – shows how many customers are repeatedly late.
- 📉 **Credit Score vs Late Payments** – lower scores cluster around higher late-payment counts.
- 📊 **Credit Utilization vs Late Payments** – high utilisation is strongly associated with risk.
- 🔁 **Total Missed_Payments vs recent late payments** – shows that historical behaviour predicts future behaviour.

These plots confirm intuitive risk patterns:
- ⚠️ Customers with **lower credit scores, higher utilisation** and **more historical** missed payments are more likely to be **high risk**.
- 💰 **Income** and **Debt-to-Income ratio** also show clear separation between low-risk and high-risk segments.

---

## 🧮 Feature Engineering & Selection

Key steps to prepare data for modelling:
### 🎯 Target Creation
<img width="697" height="58" alt="image" src="https://github.com/user-attachments/assets/74b91d82-9c84-499e-8a0c-d44ed98c884a" />

Customers with Late_Missed_Count >= 3 are labelled as **High Risk (1)**, others as **Low Risk (0)**.

### 🔡 Encoding Categorical Features
<img width="570" height="295" alt="image" src="https://github.com/user-attachments/assets/558438d1-699e-4a80-b84e-baf355b40895" />
This converts Employment_Status into a numeric feature for modelling.

### 🧱 Feature Candidates
<img width="607" height="165" alt="image" src="https://github.com/user-attachments/assets/1049e745-a033-46be-a005-47dc64fdfba4" />
These features are used as inputs to the machine learning models.

### ⚙️ Standardisation & Train/Test Split
- 📏 Numerical features are **standardised** using StandardScaler.
- ✂️ Data is split into **training** and **test sets** with train_test_split to evaluate generalisation.

### ⭐ Feature Importance (ANOVA F-test)
- Used SelectKBest(f_classif) to **rank all candidate features** and select the **top 5 most predictive variables**.
- A **correlation heatmap** is plotted to check **multicollinearity** and relationships between features.

---

## 🤖 Model Development

Two main models are trained and compared:
### 1️⃣ Logistic Regression – Simple & Interpretable
- ⚖️ class_weight="balanced" to handle class imbalance.
- 📏 Features are **standardised**.
- 🔧 Hyperparameters tuned using GridSearchCV:
    - Regularisation strength
    - Penalty
    - Solver
    - Class weights

### 2️⃣ Random Forest Classifier – Non-linear Baseline
- 🌳 Able to capture non-linear relationships and feature interactions.
- 🔧 Tuned hyperparameters include:
      - Number of trees (n_estimators)
      - Maximum depth (max_depth)
      - Minimum samples split (min_samples_split)
      - Minimum samples leaf (min_samples_leaf)
      - Class weights

### 📏 Evaluation Metrics
Both models are evaluated on the test set using:
- ✅ Accuracy
- 🎯 Precision
- 📉 Recall
- ⚖️ F1 Score
- 📈 ROC–AUC Score
- ⏱ Training time

### 🧠 Feature Importance Analysis
- 🧮 **Logistic Regression coefficients** – show the **direction and strength** of impact for each feature.
- 🌲 **Random Forest feature importances** – show the **relative contribution** of each feature in a non-linear model.

---
## 📊 Results & Insights
Exact numbers may vary with different random splits / hyperparameters, but the overall pattern is:

### ✅ Overall Performance
- Both models achieve **strong classification performance**, with **Logistic Regression** and **Random Forest** showing very similar **AUC and F1 scores**.
- **Random Forest**:
  - Slightly better on **pure predictive power**, especially for complex interactions.
- **Logistic Regression**:
  - **Fully transparent** and **faster** to train and infer.

### 🆚 Model Comparison
The notebook includes:
- 📋 A **comparison table** summarising **metrics** for both models.
- ⚖️ A **pros & cons** matrix comparing Logistic Regression vs Random Forest across:
  - Interpretability
  - Performance
  - Speed
  - Deployment complexity
  - Regulatory compliance
  - Maintenance
- 📊 Visual comparison of **feature importance** between both models.
---

## 🏆 Selected Model
Final Choice: ✅ Optimised Logistic Regression

### 💡 Why Logistic Regression?
- 📈 **Strong, stable performance** with competitive AUC/F1 compared to Random Forest.
- 🔍 Transparent feature coefficients support **regulatory compliance** and **fair-lending requirements**.
- 🗣 Easy to explain to non-technical stakeholders
  → e.g., “this feature increases risk by X%”.
- ⚙️ Lightweight and simple to integrate into existing **risk engines** and **decision workflows**.
---

## 🔄 Final Pipeline (Conceptual)

<img width="457" height="321" alt="image" src="https://github.com/user-attachments/assets/0f11c53d-de9d-4de8-a93b-427a12769037" />

---
## ⚖️ Fairness & Governance Considerations
The notebook also designs a **fairness monitoring framework** for future production use.

- **👥 Protected Attributes to Monitor**
  - Age groups
  - Income bands
  - Credit profile tiers

- **📐 Fairness Metrics (Conceptual)**
  - ⚖️ Statistical parity – selection rates across groups
  - 🚨 Predictive equality – false-positive rates
  - 🟰 Equalised odds – error rates across groups
  - 🎯 Treatment equity – precision by group

---

## 🧾 Key Takeaways
- Built a complete **credit-risk classification pipeline** from raw Excel data to cleaned dataset, EDA, feature engineering and model selection.
- Compared a **simple interpretable model (Logistic Regression)** with a more complex **Random Forest** baseline.
- Selected Logistic Regression as the **final model** due to its balance of performance, interpretability and regulatory alignment.
- Produced **artifacts** (cleaned data, text summary, plots) that can be used by risk, product and collections teams to understand and act on delinquency risk.
