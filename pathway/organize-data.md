# 3. Organize your data

This is the step people skip, and it is the one that costs the most to skip.

Nearly every preprocessing pipeline worth using — [fMRIPrep](../tools/brain_imaging/fmriprep.md),
[QSIPrep](../tools/brain_imaging/qsiprep.md), [MRIQC](../tools/brain_imaging/mriqc.md) —
takes **BIDS** as its input format. If your data is in BIDS, those tools run with almost
no configuration. If it is not, you will either write conversion glue for each one or
give up on them.

## BIDS

- **[The Brain Imaging Data Structure](../tools/data_management/bids.md)** — what the
  specification is, why it makes data FAIR, and the surrounding tool ecosystem

BIDS is a filesystem convention, not a file format: a directory layout, consistent naming,
and JSON sidecars carrying acquisition metadata. Extensions cover EEG, MEG, and PET, so
the same conventions apply beyond MRI.

Practical advice from people who have done it: **convert one subject by hand before you
automate anything.** The validator is strict and its errors assume you already know the
specification. An hour spent understanding the layout on a single subject saves days of
fighting a conversion script.

## Managing a whole dataset

One subject is a conversion problem; a hundred is a bookkeeping problem — which subjects
have been processed, with which pipeline version, and which failed.

- **[Nipoppy](../tools/brain_imaging/nipoppy.md)** — a framework for organizing and
  tracking pipeline runs across a full dataset, rather than invoking tools per subject

## Keeping track of the rest

- **[Project management](../tools/project-management.md)** — organizing the project around
  the data
- **[Zettelkasten](../tools/zettelkasten.md)** — a note-taking method for keeping research
  notes navigable over a multi-year project

**Next:** [Preprocess](preprocess.md).
