# 5. Analyze

This is the step the book cannot sequence for you — the right method depends entirely on
the question. What it can do is show you what scholars in this program chose, and why.

## Methods in use here

- **[Deep learning](../deep-learning.md)** — the entry point, and the most widely shared
  method in the program
- **[Graph neural networks](../methods/graph-neural-networks.md)** — when your data is a
  network and flattening it into a vector throws away the structure
- **[Foundation models and transformers](../methods/foundation-models.md)** — pretrain
  broadly on open data, fine-tune on your task
- **[Transfer learning](../methods/transfer-learning.md)** — the practical answer to a
  clinical cohort of a few hundred subjects
- **[Normative modelling](../methods/normative-modelling.md)** — per-subject deviation
  from a healthy reference, instead of a group average
- **[Geometry-aware methods](../methods/geometry-aware.md)** — respecting the curved
  space connectomes actually live in

## Start from someone else's problem

Often faster than starting from the method: find the scholar whose question resembles
yours and read what they did.

Browse by **[research topic](../research_topics/alzheimers.md)** —
[Alzheimer's](../research_topics/alzheimers.md),
[dementia](../research_topics/dementia.md),
[aging](../research_topics/aging.md),
[Parkinson's](../research_topics/parkinsons.md),
[depression](../research_topics/depression.md),
[seizures](../research_topics/seizures.md) — or by
**[modality](../modalities/fmri.md)**. Each hub lists the scholars working on it with a
line on their specific angle.

## Two things that will come up

- **[Working with imbalanced data](../discussions/imbalanced-data.md)** — clinical outcome
  prediction almost always has far more negatives than positives, and accuracy is a
  misleading metric when it does
- **[Programming obscurities](../discussions/coding-obscurities.md)** — why the same
  function gives different answers in MATLAB and Python, and what to do about it. Written
  because it cost someone here real time

## Tools

[PyTorch Geometric](../tools/brain_imaging/pyg-graph-nets.md),
[BrainLM](../tools/brain_imaging/brainlm.md),
[Brian](../tools/brain_imaging/brian.md) for spiking network simulation, and the
[large language model](../ai_models/llm-overview.md) notes.

**Next:** [Share your work](share-your-work.md).
