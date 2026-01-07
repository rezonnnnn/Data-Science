# 💰 Loan Default Risk Analytics: Comprehensive EDA

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

## 📌 Overview

Consumer finance companies lose billions annually approving high-risk loans while simultaneously rejecting creditworthy applicants due to insufficient credit history. This project performs comprehensive exploratory data analysis on **307,511 loan applications** to identify behavioral patterns and risk indicators that predict default probability. Analyzing 122 features spanning demographics, financial history, and employment data, the study reveals severe **class imbalance (11.4:1 ratio)** and uncovers high-risk segments—maternity leave applicants show 3× higher default rates, low-skilled laborers exhibit 2.5× elevated risk, and civil marriage status correlates with 1.8× increased defaults. These insights enable data-driven loan approval policies that reduce financial losses while expanding access to creditworthy customers.

## 🎯 Objective

Conduct multi-dimensional exploratory analysis to identify statistical patterns differentiating default-prone applicants from reliable payers. Handle severe class imbalance (91.9% vs 8.1%), manage 67 features with missing values (49 columns dropped at >40% threshold), and deliver actionable risk segmentation profiles for underwriting policy optimization.

## 📊 Data Source

**[Home Credit Default Risk (Kaggle-style dataset)](https://www.kaggle.com/c/home-credit-default-risk):** 307,511 loan applications with 122 features including AMT_INCOME_TOTAL, AMT_CREDIT, AMT_ANNUITY, demographic attributes (age, gender, family status), employment metrics (DAYS_EMPLOYED, occupation type), and housing characteristics. Supplemented by previous_application.csv (521,277 historical records) tracking prior loan outcomes (Approved, Cancelled, Refused, Unused). Key challenge: 67 columns with missing data (0.3%-69.9% nulls) and binary target exhibiting extreme imbalance.

## 🔧 Methodology

**Data Quality Pipeline:** Missing value assessment → column removal (>40% null threshold eliminated 49 features) → median imputation for remaining nulls → outlier detection via IQR method → feature engineering (AGE_YEARS, EMPLOYMENT_YEARS derived from negative day counts).

**Exploratory Framework:** Univariate analysis (distributions of AMT_INCOME_TOTAL, AMT_CREDIT, AMT_ANNUITY, age, employment tenure), bivariate analysis (default rates segmented by NAME_INCOME_TYPE, NAME_EDUCATION_TYPE, NAME_FAMILY_STATUS, OCCUPATION_TYPE), correlation analysis (top 15 features vs TARGET), and multivariate profiling (interaction effects between income, education, and family structure). Visualization-heavy approach with 20+ plots including histograms, bar charts, correlation heatmaps, and overlapping distributions comparing defaulters vs non-defaulters.

## 💡 Key Insights

- **Income source drives risk:** Maternity leave (highest default rate), unemployed, and working-class applicants show 15-30% higher default probability than pensioners and commercial associates—unemployment instability outweighs income levels
- **Education inversely correlates with default:** Lower secondary education exhibits 12% default rate (3× baseline), while academic degree holders maintain <5% default—financial literacy and earning potential compound protective effects
- **Marital status predicts stability:** Civil marriage and single/not married applicants default at 10-11% vs. 6% for married/widowed—legal commitment proxy for financial responsibility and dual-income buffers
- **Occupation-specific vulnerabilities:** Low-skill laborers (15% default), drivers (13%), and waiters/barmen (12%) concentrate risk vs. accountants and core staff (<7%)—income volatility and job security critical differentiators

## 🛠️ Tech Stack

**Core:** Python 3.8+, Pandas, NumPy, Matplotlib, Seaborn, SciPy (statistical tests)  
**Techniques:** Univariate/Bivariate/Multivariate EDA, Class Imbalance Analysis, Correlation Analysis, Missing Value Treatment

## 🚀 How to Run

```bash
git clone https://github.com/yourusername/loan-default-risk-eda.git
cd loan-default-risk-eda
pip install -r requirements.txt
jupyter notebook loan_default_risk_eda.ipynb
```
**Runtime:** ~5-7 minutes | **Output:** 20+ visualizations + risk segmentation profiles

## 📁 File Structure

```
├── loan_default_risk_eda.ipynb                  # Main EDA notebook (6 sections)
├── target_distribution.png                      # Class imbalance visualization
├── default_rate_by_category.png                 # Risk segmentation charts
├── correlation_heatmap.png                      # Feature correlation matrix
├── financial_features_dist.png                  # Income/credit distributions
└── requirements.txt                             # Dependencies
```

**Data:** Home Credit Default Risk dataset (available on Kaggle) - 307,511 applications × 122 features

---

**Analysis Scope:** 20+ statistical analyses | 6 visualization types | **Class Imbalance:** 11.4:1 ratio | **Missing Data:** 67 features (49 dropped) | **Risk Segments:** 4 high-priority categories identified
