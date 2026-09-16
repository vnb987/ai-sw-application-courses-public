# Week 2 — Supervised Learning I (k-NN, Linear Regression)

**Lecture theme:** Supervised learning fundamentals — k-nearest neighbors, linear regression, and other basic supervised algorithms.

## Project: Flower/Tumor Classifier, House Price Predictor & k-NN Regression

**Part A — k-Nearest Neighbors**, on three datasets, all built into
scikit-learn (nothing to download):

- **Iris** (classification) — classify flowers into 3 species from 4
  measurements
- **Breast Cancer** (classification) — classify tumors as malignant/benign
  from 30 measurements
- **California Housing** (regression) — predict a district's median house
  price from 8 features; k-NN regression averages the `k` nearest
  neighbors' target values instead of voting

For each dataset, a pair of blocks shows the basic k-NN workflow — split the
data, create the model (`k=1`), fit, evaluate — so you see the exact same
four-step pattern repeat across classification and regression. Then a
hands-on exercise section asks you to sweep `k` from 1 to 20 yourself for
each dataset and plot how accuracy (or RMSE, for housing) changes.

**Part B — Linear Regression & Regularization**:

1. Plain `LinearRegression` on the **diabetes** dataset — predict a numeric
   disease-progression score from a single health measurement (BMI), and
   read the fitted line as "for every +1 unit of X, the prediction changes
   by *this much*."
2. **Why scale before Ridge/Lasso?** Load diabetes again with `scaled=False`
   to get its original, unstandardized 10 features (e.g. `age` in 19–79,
   `s5` in 3.26–6.11) and fit `Ridge`/`Lasso` directly on them — the
   unscaled Lasso's coefficients end up large for naturally small-range
   features regardless of true importance. Apply `StandardScaler` and
   refit with the same `alpha`: R² improves (Ridge 0.464→0.478, Lasso
   0.430→0.458) and the zeroed-out coefficients make more sense, closing
   with a before/after bar chart.
3. `LinearRegression → Ridge → Lasso → RidgeCV → LassoCV`, in that order, on
   Kaggle's **[Song Popularity](https://www.kaggle.com/datasets/yasserh/song-popularity-dataset)**
   dataset — predicting a song's 0–100 popularity score from its audio
   features (danceability, energy, tempo, etc.). Ridge and Lasso are
   introduced first with a hand-picked `alpha` (with a Korean explanation
   of what `alpha` controls and typical candidate values for each), then
   `RidgeCV`/`LassoCV` show how cross-validation searches for the best
   `alpha` automatically, closing with a 5-model R² comparison + chart.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week02-supervised-learning-1/project.ipynb)

## Try it yourself

Compare k-NN against a "dumb" majority-class baseline on Breast Cancer,
compare linear regression against a "predict the average" baseline, add a
second feature (`s5`) to the regression (starter code for combining the two
features and splitting the data is included, so the exercise is just
fitting and comparing the R²), and turn Song Popularity into a binary
classification problem (popular vs. not, split at the median) to try
`LogisticRegression` — with its representative constructor arguments (`C`,
`l1_ratio`, `solver`, `max_iter`, `class_weight`) explained inline,
including that `penalty` is deprecated as of scikit-learn 1.8+ in favor of
`l1_ratio`/`C`.
