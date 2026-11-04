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
6. **A quick multiple-imputation (MICE) example** — Titanic's `Age` isn't a
   great dataset to showcase it, since it barely correlates with anything
   beyond `Pclass`/`Sex`. Instead, `IterativeImputer` is applied to the
   **user x movie rating matrix** from Week 5's clustering capstone (real
   [MovieLens](https://movielens.org/) data), just to show it fills every
   blank with a *different*, correlation-aware value instead of one flat
   number — there's no ground truth here to score it against, so this is a
   demonstration, not a comparison.
7. **A rigorous comparison: mean vs. median vs. mode vs. regression vs.
   MICE** — using the [UCI Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality)
   dataset (1,599 wines, 11 physicochemical measurements → quality score)
   and a `RandomForestRegressor`, this runs the actual experiment: train on
   the complete data for a baseline RMSE, then randomly knock out 5%, 10%,
   20%, and 30% of the **training** set's input features, fill them back
   in with each method, and train a **new** model on each imputed version
   — evaluating all of them on the same untouched test set. At low
   missingness all five methods perform similarly, but mode becomes the
   clear loser once missingness reaches 20-30%, while regression and MICE
   separate from the pack and end up closest to the clean baseline — a
   concrete, ground-truth-backed answer to "does the imputation method
   actually matter?"
8. **Outliers** — flag high-`Fare` passengers with the IQR method, then
   reason about whether to keep them (they're real 1st-class fares, not
   errors) or cap them
9. **Does the outlier-removal method matter? (Wine Quality)** — ~5% of the
   Wine Quality training rows are contaminated with synthetic outliers
   (each one mixes real measurements from several different wines, so no
   single column looks unusual on its own, only the combination). A
   `RandomForestRegressor` is then compared with no removal against
   removing them via **IQR**, **LOF**, and **PCA reconstruction error**.
   IQR ends up flagging far more rows than it actually catches of the true
   outliers (it only ever looks at one column at a time) and removing them
   makes the model *worse* than doing nothing; LOF and PCA reconstruction
   error — which judge a row by its whole combination of features — flag a
   tighter, more accurate set and genuinely bring performance back toward
   the uncontaminated baseline.
10. **Ordinal vs. nominal encoding** — `Pclass` (ordinal, already numeric)
   used as-is vs. `Sex`/`Embarked` (nominal) one-hot encoded
11. **Leakage-safe scaling** — a 3-way train/validation/test split, then a
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
