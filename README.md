# 🚢 Titanic Survival Classification

## Overview

Can passenger information be used to predict who survived the Titanic?

For this project, I used the **Titanic Kaggle dataset** to build and compare several classification models in R. I worked through the full machine learning process, including data cleaning, model training, cross-validation, model comparison, and generating predictions for unseen test data.

This project was completed as a midterm for **STAT 652: Statistical Learning**.

**Final Kaggle Score: 0.76555**

---

## 📊 Project Workflow

### 1. Data Preparation

I began by cleaning the training and test datasets so that they could be used consistently across the different models.

The preprocessing included:

- Converting cabin numbers into cabin-letter categories
- Converting categorical predictors into factors
- Handling missing values in `Age` and `Fare`
- Creating an `"Unknown"` category for missing categorical information
- Checking factor levels between the training and test datasets
- Removing identifier variables that were not useful for prediction
- Splitting the labeled data into **75% training and 25% validation sets**

---

### 2. Establishing a Baseline

Before fitting more complex models, I created a **Null Model** to establish a baseline.

The Null Model predicted the majority class and achieved a validation accuracy of approximately:

**64.1%**

This gave me a starting point for determining whether the other classification methods were actually improving prediction performance.

---

## 🤖 Models

I trained and compared six classification approaches:

| Model | Validation Accuracy |
|---|---:|
| Null Model | 64.1% |
| K-Nearest Neighbors | 83.4% |
| Boosted C5.0 | **86.1%** |
| Random Forest | 84.3% |
| LASSO Logistic Regression | 82.5% |
| Naive Bayes | 75.8% |

For models requiring hyperparameter selection, I used **5-fold cross-validation** to tune the models.

---

## 🔧 Model Tuning

### K-Nearest Neighbors

KNN predictors were normalized because the algorithm relies on distances between observations.

Values of `K` from 1 through 30 were evaluated using cross-validation.

**Selected K: 17**

### Boosted C5.0

I evaluated different numbers of boosting trees using cross-validation.

**Selected number of trees: 11**

### Random Forest

The Random Forest model used 500 trees while tuning `mtry` and `min_n`.

**Selected parameters:**

```text
mtry = 4
min_n = 5
```

### LASSO Logistic Regression

Regularized logistic regression was implemented using LASSO (`mixture = 1`).

**Selected penalty:**

```text
0.002395027
```

### Naive Bayes

I tuned the smoothing and Laplace correction parameters.

**Selected parameters:**

```text
Smoothness = 0.5
Laplace = 2
```

---

## 📈 Model Evaluation

I evaluated the models using multiple approaches rather than relying only on training accuracy.

The evaluation included:

- Accuracy
- Cohen's Kappa
- Confusion matrices
- ROC curves
- AUC
- Training vs. validation performance

Comparing training and validation results also helped identify models
