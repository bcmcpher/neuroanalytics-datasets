# Coverage roadmap

This page tracks known gaps in the book — topics that belong here and are not yet written.
It exists so that contributors can see where the holes are without having to audit
80-odd pages, and so that the reasoning behind each gap is recorded rather than
rediscovered.

## How the gaps were identified

The book was compared against a full research-lifecycle model — a nine-stage pipeline
(propose, initialize, curate, analyze, checkpoint, QC, export, publish, disseminate)
running inside a continuous administrative track covering funding, ethics, deadlines and
credit.

The comparison produced one clear finding: **the book covers the middle of the lifecycle
well and both ends barely at all.**

```
Lifecycle:  Govern → Initialize → Curate → Analyze → Checkpoint → QC → Export → Publish → Disseminate
Coverage:   ░░░░░░   ████████     ██████   ███████   ░░░░░░░░░░   ███  ░░░░░░   ░░░░░░░   ░░░░░░░░░░
            └─ thin ─┘                                            └────────── thin ──────────┘
            └──────────── administrative track: thin throughout ────────────┘
```

The [Start Here pathway](../pathway/overview.md) reflects the same shape: it begins at
"find data" and ends at "share your work", which skips what must be settled *before* data
access and stops short of what turns an analysis into a citable research product.

Documentation of tools is genuinely strong. Documentation of **process** is where the gaps
are.

## Priority 1 — Provenance and data versioning

The largest single hole, now partly filled.

| Topic | Status |
|---|---|
| [DataLad](../tools/data_management/datalad.md) | **Written** |
| YODA project layout | Covered inside the DataLad page |
| git-annex / large-file versioning | Covered inside the DataLad page |

Before this, DataLad appeared in four pages purely as a name in a list, despite being the
mechanism most of the reproducibility advice elsewhere in the book depends on.

## Priority 2 — Before you touch data

Nothing in the book covered this stage. A new scholar's first real blocker is usually data
access, and the book documented *which* datasets exist without ever describing how to get
into one.

| Topic | Status |
|---|---|
| [Ethics and data access](../governance/ethics-and-data-access.md) | Stub — highest value here |
| [Data management plans](../governance/data-management-plans.md) | Stub |
| [Pre-registration](../governance/pre-registration.md) | Stub |

## Priority 3 — Turning an analysis into a research product

The book stops at "share your work". The steps that make work citable and reusable are
absent.

| Topic | Status |
|---|---|
| [Releasing data and code](../publishing/data-and-code-release.md) | Stub — OSF, Zenodo, DOIs |
| [Reporting guidelines](../publishing/reporting-guidelines.md) | Stub — COBIDAS, TRIPOD |
| [Executable articles](../publishing/executable-articles.md) | Stub — NeuroLibre |

## Priority 4 — Curation depth

BIDS is explained as a standard, but not as a task you have to perform.

| Topic | Status |
|---|---|
| [Getting data into BIDS](../tools/data_management/raw-to-bids.md) | Stub — dcm2niix, HeuDiConv, validator |
| [Neurobagel and semantic annotation](../tools/data_management/neurobagel.md) | Stub — SNOMED, harmonization |

Cross-cohort pooling is a premise of several CNS projects, and variable harmonization is
the unglamorous step it depends on.

## Priority 5 — Administration and credit

| Topic | Status |
|---|---|
| [Credit and contributions](../governance/credit-and-contributions.md) | Stub — ORCID, CRediT |
| [Research administration](../governance/research-administration.md) | Stub — decision logs, obligations |

## Priority 6 — AI in the research workflow

The existing [AI models](../ai_models/llm-overview.md) section covers how large language
models work. It does not cover working *with* them, which is now part of most people's
daily practice and has unresolved implications for provenance.

| Topic | Status |
|---|---|
| [AI assistants in the research workflow](../ai_models/ai-assisted-research.md) | Stub |
| [Agent-callable methods](../ai_models/agent-callable-methods.md) | Stub — MCP, Paper2Agent |

## Priority 7 — A quality framework

| Topic | Status |
|---|---|
| [STAMPED principles](../governance/stamped.md) | Stub |

The book already argues for most of STAMPED without naming it — containers for
portability, provenance for tracking, BIDS for modularity. Naming the framework would let
those arguments reinforce each other instead of appearing as unrelated advice.

## Also outstanding

- **Testimonial sections are empty.** Every scholar page has a `Tools & Resources I Used`
  section awaiting its author. See the [scholar page template](bio-template.md). This is
  the highest-value outstanding item in the whole book and cannot be written by anyone
  other than the scholar concerned.
- **[Gourab K Sar's page](../cohort2/gourab_k_sar.md)** is not linked from any topic hub —
  his project needs a few more sentences before it can be categorized.
- **[Johanna Bayer's page](../cohort2/johannaBayer.md)** has no Project section; hers is
  currently embedded in the Background paragraph.
- **Extending the pathway.** [Start Here](../pathway/overview.md) has six steps. Once the
  governance and publishing pages exist, it should gain a step at each end.

## Contributing

Every stub above states what it needs. Pick one, write it, open a PR — and if you have
actually done the thing, write from that experience rather than from the documentation.
The first-hand version is worth considerably more.
