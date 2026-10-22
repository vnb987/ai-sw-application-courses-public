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
(a.k.a. market basket analysis) — applied to real listening data from
[`Gabriel-Kahen/user_music_listening_dataset`](https://github.com/Gabriel-Kahen/user_music_listening_dataset)
(a GitHub mirror of the Kaggle dataset `gabrielkahen/music-listening-data-500k-users`):
~476,000 Last.fm users' personal top-50 artist lists, ~531,000 unique
artists, downloadable with no login. Unlike the older HetRec 2011 dataset
this replaced, it's confirmed (in-notebook, not assumed) to actually
contain contemporary artists — Taylor Swift, Olivia Rodrigo, Chappell
Roan, BTS, BLACKPINK, NewJeans and more are all present, each reported
with its real popularity rank among ~531K artists. Each user's top-50 set
becomes a "transaction," `mlxtend`'s **Apriori** algorithm mines frequent
artist combinations (`low_memory=True`, needed for this much larger
item/user space), and `association_rules` turns those into rules scored
by **support**, **confidence**, and **lift** (with an explanation of why
lift corrects confidence's bias toward already-popular artists).
Preprocessing samples 50,000 users and keeps the top 500 most-listened
artists — chosen specifically to keep all of the example contemporary
artists above instead of just collapsing to decade-old classics.
Visualizations cover the most popular artists, the distribution of
frequent-itemset sizes, and a support-vs-confidence scatter colored by
lift. The centerpiece is an `ipywidgets` recommender: search and select
your own favorite artists, tune Min Support / Confidence / Lift / Min
Antecedent Length sliders, and get ranked recommendations — derived only
from the mined rules, matched by **antecedent-subset** (not exact-match),
aggregated when multiple rules recommend the same artist, with a
plain-language explanation and a clear "no matching rules" message rather
than a fabricated recommendation when nothing applies. The Min Antecedent
Length slider is a direct, hands-on way to see how requiring *all* of
your selected artists together (rather than any single one) sharpens
recommendations: for `{Taylor Swift, Olivia Rodrigo}`, raising it from 1
to 2 drops single-artist-triggered rules and keeps only ones genuinely
requiring both — e.g. Sabrina Carpenter's confidence jumps from a
single-artist rule to a much stronger 0.61 once both are required. On
real data, `{Taylor Swift, Olivia Rodrigo}` surfaces Gracie Abrams/
Chappell Roan/Sabrina Carpenter, and `{BTS, BLACKPINK}` surfaces TOMORROW
X TOGETHER/Seventeen/ITZY — genuinely coherent, contemporary clusters.
