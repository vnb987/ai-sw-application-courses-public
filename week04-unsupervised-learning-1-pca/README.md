# Week 4 — Unsupervised Learning I (Dimensionality Reduction, PCA)

**Lecture theme:** Unsupervised learning — dimensionality reduction, PCA, and NMF.

## Project: Visualizing Handwritten Digits with PCA, Feature Selection & NMF

High-dimensional data is hard to work with (the "curse of dimensionality") —
there are two families of fix: **feature selection** (pick a subset of the
original features) and **feature extraction** (transform features into new
ones). This week covers a method from each family, plus a second extraction
method for comparison:

**Part 1 — Feature Selection:** predicting a student's exam score from 8
candidate signals (only 3 are genuinely useful; one is a near-duplicate of
another; the rest are noise). Implements and compares all four classic
subset-selection strategies:
- **Exhaustive search** — try every possible subset (feasible here since
  there are only 8 features → 255 subsets; explicitly not feasible for more)
- **Forward selection** — start empty, greedily add the most helpful
  remaining feature each step
- **Backward elimination** — start full, greedily remove the least useful
  feature each step
- **Stepwise selection** — alternates forward/backward steps so a feature
  can be reconsidered and removed later

**Part 2 — PCA (Feature Extraction):** no labels used for training here —
**PCA** finds the directions of greatest variation in scikit-learn's
built-in handwritten digit images and compresses them, without ever being
told what a "0" or a "7" looks like.
- Compress each 64-pixel image down to just 2 numbers, and watch same-digit
  clusters emerge in a 2D scatter plot purely from pixel variation
- See how many components are needed to keep 95% of the variance, and how
  reconstruction quality degrades with fewer components
- **Limitations of PCA**, shown concretely: PCA collapses two non-linear
  crescents (`make_moons`) into an overlapping mess (it assumes roughly
  linear/Gaussian structure), and a synthetic 2-class example where the
  highest-variance direction (PC1) barely beats a coin flip at
  classification while the original features get 90%+ accuracy (PCA never
  looks at the label)

**Part 3 — NMF (Non-negative Matrix Factorization):** another feature
extraction method, but constrained to non-negative values — a natural fit
for pixel brightness (which is never negative). The 8x8 digit images are a
bit too small to make PCA vs. NMF's difference easy to see, so this part
switches to scikit-learn's built-in **Olivetti faces** (400 64x64 face
photos, 40 people) and compares components side by side: PCA's components
("eigenfaces") are diffuse, ghostly red/blue patterns with negative
values, while NMF's look like recognizable face *parts* — an eyebrow, a
nose, shading around the eyes — at the cost of slightly higher
reconstruction error, since PCA is the mathematically optimal linear
reconstruction for a given number of components.

Part 3 closes with a **recent trend**: autoencoders — a neural-network
take on the same "compress, then reconstruct" idea, built here with
scikit-learn's `MLPRegressor` (PyTorch isn't introduced until a later
week) by training it to predict its own input back through a small
bottleneck. A **linear** autoencoder (no activation function) lands on
almost exactly PCA's reconstruction error, concretely demonstrating the
textbook result that a linear autoencoder learns the same subspace as
PCA. A **non-linear** (ReLU) autoencoder is also tried and — with only
400 training photos — typically comes out *worse* than PCA/NMF, a
realistic lesson that neural approaches need far more data (and, later,
convolutional architectures) before their extra flexibility pays off.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week04-unsupervised-learning-1-pca/project.ipynb)

## Try it yourself

Plot the digits in 3D instead of 2D, spot which digit clusters overlap the
most (and whether that matches digits that look alike when handwritten),
try reconstructing with just 1 PCA component, and confirm PC1/PC2 are
uncorrelated by construction. Then modify the feature-selection dataset so
a feature gets added early but becomes redundant once a better one is
added later — does stepwise selection catch it and remove it? — and try
more NMF components (16 or 32) to see if reconstructed faces get sharper.

## Capstone: DEVTi — Discover Your Developer DNA with PCA

A much larger capstone built entirely around this week's main topic,
analyzing **developer and problem-solving style** instead of a generic
MBTI-style personality test. Instead of hand-picking 4 style axes up
front, it defines **64 fine-grained developer traits** (across
communication, analysis, planning and building habits), writes **40
natural-language survey questions** relatable to CS students of any
experience level (each weighted across 5-7 related traits), and lets
**PCA itself discover** 4 interpretable axes (Collaborative↔Solo,
Analytical↔Intuitive, Planner↔Explorer, Builder↔Visionary) from 10,000
simulated student respondents — since real large-scale survey data
isn't available, a generative model (latent dev-style → 64 traits →
simulated Likert responses) stands in for it. Because PCA is unsupervised,
its components don't automatically line up with the 4 intended axes, so
each component is matched to its best-fitting axis by correlation
(`scipy.optimize.linear_sum_assignment`) and sign-corrected — not a
replacement for PCA, just how its output gets interpreted. The notebook
then classifies the resulting score into one of 16 developer characters
(each with a nickname, emoji, description, strengths, cautions, a
"synergy" teammate type, and playfully-framed recommended fields),
visualizes explained variance and per-axis PCA loadings, and finally lets
you take the actual 40-question survey via `ipywidgets` (with a live
progress indicator) — projecting your answers into the *already fitted*
PCA space (never refitting PCA on a single response). An explicit
disclaimer: this is an educational PCA simulation, not a validated
assessment of real job aptitude or developer skill.
