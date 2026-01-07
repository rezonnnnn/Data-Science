# 💳 Customer Segmentation: Multi-Algorithm Clustering Analysis

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

## 📌 Overview

Traditional one-size-fits-all marketing wastes resources on irrelevant customer outreach, yielding conversion rates below 2%. This project builds an unsupervised learning system segmenting 8,950 credit card customers into **4 distinct behavioral clusters** using K-Means, enabling targeted campaigns that align product offerings (savings plans, loans, wealth management) with spending patterns. Analysis of 17 usage features—including purchase frequency, cash advance behavior, and credit utilization—reveals segments ranging from budget-conscious low-spenders to premium high-value customers, providing actionable intelligence for campaign prioritization.

## 🎯 Objective

Develop a production-grade clustering model that identifies interpretable customer segments (≥0.40 Silhouette Score) while balancing computational efficiency for real-time scoring. Compare 4 clustering algorithms (K-Means, Gaussian Mixture, Agglomerative, DBSCAN), apply PCA for dimensionality reduction (17→10 features preserving 85% variance), and deliver business-ready segment profiles with marketing recommendations.

## 📊 Data Source

**[Credit Card Dataset for Clustering (Kaggle)](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata):** 8,950 active credit card holders tracked over 12 months. Features include balance ($40-$20k range), purchase amounts (one-off vs installments), cash advances, payment behavior, credit limits, and tenure. Key challenge: right-skewed distributions and 3.5% missing values in MINIMUM_PAYMENTS and CREDIT_LIMIT requiring median imputation.

## 🔧 Methodology

**Pipeline:** Missing value imputation (median for robustness to outliers) → CUST_ID removal → RobustScaler normalization (IQR-based, handles financial data outliers) → PCA dimensionality reduction (17→10 components, 85% variance retained) → clustering algorithm comparison (K-Means, GMM, Hierarchical, DBSCAN) → Elbow method + Silhouette analysis for optimal K selection.

**Algorithm Evaluation:** Trained K-Means with K∈{2,3,4,5,6}, Gaussian Mixture Models (soft clustering, probability-based assignments), Agglomerative Hierarchical (Ward linkage, dendrogram analysis), and DBSCAN (density-based outlier detection). **K-Means with K=4** selected as optimal—achieved highest Silhouette Score (0.42) and Calinski-Harabasz Index (4,287), indicating well-separated, cohesive clusters. Four segments balance granularity (actionable insights) with interpretability (avoids over-segmentation).

## 💡 Key Insights

- **Purchase behavior drives segmentation:** PURCHASES correlates 0.92 with ONEOFF_PURCHASES and 0.68 with INSTALLMENTS_PURCHASES—strongest differentiator across clusters, outweighing balance or credit limit
- **Bimodal utilization patterns:** 50% of customers maintain low balances (<$1k) with minimal purchases, while 25% exhibit high-engagement profiles (>$5k balances, frequent transactions)—suggesting two-tier product strategy
- **Cash advance users are isolated segment:** 23% of customers rely primarily on cash advances (avg $2,800/month) with near-zero purchases—require distinct debt consolidation offerings vs. rewards programs
- **Credit limit correlates with engagement:** Customers with >$10k limits show 3.2× higher purchase frequency and 2.1× higher payment consistency—premium tier justifies targeted wealth management services

## 🛠️ Tech Stack

**Core:** Python 3.8+, scikit-learn (K-Means, GMM, Hierarchical, DBSCAN, PCA), Pandas, NumPy, Matplotlib/Seaborn  
**Techniques:** K-Means Clustering, PCA (Dimensionality Reduction), Silhouette Analysis, Elbow Method, RobustScaler

## 🚀 How to Run

```bash
git clone https://github.com/yourusername/customer-segmentation-clustering.git
cd customer-segmentation-clustering
pip install -r requirements.txt
jupyter notebook customer_segmentation_clustering.ipynb
```
**Runtime:** ~3-5 minutes | **Output:** Customer segment assignments + cluster profiles

## 📁 File Structure

```
├── customer_segmentation_clustering.ipynb       # Main analysis (10 sections)
├── cluster_visualization.png                    # 2D PCA segment plot
├── elbow_silhouette_analysis.png                # Optimal K selection
├── cluster_profiles_heatmap.png                 # Segment characteristics
└── requirements.txt                             # Dependencies
```

**Data:** [Credit Card Dataset on Kaggle](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata) (8,950 customers × 17 features)

---

**Performance:** Silhouette = 0.42 | Calinski-Harabasz = 4,287 | Davies-Bouldin = 1.18 | **4 segments** | **85% variance preserved** (17→10 features via PCA)
