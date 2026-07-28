# Deep Learning

Deep learning is the most widely shared method in the program — six scholars use it, on
problems ranging from connectome classification to spectrogram regression. This page is
the entry point; the more specific approaches have their own pages under Research
Methods.

Neuroimaging poses a particular difficulty for these models: sample sizes are small by
machine learning standards (hundreds to thousands of subjects, not millions), the data
are high-dimensional, and clinical labels are often imbalanced. Most of the strategies
below are responses to that constraint — reusing representations learned elsewhere, or
choosing an architecture that respects the structure of the data instead of flattening it.

## CNS Projects

- [Josh Neudorf](cohort1/josh_neudorf.md) — graph neural networks on structural and
  functional connectomes
- [Hao-Ting Wang](cohort1/hao-ting_wang.md) — transfer learning from pooled datasets
  into a smaller clinical cohort
- [Tom George](cohort2/tom_george.md) — self-supervised pretraining of a
  neuro-foundation model
- [Mohamed Abdelhack](cohort1/mohamed_abdelhack.md) — modelling visual inference and
  how perturbations emulate psychiatric conditions
- [Vibujithan Vigneshwaran](cohort1/vibujithan_vigneshwaran.md) — causal deep learning
  for neuroimaging, with a focus on interpretability and generalization
- [Lindsay Munroe](cohort1/lindsay_munroe.md) — explainable AI for predicting
  neurodegenerative disease progression

## Specific approaches

- [Graph neural networks](methods/graph-neural-networks.md) — when the data is a network
- [Foundation models and transformers](methods/foundation-models.md) — pretrain broadly,
  fine-tune narrowly
- [Transfer learning](methods/transfer-learning.md) — borrowing representations when your
  clinical sample is small
- [Normative modelling](methods/normative-modelling.md) — a statistical alternative worth
  knowing about before reaching for a network
- [Geometry-aware methods](methods/geometry-aware.md) — respecting the curved space that
  connectomes actually live in

## Software and Tools

- [PyTorch Geometric](tools/brain_imaging/pyg-graph-nets.md) — graph neural networks,
  with a worked neuroimaging example
- [BrainLM](tools/brain_imaging/brainlm.md) — a brain language model for fMRI time series
- [Code environments](tools/computer_science/code-environments.md) — reproducible
  dependency management, which matters more than usual once CUDA is involved
- [Containers](tools/computer_science/containers.md) — pinning an entire software stack
- [Compute Canada / DRAC](tools/computer_science/compute-canada.md) and
  [HPC jobs](tools/computer_science/hpc-jobs.md) — where the GPUs are
- [Working with imbalanced data](discussions/imbalanced-data.md) — a practical
  discussion of the class-imbalance problem common to clinical prediction
