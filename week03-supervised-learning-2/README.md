# Week 3 — Supervised Learning II (Decision Tree, Ensembles, Boosting)

**Lecture theme:** Tree-based models, in the order they historically build on
each other — decision tree → random forest → AdaBoost → gradient boosting →
XGBoost → LightGBM.

## Project: Tree Ensembles & Boosting Showdown

Six models, same head-to-head comparison, but this time each one is
explained with its own key hyperparameters (candidate values + defaults)
before you train it:

- **Decision Tree** — one tree of yes/no questions
- **Random Forest** — many trees trained independently, voting together (bagging)
- **AdaBoost** — weak trees trained sequentially, each focusing on the last one's mistakes
- **Gradient Boosting (GBM)** — each new tree fits the ensemble's residual error
- **XGBoost** — a heavily optimized, regularized gradient boosting library
- **LightGBM** — a faster gradient boosting library using leaf-wise tree growth

All six train on the same real, imbalanced open dataset from Kaggle —
**[Calorie Burn Efficiency](https://www.kaggle.com/datasets/parasharmanu/close-to-realistic-calorie-efficiency-dataset)**
— predicting a person's calorie-burn efficiency (Low/Moderate/High) from
activity and body metrics, so the final comparison is a fair, apples-to-
apples one. All train/test splitting uses scikit-learn's `train_test_split`
(stratified).

Before the six-model comparison, a short section introduces automated
hyperparameter search — **GridSearchCV**, **RandomizedSearchCV**, and
**HalvingRandomSearchCV** (with each one's own key parameters and defaults)
— and the six-model showdown uses each model's *tuned* version
(via RandomizedSearchCV) rather than hand-picked hyperparameters. Right
before the capstone, a summary table + chart compares accuracy, training
time, and inference time across all six tuned models.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/week3-boosting-update/week03-supervised-learning-2/project.ipynb)

## Try it yourself

Sweep one hyperparameter (e.g. XGBoost's `max_depth`) across a few values and
plot accuracy vs. that value — where does it start overfitting?

## Capstone: Predict Tomorrow's Stock Price with XGBoost

Fetch real historical price data with `yfinance`, engineer technical-indicator
features (moving averages, volatility, momentum), and train an
`XGBRegressor` to predict the next day's closing price — then plot
predicted vs. actual and compute RMSE.
