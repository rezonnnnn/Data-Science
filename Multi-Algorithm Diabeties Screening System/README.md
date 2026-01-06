# 🏥 Diabetes Prediction: Multi-Algorithm Classification System

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7+-DC143C?style=flat&logo=xgboost&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

## 📌 Overview

Early diabetes detection saves lives, yet clinical screening relies on expensive lab tests and physician availability. This project builds a machine learning system predicting diabetes risk with **84% ROC-AUC** and **78-80% accuracy** using only 8 readily-available biometric measurements. Trained on 614 patients from the Pima Indians Diabetes Database, the model employs ensemble methods and SMOTE resampling to handle class imbalance (65-35 split), providing a scalable triage tool for under-resourced healthcare settings.

## 🎯 Objective

Develop a production-grade binary classifier that achieves >80% sensitivity (minimizing false negatives in medical context) while maintaining interpretability for clinical decision support. Handle biological impossibilities in data (zero values in blood pressure/glucose), engineer clinically meaningful features, and compare 5 ML algorithms to identify optimal approach.

## 📊 Data Source

**[Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database):** 614 training samples, 154 test samples from female patients of Pima Indian heritage (age 21+). Features include glucose concentration, blood pressure, BMI, insulin levels, diabetes pedigree function, and age. Key challenge: biologically impossible zero values (0.3-6.6% of features) representing missing data requiring imputation.

## 🔧 Methodology

**Pipeline:** Zero-value identification (medical impossibilities) → median imputation stratified by outcome → 7 feature engineering operations (BMI categories per WHO classification, glucose risk tiers per ADA guidelines, HOMA-IR insulin resistance proxy, polynomial interactions) → RobustScaler (IQR-based, resists outliers) → SMOTE oversampling (balances 65-35 class distribution) → 5-fold stratified cross-validation.

**Algorithm Evaluation:** Trained Logistic Regression (baseline interpretability), Random Forest (ensemble robustness), XGBoost (gradient boosting efficiency), Gradient Boosting (sequential error correction), and SVM (non-linear boundaries). **XGBoost** selected as optimal based on ROC-AUC (0.84), F1 score (0.73), and calibration—outperforming alternatives by 3-5% on validation set while maintaining <500ms inference time.

## 💡 Key Insights

- **Glucose dominates prediction:** Concentration (r=0.47) is strongest single feature; patients with fasting glucose >126 mg/dL exhibit 4.2× higher diabetes prevalence
- **BMI amplifies risk non-linearly:** Obesity (BMI >30) combined with elevated glucose creates multiplicative interaction—engineered feature GlucoseBMI_Interaction ranks #4 in importance
- **Age stratification matters:** Risk accelerates post-45; age-glucose polynomial feature improves recall by 7% for older cohorts vs. linear age alone
- **False negatives are costly:** Model tuned for 85% sensitivity at expense of precision—in clinical triage, missing positive case (delayed treatment) outweighs false alarm burden

## 🛠️ Tech Stack

**Core:** Python 3.8+, scikit-learn (ensemble methods, preprocessing), XGBoost, imbalanced-learn (SMOTE), Pandas, NumPy, Matplotlib/Seaborn  
**Techniques:** SMOTE Resampling, Stratified K-Fold CV, Feature Engineering (domain-informed), Mann-Whitney U Testing, ROC-AUC Optimization

## 🚀 How to Run

```bash
git clone https://github.com/yourusername/diabetes-classification-ml.git
cd diabetes-classification-ml
pip install -r requirements.txt
jupyter notebook Module6_Diabetes_Classification__Analysis.ipynb
```
**Runtime:** ~5-7 minutes | **Output:** `diabetes_predictions.csv` + performance dashboard

## 📁 File Structure

```
├── Module6_Diabetes_Classification__Analysis.ipynb  # Main analysis (9 sections)
├── Executive_Summary.md                             # Technical deep-dive
├── Data/
│   ├── train.csv                                    # 614 training samples
│   └── test.csv                                     # 154 test samples
└── requirements.txt                                 # Dependencies
```

---

**Performance:** ROC-AUC = 0.84 | Accuracy = 78-80% | F1 = 0.73 | Sensitivity = 85% | **5 algorithms compared** | **7 engineered features**
