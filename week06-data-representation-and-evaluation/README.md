# Week 6 — Data Representation & Model Evaluation

**Lecture theme:** How to represent data for a model (encoding, feature
engineering, missing values, outliers, leakage-safe scaling), then how to
properly evaluate the model you trained on it (cross-validation, confusion
matrix, precision/recall, ROC/AUC).

## Part 1 — Project: Used Car Price Predictor

Machine learning models only understand numbers — but real data is full of
text categories ("SUV", "diesel", "automatic"). This part builds a small
used-car dataset and shows, step by step, how the *same* linear regression
model gets dramatically better as we improve how the data is represented:

1. Numbers-only baseline (ignore categorical columns) → bad
2. Add categorical columns via **one-hot encoding**
3. Add an **engineered feature** (car age from purchase year)
4. **Scale** the features and compare error at every step

Then, using real
[Titanic passenger data](https://www.kaggle.com/datasets/yasserh/titanic-dataset)
(downloadable with no Kaggle login, unlike a competition dataset), the rest
of this part's preprocessing topics:

5. **Missing values** — three columns, three strategies: drop `Cabin`
   (>70% missing), fill `Embarked` with the mode (only 2 missing), and fill
   `Age` with its `(Pclass, Sex)` group median (~20% missing — too much to
   drop, too group-dependent for a single global mean)
6. **Outliers** — flag high-`Fare` passengers with the IQR method, then
   reason about whether to keep them (they're real 1st-class fares, not
   errors) or cap them
7. **Ordinal vs. nominal encoding** — `Pclass` (ordinal, already numeric)
   used as-is vs. `Sex`/`Embarked` (nominal) one-hot encoded
8. **Leakage-safe scaling** — a 3-way train/validation/test split, then a
   side-by-side comparison of a `StandardScaler` fit on the full dataset
   (leaky) vs. fit on the training set only (correct), making the
   difference in the learned mean/std concrete

## Part 2 — Project: Breast Cancer Diagnosis Evaluator

A single train/test split can be lucky or unlucky. This part trains a
logistic regression classifier on scikit-learn's built-in breast cancer
diagnostic dataset (predict malignant vs. benign from 30 measurements) and
properly evaluates it, using the same train/validation/test rigor from
Part 1:

- **k-fold cross-validation** instead of one split
- **Confusion matrix** — which mistakes does the model actually make?
- **Precision, recall, F1** — and why accuracy alone can be misleading, especially
  for a medical diagnosis task where missing a malignant case is worse than a
  false alarm
- **ROC curve & AUC**

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week06-data-representation-and-evaluation/project.ipynb)

## Try it yourself

**Part 1:** Try label encoding instead of one-hot encoding for the brand
column and see why it can silently confuse a linear model. Then try
Z-score-based outlier detection on `Fare` instead of IQR, and look again at
the used-car example's own scaling step to spot (and explain) its own
leakage-safety issue.

**Part 2:** Adjust the classification threshold and watch precision and
recall trade off against each other.

## Capstones

This week has **two** capstones, one per part — do them in order.

**Part 1 — Used Textbook Price Estimator:** 200 dummy campus marketplace
listings (category, condition, age, original price → sold price). Apply
one-hot encoding + feature engineering + linear regression to estimate a
fair price for something you want to sell.

**Part 2 — Late-Submission Risk Predictor:** 250 dummy assignment records
(days before started / estimated hours / other deadlines that week /
difficulty → submitted late or not). Apply logistic regression + cross-
validation + confusion matrix/precision/recall to predict how risky your
next assignment is.
