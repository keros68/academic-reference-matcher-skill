# Example Requests

These examples show how to invoke the skill without baking in fake citations.

## Add References To An English Paragraph

```text
Use $academic-reference-matcher in add mode. Find 2-4 scholarly references for the claims in this paragraph, use APA style, and include a claim-reference table with confidence labels:

[paste paragraph]
```

Expected behavior:

- extract only claims that need citation;
- search scholarly records before general web results;
- insert citations next to supported claims;
- include DOI or stable URL when available;
- mark claims as unverified if no direct support is found.

## Verify Existing Citations

```text
Use $academic-reference-matcher in verify mode. Check whether each citation in this paragraph supports the claim it is attached to. Keep the output as a table.

[paste paragraph with citations]
```

Expected behavior:

- check title, abstract, metadata, and available full text;
- score each citation using the verification rubric;
- keep correct citations, flag weak ones, and suggest replacements only when better evidence is found.

## Chinese GB/T 7714 Reference Matching

```text
使用 $academic-reference-matcher。请为下面这段中文论文引言找参考文献，优先使用近五年文献，输出 GB/T 7714 格式，并说明每条文献支持哪一句话。

[粘贴中文段落]
```

Expected behavior:

- preserve Chinese claim meaning;
- search both Chinese and English keywords;
- use GB/T 7714 unless the user asks for another style;
- explain weak or unverified matches in Chinese.

## Deep Search With Segment IDs

```text
Use $academic-reference-matcher in deep mode. Split this introduction into stable segment IDs, plan separate query families for each citation-worthy claim, search at least two scholarly routes where possible, and include a compact search audit.

[paste long introduction or subsection]
```

Expected behavior:

- assign `S001`, `S002`, ... to citable claims;
- label claim types before searching;
- vary query families instead of reusing one broad query;
- route sources by field and evidence need;
- report accepted, weak, rejected, and unverified candidates.

## Audit-Oriented Search

```text
Use $academic-reference-matcher in audit mode. I am preparing a systematic review background section. Create a reproducible search log, explain source limits, and do not claim exhaustive coverage unless the search strategy is bounded.

[paste topic, inclusion scope, or manuscript section]
```

Expected behavior:

- state scope, date range, databases/routes, and search limits;
- produce a claim-reference table with evidence basis;
- include rejected candidates and stopping reasons;
- distinguish literature discovery from citation support.

## No Reliable Match

```text
Use $academic-reference-matcher. If no paper directly supports the claim, do not invent one. Show what you checked and why candidates were rejected.

[paste claim]
```

Expected behavior:

```text
Could not verify:
- Claim: ...
  Checked: ...
  Best candidates rejected: ...
  Reason: ...
  Next step: ...
```
