# 📊 Google Analytics US E-Commerce Dashboard: Tableau Visualization

![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat&logo=tableau&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=flat&logo=google-sheets&logoColor=white)
![Analytics](https://img.shields.io/badge/Google%20Analytics-E37400?style=flat&logo=google-analytics&logoColor=white)

## 📌 Overview

E-commerce businesses struggle to identify regional performance patterns across 50+ US states with limited visibility into conversion efficiency and revenue concentration. This project transforms **Google Analytics 2021 data** spanning all US states into an interactive Tableau dashboard revealing geographic revenue distribution, transaction volume leaders, and conversion optimization opportunities. Built on **cleaned web analytics data** (127K+ sessions, 21K+ transactions, $2.3M revenue), the four-panel dashboard exposes California's dominance (32% of total revenue despite 29% bounce rate), scatter analysis pinpointing conversion inefficiencies (Washington achieves 8.5% conversion vs 3.4% Florida despite similar traffic), and treemap visualization showing monetization gaps—enabling data-driven regional marketing allocation.

## 🎯 Objective

Design an executive-ready Tableau dashboard synthesizing Google Merchandise Store web analytics into actionable insights via: (1) geographic heatmap identifying revenue concentration patterns, (2) transaction volume rankings revealing high-engagement states, (3) scatter plot diagnosing bounce rate vs conversion rate efficiency, (4) treemap exposing user volume vs monetization imbalance. Deliver publish-ready visualization demonstrating data wrangling (Google Sheets), geocoding, calculated fields (Revenue per User, Avg Order Value, Revenue Tiers), and multi-chart dashboard composition.

## 📊 Data Source

**Google Analytics 4 Demo Property:** [Google Merchandise Store](https://support.google.com/analytics/answer/6367342) Location Report for United States (2021 full year). Dataset includes 50 US states + "(not set)" with metrics: Users (74,623 CA → 531 WY), Sessions (127K CA → 778 WY), Transactions (9,230 CA → 8 WY), Revenue ($746K CA → $677 WY), Bounce Rate (29%-57% range), Ecommerce Conversion Rate (2.4%-8.5% range), Session Duration, Pages/Session. Data wrangling performed in Google Sheets: revenue string parsing (removing "US$" prefix), duplicate removal, format standardization, calculated field engineering (Revenue Tiers, Revenue per User, Avg Order Value).

## 🔧 Methodology

**Data Preparation (Google Sheets):** CSV import → whitespace removal → header formatting → duplicate validation (50 states + 1 "(not set)" = 51 rows) → totals row elimination → revenue string parsing (LEFT/RIGHT functions extracting numeric values from "US$XXX.XX") → data type conversion (text → numeric for calculations) → column resizing/renaming → export as cleaned_analytics_data.csv.

**Tableau Dashboard Design:** Data connection → geocoding (Region field mapped to State/Province geographic role) → calculated field creation (Revenue per User = SUM(Revenue)/SUM(Users), Avg Order Value = SUM(Revenue)/SUM(Transactions), Revenue Tier binning via IF statements) → visualization construction: (1) **Filled Map** (states colored by revenue gradient, darker = higher revenue), (2) **Horizontal Bar Chart** (Top 10 states ranked by transaction count), (3) **Scatter Plot** (Bounce Rate X-axis, Conversion Rate Y-axis, state labels, reference lines for averages), (4) **Treemap** (rectangle size = Users, color intensity = Revenue, state labels showing values). Dashboard composition with consistent color scheme (blue-green gradient), title formatting, layout optimization for readability.

## 💡 Key Insights

- **Revenue concentration extreme:** California generates $746K (32% of US total) with 9,230 transactions—3× more than #2 New York ($155K)—revealing hyper-concentrated market requiring separate CA-specific strategy vs. rest-of-nation approach
- **Conversion efficiency paradox:** Washington achieves 8.5% conversion rate (highest nationwide) with only 29% bounce rate, while Florida suffers 3.4% conversion despite similar traffic volume—indicating landing page/checkout friction issues addressable via A/B testing and user journey optimization
- **High-traffic low-monetization gap:** Texas ranks #3 in users (20K) but #5 in revenue per user ($6.32), underperforming California's $10.00—suggests product-market fit issues or pricing elasticity requiring localized merchandising and promotional strategies
- **Bounce rate doesn't predict conversion linearly:** Scatter plot reveals Nebraska (45% bounce, 4.9% conversion) outperforms Maine (41% bounce, 3.9% conversion)—demonstrating quality-over-quantity traffic principle where engaged visitors matter more than raw session counts

## 🛠️ Tech Stack

**Data Wrangling:** Google Sheets (LEFT/RIGHT functions, data validation, formatting)  
**Visualization:** Tableau Public (maps, bar charts, scatter plots, treemaps, calculated fields)  
**Data Source:** Google Analytics 4 (Location Report, E-commerce metrics)

## 🚀 Live Dashboard

**[View Interactive Dashboard on Tableau Public](https://public.tableau.com/views/GoogleAnalyticsUS2021Visualization/MainDashboard)**

**Features:**
- Interactive map with drill-down capability
- Filterable bar charts and treemap
- Hover tooltips showing detailed metrics
- Mobile-responsive design

## 📁 File Structure

```
├── google_analytics_us_2021_dashboard.twbx         # Tableau workbook (packaged)
├── cleaned_analytics_data.csv                       # Wrangled data (51 states)
├── Analytics_Master_View_Location_2021.csv          # Raw Google Analytics export
├── dashboard_screenshot.png                         # Dashboard preview image
└── README.md                                        # Project documentation
```

**Data Dictionary:**
- **Users/Sessions/Transactions:** Volume metrics
- **Revenue:** Total e-commerce revenue (USD)
- **Bounce Rate:** % sessions with <2 page views
- **Ecommerce Conversion Rate:** Transactions / Sessions
- **Revenue Tier:** Binned categories (Dominant >$150K, Established $50-150K, Growing $10-50K, Emerging <$10K)

---

**Dashboard Metrics:** 50 US states analyzed | $2.3M total revenue | 21.5K transactions | 4 interactive visualizations | **Publish Date:** 2021 Annual Report
