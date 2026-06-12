# Paywall-Aware Access

Use this when a relevant paper is paywalled or only partial information is visible. The goal is better evidence handling, not paywall circumvention.

## Allowed Uses Of Paywalled Metadata

Metadata can be used for:

- discovering candidate papers;
- checking bibliographic facts such as title, authors, year, venue, DOI, publication status, and version;
- deciding whether to search for an open version, preprint, author manuscript, repository copy, or user-provided PDF;
- explaining why a paper is promising but not yet verified.

Metadata alone is usually not enough to support:

- empirical results;
- causal mechanisms;
- comparative claims;
- clinical, legal, or policy recommendations;
- detailed method or dataset claims;
- claims about effect size, direction, or statistical significance.

## Evidence Tiers

| Tier | Visible evidence | Allowed confidence |
|---|---|---|
| Discovery-only | title, keywords, indexing metadata, citation graph | Low or candidate only |
| Abstract-supported | abstract directly addresses the claim | Low to Medium |
| Snippet-supported | official publisher or database snippet directly addresses the claim | Low to Medium, note source |
| Fulltext-supported | full text, user PDF, accepted manuscript, official guideline, dataset record | Medium to High |
| Bibliographic-only | metadata for authors/year/venue/DOI/publication status | High only for bibliographic claims |

## Legal Access Routes

Prefer these routes before giving up:

- OpenAlex OA URL, Unpaywall, DOAJ, CORE, Europe PMC, PubMed Central, arXiv, bioRxiv, medRxiv, SSRN, institutional repositories, author pages.
- Publisher abstract, Crossref metadata, PubMed record, Semantic Scholar record, dataset repository, standards body page.
- User-provided PDFs, Zotero/Mendeley exports, BibTeX/RIS files, local paper libraries, or institutionally accessed pages supplied by the user.

Do not instruct the agent to bypass paywalls, defeat CAPTCHA, scrape behind login walls, reuse unauthorized cookies, or fetch from unauthorized sources.

## Reporting Pattern

```text
Candidate but not verified:
- Paper: ...
  Visible evidence: title/keywords/abstract/snippet/metadata
  Why it may be relevant: ...
  Limit: full text unavailable / abstract unavailable / only metadata visible
  Confidence: Low or candidate-only
  Next legal route: OA version / preprint / user PDF / library access / author manuscript
```
