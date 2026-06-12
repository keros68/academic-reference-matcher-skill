# Search Sources

Use the agent's available tools first. These notes help choose sources and queries; they do not require any specific API.

## Default Source Order

1. Local or user-provided library: PDFs, BibTeX, RIS, EndNote XML, Zotero/Mendeley export, DOI list, previous manuscript references.
2. Open metadata: OpenAlex, Crossref, arXiv, PubMed, Europe PMC, Semantic Scholar.
3. Publisher and society pages: Nature, Science, Elsevier, Springer, Wiley, IEEE, ACM, Oxford, Cambridge, Taylor & Francis, MDPI, Frontiers, PLOS, BioMed Central.
4. Official sources: standards bodies, government agencies, clinical guidelines, protocol registries, dataset repositories.
5. General web search: use only to discover stable scholarly records or official reports.

Do not rely on unofficial Google Scholar scraping, CAPTCHA bypasses, or brittle search-result parsing. If Google Scholar-like results are available through the user's normal browsing context, use them only as discovery hints and verify against stable records such as DOI, PubMed, arXiv, publisher, or repository pages.

## Query Patterns

For one claim, try 2-4 query shapes:

- Exact mechanism or result: `"term A" "term B" "effect/result"`
- Entity plus method: `"material/disease/model" "method/assay" review`
- DOI/title search when checking an existing citation.
- Author-year search when the user gives partial citation text.
- Domain-limited search for official records, such as `site:pubmed.ncbi.nlm.nih.gov`, `site:doi.org`, `site:arxiv.org`, or a publisher domain.
- Chinese-English paired search when the source text is Chinese: search the original Chinese terms, translated English technical terms, and common abbreviations.

For Deep or Audit tasks, do not stop at the first plausible hit. Vary at least one of: synonym set, source database, field qualifier, year range, or study-type term.

## Source Fit

- Biomedical claims: PubMed, Europe PMC, clinical guidelines, trial registries.
- Computer science and AI: arXiv, ACM, IEEE, Semantic Scholar, conference proceedings.
- Physics/math: arXiv, ADS when available, publisher pages.
- Social science: Crossref, OpenAlex, SSRN when appropriate, journals and reports.
- Standards or regulation: official standards bodies or government pages first.

## Chinese Academic Text

- Preserve the user's Chinese terminology when extracting claims.
- Search both Chinese and English keywords for technical terms, diseases, materials, methods, and institutions.
- Prefer GB/T 7714 when the user asks for Chinese thesis, Chinese journal, or Chinese grant-style references and does not specify another style.
- Do not force Chinese summary claims into narrower English claims during translation; verify the original meaning.
- For China-specific policy, standards, geography, or datasets, prioritize official Chinese sources, standards records, and stable repository pages.

## Access Limits

If a full text is paywalled, use metadata, abstract, keywords, publisher snippets, PubMed records, accepted manuscript copies, or user-provided PDFs. State that the full text was not checked when it matters.

Paywalled records are still useful for discovery: titles, keywords, author lists, journal scope, DOI metadata, and citation graph context can identify candidate papers. They are not enough for strong support unless the claim is purely bibliographic.
