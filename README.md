# Academic Reference Matcher Skill

A portable agent skill for finding, verifying, replacing, and formatting scholarly references for academic claims.

The skill is intentionally tool-agnostic: it expects the host agent to use whatever web, browser, academic search, citation, PDF, or local-library tools it already has. The skill supplies the workflow and quality bar:

- identify citation-worthy claims;
- search scholarly sources instead of general summaries;
- verify whether a candidate paper actually supports the claim;
- format results as inline citations, reference lists, BibTeX/RIS, or claim-reference tables;
- avoid invented citations and clearly mark unverified claims.
- disclose weak matches, paywall limits, and search gaps.

## 中文介绍

Academic Reference Matcher 是一个通用的智能体技能，用于为学术文本查找、验证、替换和格式化参考文献。它不绑定特定平台或搜索 API，而是让宿主智能体使用自身已有的联网、浏览器、学术检索、PDF 或本地文献库能力。

这个 skill 重点解决五件事：

- 识别段落中真正需要引用支撑的学术论断；
- 优先检索论文、DOI、预印本、官方指南、数据集等可靠来源；
- 判断候选文献是否真的支持原文 claim，而不是只匹配关键词；
- 按 APA、GB/T 7714、Vancouver、IEEE、BibTeX、RIS 等格式输出引用，并标明无法验证的内容。
- 诚实说明弱匹配、付费墙、检索覆盖不足等限制。

## Task modes

- `add` - find citations for uncited claims.
- `verify` - check whether existing citations really support the attached claims.
- `replace` - find stronger or more accurate alternatives for weak or wrong citations.
- `format` - convert known references to APA, GB/T 7714, Vancouver, IEEE, BibTeX, RIS, or another requested style.
- `extract` - identify citation-worthy claims before searching.

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

## Examples

See `examples/example-requests.md` for prompt patterns covering:

- adding references to an English paragraph;
- checking whether existing citations support a claim;
- finding GB/T 7714 references for Chinese academic text;
- reporting no reliable match without inventing citations.

## Known limitations / 已知局限

- The skill does not include its own search engine or paid database access. It depends on the host agent's available web, browser, scholarly database, PDF, or local-library tools.
- It cannot guarantee exhaustive literature coverage unless the user provides a bounded corpus or a reproducible database search strategy.
- Paywalled full text, missing abstracts, incomplete metadata, and rate limits can reduce verification quality.
- It should not rely on unofficial Google Scholar scraping or CAPTCHA workarounds; use Scholar-like results only as discovery hints and verify against stable scholarly records.
- Citation formatting may still need journal-specific polishing for edge cases such as consortium authors, translated titles, preprint-to-journal version matching, or Chinese-English mixed bibliographies.

中文说明：

- 这个 skill 本身不自带搜索引擎，也不提供付费数据库权限，效果取决于宿主智能体能访问哪些工具和资料。
- 如果没有限定数据库、检索式或文献库，它不能承诺“穷尽所有相关文献”。
- 遇到付费墙、摘要缺失、元数据不完整或访问频率限制时，验证质量会下降。
- 不建议依赖非官方 Google Scholar 抓取或绕过验证码；应回到 DOI、PubMed、arXiv、出版社、机构库等稳定记录核验。
- 复杂期刊格式、团体作者、预印本与正式发表版本对应关系、中英文混排参考文献，可能仍需要人工终审。

## Contents

- `SKILL.md` - main skill instructions and trigger description
- `references/search-sources.md` - source selection and query patterns
- `references/verification-rubric.md` - relevance scoring rubric
- `references/output-formats.md` - output contracts and citation style notes
- `examples/example-requests.md` - practical request and output patterns
- `agents/openai.yaml` - optional UI metadata for compatible runtimes

## License

MIT
