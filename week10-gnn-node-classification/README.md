# Week 10 — RNN, LSTM, GRU

**Lecture theme:** How RNNs carry information across time steps, why they
struggle with long sequences (vanishing gradients), and how LSTM/GRU fix
that — plus where LSTM-based models are actually used.

## Project: Three Hands-On Examples — Image Captioning, Text-to-Speech, Translation

Three short, independent examples, each built around an LSTM or GRU doing
real sequence-generation work:

1. **Image Captioning** — a pretrained, frozen CNN (ResNet18) encodes a
   photo into a feature vector, and an **LSTM decoder you train from
   scratch** (on a subset of real COCO captions, downloaded directly from
   the official COCO dataset) generates a caption for it one word at a
   time (with a diagram of the CNN-encoder → LSTM-decoder architecture).
   Comes with a default image (`zidane.jpg`, the same one from Week 9) and
   an optional Colab-upload cell for your own photo.
2. **Text-to-Speech (TTS)** — a pretrained **Tacotron2** model (its decoder
   is itself LSTM-based) turns a typed English sentence into a mel
   spectrogram, which a Griffin-Lim vocoder turns into audio you can play
   right in the notebook.
3. **Translation** — a **GRU Encoder-Decoder with attention**, trained from
   scratch (English→Korean, on a filtered subset of real human-translated
   sentence pairs from the Tatoeba Project),
   translates a sentence you type, and the result is compared side by side
   with a real call to **Google Translate**. The gap between the two is
   itself the lesson: a small model trained briefly in class vs. a
   production system trained at massive scale.

Part 1, 2, and 3 only need the shared setup in Part 0, so you can run them
in any order.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week10-gnn-node-classification/project.ipynb)

A GPU runtime (`Runtime > Change runtime type`) is recommended — Part 1 and
Part 3 train a model from scratch inside the notebook. The full notebook
takes roughly 15–20 minutes end-to-end on a Colab GPU, most of it spent
downloading the COCO caption images in Part 1.
