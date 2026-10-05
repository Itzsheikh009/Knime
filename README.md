# ⚡ KNIME Analytics Workflows & Machine Learning Pipelines

[![KNIME Version](https://img.shields.io/badge/KNIME-v5.x-FFD000?style=for-the-badge\&logo=knime\&logoColor=black)](https://www.knime.com/)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge\&logo=python\&logoColor=white)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

A collection of **KNIME Analytics Platform workflows** demonstrating practical data science and machine learning tasks, including data preprocessing, classification, model comparison, ROC/AUC evaluation, visualization, and automated data workflows.

---

## 📌 Project Overview

This repository demonstrates an end-to-end **Customer Churn Classification** workflow built in KNIME.

The main objective is to preprocess customer data, train multiple machine learning models, compare their performance, and identify the model that provides the best classification results.

### 🎯 Main Objectives

* Import and prepare a customer churn dataset
* Handle missing values
* Normalize numerical features
* Split data into training and testing sets
* Train multiple classification models
* Generate predictions on test data
* Compare model performance
* Evaluate models using **ROC curves and AUC**
* Identify the best-performing classifier

---

# 🔄 Workflow Architecture

```text
                    ┌─────────────────┐
                    │   CSV Reader    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Missing Value  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Normalizer   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │Table Partitioner│
                    └────────┬────────┘
                             │
                 ┌───────────┴───────────┐
                 │                       │
                 ▼                       ▼
        ┌─────────────────┐     ┌────────────────────┐
        │ Decision Tree   │     │ Logistic Regression│
        │     Learner     │     │      Learner       │
        └────────┬────────┘     └──────────┬─────────┘
                 │                         │
                 ▼                         ▼
        ┌─────────────────┐     ┌────────────────────┐
        │ Decision Tree   │     │ Logistic Regression│
        │    Predictor    │     │     Predictor      │
        └────────┬────────┘     └──────────┬─────────┘
                 │                         │
                 └───────────┬─────────────┘
                             ▼
                    ┌─────────────────┐
                    │Column Appender  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    ROC Curve    │
                    │   Evaluation    │
                    └─────────────────┘
```

---

# 🤖 Machine Learning Models

Two supervised classification algorithms were evaluated for predicting customer churn:

### 1. Logistic Regression

A linear classification algorithm that estimates the probability of a customer belonging to the churn class.

**Advantages:**

* Simple and fast
* Easy to interpret
* Works well for linearly separable relationships
* Provides probability-based predictions

### 2. Decision Tree

A tree-based classification algorithm that makes predictions using a sequence of decision rules.

**Advantages:**

* Easy to understand and visualize
* Captures non-linear relationships
* Requires relatively little preprocessing
* Useful for rule-based interpretation

---

# 📊 Model Performance

The models were evaluated using the **ROC Curve** and **Area Under the Curve (AUC)**.

| Model                      | Prediction Column    | Classification Type         |       AUC | Performance |
| -------------------------- | -------------------- | --------------------------- | --------: | ----------- |
| 🥇 **Logistic Regression** | `P (Churn=Yes)`      | Linear / Parametric         | **0.846** | **Best**    |
| 🥈 **Decision Tree**       | `P (Churn=Yes) (#1)` | Tree-Based / Non-Parametric | **0.716** | Baseline    |
| ⚪ **Random Classifier**    | `random classifier`  | Random Guess                | **0.500** | Reference   |

### 🏆 Best Model

**Logistic Regression achieved the highest AUC of 0.846**, outperforming the Decision Tree model, which achieved an AUC of 0.716.

This indicates that Logistic Regression provided better discrimination between customers who are likely to churn and those who are not in this experiment.

---

# 📈 ROC & AUC Analysis

The **ROC (Receiver Operating Characteristic) curve** evaluates how well a classification model distinguishes between positive and negative classes at different probability thresholds.

**AUC (Area Under the Curve)** summarizes the ROC curve into a single performance score:

* **1.0** → Perfect classification
* **0.9–1.0** → Excellent
* **0.8–0.9** → Good
* **0.7–0.8** → Fair
* **0.5** → Random performance

### Results

```text
AUC Comparison

Logistic Regression   █████████████████░░░  0.846
Decision Tree         ██████████████░░░░░░  0.716
Random Classifier     ██████████░░░░░░░░░░  0.500
```

The results show that **Logistic Regression performed considerably better than the Decision Tree** for this dataset.

---

# 🧹 Data Preprocessing

Before training the models, the dataset was processed using the following KNIME nodes:

### 1. CSV Reader

Loads the customer churn dataset into the KNIME workflow.

### 2. Missing Value

Detects and handles missing values to prepare the dataset for machine learning.

### 3. Normalizer

Scales numerical features to a suitable range, helping ensure that features with different scales do not disproportionately affect the model.

### 4. Table Partitioner

Splits the dataset into:

* **Training Data** → Used to train the machine learning models
* **Testing Data** → Used to evaluate model performance

---

# 🔬 Evaluation Process

The general machine learning pipeline follows these steps:

```text
Dataset
   ↓
Data Preprocessing
   ↓
Train/Test Split
   ↓
Model Training
   ↓
Prediction
   ↓
Performance Evaluation
   ↓
ROC Curve & AUC
   ↓
Model Comparison
```

The models are trained using the **training data** and then used to generate predictions on the **testing data**. This helps evaluate how well each model performs on unseen data.

---

# 🛠️ Tools & Technologies

| Tool                         | Purpose                                   |
| ---------------------------- | ----------------------------------------- |
| **KNIME Analytics Platform** | Workflow development and machine learning |
| **Logistic Regression**      | Classification                            |
| **Decision Tree**            | Classification                            |
| **ROC Curve**                | Model evaluation                          |
| **AUC**                      | Performance measurement                   |
| **CSV Dataset**              | Input data                                |

---

# 📁 Repository Structure

```text
KNIME-Analytics-Workflows/
│
├── README.md
│
├── workflows/
│   ├── Customer_Churn.knwf
│   └── ...
│
├── datasets/
│   └── customer_churn.csv
│
├── screenshots/
│   ├── workflow.png
│   ├── decision_tree.png
│   ├── logistic_regression.png
│   └── roc_curve.png
│
└── LICENSE
```

---

# 📌 Key Findings

* **Logistic Regression** achieved the best AUC score of **0.846**.
* **Decision Tree** achieved an AUC of **0.716**.
* The random classifier provided the reference AUC of **0.500**.
* Logistic Regression showed better ability to distinguish churned customers from non-churned customers.
* ROC/AUC provides a useful way to compare classification models independently of a single probability threshold.

---

# 🚀 Future Improvements

The workflow can be extended by adding:

* Random Forest
* K-Nearest Neighbors (KNN)
* Naive Bayes
* Support Vector Machine (SVM)
* XGBoost
* Confusion Matrix
* Accuracy, Precision, Recall, and F1-Score
* Hyperparameter tuning
* Cross-validation
* Feature selection
* Class imbalance handling

These improvements can provide a more comprehensive comparison of machine learning algorithms.

---

# 🎓 Learning Outcomes

Through this project, the following concepts were practiced:

* Data preprocessing
* Missing-value handling
* Feature normalization
* Train/test splitting
* Supervised machine learning
* Classification
* Model prediction
* ROC curve analysis
* AUC evaluation
* Machine learning model comparison
* Building visual workflows in KNIME

---

## 👨‍💻 Author

**Abdur Rehman**

Data Science Student | Machine Learning Enthusiast

**Focus Areas:**
Data Science • Machine Learning • Python • Data Analysis • AI

---

## ⭐ Conclusion

This project demonstrates how **KNIME Analytics Platform** can be used to build a complete machine learning pipeline without requiring extensive programming.

Based on the experimental results, **Logistic Regression was the best-performing model**, achieving an **AUC of 0.846**, compared with **0.716 for Decision Tree**.

The workflow provides a practical foundation for experimenting with additional machine learning algorithms and evaluation techniques.
