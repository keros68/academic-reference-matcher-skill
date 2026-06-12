# Source Routing

Use this to choose where to search. The goal is better evidence fit, not more sources for their own sake.

## Default Routing

| Claim Need | First Routes | Secondary Routes |
|---|---|---|
| DOI/title verification | DOI.org, Crossref, publisher page | OpenAlex, Semantic Scholar |
| Biomedical result | PubMed, Europe PMC, publisher page | OpenAlex, Crossref |
| Clinical guidance | official guideline body, PubMed | publisher page, government source |
| Computer science / AI | arXiv, Semantic Scholar, ACM/IEEE pages | OpenAlex, Crossref |
| Dataset / benchmark | dataset repository, dataset paper, official docs | OpenAlex, Semantic Scholar |
| Standards / regulation | official standards body or regulator | scholarly commentary only as background |
| Review background | OpenAlex, PubMed, Crossref, Semantic Scholar | publisher pages |
| Chinese policy, standard, or local dataset | official Chinese source, standard record, repository | scholarly index as background |

## Source Diversity

For Standard+ tasks, try at least two independent scholarly routes when possible. "Independent" means not just two pages copying the same metadata. Examples:

- Crossref record plus publisher abstract.
- PubMed record plus journal page.
- arXiv record plus conference/publisher version.
- OpenAlex discovery plus DOI/publisher verification.

## Freshness And Classics

- For emerging topics, include a recent-route query using the last 3-5 years.
- For foundational background, include a classic-route query using seminal authors, reviews, or high-citation discovery.
- Do not prefer recent papers automatically when the claim is historical or definitional.

## Version Handling

- Prefer the peer-reviewed version over a preprint when both exist and the claim depends on final results.
- A preprint is acceptable for fast-moving fields, but label it as a preprint when relevant.
- If the title, author list, or year differs across records, note possible version mismatch.

## When To Stop Expanding

Stop expanding when new searches return only duplicates, topic-neighbor papers, or lower-quality support. For Audit work, record the stopping reason in the search audit.
