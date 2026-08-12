# Release Notes

## v1.2.0 — 12 August 2026

Regenerates all computation outputs with the corrected akkapros engine (v3.2.0) and clarifies the status of the three accent styles.

### Changes

- **Data regeneration (akkapros 3.2.0)** — `outputs/` (full-corpus and Erra and Išum) regenerated after a bug fix in the prosody engine (CR-111): the last-resort accentuation fallback now consistently targets the first syllable of the word. Aggregate counts and rates are unchanged (2,580 / 16.75% full-corpus bi; 4,989 / 32.38% mono; Erra 547 / 18.30%); the last-resort type distribution (C:V 18, ʔ:V 15) and a few second-decimal acoustic metrics were updated (e.g. ΔC 68.82 ms bi; mono ΔC 61.43 ms, VarcoC 49.74, rPVI-C 72.60, nPVI-V 27.08).
- **Research note** — Added `notes/distilled/Notes-N-Data-Update-and-Accent-Styles.md` documenting the regeneration, the last-resort rule, and the status of the three accent styles (LOB, AOB, SOB).
- **Style clarifications** — Corrected notes that attributed the SOB hierarchy to Huehnergard's standard description. The standard academic model is implemented as AOB (akkapros 3.2.0, CR-112); SOB is a speculative testing variant, not an attested academic style. README, bibliography, and the affected notes were updated accordingly.
- **README fixes** — Corrected the `notes/dist/` -> `notes/distilled/` path, updated the accent-style list and the notes table, and refreshed the citation version.
- **New output artifacts** — AOB-style artifacts (full-corpus and Erra and Išum, bi and mono) are now included in `outputs/` as pipeline outputs (akkapros 3.2.0, CR-112). The study itself uses only LOB. Script-format artifacts (GIR and XAR) are included for the three styles; they are by-products of the pipeline.

### Note

The article draft remains unpublished and is not part of this repository.

---

## v1.1.1 — 29 May 2026

Remove irrelevant xar files from computation data.

### Changes

- In `outputs` directory :
  - `erra-and-ishum.yaml`: set xar option to false
  - `full-corpus.yaml` set xar option to false
  - remove *xar* files in `full-corpus/` and `erra-and-ishum/`

---

## v1.1.0 — 24 May 2026

Adds distilled research notes — cleaned, public-ready versions of the complete research log and all 13 topical research notes.

### Changes

- Added `notes/distilled/` directory containing:
  - `research-notes-prep.md`: complete research log (notes 001–537), renamed and cleaned from the original `notes/research-notes.md`
  - `Notes-A-Foundations.md` through `Notes-M-Oral-Acquisition.md`: cleaned versions of all 13 topical research notes
- Fixed duplicate title line in research notes
- Removed all 'invalid note' and 'superseded' markers
- Removed all TODO/FIXME/XXX markers
- Content is appropriate for public release

---

## v1.0.1 — 15 May 2026

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20199708.svg)](https://doi.org/10.5281/zenodo.20199708)

Zenodo DOI integration. This release assigns a persistent identifier to the repository, enabling citation in academic publications.

### Changes

- Added Zenodo DOI badge to README
- Added GitHub release badge to README
- Added license badge to README
- Fixed git branch structure (master → main)
- Updated release notes format

---

## v1.0.0 — 15 May 2026

Initial release of the research notes and working files accompanying the computational reconstruction of Babylonian prosody.

### Purpose

This repository provides research materials, input data, and computational outputs for the study of Babylonian prosody. It accompanies the main [akkapros](https://github.com/samuelkabak/akkapros) toolkit (v3.0.1+), the open-source Python package for Akkadian prosody analysis.

The repository contains:

- **Research notes** (`notes/`): Public-facing notes covering foundations, corpus, academic model, metrics, hypotheses, algorithm, results, implementation, timing model, TTS, article content, and parameter justifications.
- **Outputs** (`outputs/`): Results of running the akkapros toolkit on sample texts, including full-corpus and Erra and Išum analyses, plus MBROLA preparation artifacts.
- **Data** (`data/`): Lexical analysis files and sample sources from the Electronic Babylonian Library.

### License

CC BY 4.0
