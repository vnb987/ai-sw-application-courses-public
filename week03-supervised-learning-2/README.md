# Week 3 — Supervised Learning II (Decision Tree, Ensembles, Neural Nets)

**Lecture theme:** More supervised algorithms — decision trees, ensemble methods, and neural networks.

## Project: Wine Classifier Showdown

Same dataset, three different learners, head to head:

- **Decision Tree** — a single tree of yes/no questions; easy to visualize and explain
- **Random Forest** — an *ensemble* of many trees voting together
- **Neural Network (MLP)** — a small multi-layer perceptron

Using scikit-learn's built-in **wine** dataset (13 chemical measurements, 3
wine cultivars), you'll train all three, compare accuracy, and look at which
features the forest thinks matter most.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week03-supervised-learning-2/project.ipynb)

## Try it yourself

Change the tree's `max_depth`, the forest's `n_estimators`, and the MLP's
hidden layer size, and see how each affects accuracy.
