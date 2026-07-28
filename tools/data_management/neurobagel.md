# Neurobagel and Semantic Annotation

BIDS standardizes *file layout*. It does not standardize what your phenotypic variables
mean. One dataset records `dx_group`, another `diagnosis`, a third `patient_status` — and
nothing tells a machine these are the same concept, or that "MCI" here matches "mild
cognitive impairment" there.

Semantic annotation closes that gap by mapping each variable onto a controlled vocabulary
such as SNOMED CT. **Neurobagel** is the Canadian-led implementation: annotate a dataset's
variables, publish the resulting graph, and datasets become searchable by participant
characteristics *across* institutions — without moving the underlying data.

This is directly relevant to anyone here pooling cohorts, which is a premise of several
CNS projects.

:::{note} This page is a stub
Needs: the Neurobagel annotation workflow, what SNOMED CT provides and where it falls
short for research variables, building a federated query node, and practical harmonization
advice when two cohorts measured the same construct with different instruments.

If you have done this on a CNS project, you are the right person to write it — open a PR.
:::

## Related

- [BIDS](bids.md)
- [Nipoppy](../brain_imaging/nipoppy.md) — already mentions Neurobagel
- [CONP](../../data/portals/conp-data-portal.md)
- [Semantic embedding for clinical metrics](../../ai_models/llm-semantic-embedding.md) — an LLM-based approach to a related problem
