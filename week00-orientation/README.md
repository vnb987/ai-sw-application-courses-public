# Week 0 — Orientation

**Lecture theme:** Course introduction — what this course covers, how the weekly materials work, and how to get set up.

## Welcome

This is a 16-week, hands-on introduction to AI/ML. You don't need any prior
AI background — just enough comfort with Python to read and edit code.
Every week pairs a short lecture with a small, self-contained project, so
you immediately try each idea in code instead of only hearing about it.

## How the course is structured

- **Weeks 1–6:** classical machine learning with scikit-learn — k-NN, linear
  regression & regularization, tree ensembles & boosting, PCA, k-means &
  DBSCAN, and how to represent data and evaluate a model properly.
- **Week 7:** midterm exam (covers weeks 1–6).
- **Weeks 8–14:** deep learning and beyond, in PyTorch — neural networks
  from scratch, CNNs, GNNs, NLP & word embeddings, RNNs, LLMs & agentic AI,
  and reinforcement learning.
- **Week 15:** final exam (covers weeks 8–14).

Each week's folder (`weekNN-topic/`) contains:

- **`README.md`** — the lecture theme, what the project covers, and the
  "Try it yourself" exercises, so you can preview a week before opening the
  notebook.
- **`project.ipynb`** — the hands-on notebook. Worked examples first, then
  a "Try it yourself" section, then (most weeks) a **capstone**: a slightly
  bigger, more open-ended problem that applies the same week's ideas to a
  new scenario, usually with a couple of `TODO`s for you to fill in
  yourself.

## Setting up

**No installation is required.** Everything runs in
[Google Colab](https://colab.research.google.com/), a free, browser-based
notebook environment — you just need a Google account.

1. Open any week's `project.ipynb` on GitHub and click the **"Open in
   Colab"** badge at the top of the file (or the top-level
   [README](../README.md)'s weekly table links straight to each week).
2. In Colab, run cells top to bottom with **`Runtime > Run all`**. Any
   package that isn't already on Colab is installed automatically by a
   `!pip install` cell inside that notebook — you don't need to install
   anything yourself ahead of time.
3. Read the markdown explanations between code cells as you go — they
   connect the code back to that week's lecture concept.

If you'd rather run notebooks locally instead of in Colab, the top-level
`requirements.txt` lists every package used across all 16 weeks — but this
is optional, not required for the course.

## What's expected each week

- Run the notebook and read through the worked examples.
- Complete the **"Try it yourself"** exercises — this is where most of the
  real learning happens, and there's often no single right answer.
- Complete that week's **capstone**, where one exists — it's the same
  ideas applied to a new, slightly more open-ended problem.

## Getting help

If something in a notebook doesn't run, first check that you ran the cells
in order from the top (`Runtime > Run all` is the easiest way to guarantee
this) — most errors come from skipping or re-running cells out of order.
Beyond that, bring questions to lecture or office hours.

Ready? Start with [Week 1](../week01-python-ai-libraries/).
