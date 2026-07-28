# Getting Data into BIDS

[BIDS](bids.md) explains what the standard *is*. This page is about the step before that:
turning what actually came off the scanner — a directory of DICOMs with inscrutable series
descriptions — into a valid BIDS dataset.

This conversion is the most common place a project stalls, and it is almost never
mentioned in methods sections. The tools are mature, but each requires you to write a
mapping from your scanner's naming conventions to BIDS entities, and that mapping is
specific to your site and protocol.

:::{note} This page is a stub
Needs: `dcm2niix` for the DICOM-to-NIfTI step, `HeuDiConv` and `BIDScoin` for the
heuristic mapping, running `bids-validator` and interpreting its errors, and what to do
about the metadata fields your scanner did not record.

If you have done this on a CNS project, you are the right person to write it — open a PR.
:::

## Related

- [BIDS](bids.md) — the standard itself
- [Organize your data](../../pathway/organize-data.md) — the pathway step
- [Nipoppy](../brain_imaging/nipoppy.md) — can drive conversion across a whole dataset
- [DataLad](datalad.md) — convert inside a versioned dataset and the conversion itself is recorded
