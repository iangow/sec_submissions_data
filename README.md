# SEC submissions reference data

Corrected SEC EDGAR submissions metadata for use with
[`sec-submissions`](https://github.com/iangow/sec_submissions). Large files are
attached to dated GitHub Releases, not stored in Git or distributed through PyPI.

## Download

- [Current corrected `filings.parquet`](https://github.com/iangow/sec_submissions_data/releases/latest/download/filings.parquet)
- [Current release and supporting files](https://github.com/iangow/sec_submissions_data/releases/latest)
- [September 30, 2026 snapshot](https://github.com/iangow/sec_submissions_data/releases/tag/2026-09-30)
- [Package documentation](https://iangow.github.io/sec_submissions/data/)

Downloads are public and do not require a GitHub account. The package downloads
the corrected filings and supporting timestamp evidence, checks every file's
SHA-256 checksum, and resumes interrupted transfers:

```sh
python -m pip install 'sec-submissions[audit] @ git+https://github.com/iangow/sec_submissions.git'
sec-submissions fetch-reference
```

Use `--version 2026-09-30` to pin a snapshot. Add `--companions` for companies,
addresses, tickers, former names, and submission-file metadata. See the package
documentation for `DATA_DIR`, `RAW_DATA_DIR`, `.env`, and the update workflow.

Each release includes `manifest.json`, which records the original SEC ZIP's
retrieval time and checksum, asset sizes and checksums, timestamp support counts,
and audit results. Fixed dated releases should not be modified; the current
download link follows the latest release.

## September 30, 2026

The original ZIP was retrieved on September 30, 2026 at 13:39 UTC. The corrected
table contains 27,272,863 filing rows. `acceptanceDateTime` is timezone-aware;
`timestamp_provenance` distinguishes 25,584,390 supported rows from 1,688,473
unresolved rows retained with an explicit Eastern-time fallback. Unresolved
rows are not verified timestamps.

A fresh simple random sample of 10,000 filing rows was frozen before independent
SGML lookups. There were 9,230 verifiable timestamps and no disagreements. The
remaining 770 rows had unavailable timestamp tags in 1994-2002 filings. The
one-sided 95% upper error bound is 0.0325% **among verifiable timestamps**, not
among all filings. Sample identifiers and outcomes are release assets.

SGML observations from this final audit are supplied as evidence for future
updates. They were collected after the candidate was frozen and were not used
to repair the audited candidate. Earlier diagnostic evidence is separate from
this independent audit.

## Attribution and license

The curated dataset and accompanying metadata are made available by Ian D. Gow
under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Cite the dataset
and the particular dated release when using it. Original SEC filings and source
materials retain their existing rights; this license covers the curated output,
not the underlying filing documents.
