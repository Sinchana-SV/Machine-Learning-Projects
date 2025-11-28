## 🛍️ Customer Segmentation using K-Means Clustering
<img width="712" height="532" alt="image" src="https://github.com/user-attachments/assets/1ba87292-4d52-4ca8-bdd8-0e0a04bdc133" />

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

## 🛠️ Tools & Libraries

- Python 
- pandas, numpy
- scikit-learn
- matplotlib, seaborn
- scikit-plot

---
