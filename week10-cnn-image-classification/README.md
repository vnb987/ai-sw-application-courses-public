# Week 10 — Convolutional Neural Networks (CNN)

**Lecture theme:** CNN theory and image classification practice.

## Project: Fashion Image Classifier with a CNN

Last week's feedforward network flattened every image into a flat list of
pixels, throwing away all spatial structure. This week you build a small
**Convolutional Neural Network (CNN)** — the standard architecture for image
tasks — on **FashionMNIST** (10 clothing categories) and compare it directly
against a feedforward network of similar size.

You'll:
- Understand what a convolution + pooling layer actually computes
- Build a small CNN (`Conv2d` → `ReLU` → `MaxPool2d`, twice, then a classifier head)
- Train it and compare accuracy against a plain feedforward network
- Visualize the learned filters and the feature maps they produce

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week10-cnn-image-classification/project.ipynb)

## Try it yourself

Add a third convolutional layer and see if accuracy improves further.
