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

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week06-data-representation/project.ipynb)

## Try it yourself

Try label encoding instead of one-hot encoding for the brand column and see why
it can silently confuse a linear model.
