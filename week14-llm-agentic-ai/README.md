# Week 14 — LLMs & Agentic AI

**Lecture theme:** Solving problems with large language models and practicing agentic AI usage.

## Project: Build a Claude-Powered Chatbot & Tool-Using Agent

Everything so far trained a model from scratch on a small dataset. This week
flips that: you call a large, already-trained model — **Claude**, via the
Anthropic API — and see how far you can get with **prompting alone**, no
training required. Then you build a minimal **agent**: a loop where the model
can decide to call a tool (a Python function you wrote), see the result, and
use it to answer.

You'll:
- Make your first API call to Claude and read the response object
- See how a **system prompt** changes the model's behavior/persona
- Build a small multi-turn conversation loop
- Give Claude two tools (a calculator and a unit converter) and watch it
  decide *when* to call each one and use the result — the basic idea behind
  every "AI agent"

## Setup: you need an API key

1. Get an API key from the [Anthropic Console](https://console.anthropic.com/)
   (each student, or the class, needs one — ask your instructor if a shared
   classroom key is provided).
2. In Colab, the notebook will prompt you to paste your key securely (it is
   never displayed or saved to the notebook file).

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week14-llm-agentic-ai/project.ipynb)

## Try it yourself

Give the agent a third tool of your own design.
