# 🧠 Unsupervised Learning on Credit Card Data  
<img width="911" height="602" alt="image" src="https://github.com/user-attachments/assets/475b3fc8-ac69-4293-b221-1684723d89f2" />

## Customer Segmentation using PCA + K-Means

This repository contains an **unsupervised machine learning project** on the classic **credit card customer dataset**.  
The goal is to understand and segment customers based on their **spending, repayment, and credit usage behaviour** using **EDA, PCA, and K-Means clustering**.

---

## 📂 Dataset Description

Each row in the dataset represents a **unique credit card customer**.

**Feature definitions:**

1. `CUSTID` – Customer ID (categorical identifier)  
2. `BALANCE` – Balance amount left in the account for purchases  
3. `BALANCEFREQUENCY` – How frequently the balance is updated (0–1)  
4. `PURCHASES` – Total amount of purchases made  
5. `ONEOFFPURCHASES` – Maximum amount spent in a single purchase  
6. `INSTALLMENTSPURCHASES` – Amount of purchases made in instalments  
7. `CASHADVANCE` – Total cash advance amount taken by the user  
8. `PURCHASESFREQUENCY` – Frequency of purchases (0–1)  
9. `ONEOFFPURCHASESFREQUENCY` – Frequency of one-off purchases (0–1)  
10. `PURCHASESINSTALLMENTSFREQUENCY` – Frequency of instalment-based purchases (0–1)  
11. `CASHADVANCEFREQUENCY` – Frequency of cash advance usage (0–1)  
12. `CASHADVANCETRX` – Number of cash advance transactions  
13. `PURCHASESTRX` – Number of purchase transactions  
14. `CREDITLIMIT` – Credit card limit for the customer  
15. `PAYMENTS` – Total amount paid by the customer  
16. `MINIMUM_PAYMENTS` – Minimum amount paid by the customer  
17. `PRCFULLPAYMENT` – Fraction of times full payment was made (0–1)  
18. `TENURE` – Tenure of credit card usage in months  

> 🔎 Note: Depending on the dataset version, some column names may include underscores (e.g., `CREDIT_LIMIT`, `PURCHASES_FREQUENCY`). The notebook handles this appropriately.

---

## 🎯 Problem Statement & Question Mapping

This project answers the following exam-style questions:

1. **EDA**  
   Perform Exploratory Data Analysis (EDA).  
   > What does the primary analysis of the key features reveal?

2. **Advanced EDA**  
   a. Missing value analysis  
   b. Outlier treatment using **Z-score**  
   c. Handling **correlated variables**

3. **PCA**  
   Perform **dimensionality reduction** using PCA such that **≥ 95% of the variance** is explained.

4. **Elbow Method**  
   Find the **optimal value of k** for K-Means clustering using the **Elbow method** and plot the elbow curve.

5. **Silhouette Method & Clustering**  
   - Find the **optimal k** using **Silhouette score**  
   - Build a **K-Means clustering** model  
   - Show the **number of observations in each cluster** using a bar plot  
---
## 🔍 1: Exploratory Data Analysis (EDA) – Summary

In the notebook, EDA covers:

- **Shape & structure** of the dataset  
- **Descriptive statistics** (mean, median, std, min, max, quartiles)  
- **Distribution analysis** for continuous variables  
- **Correlation analysis** between financial and behavioural features  
- **Visualisations**, such as:
  - Histograms / KDE plots  
  - Boxplots for skewed features  
  - Correlation heatmap  
  - Scatter plots (e.g., `BALANCE` vs `CREDITLIMIT`)

### 🧠 Key Insights from Primary Analysis

- **Balances (`BALANCE`)**  
  - Highly skewed: most customers maintain **low to moderate balances**, with a smaller group carrying **very high balances**.  
  - Suggests diverse repayment behaviour and potential risk segments.

- **Purchases & Frequency (`PURCHASES`, `PURCHASESFREQUENCY`)**  
  - Clear separation between **inactive/low-usage** and **high-usage** customers.  
  - Some customers rarely use the card; others use it intensely and frequently.

- **Cash Advances (`CASHADVANCE`, `CASHADVANCEFREQUENCY`)**  
  - Only a subset of customers rely heavily on cash advances.  
  - These customers may represent **higher credit risk** profiles.

