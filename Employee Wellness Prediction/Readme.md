# 🧠 Employee Wellness Prediction – Mental Health Treatment Classifier
<img width="708" height="697" alt="image" src="https://github.com/user-attachments/assets/9f6984e3-6349-42f0-95c3-eae9ef4df51a" />

This repository contains a **Machine Learning Project** that predicts whether an employee is likely to **need mental health treatment**, based on demographic details, work environment and perceptions about mental health.

The entire end-to-end workflow – from **data cleaning, EDA and feature engineering to model training and evaluation** – is implemented in the Jupyter notebook included in this repo.

---

## 📌 Problem Statement

After a serious incident involving an employee’s mental health, a tech company wants to **proactively identify employees who may need support** using the data they already collect through HR and surveys.

The goals of this project are to:

- 🔍 **Predict** whether an employee is likely to need mental health treatment  
- 🧭 **Understand key risk factors** (family history, work interference, support systems, leave policies, etc.)  
- 🛠️ Enable organisations to design **targeted wellness programs** and improve employee well-being and productivity  

The problem is framed as a **binary classification task** with the target variable:

> `treatment` → “Yes” (needs treatment) / “No” (does not need treatment)

---

## 🧱 Tech Stack

- 🐍 **Python**
- 📓 **Jupyter Notebook**
- 📊 **Pandas, NumPy** – data manipulation
- 📈 **Matplotlib, Seaborn** – visualisation
- 🤖 **Scikit-learn, XGBoost** – machine learning models & evaluation

All implementation details (code, plots, experiments) are inside the `.ipynb` notebook.

---

## 📂 Data Description

The dataset (train & test CSVs from the hackathon) contains:

### 👤 Demographics
- `Age`
- `Gender`
- `Country`

- 👨‍💻 **Employment & Work Context**  
  - `self_employed` – Are you self-employed?  
  - `no_employees` – Size of the company  
  - `remote_work` – Do you work remotely at least 50% of the time?  
  - `tech_company` – Is your employer primarily a tech company?

- 🧠 **Mental Health Awareness & Support**  
  - `family_history` – Family history of mental illness  
  - `work_interfere` – Does mental health interfere with work?  
  - `benefits` – Mental health benefits provided by employer  
  - `care_options` – Awareness of care options  
  - `wellness_program` – Wellness programs discussing mental health  
  - `seek_help` – Availability of resources to learn & seek help  
  - `anonymity` – Is anonymity protected when using mental health resources?

- 🏥 **Perceptions Around Disclosure**  
  - `leave` – Ease of taking medical leave for mental health  
  - `mental_health_consequence` – Perceived negative consequences for discussing mental health  
  - `phys_health_consequence` – Perceived consequences for physical health issues  
  - `coworkers` – Comfort discussing with coworkers  
  - `supervisor` – Comfort discussing with supervisors  
  - `mental_health_interview` – Willingness to mention mental health in an interview  
  - `phys_health_interview` – Willingness to mention physical health in an interview  
  - `mental_vs_physical` – Does employer take mental health as seriously as physical?

- 🔍 **Other**  
  - `obs_consequence` – Observed negative consequences for coworkers  
  - `comments` – Free-text comments (later dropped due to sparsity)

- 🎯 **Target Variable (train only)**  
  - `treatment` – Does the employee need treatment? (`Yes` / `No`)

Free-text and highly sparse fields (e.g., `comments`) are not used in the final model.

---

## 🔎 Approach

The full pipeline is implemented step-by-step in the notebook. At a high level:

### 1️⃣ Data Cleaning & Preparation

- 🧹 Removed or re-purposed columns that were not useful (e.g. timestamp, state, free-text comments).
- 🎂 Cleaned and normalised **Age** (fixed unrealistic values and created meaningful age bins).
- 🚻 Standardised **Gender** values (many messy variations) into a small set of categories.
- 🌍 Reduced **Country** granularity by mapping to broader **regions** (e.g. Asia, Europe, North America).
- 🧩 Handled missing values using sensible defaults (e.g. “Don’t know”, “No”, “Never”) depending on the question context.
- 🔡 Converted all relevant categorical features into **numeric representations** (ordinal scales, binary flags, one-hot encodings).

### 2️⃣ Exploratory Data Analysis (EDA)

- 📈 Explored distributions of **Age, Gender, Country/Region, family history, benefits, leave, work interference** etc.
- 🔁 Compared the **treatment** rate across:
  - Family history vs no family history  
  - Different levels of work interference  
  - Comfort discussing issues with coworkers/supervisors  
  - Ease/difficulty of taking mental health leave  
- 🧩 Identified patterns such as:
  - Higher likelihood of treatment among those with **family history** of mental illness  
  - Strong link between **work interference** and treatment  
  - Importance of **supportive culture, benefits and wellness programs**

All plots and insights are available in the notebook.

### 3️⃣ Feature Engineering

- ✅ Created clean, model-ready features from:
  - Demographics (age bins, gender)
  - Region (from country)
  - Work context (remote work, tech company, company size)
  - Perceptions & support (benefits, care options, anonymity, leave, consequences, etc.)
- 📏 Prepared **feature matrix `X`** and **target `y`**, then split into **train/test** sets.
- 🔄 Applied **scaling** where required (e.g. for linear models).

### 4️⃣ Model Training & Evaluation

Multiple models were trained and compared:

- 📉 **Logistic Regression** – simple, fast, interpretable baseline  
- 🌲 **Random Forest Classifier** – tree-based ensemble for non-linear patterns  
- ⚡ **XGBoost Classifier** – gradient boosting for potentially higher accuracy  

For each model, the notebook evaluates:

- Accuracy  
- Precision, Recall, F1-score  
- ROC–AUC  
- Confusion Matrix  

Additionally, **cross-validation** is used to check stability across different splits.

---

## 📊 Results & Insights

> Exact metric values are documented inside the notebook.

High-level findings:

- All three models perform **reasonably well** on the classification task.
- **XGBoost / Random Forest** tend to offer stronger raw predictive performance.
- **Logistic Regression** provides an excellent balance of:
  - Competitive performance  
  - Interpretability (easy to explain feature effects)  
  - Simplicity and speed  

From the analysis, some features consistently stand out as important:

- ✅ **Family history** of mental illness  
- ✅ **Work interference** due to mental health  
- ✅ Perceived **consequences** of talking about mental health  
- ✅ Quality of **benefits, care options and wellness programs**  
- ✅ Comfort with **coworkers/supervisors** and ease of taking **leave**

These insights can help HR and leadership teams **prioritise interventions**, such as:

- Improving leave policies  
- Promoting mental health awareness  
- Building psychologically safe environments  
- Strengthening wellness and counselling programs  

---

## 🗂️ Repository Structure

Suggested layout:

```text
.
├── Final_Hackathon.ipynb   # Main notebook with full pipeline
├── train.csv               # Training dataset (not committed if private)
├── test.csv                # Test dataset (not committed if private)
├── submission.csv          # Example submission file (generated)
└── README.md               # Project documentation (this file)
