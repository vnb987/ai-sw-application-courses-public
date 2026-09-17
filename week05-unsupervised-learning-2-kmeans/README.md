# Week 5 — Unsupervised Learning II (Clustering, K-Means)

**Lecture theme:** Unsupervised learning — clustering with k-means.

## Project: Customer Segmentation with K-Means

A classic business use case for unsupervised learning: given customers'
**annual income** and a **spending score**, automatically discover natural
customer segments — with no labels telling the algorithm what a "segment" is.

You'll:
- Generate a realistic synthetic customer dataset (5 income/spending groups)
- Use the **elbow method** to pick a sensible number of clusters
- Run K-Means and visualize the discovered segments and their centers
- Interpret each segment in plain business language
- See **why initial centroids matter**: a hand-picked *bad* starting point
  (two of three centroids dropped inside the same dense group) is run
  through Lloyd's algorithm step by step, plotting all 6 iterations, so you
  watch one true group get wrongly split while two separate ones get merged
  — then a *good* starting point (one centroid per true group) is run
  through the same 6 iterations side by side, converging correctly from the
  first step, before comparing both runs' final inertia against
  scikit-learn's default (`init='k-means++'`, `n_init=10`)

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week05-unsupervised-learning-2-kmeans/project.ipynb)

## Try it yourself

Try a "wrong" number of clusters and see clusters get awkwardly split or merged.
