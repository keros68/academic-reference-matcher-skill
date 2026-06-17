# Academic Reference Matcher

Academic Reference Matcher is a Codex skill for finding, verifying, replacing, and formatting scholarly references for academic writing.

It is designed for claims, paragraphs, manuscripts, literature reviews, rebuttals, grant text, and citation lists. The core workflow is:

```text
academic text
-> claim extraction
-> targeted scholarly search
-> support verification
-> citation formatting and audit notes
```

## Install

Clone this repository into your Codex skills directory using the skill name from `SKILL.md`.

Windows PowerShell:

```powershell
git clone https://github.com/keros68/academic-reference-matcher-skill.git "$env:USERPROFILE\.codex\skills\academic-reference-matcher"
```

macOS/Linux:

```bash
git clone https://github.com/keros68/academic-reference-matcher-skill.git ~/.codex/skills/academic-reference-matcher
```

Then start a new Codex thread and call:

```text
Use $academic-reference-matcher to find and verify scholarly references for this paragraph.
```

## What It Produces

- Citation-worthy claim extraction.
- Candidate scholarly references for each claim.
- Verification of whether a reference actually supports the claim.
- Confidence labels and support rationales.
- Tables that separate `candidate found` from `claim supported`.
- Copy-ready reference lists in styles such as APA, GB/T 7714, Vancouver, IEEE, BibTeX, RIS, or DOI-linked formats when metadata is available.
- Search-audit notes for Standard, Deep, or Audit tasks.
- "Could not verify" sections for unsupported or weakly supported claims.

## Task Modes

- `Add` - find citations for uncited claims.
- `Verify` - check whether existing citations support attached claims.
- `Replace` - find stronger or more accurate sources.
- `Format` - convert known references into a requested citation style.
- `Extract` - identify citation-worthy claims without searching yet.

## Quality Bar

Academic Reference Matcher is strict about evidence:

- Never invent citations, DOIs, authors, journals, or years.
- Prefer primary literature, systematic reviews, standards, datasets, or official documentation.
- Treat title and keyword similarity as discovery, not proof.
- Lower confidence when only metadata or abstracts are available.
- Disclose paywalls, inaccessible PDFs, weak matches, and unverified claims.

## Repository Layout

- `SKILL.md` - Codex skill instructions.
- `agents/openai.yaml` - UI metadata for compatible runtimes.
- `references/query-planning.md` - claim-to-query planning.
- `references/search-sources.md` - source selection guidance.
- `references/source-routing.md` - domain-aware routing.
- `references/paywall-aware-access.md` - access-limit handling.
- `references/verification-rubric.md` - support-confidence rubric.
- `references/output-formats.md` - output contracts and citation-style notes.
- `references/search-audit.md` - compact audit guidance.
- `examples/example-requests.md` - sample requests.

## Limits

This skill provides workflow and quality control. It does not include a built-in search engine, paid database access, PDF downloader, or paywall bypass. Search quality depends on the host agent's tools, the user's provided corpus, and accessible scholarly records.

For systematic reviews, meta-analyses, high-stakes manuscript revisions, or final journal formatting, human review is still recommended.

## License

MIT. See [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md).
