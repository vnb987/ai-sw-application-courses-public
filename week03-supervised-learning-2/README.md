# Week 3 — Supervised Learning II (Decision Tree, Ensembles, Boosting)

**Lecture theme:** Tree-based models, in the order they historically build on
each other — decision tree → random forest → AdaBoost → gradient boosting →
XGBoost → LightGBM.

## Project: Tree Ensembles & Boosting Showdown

Six regressors, same head-to-head comparison, but this time each one is
explained with its own key hyperparameters (candidate values + defaults)
before you train it:

- **Decision Tree** — one tree of yes/no questions
- **Random Forest** — many trees trained independently, voting together (bagging)
- **AdaBoost** — weak trees trained sequentially, each focusing on the last one's mistakes
- **Gradient Boosting (GBM)** — each new tree fits the ensemble's residual error
- **XGBoost** — a heavily optimized, regularized gradient boosting library
- **LightGBM** — a faster gradient boosting library using leaf-wise tree growth

All six train on Kaggle's classic **[House Prices: Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)**
competition — predicting a house's `SalePrice` from 12 strong numeric
features (full categorical encoding is deferred to Week 6's data
representation topic) — so the final comparison is a fair, apples-to-apples
one. All train/test splitting uses scikit-learn's `train_test_split`.

Before the six-model comparison, a short section introduces automated
hyperparameter search — **GridSearchCV**, **RandomizedSearchCV**, and
**HalvingRandomSearchCV** (with each one's own key parameters and defaults),
positioned right after AdaBoost. Decision Tree/Random Forest/AdaBoost use
hand-picked hyperparameters; Gradient Boosting/XGBoost/LightGBM use each
model's *tuned* version (via RandomizedSearchCV). Right before the capstone,
a summary table + chart compares RMSE, training time, and inference time
across all six models.

## Setup: a free Kaggle account + accepting the competition rules

Unlike a plain dataset, a **competition** download requires being logged
into a (free) Kaggle account and clicking **"Join Competition"** once on the
[competition page](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
to accept its rules — `kagglehub` will prompt you to log in the first time
you run that cell.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/week3-boosting-update/week03-supervised-learning-2/project.ipynb)

## Try it yourself

Log-transform `SalePrice` before training (and un-transform the predictions
before scoring) — does RMSE improve? This is what the real competition's
RMSLE metric rewards.

## Capstone: Predict Tomorrow's Stock Price with XGBoost

Fetch real historical price data with `yfinance` (open/high/low/close/
adjusted-close/volume plus 5/20/60/120-day moving averages), and train an
`XGBRegressor` to predict the next day's closing price — then plot
predicted vs. actual and compute RMSE.
