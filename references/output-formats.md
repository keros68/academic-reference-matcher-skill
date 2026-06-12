# Output Formats

Follow the user's requested style. If no style is requested, use author-year inline citations and a compact reference list.

## Multi-Claim Table

| Claim | Mode | Best reference | Support | Evidence basis | Confidence | Notes |
|---|---|---|---|---|---|---|
| Short claim text | Add/Verify/Replace | Author et al., year, title, DOI/URL | One-sentence support rationale | Abstract/full text/metadata/snippet/PDF | High/Medium/Low | Access limits or caveats |

## Reference Fields

Capture these fields when available:

- Authors
- Year
- Title
- Venue
- DOI
- Stable URL
- PMID, arXiv ID, ISBN, standard number, or dataset accession when relevant

## Style Notes

- APA: author-year inline citations; reference list with DOI URL when available.
- GB/T 7714: numeric or author-year form based on user request; preserve Chinese punctuation if the surrounding text is Chinese.
- Vancouver: numbered citations in order of appearance.
- IEEE: bracketed numbered citations in order of appearance.
- BibTeX/RIS: output machine-readable entries only when requested, and avoid placeholder fields.

## Unverified Claims

Use this section when no reliable match is found:

```text
Could not verify:
- Claim: ...
  Checked: source and query summary
  Best candidates rejected: title/year/why rejected
  Reason: no direct scholarly support found / access unavailable / candidates only weakly related
  Next step: ask user for bibliography/PDF/corpus or revise the claim
```

## Verification Summary

For larger tasks, end with:

```text
Checked sources: ...
Queries used: ...
Accepted references: N
Weak or partial matches: N
Unverified claims: N
Access limits: ...
```
