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

**Part B — Linear Models: Regression & Regularization**:

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
3. `LogisticRegression → RidgeClassifier → LogisticRegression(L1) →
   RidgeClassifierCV → LogisticRegressionCV`, in that order, on Kaggle's
   **[Gisette](https://www.kaggle.com/datasets/fedesoriano/gisette-dataset-mnist-digits-4-and-9)**
   dataset — separating handwritten digits **4 vs. 9** from 5,000 features,
   about half of which are pure noise by design (a NIPS 2003 feature
   selection benchmark). With features outnumbering training rows, an
   unregularized `LogisticRegression` baseline overfits badly (great
   training fit, weak test accuracy). This time real classifiers are used
   throughout instead of regressing on encoded labels: `RidgeClassifier`
   is Ridge's classification counterpart, and since there's no
   "LassoClassifier," `LogisticRegression` with an L1 penalty
   (`l1_ratio=1`, `solver='saga'`) plays that role — introduced first with
   a hand-picked regularization strength (with a Korean explanation of
   `alpha`/`C` and typical candidate values for each), then
   `RidgeClassifierCV`/`LogisticRegressionCV` show how cross-validation
   searches for the best value automatically — the L1 classifier zeroes
   out hundreds of the noise features outright, closing with a 5-model
   test-accuracy comparison + chart. A couple of real 4/9 digit images
   from scikit-learn's bundled `load_digits()` open the section for
   intuition (Gisette's own 5,000 features aren't raw pixels, so they
   can't be plotted directly).

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week02-supervised-learning-1/project.ipynb)

## Try it yourself

Compare k-NN against a "dumb" majority-class baseline on Breast Cancer,
compare linear regression against a "predict the average" baseline, and add
a second feature (`s5`) to the regression — starter code for combining the
two features and splitting the data is included, so the exercise is just
fitting and comparing the R².
