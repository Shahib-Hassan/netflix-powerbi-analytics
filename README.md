# 🎬 Netflix Content Performance & ROI Analytics Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)
![Data Modeling](https://img.shields.io/badge/Data_Model-Star_Schema-red?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Data_Source-Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)

An executive-grade, interactive Power BI report designed to analyse content profitability, viewer ratings, and portfolio ROI across global media streaming data. Wrapped in a custom, Netflix-inspired dark UI.

---

## 📸 Dashboard Overview

| Executive View | Filtered Category View | Detail View |
|---|---|---|
| ![Executive Dashboard](https://raw.githubusercontent.com/Shahib-Hassan/netflix-powerbi-analytics/main/images/dashboard_main.png) | ![Filtered Dashboard](https://raw.githubusercontent.com/Shahib-Hassan/netflix-powerbi-analytics/main/images/dashboard_filtered.png) | ![Detail View](https://raw.githubusercontent.com/Shahib-Hassan/netflix-powerbi-analytics/main/images/dashboard_detail.png)|

---

## 🎯 Key Business Questions & Insights

* **Portfolio Efficiency:** How effectively does budget allocation drive gross revenue and net profit across media types?
* **Genre Profitability:** Which content categories act as primary financial growth drivers for the catalog?
* **ROI Optimization:** What is the historical return on investment (ROI) distribution across release windows?

### 💡 Core Key Takeaways:
* **Top Performers:** Drama and Thriller genres led total net profitability across the entire library.
* **Portfolio Returns:** Maintained an overall average portfolio **ROI above 200%**.
* **Interactivity:** Dynamic slicers enable instant drill-down into specific release windows, media formats (Movies vs. TV Shows), and multi-genre combinations.

---

## 🏗️ Architecture & Data Modelling

The project is structured around a **Star Schema** dimensional model to ensure optimal DAX performance, quick query execution, and seamless dynamic filtering.

```text
                  ┌────────────────────────┐
                  │ Dim_Content_Metadata   │
                  └───────────┬────────────┘
                              │ 1
                              │
                              │ *
┌────────────────┐ *      ┌───┴──────────────────────┐      * ┌───────────────────────┐
│ Dim_Geography  ├────────┤ Fact_Content_Performance ├────────┤ Dim_Talent_Production │
└────────────────┘        └───┬──────────────────────┘        └───────────────────────┘
                              │ *
                              │
                              │ 1
                  ┌───────────┴────────────┐
                  │        Dim_Date        │
                  └────────────────────────┘
```
---

## 🧮 DAX Measures & Logic

Key business metrics were developed using custom, explicit DAX formulations:

  ```dax
  Total Revenue = SUM(Fact_Content_Performance[Revenue])
  Total Profit = [Total Revenue] - SUM(Fact_Content_Performance[Budget])
  ROI % =  DIVIDE( [Total Profit], SUM(Fact_Content_Performance[Budget]), 0)
  ```
