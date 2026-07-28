# Agent-Callable Methods

If the goal is research that others can build on quickly, the natural next step past a
released dataset and re-executable article is a method someone else's assistant can simply
*call* — your analysis exposed as a tool, invocable on new data, with its parameters and
assumptions described in machine-readable form.

The **Model Context Protocol (MCP)**, mentioned briefly in the
[LLM overview](llm-overview.md), is the emerging standard for that interface.
**Paper2Agent** is the pattern of packaging a paper's methods as exactly this kind of
callable bundle.

This is speculative relative to the rest of the book, and included because it is where
reproducible-research tooling is visibly heading — a method that can be invoked is a much
lower barrier to reuse than a method that must be reimplemented from a description.

:::{note} This page is a stub
Needs: what an MCP server for a research method looks like in practice, how to describe
methods so they are safely callable on data they were not validated for, and worked
examples from CNS projects.

If you have done this on a CNS project, you are the right person to write it — open a PR.
:::

## Related

- [LLM overview](llm-overview.md) — introduces MCP
- [AI assistants in the research workflow](ai-assisted-research.md)
- [Executable articles](../publishing/executable-articles.md)
- [STAMPED principles](../governance/stamped.md) — Actionability
