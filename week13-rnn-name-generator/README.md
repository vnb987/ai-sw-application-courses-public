# Week 13 — Recurrent Neural Networks (RNN)

**Lecture theme:** Modeling sequential data with RNNs.

## Project: Name Generator with a Character-Level LSTM

Images and tables don't have an inherent order, but text, speech, and time
series do — the order of characters in a word matters. This week you train a
small **character-level LSTM** on a list of ~200 real first names, one letter
at a time, and then sample brand-new, never-seen names from it.

You'll:
- Turn text into sequences of integers (character-level tokenization)
- Build a small `nn.LSTM`-based model that predicts "what letter comes next?"
- Train it and watch generated names get more name-like over epochs
- Sample new names, with a "temperature" knob controlling how adventurous the
  model gets

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week13-rnn-name-generator/project.ipynb)

## Try it yourself

Train on a list of your own choosing (Pokémon names, cities, ...) instead of
first names.
