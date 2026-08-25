# Week 9 — PyTorch Basics

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

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week09-pytorch-intro/project.ipynb)

## Try it yourself

Add a hidden layer, or change the learning rate, and see how training changes.
