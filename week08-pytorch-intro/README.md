# Week 8 — PyTorch Basics

**Lecture theme:** Building and training a neural network from scratch with PyTorch.

## Project: Handwritten Digit Classifier with PyTorch

In Week 3 we used scikit-learn's ready-made `MLPClassifier`. This week you
build the same kind of network **from scratch in PyTorch** — the library
you'll use for the rest of the course (CNNs, GNNs, RNNs, all sit on top of
this) — and train it on the classic **MNIST** dataset of handwritten digits.

You'll:
- Learn just enough tensor basics to be dangerous
- Define a small feedforward network with `nn.Module`
- Write the training loop yourself: forward pass → loss → backward pass → optimizer step
- Track training loss and test accuracy across epochs
- Look at which digits the trained model gets wrong

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week08-pytorch-intro/project.ipynb)

## Try it yourself

Add a hidden layer, or change the learning rate, and see how training changes.

## Extended Capstone (optional): Seoul Bike Sharing Demand with an MLP

A step up in scope: a **regression** problem on real **tabular** data
instead of classifying images — predicting hourly bike-rental demand in
Seoul from weather and time features (hour, temperature, humidity, wind
speed, visibility, dew point, solar radiation, rainfall, snowfall, season,
holiday, and whether the system was even running that hour), using the
[UCI Seoul Bike Sharing Demand dataset](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand)
(8,760 real hourly records, downloaded from a GitHub mirror with no login).
Covers the full pipeline end to end: dropping the unneeded `Date` column,
encoding `Holiday`/`Functioning Day` as binary flags and one-hot encoding
`Seasons`, a 60/20/20 train/validation/test split, and fitting
`StandardScaler` on the training data only to avoid leakage.

The core experiment: a from-scratch PyTorch MLP (fixed at two hidden
layers, ReLU, no output activation since it's regression) trained four
times with the exact same settings — only the neuron count per hidden
layer changes (**16 → 32 → 64 → 128**). Comparing MAE/MSE/RMSE/R² on the
same held-out test set, plus per-model train/validation loss curves, a
test-RMSE-vs-neuron-count plot, and an actual-vs-predicted scatter for the
best model, shows test RMSE improving steadily from 16 to 128 neurons —
but the training/validation loss gap also widens sharply with model size
(a clear, concrete overfitting signal), setting up five discussion
questions about why more neurons isn't a free lunch, and a closing note
that neuron count is only one of many hyperparameters worth tuning
properly (echoing Week 6's k-fold-CV-based hyperparameter search).
