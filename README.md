# 🧠 Recipe Site Traffic — Data Scientist Practical Exam

> Automated classification of **High vs Low traffic** recipes with transparent validation, EDA, and supervised learning.

![status](https://img.shields.io/badge/status-complete-brightgreen)
![python](https://img.shields.io/badge/python-3.10%2B-blue)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

---

## 🧭 Project Overview
Commercial recipe sites aim to predict which recipes will attract **high site traffic**.  
This project automates that prediction using **supervised learning** as part of the **Data Scientist Professional Practical Exam**.

- **Goal:** Predict `high_traffic` (High vs Low) from nutritional and categorical recipe data.  
- **Dataset:** 947 recipes × 8 variables.  
- **Target:** `high_traffic` (binary classification).  
- **Final model:** **Gradient Boosting Classifier (GBC)** achieving **85.3% test accuracy**.

---

## 📂 Repository Structure

---

## 📊 Data Overview

**Columns:**
- `recipe` — recipe ID  
- `calories`, `carbohydrate`, `sugar`, `protein` — numeric nutritional features  
- `category` — food type (10 groups)  
- `servings` — integer (cleaned)  
- `high_traffic` — target label (“High” / “Low”)

**Cleaning & Validation Summary**
- Replaced all `NaN` values in numeric columns with their **mean**.  
- `high_traffic`: filled missing with “Low”, encoded `High=1`, `Low=0`.  
- `category`: merged “Chicken Breast” into “Chicken”.  
- `servings`: removed text (e.g., “as a snack”), converted to integer.  
- Scaled numeric features using `StandardScaler`.  
- One-hot encoded categorical variables.

---

## 🔎 Exploratory Analysis Highlights
- **Category distribution:** “Chicken” is the most frequent.  
- **Serving sizes:** 4 servings dominate (family-sized trend).  
- **Traffic balance:** about **60% High**, 40% Low — moderately imbalanced.  
- **Correlation analysis:** modest relationships among nutrition features.  
- **Insight:** nutrition and category both influence site traffic, suggesting a non-linear boundary.

Example plots (in notebook):
- Correlation heatmap  
- Category frequency bar chart  
- High vs Low traffic countplots  
- Boxplots of calories vs traffic

---

## 🧠 Modeling

### Problem Type
Binary classification (`high_traffic` → 0/1)

### Models Tested
- Logistic Regression  
- KNN  
- GaussianNB  
- Decision Tree  
- Random Forest  
- LinearSVC  
- Perceptron  
- SGDClassifier  
- Gradient Boosting Classifier  

### Cross-Validation Results (sample)
| Model | Mean CV Accuracy |
|--------|------------------|
| Logistic Regression | 0.7636 |
| SGDClassifier | 0.7550 |
| Random Forest | 0.7305 |
| Gradient Boosting (tuned) | **0.853 (test)** |

### Best Model
**Gradient Boosting Classifier (GBC)**  
Parameters:  
```python
n_estimators = 250
learning_rate = 0.05
max_depth = 1
random_state = 480
