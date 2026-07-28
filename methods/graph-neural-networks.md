# Graph Neural Networks

A connectome *is* a graph: brain regions are nodes, connectivity strengths are edges.
Standard deep learning architectures require flattening that graph into a vector, which
throws away the relational structure and forces the model to relearn it from data it
does not have enough of. Graph neural networks operate on the graph directly.

The practical payoff is parameter efficiency. Because a GNN shares weights across nodes
rather than learning a separate parameter per connectome entry, it needs far fewer
parameters to reach the same accuracy — which matters a great deal when your clinical
cohort has a few hundred subjects.

## Why it appears in this program

Both projects using GNNs are prediction problems on brain networks where interpretability
is as important as accuracy. Methods such as GNNExplainer can probe a trained model to
identify which specific edges or regions drove a prediction, which is what makes the
output clinically meaningful rather than just a score.

## CNS Projects

- [Josh Neudorf](../cohort1/josh_neudorf.md) — GNN deep learning to predict progression
  from mild cognitive impairment to dementia, integrating structural and functional
  connectivity in one model along with regional attributes (graph theory measures,
  neurotransmitter expression, cortical thickness) and individual-level covariates
- [Sima Abbasi Habashi](../cohort2/sima_abbasi.md) — graph learning as part of a
  multi-modal pipeline linking genetic variation to white matter hyperintensity burden

## Getting started

- [PyTorch Geometric](../tools/brain_imaging/pyg-graph-nets.md) — the most developed
  technical document in this book, with a worked neuroimaging example
- [Deep learning](../deep-learning.md) — general context
- [fMRI](../modalities/fmri.md) and [DWI](../modalities/dwi.md) — where the connectomes
  come from
