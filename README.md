# llm-translator — Hybrid Diffusion-LLM + Autoregressive Translation

A research prototype for **English → Bengali machine translation** that combines a
**diffusion-based semantic planner** with an **autoregressive decoder**, aimed at
improving coherence and grammatical structure for a low-resource language pair.

## Problem

Standard sequence-to-sequence translation models tend to lose long-range structure
in longer sentences, and purely autoregressive decoders can drift semantically even
when the output reads fluently. This is especially visible for low-resource
languages like Bengali, where parallel training data is limited.

## Approach

1. **Diffusion planner** — generates a coarse, global semantic plan of the target
   sentence before any tokens are decoded, capturing long-range dependencies and
   sentence-level structure up front.
2. **Autoregressive decoder** — conditions on the plan to produce the final,
   fluent, token-level translation, handling local grammar and idiom.
3. **IndicNLP integration** — tokenization and preprocessing for English → Bengali
   adapted to the IndicNLP pipeline to handle Bengali morphology.

## Highlights

- Two-stage architecture: global planning followed by local refinement.
- Evaluated against autoregressive-only and diffusion-only baselines using
  **BLEU** and **chrF++**.
- Focus on semantic fidelity in longer, structurally complex sentences.

## Status

Proof-of-concept implemented as a Jupyter notebook (`MT/diffusion_LLMs.ipynb`).
Not production-ready — intended as a demonstration of the hybrid planning +
decoding idea for low-resource NMT.

## Tech Stack

Python, PyTorch, HuggingFace Transformers, IndicNLP

## Repo Structure

```
diffu-nmt/
├── MT/
│   ├── diffusion_LLMs.ipynb   # main notebook: planner + decoder pipeline
│   └── train_data1.json       # training data
└── README.md
```
