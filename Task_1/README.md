# CodeAlpha Machine Learning Internship — Task 1: Credit Scoring Model

![Python](https://img.shields.io/badge/Python-3.11%2B-blue.svg)
![Scikit--Learn](https://img.shields.io/badge/Scikit--Learn-1.3%2B-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

## 📌 Project Overview
This project is developed as part of the **CodeAlpha Machine Learning Internship**. The objective is to build a high-performance **Credit Scoring Model** that evaluates an applicant's creditworthiness and predicts the likelihood of credit default based on historical financial records, socio-demographic indicators, and credit history.

---

## 🎯 Business Context & Problem Formulation
In financial lending, granting credit to high-risk applicants leads to significant capital loss (**False Negatives**), while declining solvent borrowers leads to forgone interest revenue (**False Positives**). 

The goal of this project is to build a robust binary classification pipeline that prioritizes:
- High detection rate (**Recall**) of bad credit applicants (Class `1`).
- Robust discrimination capacity measured via **ROC-AUC** and **Precision-Recall** dynamics.
- Interpretability through **Feature Importance** and risk factor extraction.

* **Target Variable**:
  * `0`: Good Credit / Solvent (Low Risk)
  * `1`: Bad Credit / Default (High Risk)

---

## 📊 Dataset: Statlog (German Credit Data)
* **Source**: UCI Machine Learning Repository
* **Total Instances**: 1,000 applicants
* **Total Features**: 20 attributes (7 numerical, 13 categorical)
* **Class Distribution**: 700 Good Credit (70%), 300 Bad Credit (30%)

---

## 🛠️ Financial Feature Engineering
To fulfill the internship requirements, 5 domain-informed financial features were engineered:

1. **`monthly_installment_est`**: Estimated monthly debt service outflow:
   $$\text{monthly\_installment\_est} = \frac{\text{credit\_amount}}{\text{duration}}$$
2. **`credit_to_age_ratio`**: Leverage relative to the borrower's life stage:
   $$\text{credit\_to\_age\_ratio} = \frac{\text{credit\_amount}}{\text{age}}$$
3. **`credit_per_dependent`**: Financial burden distributed per dependent:
   $$\text{credit\_per\_dependent} = \frac{\text{credit\_amount}}{\text{dependents} + 1}$$
4. **`installment_burden_index`**: Composite indicator of cash-flow pressure:
   $$\text{installment\_burden\_index} = \text{monthly\_installment\_est} \times \text{installment\_rate}$$
5. **`high_risk_account_flag`**: Binary flag identifying applicants with overdrawn checking accounts (`A11`: $<0$ DM) and minimal/no savings (`A61`: $<100$ DM).

---

## 🤖 Models Implemented & Methodology
A data preprocessing pipeline was implemented with `ColumnTransformer`:
* **Numerical Features**: Standardized using `StandardScaler`.
* **Categorical Features**: Encoded using `OneHotEncoder(handle_unknown='ignore', drop='first')`.
* **Train/Test Split**: 80/20 Stratified Split (`random_state=42`) preserving class ratios.

### Algorithms Compared:
1. **Logistic Regression**: Linear probabilistic classifier with `class_weight='balanced'`.
2. **Decision Tree Classifier**: Non-linear tree classifier with `max_depth=5` to prevent overfitting.
3. **Random Forest Classifier**: Ensemble of 200 decision trees (`max_depth=8`) with bagging and feature sub-sampling.

---

## 📈 Model Performance & Evaluation

| Model | Accuracy | Precision | Recall (Default Detection) | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | **74.5%** | **55.2%** | **80.0%** | **0.653** | **0.811** |
| **Random Forest** | **73.5%** | **54.7%** | **68.3%** | **0.607** | **0.791** |
| **Decision Tree** | 64.0% | 44.3% | 78.3% | 0.566 | 0.739 |

### Key Findings & Insights:
* **Optimal Model**: **Logistic Regression** achieved the highest **Recall (80.0%)** and **ROC-AUC (0.811)**, detecting 48 out of 60 bad credit applicants in the unseen test set.
* **Top Risk Drivers**:
  1. `checking_account_A14` (No checking account) & `A11` (Negative balance)
  2. `credit_history_A34` (Critical account history)
  3. `duration` (Longer loan terms strongly correlate with higher default rates)
  4. `installment_burden_index` & `credit_to_age_ratio` (Engineered financial burden indicators)

---

## 🚀 How to Run the Project

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/CodeAlpha_CreditScoringModel.git
cd CodeAlpha_CreditScoringModel
```

### 2. Set up virtual environment & install requirements
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/Mac:
source .venv/bin/activate

pip install -r requirements.txt
```

### 3. Open and run the Jupyter Notebook
```bash
jupyter notebook Task_1/Task1.ipynb
```
*(All cells are pre-executed with embedded visualizations, metrics, and explanations).*

---

## 📁 Repository Structure
```text
├── Task_1/
│   ├── Task1.ipynb           # Complete, pre-executed Jupyter Notebook
│   ├── german.data           # Statlog German Credit Data
│   └── README.md             # Task documentation and report
├── requirements.txt          # Python dependencies
└── Machine Learning Tasks & Instructions — CodeAlpha M1.pdf
```
