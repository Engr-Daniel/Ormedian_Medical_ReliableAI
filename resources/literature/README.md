# Literature resources

Use [references.bib](references.bib) as the shared bibliography and [literature-map.csv](literature-map.csv) to track questions, methods, evidence, and reading progress. Both begin without paper entries; add only verified sources during the literature unit.

Use one stable citation key per paper, matching its BibTeX key. Verify authors, title, year, venue, and DOI or canonical URL against the publisher or original source. Use ISO dates (`YYYY-MM-DD`) for date fields. Record one paper per CSV row; quote cells containing commas or newlines.

| Fields | Meaning |
| --- | --- |
| `citation_key`, `title`, `authors`, `year`, `venue`, `doi`, `url` | Bibliographic identity and retrievable source |
| `date_added`, `reading_status` | Tracking date and progress: queued, skimmed, read, or critiqued |
| `research_question`, `main_claim`, `method` | The question and what the authors propose |
| `dataset`, `evaluation`, `key_evidence` | Data, evaluation setup, and evidence supporting the claim |
| `limitations`, `open_questions`, `relevance` | Your critique and connection to the program |
| `code_url`, `notes_path` | Public implementation if available and path to your reading note relative to the repository root |

Leave unverified or unavailable information blank and explain uncertainty in the reading note. Do not invent dataset details, numerical findings, or citations. Keep detailed reasoning in [research-notes/](../../research-notes/README.md) and link it through `notes_path`.

Zotero is an optional personal reference manager; collaborators must be able to use these plain-text files without it. Store research-paper PDFs outside the repository and never commit them. Bibliographic metadata and source links belong here.
