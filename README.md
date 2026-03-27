# Bank Customer Churn Prediction

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![XGBoost](https://img.shields.io/badge/XGBoost-Best%20Model-red)
![Status](https://img.shields.io/badge/Status-Completed-green)

## Project Overview

This project predicts which bank customers are likely to **churn** (leave the bank) based on their profile and behavior. By identifying at-risk customers in advance, banks can take targeted actions to retain them.

---

## Dataset

- **Source:** [Churn Modelling Dataset (Kaggle)](https://raw.githubusercontent.com/alishermutalov/praktikum-datasets/refs/heads/praktikum/Churn_Modelling.xls)
- **Samples:** 10,000 customers × 14 columns
- **Target:** `Exited` → 0 = Stayed, 1 = Churned
- **Class imbalance:** 1,607 stayed vs 393 churned (in test set)

| Feature | Description |
|---------|-------------|
| `CreditScore` | Customer's credit score |
| `Geography` | Country (France, Spain, Germany) |
| `Gender` | Male / Female |
| `Age` | Customer age |
| `Tenure` | Years as a bank customer |
| `Balance` | Account balance |
| `NumOfProducts` | Number of bank products used |
| `HasCrCard` | Has credit card (0/1) |
| `IsActiveMember` | Active member (0/1) |
| `EstimatedSalary` | Estimated annual salary |
| `Exited` | Target — churned or not |

---

## Data Preprocessing

- Dropped irrelevant columns: `RowNumber`, `CustomerId`, `Surname`
- **Label Encoding:** `Gender` → numeric
- **One-Hot Encoding:** `Geography` → dummy variables (`drop_first=True`)
- Train/Test split: **80% / 20%** (`random_state=42`)
- Applied **StandardScaler** for feature normalization

---

## Models Trained

Five classification models were built and compared:

| Model | Accuracy | Recall (Churn) | F1-Score (Churn) |
|-------|----------|----------------|------------------|
| Logistic Regression | 0.81 | 0.20 ❌ | 0.29 |
| SVM | 0.86 | 0.38 | 0.51 |
| Decision Tree | 0.78 | 0.50 | 0.47 |
| Random Forest | 0.87 | 0.47 | 0.58 |
| **XGBoost** | **0.87** | **0.55 🔥** | **0.63 🔥** |

---

## Best Model: XGBoost

XGBoost achieved the best balance between accuracy and recall — the most critical metric for churn detection where missing a churning customer is costly.

```
              precision    recall  f1-score   support
           0       0.90      0.95      0.92      1607
           1       0.72      0.55      0.63       393
    accuracy                           0.87      2000
```

---

## Evaluation Metrics Used

- **Accuracy** — overall correctness
- **Precision** — of predicted churners, how many actually churned
- **Recall** — of actual churners, how many were caught *(most important)*
- **F1-Score** — balance between precision and recall
- **ROC Curve & AUC** — for each model
- **Confusion Matrix** — TP, TN, FP, FN breakdown

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| `Python` | Core language |
| `Pandas / NumPy` | Data manipulation |
| `Matplotlib / Seaborn` | Visualization |
| `Scikit-learn` | ML models & evaluation |
| `XGBoost` | Best performing model |

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/husan-ai/customer-churn-prediction.git
cd customer-churn-prediction

# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook Customer_churn_ML_mijoz_noroziligi_.ipynb
```

---

## Requirements

```
numpy
pandas
matplotlib
seaborn
scikit-learn
xgboost
jupyter
```

---

## Future Improvements

- [ ] Handle class imbalance using **SMOTE** or class weighting
- [ ] Hyperparameter tuning with **GridSearchCV**
- [ ] Feature importance analysis
- [ ] Improve **Recall** for churn class further
- [ ] Deploy as a web app using **Flask** or **Streamlit**

---

## Author

**Husan**  
ML | DL | NLP  
GitHub: [@husan-ai](https://github.com/husan-ai)
