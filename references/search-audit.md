# Search Audit

Use this for Standard+ tasks, and always for Deep or Audit tasks. Keep it compact unless the user asks for a full reproducibility log.

## Compact Audit

```text
Search depth: Quick/Standard/Deep/Audit
Scope: field, language, date range, source limits
Segment IDs: S001-S00N
Sources checked: OpenAlex, Crossref, PubMed, arXiv, publisher pages, user PDFs, etc.
Query families:
- S001: ...
- S002: ...
Accepted evidence: N high, N medium, N low
Rejected candidates: title/year/reason
Access limits: paywall, abstract-only, metadata-only, database unavailable
Stopping reason: direct support found / no better match after alternate route / user-specified limit
```

## Rejection Reasons

Use specific reasons:

- same topic but not the same claim;
- wrong population, material, method, model, geography, or time period;
- review/background only, not direct support;
- preprint superseded by published version;
- retracted, expression of concern, or outdated guideline;
- metadata-only and insufficient for the claim;
- inaccessible full text and abstract does not establish support.

## Audit Integrity

- Do not list sources that were not actually checked.
- Do not imply exhaustive coverage unless the corpus and query strategy were bounded.
- If the host agent's search tool hides exact query syntax, summarize the query intent and source route.
- If a tool failed, record the failure briefly instead of pretending it was searched.
