# 🏦 ApexPlanet Internship – Task 1: Data Immersion & Wrangling

---

## 📌 Objective

To rapidly acquire, understand, clean, and prepare a real-world financial dataset for analysis. This task covers the critical first step of any data analytics project — data wrangling — including profiling, quality assessment, cleaning, and feature engineering.

---

## 📂 Repository Structure

```
ApexPlanet-DataAnalytics-Task1/
│
├── data/
│   ├── Delinquency_prediction_dataset.csv      # Raw dataset
│   └── cleaned_dataset.csv                     # Cleaned, analysis-ready dataset
│
├── data_dictionary.md                          # Column descriptions and business context
├── data_cleaning.py                            # Python cleaning & transformation script
└── README.md                                   # Project overview (this file)
```

---

## 🗂️ Dataset Overview

| Property | Details |
|---|---|
| **Dataset Name** | Delinquency Prediction Dataset |
| **Rows** | 500 customer records |
| **Columns** | 19 features |
| **Target Variable** | `Delinquent_Account` (0 = Not Delinquent, 1 = Delinquent) |
| **Domain** | Banking / Financial Risk Analytics |

### Columns at a Glance

| Column | Type | Description |
|---|---|---|
| `Customer_ID` | String | Unique customer identifier (e.g., CUST0001) |
| `Age` | Integer | Age of the customer |
| `Income` | Integer | Annual income in USD |
| `Credit_Score` | Integer | Credit score of the customer |
| `Credit_Utilization` | Float | Ratio of credit used vs. credit available |
| `Missed_Payments` | Integer | Total number of missed payments |
| `Delinquent_Account` | Integer | **Target**: 1 = Delinquent, 0 = Not Delinquent |
| `Loan_Balance` | Integer | Outstanding loan balance in USD |
| `Debt_to_Income_Ratio` | Float | Debt relative to income |
| `Employment_Status` | String | Employment type (Employed, Unemployed, etc.) |
| `Account_Tenure` | Integer | Number of months the account has been active |
| `Credit_Card_Type` | String | Type of credit card (Gold, Platinum, Student, etc.) |
| `Location` | String | City of residence |
| `Month_1` to `Month_6` | String | Payment status per month (On-time / Late / Missed) |

---

## 🔍 Data Quality Issues Found

During the initial profiling of the raw dataset, the following issues were identified:

| Issue | Column(s) Affected | Count |
|---|---|---|
| Missing values | `Income` | 39 rows |
| Missing values | `Loan_Balance` | 29 rows |
| Missing values | `Credit_Score` | 2 rows |
| Inconsistent text casing | `Employment_Status` | `'EMP'`, `'employed'`, `'retired'` (non-standard) |
| No duplicate rows | — | 0 duplicates ✅ |

### Class Distribution (Target Variable)
| Delinquent_Account | Count |
|---|---|
| 0 – Not Delinquent | 420 (84%) |
| 1 – Delinquent | 80 (16%) |

> ⚠️ The dataset is **imbalanced** — only 16% of customers are delinquent. This will be important for future modelling tasks.

---

## 🧹 Cleaning & Transformation Steps

The following steps were applied in `data_cleaning.py`:

1. **Missing Value Treatment**
   - `Income` and `Loan_Balance` — filled with **median** (robust to outliers)
   - `Credit_Score` — filled with **median**

2. **Standardizing `Employment_Status`**
   - Mapped inconsistent values → `'EMP'` → `'Employed'`, `'employed'` → `'Employed'`, `'retired'` → `'Retired'`

3. **Feature Engineering**
   - Created `Total_Late_Payments`: count of months with `'Late'` or `'Missed'` payment status across Month_1 to Month_6
   - Created `Payment_Reliability_Score`: ratio of `'On-time'` months out of 6

4. **Output**
   - Saved final cleaned dataset as `data/cleaned_dataset.csv`

---

## ⚙️ How to Run

### Prerequisites
```bash
pip install pandas
```

### Run the cleaning script
```bash
python data_cleaning.py
```

This will generate `data/cleaned_dataset.csv` — the analysis-ready dataset.

---

## 🛠️ Tools & Technologies

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-green?logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

---

## 👤 Auth

## 🏢 About ApexPlanet

[ApexPlanet Software Pvt. Ltd.](https://www.apexplanet.in) is dedicated to driving innovation in digital solutions and nurturing the next generation of tech talent through hands-on internship programs.
