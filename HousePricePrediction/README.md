
# 🏠 House Price Prediction — Machine Learning Regression Project

![Python Version](https://img.shields.io/badge/Python-3.8+-blue.svg)
![ML Framework](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange)
![Data Tool](https://img.shields.io/badge/Data%20Analytics-Pandas%20%26%20Seaborn-green)

An end-to-end Machine Learning project completed during Week 1 of the Data Science Internship. This project focuses on analyzing housing features (such as area, rooms, amenities) to predict property values, comparing parametric (Linear Regression) and non-parametric (Random Forest) models, and delivering data-driven insights for real estate businesses.

---

## 🎯 Problem Statement
Real estate buyers and sellers often rely on guesswork or outdated historical benchmarks to estimate a property's fair value. This project aims to:
1. Build a robust regression model to predict house prices based on physical attributes and amenities.
2. Identify which property features exert the strongest influence on market valuation to assist strategic real estate decision-making.

---

## 📦 Dataset
The analysis uses the **Housing Prices Dataset** from Kaggle, consisting of 545 rows and 13 property feature columns (including `area`, `bedrooms`, `bathrooms`, `airconditioning`, `furnishingstatus`, etc.). 

* **Target Variable:** `price`
* **Source:** [Kaggle Housing Prices Dataset](https://www.kaggle.com/datasets/yasserh/housing-prices-dataset)

---

## 🛠️ Project Workflow

### 1. Data Exploration & Cleaning
* Checked for structural dimensions and verified zero missing data values.
* Drop-tested and handled duplicate rows.
* Handled categorical parameters (`mainroad`, `guestroom`, `basement`, `airconditioning`, `prefarea`, `furnishingstatus`) via **One-Hot Encoding** (`pd.get_dummies`) to optimize mathematical compatibility.

### 2. Feature Analysis & Correlations
Evaluated data relationships using Pearson Correlation matrices. Comfort parameters and raw dimensions scored significantly higher against market value than baseline room quantities.

### 3. Model Training & Evaluation
The dataset was split using an **80/20 train/test split**. Two algorithms were evaluated against standard regression metrics (MAE, RMSE, $R^2$):
* **Linear Regression**
* **Random Forest Regressor** (100 Estimators)

---

## 📊 Evaluation Results & Model Comparison

| Metric | Linear Regression | Random Forest |
| :--- | :---: | :---: |
| **MAE (Mean Absolute Error)** | **$970,043.40** | $1,021,546.04 |
| **RMSE (Root Mean Squared Error)** | **$1,324,506.96** | $1,400,565.97 |
| **R² Score (Variance Explained)** | **0.6529** | 0.6119 |

### 🏆 Key Findings:
* **The Winning Model:** **Linear Regression** outperformed Random Forest across all parameters, capturing **65.29%** of the variance in pricing within the test set.
* **Top 5 Valuation Drivers (Random Forest Feature Importances):**
  1. `area` (46.84%)
  2. `bathrooms` (15.15%)
  3. `airconditioning_yes` (6.27%)
  4. `parking` (5.75%)
  5. `stories` (5.71%)

---

## 💡 Key Insights & Business Recommendations

* **Surprising Discovery:** The presence of **air conditioning** correlates much more strongly with a higher sales price (**0.45**) than the actual number of **bedrooms** (**0.37**). Practical comfort and utility outrank basic space subdivisions.
* **Strategic Recommendation:** Real estate firms and property flippers should prioritize modernizing bathrooms and installing climate-control infrastructure (AC) over constructing additional bedrooms. These updates introduce a disproportionately higher ROI relative to renovation costs.

---

## 📂 Repository Structure

```text
├── HousePricePrediction/
│   ├── analysis.ipynb              # Complete Jupyter Notebook containing all 5 tasks
│   ├── Housing.csv                 # Raw dataset from Kaggle
│   ├── summary.pdf                 # 1-page business summary report 
│   └── charts/                     # Generated data visualizations
│       ├── price_distribution.png  # Task 4 - Chart 1: Price Histogram
│       ├── correlation_heatmap.png # Task 4 - Chart 2: Feature Heatmap Matrix
│       └── actual_vs_predicted.png # Task 4 - Chart 3: Actual vs. Predicted scatter
└── README.md                       # Repository overview and documentation
