# Release Notes

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
