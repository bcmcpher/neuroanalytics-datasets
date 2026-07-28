# Transfer Learning

Clinical neuroimaging cohorts are small. A pre-symptomatic Alzheimer's study might have a
few hundred subjects, which is nowhere near enough to train a deep network from scratch
without overfitting. Transfer learning sidesteps this: pretrain a model on a large pooled
dataset, then fine-tune it on the small clinical sample, so that the representations are
learned where the data is abundant and only the task-specific mapping is learned where it
is scarce.

The interesting assumption underneath it is scientific rather than technical. Pooling
across conditions only helps if those conditions share underlying brain changes — which
is exactly the hypothesis that motivates studying neurodegenerative and psychiatric
conditions as a spectrum rather than in isolation.

## CNS Projects

- [Hao-Ting Wang](../cohort1/hao-ting_wang.md) — pooling multiple datasets to pretrain a
  model, then using transfer learning to predict diagnoses within the smaller
  [PREVENT-AD](../data/databases/prevent-ad.md) cohort. The premise is that Alzheimer's
  disease, schizophrenia and autism spectrum disorder show significant overlap in
  underlying brain changes, so they are better investigated together

## Getting started

- [Foundation models](foundation-models.md) — the same idea at much larger scale
- [Deep learning](../deep-learning.md) — general context
- [Working with imbalanced data](../discussions/imbalanced-data.md) — small clinical
  cohorts usually bring a class imbalance problem with them
