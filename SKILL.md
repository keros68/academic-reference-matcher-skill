---
name: academic-reference-matcher
description: Use when finding, adding, verifying, replacing, or formatting scholarly references for academic claims, paragraphs, manuscripts, literature reviews, rebuttals, grant text, or citation lists; use when checking whether cited papers support a claim, identifying claims that need citations, or producing APA, GB/T, Vancouver, IEEE, BibTeX, RIS, or DOI-linked references.
---

# Academic Reference Matcher

## Overview

Find and verify scholarly references for user-provided academic text. Prefer the agent's built-in web, search, database, browser, citation, or library tools; this skill supplies the workflow and quality bar rather than a required external API.

## Core Rules

- Never invent citations, DOIs, author names, journal names, or publication years.
- Separate "candidate reference found" from "reference supports the claim".
- Use primary literature, systematic reviews, standards, datasets, or official documentation before blogs and secondary summaries.
- Preserve the user's requested citation style and language. If none is requested, default to author-year inline citations plus a compact reference list.
- If web/database access is unavailable, ask for a bibliography, search export, DOI list, PDF set, Zotero library, or pasted search results.

## Workflow

1. Scope the task.
   - Identify the field, date sensitivity, citation style, language, and whether the user wants new citations, verification of existing citations, or both.
   - For long documents, process by section and keep citation numbering stable.

2. Extract citation-worthy claims.
   - Mark empirical, causal, comparative, quantitative, methodological, historical, or definitional claims.
   - Do not cite generic transitions, obvious background, or the user's own stated contribution unless requested.

3. Search broadly, then narrowly.
   - Start with exact phrases and key technical terms from the claim.
   - Search title/abstract/DOI sources before general web search when available.
   - Load `references/search-sources.md` when choosing sources or building queries.

4. Verify relevance.
   - Read enough of the title, abstract, metadata, snippets, and available full text to judge support.
   - Score each candidate using `references/verification-rubric.md` when the task has multiple candidates or high accuracy requirements.
   - Prefer papers that directly support the claim over papers that merely share keywords.

5. Format and insert citations.
   - Use the user's requested style. Load `references/output-formats.md` for output contracts and style notes.
   - Keep citations adjacent to the claims they support.
   - Include uncertainty notes for weak matches instead of silently overstating confidence.

## Search Strategy

Use at least two independent scholarly sources for important claims when possible. Good default order:

1. User-provided bibliography, PDFs, Zotero/Mendeley export, or project library.
2. OpenAlex, Crossref, Semantic Scholar, PubMed/Europe PMC, arXiv, IEEE/ACM/ScienceDirect/Springer/Nature pages when accessible.
3. General web search only to locate publisher pages, DOI records, preprints, or official reports.

For each selected reference, capture enough provenance to let the user audit it: title, authors, year, venue, DOI or stable URL, and a one-sentence support rationale.

## Output

For small requests, answer in prose with inserted citations and a reference list.

For multi-claim matching, use this compact table:

| Claim | Best reference | Support | Confidence | Notes |
|---|---|---|---|---|

Use confidence labels:

- High: directly supports the claim with matching population, method, mechanism, or result.
- Medium: supports the broader point but differs in scope, method, or context.
- Low: related background only; do not present as strong support.

End with a "Could not verify" section for claims with no reliable match.

## Common Mistakes

- Do not treat high citation count as relevance.
- Do not cite a review for a specific experimental result unless the review clearly reports it and the user accepts secondary sources.
- Do not use a paper just because its abstract contains the same terms.
- Do not replace a user's citation unless the current reference is wrong, weak, retracted, inaccessible, or outside the requested scope.
- Do not hide missing access. Say what was checked and what could not be opened.
