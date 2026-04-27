# 🛒 Food Delivery Analysis & Hybrid Recommendation Engine

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-150458.svg)](https://pandas.pydata.org/)
[![NetworkX](https://img.shields.io/badge/NetworkX-Graph_Theory-005b9f.svg)](https://networkx.org/)
[![MLxtend](https://img.shields.io/badge/MLxtend-Association_Rules-ff69b4.svg)](http://rasbt.github.io/mlxtend/)

---

## 📌 Project Overview
In the highly competitive landscape of food delivery and online grocery retail, understanding consumer ordering behavior is a critical driver for revenue growth, inventory optimization, and customer retention. This repository contains a robust, end-to-end Data Mining pipeline designed to uncover hidden purchasing patterns and deploy an intelligent recommendation system using the large-scale [Instacart Online Grocery Basket Dataset](https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset).

This project bridges the gap between descriptive statistics and predictive machine learning. By analyzing millions of transactional records, the system mathematically maps out exactly which items are ordered together, establishing a foundation for automated, data-driven cross-selling.

---

## 🏗️ Core Architecture & Pipeline

### 1. Data Preprocessing & Dimensionality Reduction
* **Transformation:** Converted a massive, highly sparse transactional dataset into a sanitized, mathematically viable matrix. 
* **Optimization:** Applied rigorous text normalization, removed anomalous single-item orders, and utilized strategic feature selection (constraining to the top 1,500 products) to heavily optimize computational performance.

### 2. Frequent Pattern Extraction (FP-Growth)
* **Efficiency:** Utilized the FP-Growth algorithm to mine frequent itemsets, completely bypassing the computational and memory bottlenecks associated with traditional Apriori methods in sparse environments (achieving ~99.5% matrix sparsity).
* **Discovery:** Successfully identified 144 frequent itemsets using a strictly defined 1% minimum support threshold.

### 3. Association Rule Mining
* **Business Logic:** Derived strict, actionable business rules evaluated through rigorous statistical metrics: **Support**, **Confidence**, and **Lift**.
* **Filtration:** Isolated the most reliable and lucrative cross-selling relationships through multi-criteria filtering, ultimately exporting the strongest rules for deployment.

### 4. Graph Theory & Network Centrality (PageRank)
* **Topological Modeling:** Modeled the entire food delivery ecosystem as an interconnected graph using `NetworkX`. Nodes represent products, and weighted edges represent co-purchases.
* **Hidden Influencers:** Applied the PageRank algorithm to pinpoint structurally central grocery items and discover "hidden influencers" that anchor consumer dietary habits, even if their raw sales volumes are not the highest.

### 5. Hybrid Recommendation Engine
* **Object-Oriented Design:** Engineered a deployable system that seamlessly integrates two distinct strategies.
* **Dual-Strategy Routing:**
  * **Primary:** Uses mined association rules for exact, personalized cross-selling suggestions.
  * **Fallback:** Utilizes graph-based PageRank popularity metrics to guarantee relevant suggestions when carts trigger no rules, effectively eliminating "cold start" failures.

---

## 📊 Visualizations & Analytics
The pipeline incorporates professional-grade visualizations to interpret the data:
* **PageRank Centrality Plots:** Horizontal, gridless bar charts highlighting the most influential network nodes.
* **Association Rule Scatter Plots:** Color-mapped distributions of Support vs. Confidence, sized by Lift, to instantly identify prime cross-selling targets.
* **Network Topology:** Filtered subgraph renderings showing the physical footprint of aggregated purchase behaviors.

---

## ⚠️ Important Notes & Execution

* **Runtime Memory:** Ensure your environment has sufficient RAM before executing the graph-based analysis cells, as rendering large topological networks is resource-intensive.
* **Environment Setup:** The pipeline uses `kagglehub` to directly download the dataset. Ensure you have an active internet connection on the first run.
* **Exported Artifacts:** The notebook will automatically generate three files in your working directory (`all_rules.csv`, `strong_rules.csv`, and `top_rules.csv`) which can be ingested by external dashboards or UI interfaces.

---

## 🧰 Prerequisites
Ensure you have the following libraries installed:

```bash
pip install pandas numpy matplotlib networkx mlxtend kagglehub
```

---

## 👥 Team Members  
Helwan National University  

| # | Name (English)                     | ID        |
|--|----------------------------------|----------|
| 1 | Omar Yasser                      | 931250621 |
| 2 | Youssef Atef Tayeh              | 931230366 |
| 3 | Ayman Nageh Mohamed Mohamed     | 931230074 |
| 4 | Omar Mostafa Abdsttar Ali       | 931250634 |
| 5 | Ismail Ibrahim Ismail           | 931230063 |

---

**Transforming raw basket data into scalable, intelligent recommendations.**
