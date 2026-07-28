# Normative Modelling

Normative modelling establishes a reference distribution of a brain measure — cortical
thickness, subcortical volume, functional connectivity — across a healthy population,
while accounting for covariates such as age and sex. An individual patient is then scored
by how far they deviate from that reference.

The appeal is that it does not assume patients form a homogeneous group. Case-control
comparisons ask whether a patient group differs from controls *on average*, which
dissolves exactly the individual variation that matters clinically. Normative models give
a per-subject deviation instead, which is what you need when the same diagnosis produces
very different brain phenotypes across people.

Think of it as the neuroimaging analogue of a paediatric growth chart: the value of the
chart is not the average curve, it is being able to say where one child sits on it.

## Why it appears in this program

Both Parkinson's disease projects use it, for the same reason — neuropsychiatric symptoms
in PD vary enormously between individuals, and the clinically useful question is about a
particular patient rather than about the group.

## CNS Projects

- [Julia-Katharina Pfarr](../cohort1/julia-katharina_pfarr.md) — adapting the pre-estimated
  Rutherford et al. lifespan model (82 sites, N=58,836, ages 2–100) to new sites and
  testing it on PD patients, to predict neuropsychiatric symptoms from scans that are
  already part of routine care
- [Johanna Bayer](../cohort2/johannaBayer.md) — a founding researcher in the field, now
  developing federated and longitudinal normative models to characterise individual
  trajectories of brain change across the lifespan, and lead developer of the velocity
  centiles methodology

## Getting started

The PCNtoolkit ecosystem is the standard implementation, and Johanna is an active
contributor to it.

- [Structural MRI](../modalities/smri.md) — cortical thickness and subcortical volume are
  the usual inputs
- [Parkinson's Disease](../research_topics/parkinsons.md) — the topic hub
- [Aging and Cognitive Decline](../research_topics/aging.md) — separating normal lifespan
  variation from pathology is the same problem in a different guise
