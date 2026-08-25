# Week 4 — Unsupervised Learning I (Dimensionality Reduction, PCA)

**Lecture theme:** Unsupervised learning — dimensionality reduction and PCA.

## Project: Visualizing Handwritten Digits with PCA

No labels used for training here — **PCA (Principal Component Analysis)** finds
the directions of greatest variation in the data and compresses it, without
ever being told what a "0" or a "7" looks like.

Using scikit-learn's built-in 8×8 handwritten digit images, you'll:
- Compress each 64-pixel image down to just 2 numbers
- Plot all ~1,800 digits in a 2D scatter plot — and watch same-digit clusters
  emerge, purely from pixel variation
- See how much information is lost by reconstructing images from the compressed version

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week04-unsupervised-learning-1-pca/project.ipynb)

## Try it yourself

Try keeping 3, 10, and 30 components instead of 2, and see how reconstruction
quality changes.
