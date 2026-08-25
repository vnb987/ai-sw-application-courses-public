# Week 12 — NLP Basics & Word Embeddings

**Lecture theme:** NLP fundamentals — representing words as vectors (word embeddings).

## Project: Word Embeddings & Semantic Similarity

How can a computer know that "king" and "queen" are related, or that "Paris"
relates to "France" the same way "Berlin" relates to "Germany"? This week you
train a small **Word2Vec** model on a purpose-built toy corpus and see word
meaning emerge as geometry — words used in similar contexts end up as nearby
vectors.

You'll:
- Train `gensim`'s Word2Vec on a small custom corpus (no huge download needed)
- Query `most_similar()` to find a word's nearest neighbors in vector space
- Try the classic **vector arithmetic** trick (`paris - france + germany ≈ berlin`)
- Visualize the learned word vectors in 2D with PCA (tying back to Week 4) and
  see words cluster by category

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week12-nlp-word-embeddings/project.ipynb)

## Try it yourself

Add your own word pairs and template sentences to the corpus, retrain, and see
if your new words' vectors show up where you'd expect.
