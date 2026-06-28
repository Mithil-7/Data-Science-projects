
# 🏢 Employee Attrition Prediction using Machine Learning

![Python Version](https://img.shields.io/badge/Python-3.8+-blue.svg)
![ML Architecture](https://img.shields.io/badge/Machine%20Learning-Classification-brightgreen)
![HR Tech](https://img.shields.io/badge/Domain-People%20Analytics-blueviolet)

An end-to-end predictive modeling project completed during Week 2 of the Data Science Internship. This system functions as an early-warning tracking mechanism to identify employee flight risks, uncover systemic drivers of turnover, and deliver actionable operational recommendations for HR leadership.

---

## 🎯 Problem Statement
Losing key talent costs corporations heavily in recruitment, onboarding, and lost productivity. The goal of this project is to:
1. Build a classification pipeline capable of predicting whether an employee is likely to leave based on lifestyle and workplace characteristics.
2. Translate complex algorithmic metrics into a non-technical strategic roadmap that an HR Director can execute immediately.

---

## 📦 Dataset & Imbalance Challenge
The project uses the **IBM HR Analytics Employee Attrition Dataset** (1,470 rows, 35 columns). 
* **Target Variable:** `Attrition` (Yes/No)
* **The Class Imbalance:** The data exhibits a sharp imbalance: **~84% of employees stay, while only ~16% leave**. To prevent the models from ignoring the minority class, class-imbalancing constraints (`class_weight='balanced'`) were embedded during training.

---

## 🛠️ Project Workflow

### 1. Data Cleaning & Engineering
* Dropped constant/uninformative features: `EmployeeNumber`, `Over18`, `StandardHours`, and `EmployeeCount`.
* Mapped the target parameter (`Attrition`) from text to binary format (`1` for Left, `0` for Stayed).
* Processed multi-class string labels (e.g., `Department`, `JobRole`, `MaritalStatus`) via One-Hot Encoding.
* Normalized continuous metrics (e.g., `MonthlyIncome`, `Age`) using `StandardScaler`.

### 2. Predictive Performance Evaluation
The data was split using a stratified **80/20 train/test split**. Three distinct classifiers were evaluated to find the best balance between catching exits (Recall) and minimizing false alarms:

| Model | Precision (Exit) | Recall (Exit) | F1-Score (Exit) | ROC-AUC Score |
| :--- | :---: | :---: | :---: | :---: |
| **Logistic Regression (Best)** | **0.4688** | **0.7660** | **0.5806** | **0.8252** |
| **Random Forest** | 0.7000 | 0.2979 | 0.4179 | 0.7963 |
| **Gradient Boosting** | 0.6364 | 0.2979 | 0.4058 | 0.7938 |

*Note: Individual metric values may fluctuate slightly depending on random seeds, but Logistic Regression consistently provides the best operational sensitivity (Recall).*

---

## 📊 Visual Diagnostics & Chart Explanations
All generated visualizations are archived in the `charts/` folder and serve distinct functions:

* **`attrition_dept_overtime.png` (Attrition by Department & Overtime Status):** Compares resignation proportions across departments. It highlights that **overtime is a universal driver of turnover**, with the absolute sharpest impact seen within the **Sales Department**.
* **`income_disparity_boxplot.png` (Salary Disparities):** A box plot illustrating that the income distribution of departed workers sits drastically lower than active staff. It visually identifies a critical threshold under **$3,000/month** where flight risk skyrockets.
* **`best_model_confusion_matrix.png` (Model Scorecard):** A four-quadrant matrix tracking correct guesses versus classification errors. It visually confirms our model's capacity to catch **~76-80% of actual impending exits**.
* **`top_10_features.png` (Operational Driver Rankings):** A horizontal bar chart ranking the key elements triggering the model's flags. **Overtime sits at the absolute top**, followed by monthly income benchmarks and short organizational tenure.
* **`model_roc_curves.png` (ROC Curve Comparison):** A multi-model accuracy graph. It mathematically justifies the selection of **Logistic Regression** by showing its curve arching closest to the top-left ideal threshold.

---

## 🔑 Key Strategic Insights

* **The Top 3 Red Flags:** **Working overtime**, maintaining a **low monthly income**, and **low tenure (under one year)** are the three strongest indicators of an impending exit.
* **Salary vs. Lifestyle:** While inadequate compensation is a major factor, salary alone does not fully explain turnover. Systemic lifestyle strains—such as high overtime demands and poor work-life balance—prove to be equally powerful catalysts for resignation.
* **Actionable Policy Interventions:**
  1. *Overtime Cap:* Implement a weekly departmental tracking log to cap consecutive overtime weeks, balancing extreme periods with mandatory time off.
  2. *Tenure Interventions:* Institute mandatory "Stay Interviews" led by HR at the 90-day and 180-day marks for all entry-level positions to intercept early-stage dissatisfaction.

---

## ⚠️ Model Limitations
**The Snapshot Constraint:** This system relies on static, historical datasets (such as year-end review scores and fixed survey ratings). It cannot capture real-time, volatile workplace changes—such as a sudden toxic shift in team culture or a sudden conflict with a supervisor—which frequently trigger unexpected, rapid resignations. It should complement everyday management intuition, not replace it.

---

## 📂 Repository Layout

```text
├── EmployeeAttrition/
│   ├── analysis.ipynb              # Notebook mapping tasks 1 through 7
│   ├── HR_Attrition.csv            # Cleaned, structured dataset
│   ├── summary.pdf                 # 1-page non-technical report for the HR Director
│   └── charts/                     # Saved high-resolution analytical plots
│       ├── attrition_dept_overtime.png
│       ├── income_disparity_boxplot.png
│       ├── best_model_confusion_matrix.png
│       ├── top_10_features.png
│       └── model_roc_curves.png
└── README.md                       # Repository documentation

```
