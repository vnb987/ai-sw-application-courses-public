# AI SW Application — Weekly Project Set

A 16-week, hands-on introduction to AI/ML for first-year university students with **little or no prior AI background**. Each week pairs the lecture theme with a small, self-contained project so students immediately try the idea in code rather than only hearing about it.

- **Audience:** beginners — first-year students, minimal programming/math prerequisites
- **Language:** Python
- **Platform:** [Google Colab](https://colab.research.google.com/) — every notebook is self-contained (no local setup, no external data files) and runs top-to-bottom with `Runtime > Run all`
- **Format:** one `project.ipynb` per week plus a short `README.md` explaining the concept, the project, and stretch exercises

## How to use these notebooks

1. Open the week's `project.ipynb` on GitHub and click the **"Open in Colab"** badge at the top (or upload the file manually at [colab.research.google.com](https://colab.research.google.com/)).
2. Run cells top to bottom (`Runtime > Run all`). Any package that isn't preinstalled on Colab is installed by a `!pip install` cell at the top of that notebook.
3. Read the markdown explanations between code cells — they connect the code back to the week's lecture concept.
4. Try the **"Try it yourself"** exercises at the end of each notebook — this is where the real learning happens.

No local installation is required. If a student prefers to run notebooks locally instead, `requirements.txt` lists the packages used across all 16 weeks.

## Weekly plan

| Week | Lecture theme | Project | Key libraries |
|---|---|---|---|
| 1 | Course intro & major Python AI libraries | [Student Exam Score Explorer](week01-python-ai-libraries/) — NumPy/pandas/matplotlib data analysis | numpy, pandas, matplotlib |
| 2 | Supervised learning I (k-NN, linear regression) | [Flower Classifier & House Price Predictor](week02-supervised-learning-1/) | scikit-learn |
| 3 | Supervised learning II (decision tree, ensembles, neural nets) | [Wine Classifier Showdown](week03-supervised-learning-2/): decision tree vs. random forest vs. MLP | scikit-learn |
| 4 | Unsupervised learning I (dimensionality reduction, PCA) | [Visualizing Handwritten Digits with PCA](week04-unsupervised-learning-1-pca/) | scikit-learn, matplotlib |
| 5 | Unsupervised learning II (clustering, k-means) | [Customer Segmentation with K-Means](week05-unsupervised-learning-2-kmeans/) | scikit-learn |
| 6 | Data representation (categorical encoding, feature engineering) | [Used Car Price Predictor](week06-data-representation/): encoding & feature engineering | pandas, scikit-learn |
| 7 | Model evaluation (cross-validation, metrics) | [Breast Cancer Diagnosis Evaluator](week07-model-evaluation/): CV, confusion matrix, ROC/AUC | scikit-learn |
| 8 | **Midterm exam** (covers weeks 1–7) | [Optional self-check review](week08-midterm-exam/) | — |
| 9 | PyTorch basics | [Handwritten Digit Classifier with PyTorch](week09-pytorch-intro/): first neural net trained from scratch | torch, torchvision |
| 10 | Convolutional neural networks (CNN) | [Fashion Image Classifier with a CNN](week10-cnn-image-classification/) | torch, torchvision |
| 11 | Graph neural networks (GNN) | [Community Detection with a GNN](week11-gnn-node-classification/): GCN on Zachary's Karate Club | torch, networkx |
| 12 | NLP basics & word embeddings | [Word Embeddings & Semantic Similarity](week12-nlp-word-embeddings/) | gensim, scikit-learn |
| 13 | Recurrent neural networks (RNN) | [Name Generator with a Character-Level LSTM](week13-rnn-name-generator/) | torch |
| 14 | LLMs & agentic AI | [Build a Local LLM Chatbot & Tool-Using Agent](week14-llm-agentic-ai/) | transformers |
| 15 | Reinforcement learning basics | [Teaching an Agent to Escape a Frozen Lake](week15-reinforcement-learning/): tabular Q-learning | gymnasium |
| 16 | **Final exam** (covers weeks 9–15) | [Exam info](week16-final-exam/) | — |

## Notes for instructors

- Every non-exam notebook builds a small, complete, runnable project rather than isolated code snippets — the goal is an "aha, I can actually build this" moment each week, not library-reference coverage.
- Datasets are either scikit-learn/torchvision built-ins (no download needed beyond the library's own cache) or small datasets generated/embedded directly in the notebook, so nothing breaks due to a missing file or a dead link.
- Week 14 needs no API key or account — it runs a small open-source model (`Qwen2.5-1.5B-Instruct`) locally in Colab, free of charge. A Colab GPU runtime makes it noticeably faster but isn't required.
- Weeks 9–15 assume Colab's free GPU is *not* required — everything trains in well under a minute or two on CPU — but enabling a Colab GPU runtime (`Runtime > Change runtime type`) will make weeks 9–13 faster.