- **Credit Limit (`CREDITLIMIT`)**  
  - Most limits fall in the **low to mid-range**, with relatively few customers holding very high limits.  
  - Indicates conservative risk policy by the issuer.

- **Tenure (`TENURE`)**  
  - Many customers have held the card for a **longer period**, hinting at stable customer relationships.

Overall, the EDA reveals **natural behavioural groups**, which motivates the use of **unsupervised clustering**.

---

## 🧹 2: Advanced EDA & Data Preprocessing

### 🧩 2a. Missing Value Analysis

- All columns are checked for **null values**.  
- Missing values appear mainly in some **payment-related fields**, e.g., `MINIMUM_PAYMENTS` or similar numeric features.  
- **Strategy used:**  
  - For numeric variables, missing values are imputed using the **median** of each column.  
  - Median imputation is robust to skewness and outliers, especially suitable for financial data.

✅ After imputation, the cleaned dataset contains **no missing values**.

---

### 📈 2b. Outlier Treatment using Z-Score

- Continuous features are examined for **extreme outliers** that can distort clustering.  
- Outliers are identified using the **Z-score method**:
  - An observation is considered an outlier if its absolute Z-score **> 3**.  
- Rows containing extreme values across multiple features (e.g., extremely high `BALANCE`, `CASHADVANCE`, `PAYMENTS`) are removed.

👉 Result:  
- The dataset is **trimmed** by removing extreme, rare behaviours, leading to **more stable and meaningful clusters**.

---

### 🔗 2c. Handling Correlated Variables

- A **correlation matrix** is computed for all numeric variables.  
- Highly correlated pairs (e.g., correlation **> 0.95**) are identified.  
  - These often occur between variables that represent similar behaviours or scaled versions of each other.

- To reduce redundancy and potential bias in distance-based clustering:
  - Features that are **highly correlated** are dropped, keeping only the more relevant or interpretable ones.

📌 This step ensures:
- Less noise  
- Reduced multicollinearity  
- Better performance of PCA and K-Means

---

### 🎛️ Final Preparation Before Modeling

- The final set of features (after imputation, outlier removal, and correlation filtering) is **standardised**.  
- **Standardisation** (zero mean, unit variance) is crucial because:
  - PCA is variance-based  
  - K-Means uses **distance metrics** that are sensitive to scale differences

The resulting matrix is the **clean, scaled input** for PCA and clustering.

---

## 📉 3: Dimensionality Reduction using PCA (≥ 95% Variance)

To reduce dimensionality while retaining most of the information, the project uses **Principal Component Analysis (PCA)**.

- PCA is applied on the **standardised features**.  
- The **explained variance ratio** of each principal component is computed.  
- The **cumulative variance curve** is analysed to find the smallest number of components that explain **at least 95%** of the total variance.

🎯 Outcome:

- Around **8 principal components** (exact number depends on the final feature set) are sufficient to capture **≥ 95%** of the variance.  
- The original high-dimensional space is compressed into a **lower-dimensional representation**, which:
  - Speeds up clustering  
  - Reduces noise  
  - Improves interpretability

These principal components are then used as input to the K-Means algorithm.

---

## 📊 4: Optimal k using the Elbow Method

To choose the correct number of clusters, the **Elbow Method** is applied:

- K-Means models are fitted for a range of cluster counts (e.g., **k = 2 to 10**).  
- For each k, the **Within-Cluster Sum of Squares (WCSS)** is computed.  
- WCSS values are plotted against k to create the **Elbow Curve**.

🧠 Interpretation:

- As k increases, WCSS decreases (clusters become tighter).  
- The **“elbow point”** is where the rate of improvement sharply slows down.  
- This point corresponds to a good trade-off between:
  - **Model complexity** (number of clusters)
  - **Explained structure** in the data

In this project, the elbow typically suggests a **small number of clusters** (often around **k ≈ 3**), which aligns with behavioural segmentation patterns.

---

## 🧩 5: Silhouette Score + Final K-Means Model

To further validate the optimal number of clusters, the **Silhouette Score Method** is used:

