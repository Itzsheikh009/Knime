# ⚡ KNIME Analytics Workflows & Machine Learning Pipelines

[![KNIME Version](https://img.shields.io/badge/KNIME-v5.x-FFD000?style=for-the-badge&logo=knime&logoColor=black)](https://www.knime.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

A structured suite of **KNIME Analytics Platform** workflows demonstrating end-to-end data preprocessing, classification model comparison, performance visualization, and automated spreadsheet manipulation.

---

## 📊 Pipeline Architecture & Performance Breakdown

### 🛠️ 1. Classifier Benchmarking & ROC Analysis

This workflow compares two supervised algorithms—**Logistic Regression** and **Decision Trees**—predicting customer churn (`Churn = Yes`).

```text
       [ 📁 CSV Reader ]
              │
      [ ❓ Missing Value ]
              │
       [ ⚖️ Normalizer ]
              │
     [ ✂️ Table Partitioner ]
        /           \
       /             \
[ 🌲 Decision Tree ]  [ 📈 Logistic Regression ]
   Learner & Predictor    Learner & Predictor
       \             /
        \           /
      [ 🔗 Column Appender ]
              │
      [ 📉 ROC Curve Node ]



True Positive Rate (Sensitivity)
1.0 ┼─────────────────────────────────╭───────────────────── Logistic Regression (AUC = 0.846)
0.8 ┼───────────────────────────╭─────╯..................... Decision Tree (AUC = 0.716)
0.6 ┼─────────────────╭─────────╯......................... Random Classifier (AUC = 0.500)
0.4 ┼───────────╭─────╯
0.2 ┼─────╭─────╯
0.0 ┼─┼───┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─
   0.0       0.20      0.40      0.60      0.80      1.00
               False Positive Rate (1 - Specificity)


<img width="1251" height="315" alt="image" src="https://github.com/user-attachments/assets/52649c37-1756-4e28-ab20-00e21b661498" />
