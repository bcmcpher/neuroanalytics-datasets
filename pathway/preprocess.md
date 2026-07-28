# 4. Preprocess

Preprocessing turns raw scanner output into something analyzable: motion corrected,
registered to a common space, denoised. The community has largely converged on a small
set of standardized pipelines, which is good news — it means this step is mostly about
running established tools carefully rather than building your own.

All of these expect [BIDS](../tools/data_management/bids.md) input. If you skipped
[step 3](organize-data.md), go back.

## Quality control first

- **[MRIQC](../tools/brain_imaging/mriqc.md)** — automated quality metrics and visual
  reports for structural and functional MRI

Run this **before** preprocessing, not after. It is far cheaper to exclude a subject at
this point than to discover a registration failure downstream and re-run everything. Most
pipeline failures trace back to a structural scan that QC would have flagged.

## The pipelines

- **[fMRIPrep](../tools/brain_imaging/fmriprep.md)** — the standard functional MRI
  pipeline; covers usage and how to read its output structure
- **[QSIPrep](../tools/brain_imaging/qsiprep.md)** — the diffusion equivalent
- **[giga_connectome](../tools/brain_imaging/gigaconnectome.md)** — extracts connectomes
  from fMRIPrep output, which is usually what you actually want for analysis

For electrophysiology the path is different:

- **[Brainstorm](../tools/brain_imaging/brainstorm.md)** — MEG/EEG analysis environment

## Running at scale

- **[Nipoppy](../tools/brain_imaging/nipoppy.md)** — tracking which subjects ran with
  which pipeline version
- **[HPC jobs](../tools/computer_science/hpc-jobs.md)** — these pipelines are
  hours-per-subject, so they belong on the cluster
- **[Containers](../tools/computer_science/containers.md)** — the pipelines are
  *distributed* as containers, and pinning the version is what makes a run reproducible

## What comes out

Know what your analysis needs before you run anything, because re-running is expensive.
See the [modality](../modalities/fmri.md) pages for what each pipeline produces and what
is typically done with it.

- **[DataLad](../tools/data_management/datalad.md)** — running pipelines through
  `datalad containers-run` records the command, its inputs, and the container version, so
  "which fMRIPrep produced this figure" stays answerable

**Next:** [Analyze](analyze.md).
