# Search Sources

Use the agent's available tools first. These notes help choose sources and queries; they do not require any specific API.

## Default Source Order

1. Local or user-provided library: PDFs, BibTeX, RIS, EndNote XML, Zotero/Mendeley export, DOI list, previous manuscript references.
2. Open metadata: OpenAlex, Crossref, arXiv, PubMed, Europe PMC, Semantic Scholar.
3. Publisher and society pages: Nature, Science, Elsevier, Springer, Wiley, IEEE, ACM, Oxford, Cambridge, Taylor & Francis, MDPI, Frontiers, PLOS, BioMed Central.
4. Official sources: standards bodies, government agencies, clinical guidelines, protocol registries, dataset repositories.
5. General web search: use only to discover stable scholarly records or official reports.

## Query Patterns

For one claim, try 2-4 query shapes:

- Exact mechanism or result: `"term A" "term B" "effect/result"`
- Entity plus method: `"material/disease/model" "method/assay" review`
- DOI/title search when checking an existing citation.
- Author-year search when the user gives partial citation text.
- Domain-limited search for official records, such as `site:pubmed.ncbi.nlm.nih.gov`, `site:doi.org`, `site:arxiv.org`, or a publisher domain.

## Source Fit

- Biomedical claims: PubMed, Europe PMC, clinical guidelines, trial registries.
- Computer science and AI: arXiv, ACM, IEEE, Semantic Scholar, conference proceedings.
- Physics/math: arXiv, ADS when available, publisher pages.
- Social science: Crossref, OpenAlex, SSRN when appropriate, journals and reports.
- Standards or regulation: official standards bodies or government pages first.

## Access Limits

If a full text is paywalled, use metadata, abstract, publisher snippets, PubMed records, accepted manuscript copies, or user-provided PDFs. State that the full text was not checked when it matters.
