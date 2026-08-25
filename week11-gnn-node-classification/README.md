# Week 11 — Graph Neural Networks (GNN)

**Lecture theme:** GNN theory and practice.

## Project: Community Detection with a Graph Neural Network

Some data isn't a table of rows and columns — it's a **network** of connected
entities (friends, web pages, molecules). This week you build a small **Graph
Convolutional Network (GCN)** *from scratch* (just PyTorch tensor operations —
no extra graph library needed beyond `networkx` for the graph itself) on the
famous **Zachary's Karate Club** graph: 34 members of a karate club, which
split into two real-world factions after a conflict.

You'll:
- Build the graph's (normalized) adjacency matrix by hand
- Implement a GCN layer as one line of matrix multiplication
- Train with only **4 labeled members** and predict which faction everyone
  else joined, using nothing but the graph's structure
- Visualize the network before and after training, and watch the two
  factions visually separate in the model's learned embedding

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week11-gnn-node-classification/project.ipynb)

## Try it yourself

Reduce the labeled set to just 2 nodes and see if the GCN can still recover
the factions from structure alone.
