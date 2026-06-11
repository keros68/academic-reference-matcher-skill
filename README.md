# Academic Reference Matcher Skill

A portable agent skill for finding, verifying, replacing, and formatting scholarly references for academic claims.

The skill is intentionally tool-agnostic: it expects the host agent to use whatever web, browser, academic search, citation, PDF, or local-library tools it already has. The skill supplies the workflow and quality bar:

- identify citation-worthy claims;
- search scholarly sources instead of general summaries;
- verify whether a candidate paper actually supports the claim;
- format results as inline citations, reference lists, BibTeX/RIS, or claim-reference tables;
- avoid invented citations and clearly mark unverified claims.

## Use

Install or copy this repository into any agent runtime that supports skills or agent instructions, then invoke:

```text
Use $academic-reference-matcher to find and verify scholarly references for this paragraph.
```

For runtimes without a formal skill loader, point the agent at `SKILL.md`.

## Contents

- `SKILL.md` - main skill instructions and trigger description
- `references/search-sources.md` - source selection and query patterns
- `references/verification-rubric.md` - relevance scoring rubric
- `references/output-formats.md` - output contracts and citation style notes
- `agents/openai.yaml` - optional UI metadata for compatible runtimes

## License

MIT
