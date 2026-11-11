# Week 7 — PyTorch Basics

**Lecture theme:** Getting comfortable with tensors and autograd before
building real neural networks.

## Project: Tensors & Autograd

So far scikit-learn has done all the heavy lifting for us (`.fit()` did
everything). Starting next week, we build networks ourselves with
**PyTorch** — so before touching a real network, this week is just about the
two building blocks everything else sits on.

You'll:
- Learn what a `Tensor` is, and the handful of options (`dtype`, `device`,
  `requires_grad`) you'll actually use
- Watch `requires_grad=True` + `.backward()` compute a real gradient
- Fit a straight line (`y = w·x + b`) to noisy data using **nothing but
  autograd** — forward pass → loss → backward pass → manual weight update,
  by hand, before `nn.Module` and optimizers hide those four steps starting
  in Week 8

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week07-pytorch-basics/project.ipynb)

## Try it yourself

Change the learning rate to see training diverge or crawl, add more noise to
the data, or extend the fit from a line to a quadratic (`y = w2*x^2 + w1*x + b`)
using the exact same four steps.
