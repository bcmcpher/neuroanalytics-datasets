# Foundation Models and Transformers

A foundation model is pretrained on a large, broad corpus with a self-supervised
objective — no labels required — and then fine-tuned on a specific downstream task with
far less data than training from scratch would need. Transformers are the architecture
that made this practical, because attention scales well and imposes few assumptions about
the structure of the input.

For neuroscience the attraction is obvious and the obstacle is equally obvious. Open
neural data is plentiful in aggregate but fragmented across modalities, species,
recording setups, and preprocessing conventions. The central research question is
therefore not "can we train a transformer" but **which invariances in neural data are
actually useful learning signals** — cross-region, cross-trial, cross-modality.

## CNS Projects

- [Tom George](../cohort2/tom_george.md) — building a large-scale neuro-foundation model
  pretrained on diverse open datasets ([CONP](../data/portals/conp-data-portal.md),
  [OpenNeuro](../data/portals/open-neuro.md), the Allen Institute) with self-supervised
  objectives, then fine-tuned for [dementia](../research_topics/dementia.md) and
  neurodegenerative disease prediction. Builds on POYO, POYO+ and POSSM, and draws on
  vision techniques such as JEPA and DINO
- [Nooshin Bahador](../cohort1/nooshin_bahador.md) — fine-tuning a Vision Transformer
  with LoRA for spectrogram regression, a concrete example of adapting a large pretrained
  model with limited compute

## Getting started

- [BrainLM](../tools/brain_imaging/brainlm.md) — a brain language model for fMRI time
  series
- [LLM overview](../ai_models/llm-overview.md) and
  [semantic embedding](../ai_models/llm-semantic-embedding.md) — the same architectural
  ideas in the language setting
- [Transfer learning](transfer-learning.md) — the closely related strategy of reusing
  representations
- [Compute Canada / DRAC](../tools/computer_science/compute-canada.md) — pretraining is
  where the GPU allocation actually matters