- For each candidate k (same range as in the elbow method), the **average silhouette score** is calculated.  
- The silhouette score measures:
  - **Cohesion:** how close points are within the same cluster  
  - **Separation:** how far they are from other clusters  

📌 A higher silhouette score indicates better-defined clusters.

### ✅ Choosing the Final k

- The value of k with the **highest silhouette score** is selected as **optimal**.  
- In this project, this often supports the elbow method and typically favours **k ≈ 3**.

### 🏁 Building the Final K-Means Model

- K-Means is refitted on the **PCA-transformed data** using the optimal k.  
- Each customer is assigned a **cluster label**, which is added back to the cleaned dataset as a new column (e.g., `Cluster`).

### 📦 Cluster Size Analysis

- The number of observations in each cluster is counted and visualised using a **bar chart**.  
- This shows how customers are distributed across the identified segments:
  - Some clusters may be small but **high-risk or high-value**.  
  - Others may be large but **low-activity or low-risk**.

---

## 🧠 High-Level Interpretation of Customer Segments

While exact values depend on the dataset, typical cluster interpretations look like:

1. **Cluster 0 – Low Usage & Low Risk 💤**  
   - Low balances and purchase amounts  
   - Few transactions  
   - Rare use of cash advances  
   - Often pay on time and do not heavily rely on credit

2. **Cluster 1 – High Spenders 💳🔥**  
   - High total purchases and transaction counts  
   - Higher credit limits  
   - Active card usage, frequent purchases  
   - Potentially profitable customers with significant card activity

3. **Cluster 2 – Revolvers / Risky Borrowers ⚠️**  
   - Higher balances and frequent use of **cash advances**  
   - Lower proportion of full payments  
   - More dependent on credit and may represent **higher default risk**

These behavioural clusters can be used for:

- Targeted marketing campaigns  
- Credit limit optimisation  
- Risk management and fraud monitoring  
- Loyalty or retention programmes

---

## ✅ End-to-End Workflow Summary

1. **Data Ingestion & EDA (Q1)**  
   - Understand distributions, relationships, and key patterns.

2. **Data Cleaning & Preparation (Q2)**  
   - Missing value imputation (median for numeric variables)  
   - Outlier removal using Z-score  
   - Dropping highly correlated features  
   - Feature scaling/standardisation

3. **Dimensionality Reduction (Q3)**  
   - PCA used to retain **≥ 95% variance** with fewer components.

4. **Cluster Tuning (Q4 & Q5)**  
   - Elbow Method → shortlist of k values  
   - Silhouette Score → final optimal k  
   - Build K-Means model on PCA features

5. **Cluster Analysis & Business Interpretation**  
   - Attach cluster labels to each customer  
   - Analyse cluster sizes and characteristics  
   - Derive insights for business decision-making

All implementation details, plots, and results are available in:  
📓 **`Unsupervised_Credit_Card.ipynb`**

---

## 💡 Possible Extensions

- Try **Hierarchical Clustering** or **DBSCAN** for non-spherical clusters  
- Use **t-SNE** or **UMAP** for 2D visualisation of clusters  
- Integrate with a **dashboard** (Streamlit / Power BI / Tableau) for business users  
- Add **RFM (Recency, Frequency, Monetary)** features for more advanced customer segmentation

---

## 🙌 Acknowledgements

- Dataset: Standard credit card customer behaviour dataset used in ML practice.  
- This project was implemented as part of an **Unsupervised Machine Learning exam/project** focusing on:
  - EDA  
  - Data preprocessing  
  - PCA  
  - K-Means clustering  
  - Cluster evaluation using Elbow and Silhouette methods.

## 🛠️ Tech Stack

- **Language:** Python 3.x  
- **Data Handling:** `pandas`, `numpy`  
- **Visualisation:** `matplotlib`, `seaborn`  
- **Machine Learning:** `scikit-learn`  
- **Environment:** Jupyter Notebook

---

## 📁 Repository Structure

```text
.
├── credit_card.csv                 # Input dataset (not included if confidential)
├── Sinchana_SV_ML_Exam2.ipynb      # Main notebook: EDA + PCA + Clustering
└── README.md                       # Project documentation
