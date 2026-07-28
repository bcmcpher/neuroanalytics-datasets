# Start Here: a research pathway

The rest of this book is organized as reference material — datasets in one place, tools
in another, methods in a third. That works well once you know what you are looking for.
It works badly on your first week.

This section is the other view: the same documents, arranged in the order you will
actually need them. Each step is short and mostly links. The depth lives in the reference
pages; this is just the thread that runs through them.

## The path

1. **[Find data](find-data.md)** — which open datasets exist, and how to get access
2. **[Get compute](get-compute.md)** — an account on a cluster, and somewhere to run code
3. **[Organize your data](organize-data.md)** — BIDS, and why converting early saves weeks
4. **[Preprocess](preprocess.md)** — QC and the standard pipelines
5. **[Analyze](analyze.md)** — the methods scholars in this program actually use
6. **[Share your work](share-your-work.md)** — git, environments, containers

## A word on order

The sequence matters more than it looks. The two most common ways a project stalls in
this field are both ordering problems:

- **Preprocessing before organizing.** Almost every pipeline worth using expects
  [BIDS](../tools/data_management/bids.md) as input. Converting first is a day; retrofitting
  it after you have written analysis scripts against a bespoke layout is a fortnight.
- **Requesting data before requesting compute.** Access applications and cluster
  allocations both take real calendar time and are independent of each other. Start both
  early, in parallel.

## You do not have to start at step 1

If you already have data and a cluster account, skip to
[organize your data](organize-data.md). If you are only here to find out which method
other scholars used for a problem like yours, go straight to
[analyze](analyze.md) — or browse the [research topics](../research_topics/alzheimers.md)
and find the scholar working closest to your question.
