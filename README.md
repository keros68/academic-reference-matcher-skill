# Academic Reference Matcher Skill

A portable agent skill for finding, verifying, replacing, and formatting scholarly references for academic claims.

The skill is intentionally tool-agnostic: it expects the host agent to use whatever web, browser, academic search, citation, PDF, or local-library tools it already has. The skill supplies the workflow and quality bar:

- identify citation-worthy claims;
- search scholarly sources instead of general summaries;
- verify whether a candidate paper actually supports the claim;
- format results as inline citations, reference lists, BibTeX/RIS, or claim-reference tables;
- avoid invented citations and clearly mark unverified claims.

## 中文介绍

Academic Reference Matcher 是一个通用的智能体技能，用于为学术文本查找、验证、替换和格式化参考文献。它不绑定特定平台或搜索 API，而是让宿主智能体使用自身已有的联网、浏览器、学术检索、PDF 或本地文献库能力。

这个 skill 重点解决四件事：

- 识别段落中真正需要引用支撑的学术论断；
- 优先检索论文、DOI、预印本、官方指南、数据集等可靠来源；
- 判断候选文献是否真的支持原文 claim，而不是只匹配关键词；
- 按 APA、GB/T 7714、Vancouver、IEEE、BibTeX、RIS 等格式输出引用，并标明无法验证的内容。

## Use

Install or copy this repository into any agent runtime that supports skills or agent instructions, then invoke:

```text
Use $academic-reference-matcher to find and verify scholarly references for this paragraph.
```

For runtimes without a formal skill loader, point the agent at `SKILL.md`.

中文使用示例：

```text
使用 $academic-reference-matcher 为这段文字查找并验证学术参考文献。
```

## Contents

- `SKILL.md` - main skill instructions and trigger description
- `references/search-sources.md` - source selection and query patterns
- `references/verification-rubric.md` - relevance scoring rubric
- `references/output-formats.md` - output contracts and citation style notes
- `agents/openai.yaml` - optional UI metadata for compatible runtimes

## License

MIT
