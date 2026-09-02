# Week 14 — LLMs & Agentic AI

**Lecture theme:** Solving problems with large language models and practicing agentic AI usage.

## Project: Build a Local LLM Chatbot & Tool-Using Agent

Everything so far trained a model from scratch on a small dataset. This week
flips that: you call an already-trained model — a small **open-source model
running locally in Colab** (no paid API, no signup) — and see how far you
can get with **prompting alone**, no training required. Then you build a
minimal **agent**: a loop where the model can decide to call a tool (a
Python function you wrote), see the result, and use it to answer.

You'll:
- Load a free, open-source instruction-tuned model directly in Colab and
  make your first generation
- See how a **system prompt** changes the model's behavior/persona
- Build a small multi-turn conversation loop
- Give the model two tools (a calculator and a unit converter) via a small
  hand-built JSON tool-calling protocol, and watch it decide *when* to call
  each one and use the result — the basic idea behind every "AI agent",
  and the same pattern hosted APIs like Claude wrap in a native `tools`
  parameter

## Setup: nothing to install ahead of time

No API key and no account needed — the notebook downloads the model
(`Qwen2.5-1.5B-Instruct`, ~3 GB) the first time you run it. It works on CPU,
but runs much faster with a GPU: in Colab, go to *Runtime → Change runtime
type → T4 GPU* before running the setup cell.

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vnb987/ai-sw-application-courses/blob/main/week14-llm-agentic-ai/project.ipynb)

## Try it yourself

Give the agent a third tool of your own design, or swap in a larger
open-source model and see if it gets more reliable at picking the right tool.
