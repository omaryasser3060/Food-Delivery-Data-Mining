# 🛒 Food Delivery Analysis & Hybrid Recommendation Engine

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-150458.svg)](https://pandas.pydata.org/)
[![NetworkX](https://img.shields.io/badge/NetworkX-Graph_Theory-005b9f.svg)](https://networkx.org/)
[![MLxtend](https://img.shields.io/badge/MLxtend-Association_Rules-ff69b4.svg)](http://rasbt.github.io/mlxtend/)
[![Transformers](https://img.shields.io/badge/HuggingFace-BERT-yellow.svg)](https://huggingface.co/)

---

## 📌 Project Overview

In the highly competitive landscape of food delivery and online grocery retail, understanding consumer ordering behavior is a critical driver for revenue growth, inventory optimization, and customer retention. This repository contains a robust, end-to-end Data Mining pipeline designed to uncover hidden purchasing patterns and deploy an intelligent recommendation system using the large-scale [Instacart Online Grocery Basket Dataset](https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset).

To enhance decision-making beyond transactional patterns, the system integrates deep learning-based sentiment analysis using the [Amazon Fine Food Reviews Dataset](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews), enabling semantic understanding of customer feedback.

This project bridges the gap between descriptive analytics, graph-based modeling, and modern NLP-driven intelligence, forming a hybrid recommendation system that is both behavior-aware and sentiment-aware.

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
* **Hidden Influencers:** Applied the PageRank algorithm to pinpoint structurally central grocery items and discover "hidden influencers" that anchor consumer dietary habits.

### 5. BERT-based Sentiment Intelligence Layer (Task 2)

* **Deep Learning Integration:** Leveraged a pre-trained BERT model (`distilbert-base-uncased-finetuned-sst-2-english`) via HuggingFace Transformers to perform large-scale sentiment analysis on customer reviews.
* **Data Engineering:** Processed over 500K textual reviews by mapping rating scores into sentiment labels (positive, neutral, negative) and applying BERT-compatible minimal preprocessing (preserving punctuation and contextual structure).
* **Efficient Inference:** Applied stratified sampling and batch inference to ensure computational feasibility while maintaining representative class distribution.
* **Model Evaluation:** Achieved ~84% accuracy on binary sentiment classification (positive vs negative) using classification reports and confusion matrices, while properly handling the neutral class limitation.
* **Error Analysis:** Identified key failure modes including sarcasm, mixed sentiment, and domain-specific vocabulary mismatch due to pre-training on non-food datasets.
* **Insight Extraction:** Discovered behavioral patterns such as longer negative reviews and high model confidence even in misclassifications, highlighting real-world NLP challenges.

### 6. Hybrid Recommendation Engine

* **Object-Oriented Design:** Engineered a deployable system that integrates behavioral patterns with semantic sentiment understanding.
* **Dual-Strategy Routing:**

  * **Primary:** Uses association rules for precise cross-selling recommendations.
  * **Fallback:** Uses PageRank to suggest globally popular items.
  * **Sentiment Filter:** Enhances recommendations by prioritizing items with high-confidence positive sentiment and filtering out negatively perceived products.

---

## 📊 Visualizations & Analytics

The pipeline incorporates professional-grade visualizations:

* **Association Rule Scatter Plots:** Support vs Confidence, scaled by Lift.
* **PageRank Centrality Charts:** Highlighting influential products.
* **Confusion Matrix & Classification Metrics:** Evaluating BERT performance.
* **Sentiment Distribution & Confidence Analysis:** Understanding model behavior and reliability.
* **Review Length Analysis:** Revealing behavioral differences across sentiment classes.

---

## ⚠️ Important Notes & Execution

* **Runtime Memory:** Ensure sufficient RAM for graph operations and NLP inference.
* **Model Limitations:** BERT model is binary (positive/negative); neutral class handled separately.
* **Sampling Strategy:** Used to balance performance and computational cost.
* **Exported Artifacts:** Generates rule files and sentiment-enriched outputs for downstream systems.

---

## 🧰 Prerequisites

```bash
pip install pandas numpy matplotlib networkx mlxtend kagglehub transformers
```

---

## 👥 Team Members

Helwan National University

| # | Name (English)              | ID        |
| - | --------------------------- | --------- |
| 1 | Omar Yasser                 | 931250621 |
| 2 | Omar Mostafa Abdsttar Ali   | 931250634 |
| 3 | Ayman Nageh Mohamed Mohamed | 931230074 |
| 4 | Youssef Atef Tayeh          | 931230366 |
| 5 | Ismail Ibrahim Ismail       | 931230063 |

---

**Transforming raw basket data into scalable, intelligent, sentiment-aware recommendations.**
