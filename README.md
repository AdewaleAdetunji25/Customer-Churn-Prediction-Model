# Customer-Churn-Prediction-Model
 

# 🧠 Customer Churn Prediction Project

This project predicts whether a customer will churn based on their demographic, transactional, service usage, and online activity data. It utilizes both Logistic Regression and Random Forest Classifiers with hyperparameter tuning.

---

## 🚀 Workflow Summary

### 1. Data Loading & Exploration
- Imported 5 sheets from Excel: Demographics, Transactions, Service, Online Activity, Churn Status
- Explored structure, types, nulls, and distributions (Age, Gender, Marital Status)

### 2. Feature Engineering
- Aggregated transaction features: TotalAmountSpent, AvgAmountSpent, NumTransactions
- Aggregated service features: TotalInteractions, Complaints, Inquiries
- Encoded online activity data
- Visualized churn distribution

### 3. Data Merging & Cleaning
- Merged all datasets on CustomerID
- Handled missing values and removed duplicates

### 4. Preprocessing
- One-hot encoded categorical variables
- Scaled numerical values
- Saved cleaned dataset

### 5. Target Encoding & Class Balancing
- Label encoded churn status
- Applied SMOTE to balance classes (796 churned / 796 not churned)

### 6. Feature Selection & Splitting
- Dropped identifiers
- Stratified 80/20 train-test split

---

## 🧪 Model Training

### Logistic Regression (Baseline)
- Accuracy: 0.68 | ROC AUC: 0.75
- Confusion Matrix: [[104, 56], [47, 112]]

### Random Forest (Default)
- Accuracy: 0.84 | ROC AUC: 0.90
- Confusion Matrix: [[146, 14], [36, 123]]

### Random Forest (Tuned)
- Accuracy: 0.85 | ROC AUC: 0.91
- Best Params: `max_depth=20`, `min_samples_split=2`, `n_estimators=200`
- Confusion Matrix: [[148, 12], [35, 124]]

---

## 🔍 Feature Importance (Top 5)

| Feature           | Importance |
|-------------------|------------|
| TotalInteractions | 0.074      |
| LoginFrequency    | 0.065      |
| Age               | 0.059      |
| Furniture         | 0.058      |
| Groceries         | 0.057      |

---

## 💾 Deployment

Final model saved using `joblib`:
```python
joblib.dump(rf, 'customer_churn_model.pkl')
