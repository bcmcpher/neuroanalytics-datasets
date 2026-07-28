# 2. Get compute

Neuroimaging does not fit on a laptop. A single fMRIPrep run is hours of CPU and tens of
gigabytes; a deep learning model wants a GPU; and datasets like UK Biobank are large
enough that where the data lives determines where you compute.

Start the account process early — it is independent of data access, and both take time.

## The national cluster

- **[Digital Research Alliance of Canada (DRAC)](../tools/computer_science/compute-canada.md)**
  — formerly Compute Canada, and where most of this program's heavy computation happens.
  Covers account setup, connecting, tying your work to a sponsoring PI, and long-term
  storage. Read this one properly; the account and sponsorship steps have real lead time
- **[Running HPC jobs](../tools/computer_science/hpc-jobs.md)** — the scheduler, job
  scripts, and how to ask for resources without either wasting an allocation or having
  jobs killed
- **[Performant computing](../tools/computer_science/performant-computing.md)** — a short
  note on making things faster

## Interactive work

- **[Compute Canada JupyterHub](../tools/computer_science/cc-jupyter-hub.md)** — notebooks
  on cluster hardware, which is the fastest route from nothing to a running analysis

## Platform-hosted alternatives

Sometimes the data does not move and you compute where it lives:

- **[UK Biobank RAP](../data/portals/ukbb-rap.md)** — the required route for UKBB
- **[brainlife.io](../data/portals/brainlife.md)** — browser-based pipelines, no cluster
  account needed

## Before you scale up

Whatever you run on the cluster has to be reproducible there, which means sorting out
dependencies before you are debugging them over SSH at scale. See
[code environments](../tools/computer_science/code-environments.md) and
[containers](../tools/computer_science/containers.md) — covered properly in
[step 6](share-your-work.md), but worth a look now if you are about to submit a thousand
jobs.

**Next:** [Organize your data](organize-data.md).
