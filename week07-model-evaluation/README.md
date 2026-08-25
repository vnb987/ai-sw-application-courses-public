# Week 7 — Model Evaluation (Cross-Validation, Metrics)

**Lecture theme:** How to properly evaluate a model — cross-validation and evaluation metrics.

## Project: Breast Cancer Diagnosis Evaluator

A single train/test split can be lucky or unlucky. This week's project trains
a logistic regression classifier on scikit-learn's built-in breast cancer
diagnostic dataset (predict malignant vs. benign from 30 measurements) and
properly evaluates it:

- **k-fold cross-validation** instead of one split
- **Confusion matrix** — which mistakes does the model actually make?
- **Precision, recall, F1** — and why accuracy alone can be misleading, especially
  for a medical diagnosis task where missing a malignant case is worse than a
  false alarm
- **ROC curve & AUC**

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week07-model-evaluation/project.ipynb)

## Try it yourself

Adjust the classification threshold and watch precision and recall trade off
against each other.
