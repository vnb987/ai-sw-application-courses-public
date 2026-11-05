# Week 6 — Data Representation & Model Evaluation

**Lecture theme:** How to represent data for a model (encoding, feature
engineering, missing values, outliers), then how to properly evaluate the
model you trained on it (train/validation/test, cross-validation, confusion
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

## Does the missing-value / outlier-handling method actually matter?

Lecture covered several ways to handle missing values (mean, median, mode,
regression, multiple imputation/MICE) and several ways to detect outliers
(IQR, Z-score, LOF, PCA reconstruction error, Isolation Forest). The
used-car example never had any missing values or outliers to clean, so
this part digs into both questions properly — each with a dataset that
actually lets us *measure* the effect of the choice, not just show what
each method does:

5. **A rigorous missing-value comparison: mean vs. median vs. mode vs.
   regression vs. MICE** — using the
   [UCI Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality)
   dataset (1,599 wines, 11 physicochemical measurements → quality score)
   and a `RandomForestRegressor`: train on the complete data for a
   baseline RMSE, then randomly knock out 5%, 10%, 20%, and 30% of the
   **training** set's input features, fill them back in with each method,
   and train a **new** model on each imputed version — evaluating all of
   them on the same untouched test set. At low missingness all five
   methods perform similarly, but mode becomes the clear loser once
   missingness reaches 20-30%, while regression and MICE separate from
   the pack and end up closest to the clean baseline.
6. **A quick multiple-imputation (MICE) example** — the comparison above
   already answers "does the method matter" with real ground truth. This
   is just a quick, fun demonstration of *how* to actually use MICE
   somewhere with much richer structure: the **user x movie rating
   matrix** from Week 5's clustering capstone (real
   [MovieLens](https://movielens.org/) data). There's no ground truth to
   score it against here, so it's a demonstration, not another
   comparison.
7. **Does the outlier-removal method matter? (Wine Quality)** — ~5% of
   the Wine Quality training rows are contaminated with synthetic
   outliers (each one mixes real measurements from several different
   wines, so no single column looks unusual on its own, only the
   combination). A `RandomForestRegressor` is then compared with no
   removal against removing them via **IQR**, **LOF**, and **PCA
   reconstruction error**. IQR ends up flagging far more rows than it
   actually catches of the true outliers (it only ever looks at one
   column at a time) and removing them makes the model *worse* than
   doing nothing; LOF and PCA reconstruction error — which judge a row by
   its whole combination of features — flag a tighter, more accurate set
   and genuinely bring performance back toward the uncontaminated
   baseline.

## Part 2 — Project: Breast Cancer Diagnosis Evaluator

A single train/test split can be lucky or unlucky — and with only a train
and test set, there's nowhere to decide *when to stop training* without
peeking at the test set. This part trains an **XGBoost** classifier on
scikit-learn's built-in breast cancer diagnostic dataset (predict malignant
vs. benign from 30 measurements), using a model that actually puts a
validation set to work:

- **Train / validation / test** — XGBoost is given a generous 200-tree
  budget but told to stop early once the **validation** score stops
  improving; the **test** set is only touched once, at the very end, to
  report the final number
- **k-fold cross-validation for hyperparameter tuning** — instead of just
  reporting an averaged accuracy, 5-fold CV on the train+validation data
  is used to search a small grid of `max_depth` and `learning_rate`
  (explained as we go), picking the best combination before the final
  refit
- **Confusion matrix** — which mistakes does the model actually make?
- **Precision, recall, F1** — and why accuracy alone can be misleading,
  especially for a medical diagnosis task where missing a malignant case
  is worse than a false alarm
- **ROC curve & AUC**

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week06-data-representation-and-evaluation/project.ipynb)
