# T1w / T2w Structural Magnetic Resonance Imaging

Structural MRI provides the anatomical reference nearly every other modality is
registered to, and supplies the morphometric measures — cortical thickness, subcortical
volume — that normative models are typically built on. T2w and FLAIR contrasts are what
make white matter lesions visible.

## Data

Essentially every dataset in this book includes structural MRI, since it is required to
process the other modalities:

- [PREVENT-AD](../data/databases/prevent-ad.md), [ADNI](../data/databases/adni.md),
  [UK Biobank](../data/databases/ukbb.md), [ABCD](../data/databases/abcd.md)

## Processing

1. Organize as [BIDS](../tools/data_management/bids.md)
2. Check quality with [MRIQC](../tools/brain_imaging/mriqc.md) — structural QC is worth
   doing carefully, because downstream registration failures usually trace back to it
3. Anatomical preprocessing is bundled into
   [fMRIPrep](../tools/brain_imaging/fmriprep.md) and
   [QSIPrep](../tools/brain_imaging/qsiprep.md) rather than run separately

## CNS Projects

- [Julia-Katharina Pfarr](../cohort1/julia-katharina_pfarr.md) — cortical thickness and
  subcortical volume as the measures underlying a lifespan normative model
- [Sima Abbasi Habashi](../cohort2/sima_abbasi.md) — T1-weighted and FLAIR imaging to
  quantify white matter hyperintensity burden
- [Diellor Basha](../cohort1/diellor_basha.md) — structural MRI alongside PET and CSF
  measures in preclinical Alzheimer's
- [Josh Neudorf](../cohort1/josh_neudorf.md) — cortical thickness as a region attribute
  in graph learning models
