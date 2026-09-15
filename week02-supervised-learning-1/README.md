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

**Part B — Linear Regression** — predict a numeric disease-progression score
from a single health measurement, and read the fitted line as "for every +1
unit of X, the prediction changes by *this much*."

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week02-supervised-learning-1/project.ipynb)

## Try it yourself

Compare k-NN against a "dumb" majority-class baseline on Breast Cancer,
compare linear regression against a "predict the average" baseline, and add
a second feature (`s5`) to the regression — starter code for combining the
two features and splitting the data is included, so the exercise is just
fitting and comparing the R².
