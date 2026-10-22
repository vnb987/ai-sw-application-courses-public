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
- Meet **DBSCAN**, a density-based alternative to K-Means: on two
  interleaving crescents (plus scattered noise points) that K-Means can't
  separate correctly, a hand-implemented DBSCAN is run with instrumentation
  that snapshots the label array after every point is processed, then 6
  evenly-spaced snapshots are plotted to show clusters growing outward from
  a seed point along the density-connected crescent shape, with leftover
  points marked as noise. The hand-rolled version is checked against
  `sklearn.cluster.DBSCAN` (100% label agreement), then a side-by-side plot
  shows K-Means splitting the crescents with an arbitrary straight-ish
  boundary versus DBSCAN correctly separating them and flagging the noise

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week05-unsupervised-learning-2-kmeans/project.ipynb)

## Try it yourself

Try a "wrong" number of clusters and see clusters get awkwardly split or merged.

## Capstone: Study Group Matcher

150 students' "preferred start time / preferred group size / focus intensity"
dummy data is provided. Run K-Means to split them into a few "study
personality" groups, then enter your own preferences and find which group
you'd match.

## Extended Capstone (optional): Movie Taste Clustering & Recommendation

A step up in scope: a small group-based recommender built on real
[MovieLens](https://movielens.org/) rating data (`ml-latest-small`, ~600
users, ~9,700 movies, ~100k ratings — downloadable with no account or
login, unlike Kaggle). A genre-balanced set of ~20-30 well-known "reference
movies" is chosen, each eligible user is represented as their rating vector
over just those movies (missing entries filled with that user's own average
rating), and K-Means groups users into taste clusters. For movies outside
the reference set, each cluster's average rating (requiring a minimum
number of ratings to trust) becomes the recommendation signal. You rate a
handful of the reference movies yourself, get assigned to a cluster via
`kmeans.predict()`, and pull that cluster's Top-5 highest-rated movies you
haven't already seen.

## Extended Capstone 2 (optional): Music Recommendation with Apriori

A different kind of unsupervised learning — **association rule mining**
(a.k.a. market basket analysis) — applied to real
[Last.fm listening data (HetRec 2011)](https://grouplens.org/datasets/hetrec-2011/)
(~1,900 users, downloadable with no login). Each user's set of listened-to
artists becomes a "transaction," `mlxtend`'s **Apriori** algorithm mines
frequent artist combinations, and `association_rules` turns those into
rules like `{Coldplay, Radiohead} → {Muse}`, scored by **support**,
**confidence**, and **lift** (with an explanation of why lift corrects
confidence's bias toward already-popular artists). Visualizations cover
the most popular artists, the distribution of frequent-itemset sizes, and
a support-vs-confidence scatter colored by lift. The centerpiece is an
`ipywidgets` recommender: search and select your own favorite artists,
tune Min Support / Confidence / Lift sliders, and get ranked recommendations
—  derived only from the mined rules, matched by **antecedent-subset**
(not exact-match), aggregated when multiple rules recommend the same
artist, with a plain-language explanation and a clear "no matching rules"
message rather than a fabricated recommendation when nothing applies. A
later section re-runs Apriori itself at a few different `min_support`
values so you can see how the number of frequent itemsets and rules
changes, closing with discussion questions on confidence's popularity bias
and Apriori's cold-start limitation. An instructor's note at the end covers
expected runtime, key preprocessing knobs, and common errors.
