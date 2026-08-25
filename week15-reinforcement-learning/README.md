# Week 15 — Reinforcement Learning Basics

**Lecture theme:** Fundamentals of reinforcement learning and basic agent training.

## Project: Teaching an Agent to Escape a Frozen Lake

No labeled data this time — a reinforcement learning agent learns purely from
**trial, error, and reward**. Using `gymnasium`'s classic **FrozenLake**
environment (a 4×4 grid with a goal, holes, and a slippery surface), you'll
implement **tabular Q-learning** from scratch and watch a completely random
agent turn into one that reliably reaches the goal.

You'll:
- Understand the state / action / reward / episode framing of RL
- Build and update a Q-table with the Q-learning update rule
- Balance exploration vs. exploitation with an epsilon-greedy policy
- Plot the reward curve across thousands of training episodes
- Visualize the learned policy on the grid

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week15-reinforcement-learning/project.ipynb)

## Try it yourself

Turn off the lake's "slippery" randomness and see how much faster the agent learns.
