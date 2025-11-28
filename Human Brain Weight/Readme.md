# 🧠 Brain Weight Prediction using Linear Regression
<img width="920" height="608" alt="image" src="https://github.com/user-attachments/assets/f8771860-5e10-41ee-8ac5-c7445bdd0250" />

This project is based on a medical dataset that includes variations in head sizes, brain weights, gender, and age range. The goal is to build a predictive model that estimates brain mass using Linear Regression.

---

## 📊 Dataset Description

The dataset was compiled from a medical study involving a group of individuals. It contains:

- **Head Size** 
- **Brain Weight** 
- **Gender** 
- **Age Range** 

---

## 🎯 Objective

To predict the **Brain Weight** using features such as **Head Size**, **Gender**, and **Age Range**, and evaluate the performance of the Linear Regression model.

---

## ✅ Model Used

- **Linear Regression**  
  A supervised learning algorithm used for predicting continuous values.

---

## 🧪 Model Evaluation

The model was trained on 80% of the data and tested on the remaining 20%.

### 📈 Results:

| Metric               | Score      |
|----------------------|------------|
| Training Accuracy    | 61.4%      |
| Test Accuracy (R²)   | **77.7%**  |
| MAE (Mean Abs Error) | 57.11      |
| MSE (Mean Sq Error)  | 5403.79    |
| RMSE                 | 73.51      |

> ✅ The model was able to explain **77%** of the variance in brain weight on unseen test data.

---

## 📌 Key Concepts Covered

- Data Cleaning
- One-Hot and Ordinal Encoding
- Train-Test Split
- Linear Regression Modeling
- Model Evaluation (R², MAE, MSE, RMSE)
- Data Visualization (Seaborn & Matplotlib)

---
