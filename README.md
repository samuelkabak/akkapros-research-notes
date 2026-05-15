# Akkadian Prosody – Research Notes

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20199708.svg)](https://doi.org/10.5281/zenodo.20199708)
[![GitHub release](https://img.shields.io/github/v/release/samuelkabak/akkapros-research-notes)](https://github.com/samuelkabak/akkapros-research-notes/releases)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Research materials, working files, and reproducibility data for the computational reconstruction of Babylonian prosody. This repository accompanies the main [akkapros](https://github.com/samuelkabak/akkapros) toolkit.

*Note: This repository contains research notes, input data, and computational outputs only. The program code resides in the main toolkit repository.*

## 📁 Repository Structure

| Folder | Contents |
|--------|----------|
| `data/samples/` | ATF input files from the Electronic Babylonian Library (eBL), used as input to the akkapros pipeline |
| `data/lexlinks/` | Manual lexical analysis of *Erra and Išum* Tablet I, including construct-aware input files |
| `outputs/` | Results of running akkapros on the corpus: metrics, syllabified text, phoneme strings, MBROLA preparation files |
| `notes/` | Research reading, reflection, and documentation (see below) |

## 📊 Corpus

The corpus consists of six Standard Babylonian literary texts (6,261 words, 15,406 syllables):

- *Enūma eliš* (tablets II, IV, VI, VII)
- *Erra and Išum* (tablet I)
- *Marduk's Address to the Demons*

The ATF source files are in `data/samples/`. The lexical analysis for *Erra and Išum* is in `data/lexlinks/`.

## 📂 Data

### `data/samples/` — ATF Input Files

Six ATF files retrieved from the [Electronic Babylonian Library (eBL)](https://www.ebl.lmu.de/), an open-access digital corpus of Akkadian and Sumerian texts maintained by the Ludwig Maximilian University of Munich. These files are the direct input to the akkapros syllabification and prosody pipeline. See `data/samples/README.md` for licensing information.

### `data/lexlinks/` — Lexical Analysis

Manual line-by-line lexical analysis of *Erra and Išum* Tablet I, tagging each word as function word, construct-state noun, or stressable word. Includes prepared construct-aware input files used for the Erra diagnostic in the article.

## 📈 Outputs

### `outputs/erra-and-ishum/`

Results for *Erra and Išum* Tablet I, including:
- Syllabified text (`*_syl.txt`)
- Prosody-realized text (`*_tilde.txt`)
- Phoneme strings with durations (`*_phone.txt`, `*_ophone.txt`)
- MBROLA-compatible phoneme strings (`*_mbrola.pho`, `*_ombrola.pho`)
- Metrics reports (`*_metrics.txt`)
- Both `bi` and `mono` mora modes

### `outputs/full-corpus/`

Results for the full six-text corpus, including:
- All pipeline stages for LOB (Literary Old Babylonian) and SOB (Standard Old Babylonian) accent styles
- Both `bi` and `mono` mora modes
- Metrics reports in JSON and plain text formats

### `outputs/mbrola-prep/`

MBROLA voice preparation files:
- Diphone inventory (`phoneprep_diphones.tsv`)
- Recording manifest (`phoneprep_manifest.tsv`)
- Recording helper HTML page (`phoneprep_recording_helper.html`)
- Word list for voice recording (`phoneprep_words.txt`)

## 📝 Research Notes

The `notes/` directory contains the research documentation organized into three layers:

### `notes/dist/` — Canonical Note Archive

Numbered thematic notes (Notes-A through Notes-M) covering:

| File | Content |
|------|---------|
| `Notes-A-Foundations.md` | Project overview, corpus description, syllable types, mora counting |
| `Notes-B-Corpus.md` | Corpus statistics, text descriptions, word counts |
| `Notes-C-Academic-Model.md` | Academic stress rules (Huehnergard, Streck), accent styles |
| `Notes-D-Metrics.md` | Acoustic metrics (%V, ΔC, VarcoC, nPVI-V, rPVI-C), reference values |
| `Notes-E-Hypotheses.md` | Hypothesis development, legal/illegal operations, design principles |
| `Notes-F-Algorithm.md` | Merge logic, diphthong processing, worked examples |
| `Notes-G-Results.md` | Results, pauses, speech rate, limitations, implications |
| `Notes-H-Implementation.md` | Data structures, CLI tools, pipeline |
| `Notes-I-Timing-Model.md` | Phonetizer timing model, drift mechanism, configuration |
| `Notes-J-TTS.md` | MBROLA integration, diphone recording, voice building |
| `Notes-K-Article-Content.md` | Article planning, argumentation, and content tracking |
| `Notes-L-Parameter-Justifications.md` | Empirical grounding for each timing model parameter |
| `Notes-M-Oral-Acquisition.md` | SLA evidence for the broader implication |

### `notes/prep/` — Exploratory Synthesis

Working notes for new assessments, hypothesis testing, and literature distillation before promotion to the canonical archive.

### `notes/notebooklm/` — Source Summaries

AI-generated summaries of uploaded research papers (Google NotebookLM), serving as a searchable reference layer for empirical data.

## 🛠️ Usage

1. Clone this repository:

   ```bash
   git clone https://github.com/samuelkabak/akkapros-research-notes.git
   ```

2. Explore `data/samples/` for ATF input files
3. See `data/lexlinks/` for the lexical analysis
4. Review `outputs/` for example results from the main toolkit
5. Read `notes/` for detailed research documentation

The files here are designed to work with the main [akkapros](https://github.com/samuelkabak/akkapros) toolkit. For installation and usage of the toolkit itself, please refer to its documentation.

## 📄 License

These research materials are shared under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. You are free to share and adapt the material with appropriate credit.

The ATF files in `data/samples/` are sourced from the Electronic Babylonian Library (eBL) and are subject to their open-access terms. See `data/samples/README.md` for details.

## 🙏 Acknowledgments

- Electronic Babylonian Library (eBL) at LMU Munich for open-access transcriptions
- John Huehnergard and Michael Streck for foundational scholarship
- The open-source community

---

*Making Akkadian sound like language again.*
