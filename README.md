# 🤖 Machine Learning Projects

Welcome to my **Machine Learning Projects** repository! 🎯  
This repo showcases end-to-end projects where I apply **Data Science & ML** to solve real-world style business problems using Python.

Currently included:

1. 🏦 **Customer Delinquency Risk Prediction – Geldium (Credit Risk ML)**
2. 🧠 **Employee Wellness Prediction – Mental Health Treatment Classifier**

Each project is implemented in its own **Jupyter Notebook**, with full workflows from **EDA → Feature Engineering → Modelling → Evaluation**.

---

## 🧱 Tech Stack

- 🐍 **Python**
- 📓 **Jupyter Notebook**
- 📊 **Pandas, NumPy** – data manipulation
- 📈 **Matplotlib, Seaborn** – data visualisation
- 🤖 **Scikit-learn, XGBoost** – machine learning models
- 🧮 **Stats & ML concepts** – EDA, feature engineering, model comparison, metrics

---

## 📁 Projects Overview

---

### 🏦 1. Customer Delinquency Risk Prediction – Geldium
<img width="1047" height="601" alt="image" src="https://github.com/user-attachments/assets/1b29bb60-e6cd-4241-8237-5db14f6e0c13" />

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

### 🧠 2. Employee Wellness Prediction – Mental Health Treatment Classifier
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

