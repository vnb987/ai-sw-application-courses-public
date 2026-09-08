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

All six train on Kaggle's **[Laptop Price](https://www.kaggle.com/datasets/muhammetvarl/laptop-price)**
dataset — predicting a laptop's price (`Price_euros`) from 5 numeric specs
pulled out of otherwise-textual columns with regex (screen size, RAM, weight,
CPU speed, storage — full categorical encoding of things like `Company`/
`TypeName` is deferred to Week 6's data representation topic) — so the final
comparison is a fair, apples-to-apples one. All train/test splitting uses
scikit-learn's `train_test_split`.

Before the six-model comparison, a short section introduces automated
hyperparameter search — **GridSearchCV**, **RandomizedSearchCV**, and
**HalvingRandomSearchCV** (with each one's own key parameters and defaults),
positioned right after AdaBoost. Decision Tree/Random Forest/AdaBoost use
hand-picked hyperparameters; Gradient Boosting/XGBoost/LightGBM use each
model's *tuned* version (via RandomizedSearchCV). Right before the capstone,
a summary table + chart compares RMSE, training time, and inference time
across all six models.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/week3-boosting-update/week03-supervised-learning-2/project.ipynb)

## Try it yourself

Log-transform the price before training (and un-transform the predictions
before scoring) — does RMSE improve? Prices are right-skewed (a handful of
very expensive laptops), so this often helps.

## Capstone: Predict Tomorrow's Stock Return with XGBoost

Fetch real historical price data with `yfinance` (open/high/low/close/
adjusted-close/volume plus 5/20/60/120-day moving averages), and train an
`XGBRegressor` to predict the next day's **return** — `(next close - today's
close) / today's close` — rather than the raw price. A "+1.5%" pattern holds
regardless of whether the stock trades at ₩50,000 or ₩100,000, so predicting
returns generalizes better from a small dataset than predicting price levels
directly. Convert back to a price only at the end (`today's close × (1 +
predicted return)`) for the actual-vs-predicted plot and RMSE.
