# AI Assistants in the Research Workflow

The existing pages in this section describe how large language models work internally and
how to use them for [synthesis](llm-methods-of-synthesis.md) and
[literature work](notebooklm.md). This page is about something different: AI assistants
embedded in the analysis workflow itself — writing pipeline code, converting data,
navigating a cluster, drafting documentation.

The interesting questions here are not about capability but about **discipline**. If an
assistant wrote the preprocessing script, what is recorded about how it was produced? If a
model suggested an analytic choice, does that belong in the decision log? Reproducibility
practice was designed around human-authored code, and the answers are not yet settled.

:::{note} This page is a stub
Needs: practical patterns for using assistants on research code, what to record about
AI-assisted steps, the failure modes worth knowing about (plausible-looking but wrong
statistics, silently outdated API usage), and where a research group should draw its
lines.

If you have done this on a CNS project, you are the right person to write it — open a PR.
:::

## Related

- [LLM overview](llm-overview.md)
- [Agent-callable methods](agent-callable-methods.md)
- [Research administration](../governance/research-administration.md) — decision logging
- [Programming obscurities](../discussions/coding-obscurities.md)
