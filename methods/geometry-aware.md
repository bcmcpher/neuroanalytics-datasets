# Geometry-Aware Methods

Functional connectomes are symmetric positive definite matrices, which means they live on
a curved Riemannian manifold rather than in flat Euclidean space. Most standard
statistical tools assume flatness, so applying them directly produces distorted distances
— the frequently used analogy is measuring the distance between two cities with a
straight ruler while ignoring the curvature of the Earth.

Geometry-aware methods take that curvature into account. **Tangent space analysis** is the
most common approach: pick a reference point on the manifold, use the Riemannian
logarithmic map to project nearby connectomes into the flat tangent space at that point,
and then apply ordinary linear methods — regression, PCA, distance metrics — to the
projections.

Two choices dominate whether this works in practice: **which reference point** you project
around, and **how much regularization** you apply to keep near-singular matrices away from
the boundary of the manifold. Both involve real trade-offs, including a data-leakage risk
in the reference choice.

## CNS Projects

- [Davor Curic](../cohort1/davor_curic.md) — applying tangent space analysis to track
  Alzheimer's disease progression through the movement of functional connectomes over
  time. **His page carries the most detailed technical writeup in this book**, covering
  the choice of reference and the bias-variance trade-off in regularization — start there
  rather than here

## Getting started

- [Davor Curic's technical description](../cohort1/davor_curic.md) — the substantive
  treatment
- [fMRI](../modalities/fmri.md) — where the connectomes come from
- [Alzheimer's Disease](../research_topics/alzheimers.md) — the topic hub
