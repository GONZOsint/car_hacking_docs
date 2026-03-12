# Automotive Keyless Entry Security – Paper Repository

Curated list of academic and industry papers, **technical blog posts**, and **GitHub PoCs** on car keyless entry security: **RKE** (Remote Keyless Entry), **PKES** (Passive Keyless Entry and Start), attacks (KeeLoq, Hitag2, relay, RollJam, RollBack), and defenses (distance bounding, PUF, MFA, etc.). Papers are stored by year and indexed in CSV for search and filtering. The full index (including blogs and PoCs) is in **papers.csv**. **papers.csv** is the source of truth; the table below is a summary and may lag—use the CSV for filtering by topic or year.

## Contents

- [Repository structure](#repository-structure)
- [Papers (chronological)](#papers-chronological)
- [Downloading papers](#downloading-papers)
- [Papers not downloaded (link-only)](#papers-not-downloaded-link-only)
- [Disclaimer](#disclaimer)

## Repository structure

```
car_hacking_docs/
├── README.md           # This file: intro, table, usage
├── papers.csv          # Index: year, title, authors, url, local_path (source of truth)
└── papers/             # Downloaded PDFs (and some .md for web articles) by year
    ├── 2005/
    ├── 2007/
    └── ... 2025/
```
