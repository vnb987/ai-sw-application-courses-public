# Week 6 — Data Representation (Categorical Encoding, Feature Engineering)

**Lecture theme:** How to represent data for a model — encoding categorical variables and feature engineering.

## Project: Used Car Price Predictor

Machine learning models only understand numbers — but real data is full of
text categories ("SUV", "diesel", "automatic"). This week's project builds a
small used-car dataset and shows, step by step, how the *same* linear
regression model gets dramatically better as we improve how the data is
represented:

1. Numbers-only baseline (ignore categorical columns) → bad
2. Add categorical columns via **one-hot encoding**
3. Add an **engineered feature** (car age from purchase year)
4. **Scale** the features and compare error at every step

Then, using real
[Titanic passenger data](https://www.kaggle.com/datasets/yasserh/titanic-dataset)
(downloadable with no Kaggle login, unlike a competition dataset), the rest
of this week's preprocessing topics:

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

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week06-data-representation/project.ipynb)

## Try it yourself

Try label encoding instead of one-hot encoding for the brand column and see why
it can silently confuse a linear model. Then try Z-score-based outlier
detection on `Fare` instead of IQR, and look again at the used-car example's
own scaling step to spot (and explain) its own leakage-safety issue.
