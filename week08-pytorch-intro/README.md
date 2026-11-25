# Week 8 — Multi-Layer Perceptron (MLP)

**Lecture theme:** Building and training a neural network from scratch with PyTorch.

## Project: Seoul Bike Sharing Demand Prediction, then MNIST Classification

This week you build a feedforward network **from scratch in PyTorch** — the
library you'll use for the rest of the course (CNNs, RNNs, LSTMs, all sit on
top of this). The main project is a **regression** problem on real tabular
data: predicting hourly bike-rental demand in Seoul from weather and time
features (hour, temperature, humidity, wind speed, visibility, dew point,
solar radiation, rainfall, snowfall, season, holiday, and whether the system
was even running that hour), using the
[UCI Seoul Bike Sharing Demand dataset](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand)
(8,760 real hourly records, downloaded from a GitHub mirror with no login).

You'll:
- Encode `Holiday`/`Functioning Day` as binary flags and one-hot encode
  `Seasons`, split 60/20/20 train/validation/test, and fit `StandardScaler`
  on the training data only to avoid leakage
- Define a from-scratch PyTorch MLP (`nn.Module`, using `nn.ModuleList` so
  the number of hidden layers is configurable) and write the training loop
  yourself: forward pass → loss → backward pass → optimizer step
- Train five models that isolate two design choices — hidden-layer **width**
  (Models A–D: 16 → 32 → 64 → 128 neurons, 2 hidden layers each) and
  hidden-layer **depth** (Model E: 1 hidden layer, same width as a 2-layer
  model) — and compare MAE/MSE/RMSE/R² on the same held-out test set
- Visualize per-model train/validation loss curves, a test-RMSE-vs-neuron-count
  plot that separates 1- vs. 2-hidden-layer models, and an hour-of-day
  actual-vs-predicted line plot that shows the MLP capturing the data's
  non-linear daily demand pattern — not just fitting a straight line

Afterward, the notebook moves to a simpler, more classic example —
classifying handwritten digits with the same kind of network on **MNIST**
— including a diagram of the network's architecture (with a zoomed-in look
at what a single hidden-layer node computes: weighted sum → ReLU) and a look
at which digits the trained model gets wrong.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week08-pytorch-intro/project.ipynb)
