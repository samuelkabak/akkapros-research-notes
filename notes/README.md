# Notes Directory

This directory contains the research notes for the Akkadian Prosody Project. The notes are organized into three layers: the canonical note archive (`dist/`), exploratory working notes (`prep/`), and NotebookLM-generated source summaries (`notebooklm/`).

---

## Directory Structure

```
notes/
├── README.md              # This file
├── dist/                  # Canonical note archive (numbered Notes-A through Notes-L)
├── prep/                  # Exploratory synthesis and working notes
└── notebooklm/            # NotebookLM-generated source summaries
```

---

## `dist/` — Canonical Note Archive

The main research notes have been split into 12 thematic files (Notes-A through Notes-L), replacing the former monolithic `research-notes.md`:

| File | Part | Content |
|------|------|---------|
| `Notes-A-Foundations.md` | A | Project overview, corpus description, syllable types, mora counting |
| `Notes-B-Corpus.md` | B | Corpus statistics, text descriptions, word counts |
| `Notes-C-Academic-Model.md` | C | Academic stress rules (Huehnergard, Streck), accent styles |
| `Notes-D-Metrics.md` | D | Acoustic metrics (%V, ΔC, VarcoC, nPVI-V, rPVI-C), reference values |
| `Notes-E-Hypotheses.md` | E | Hypothesis development, legal/illegal operations, design principles |
| `Notes-F-Algorithm.md` | F | Merge logic, diphthong processing, worked examples |
| `Notes-G-Results.md` | G | Results, pauses, speech rate, limitations, implications |
| `Notes-H-Implementation.md` | H | Data structures (Syllable, Word, MergedUnit), CLI tools, pipeline |
| `Notes-I-Timing-Model.md` | I | Phonetizer timing model, drift mechanism, configuration structure |
| `Notes-J-TTS.md` | J | MBROLA integration, diphone recording, voice building |
| `Notes-K-Article-Content.md` | K | Article planning, argumentation, and content tracking |
| `Notes-L-Parameter-Justifications.md` | L | Empirical grounding for each timing model parameter |

The former monolithic `research-notes.md` is also preserved in `dist/` for historical reference.

### Note Numbering

Notes are numbered sequentially within each part:
- Part A: A-001 through A-030
- Part B: B-001 through B-030
- Part C: C-001 through C-030
- Part D: D-031 through D-048
- Part E: E-049 through E-065
- Part F: F-066 through F-087
- Part G: G-088 through G-129
- Part H: H-130 through H-141
- Part I: I-142 through I-150
- Part J: J-151 through J-159
- Part K: K-160 through K-184
- Part L: L-200 through L-226

### Parameter Supersession

Note L-201 (Parameter Supersession Note) documents that the parameter justifications in Part L supersede the earlier, less rigorous justifications in notes 200–230 of the original monolithic file. For any research use, cite the parameter values and justifications from Part L, not the earlier notes.

---

## `prep/` — Exploratory Synthesis

New assessment notes based on comments, discussions, reading summaries, or tool-assisted literature digestion should be drafted in `notes/prep/` first. They should only be incorporated into the main note stream after they have been checked, reduced, and rewritten in a form that is fit for citation-sensitive research use.

### Why The Prep Layer Exists

The prep layer separates exploratory synthesis from the canonical note record. This matters for three reasons:

1. Early assessments often mix secure data, provisional interpretation, and discarded hypotheses.
2. Comparative phonetic and prosodic material often needs one more pass before it can be stated in a stable Akkadian-facing formulation.
3. The main note file should remain usable as a reliable base for article drafting and program design without carrying visible traces of exploratory overreach.

### Workflow

1. **Start in `notes/prep/`.** Write the first usable version of any new assessment note there, especially when it arises from comments, discussion threads, reading extracts, or synthetic literature review.

2. **Separate evidence from inference.** State what the sources actually show, then distinguish any extrapolation, modeling step, or Akkadian-specific implication.

3. **Ground claims explicitly.** Use in-text citations in the form `(Author Year)` where the bibliography supports that level of precision. If the bibliographic detail is uncertain in the workspace, do not invent it.

4. **Add a bibliography block.** Prep notes should end with a short bibliography section listing the works actually used in the note.

5. **Promote only the distilled result.** Once the prep note is stable, transfer only the grounded conclusions, usable tables, and carefully framed implications into the main note file.

6. **Mark hypotheses as hypotheses.** In the public note layer, grounded observations belong in `WHAT`. Interpretive or model-building claims in `WHY` or `THUS` should either be sourced or explicitly marked as provisional, for example with `POSSIBLY:` or `PROPOSED MODEL:`.

### What Belongs In `notes/prep`

- Assessments of reviewer comments or informal comments
- Discussion notes that test an interpretation before it enters the main synthesis
- Reading notes distilled from secondary scholarship
- Comparative timing tables assembled from several sources
- Provisional model checks, threshold notes, and evidence-ranking exercises
- Corrections of earlier misunderstandings, if they still help explain the later synthesis

### Current Prep Notes

| File | Topic |
|------|-------|
| `class-positional-ranges-hypothesis-check.md` | Tests three-class positional hypothesis for consonants |
| `coda-pause-compensation-formal-model.md` | Formal model for CVC/CVV timing equivalence |
| `coda-pause-compensation-hypothesis.md` | Compensation hypothesis statement |
| `compensation-model-qa-assessment.md` | Assesses source support for compensation model |
| `onset-post_vocalic-parameter-choice.md` | Parameter reduction to onset vs. post-vocalic |
| `positional-comparability-audit.md` | Methodological correction on measurement comparability |
| `special-realization-placement.md` | YAML placement rationale for hiatus and vowel_transition |
| `syllable-total-vs-mora-boundary.md` | Checks perceptual thresholds for whole-syllable templates |

---

## `notebooklm/` — NotebookLM Source Summaries

This directory contains AI-generated summaries of uploaded research papers, produced by Google NotebookLM. These files are **source-driven summaries** — they extract and organize data points from the uploaded literature but do not provide original analysis.

### Purpose

The NotebookLM files serve as a **searchable reference layer** for the empirical data used in the project. They are not analytical documents. They are the raw material from which the analytical prep notes and canonical notes are distilled.

### Relationship to Other Layers

```
Research papers (uploaded to NotebookLM)
    ↓
notebooklm/  (AI-generated summaries — raw data extraction)
    ↓
prep/        (analytical distillation — evidence separated from inference)
    ↓
dist/        (canonical notes — stable, publication-facing formulations)
```

### File Inventory

The NotebookLM files cover the following domains:

**Consonant timing:**
- `consonant-classes.md`, `consonants-more-data.md` — Consonant classification and duration data
- `fricatives.md`, `fricatives-3.md`, `fricatives-4.md` — Fricative duration data
- `geminates.md`, `geminate-fricatives.md`, `gemination-minimum.md` — Gemination thresholds
- `liquid-nasal.md`, `non-stops.md` — Sonorant and glide data
- `segmental-data.md` — Comprehensive segmental duration table
- `table-of-classes.md` — Normalized timing table by model class

**Vowel timing:**
- `long-vowels.md`, `long-vs-short.md` — Vowel quantity data
- `vowels-and-transitions.md`, `vowels-length.md` — Vowel duration ranges
- `verylong-vowels.md` — Overlong vowel data
- `hiatus.md`, `hiatus-transition.md` — Hiatus and vowel transition data

**Syllable and CVC timing:**
- `cvc-syllables.md`, `cvc-timing-foundation.md` — CVC as timing anchor
- `new-cvc.md`, `new-reference-data.md` — Additional CVC data
- `syllables-timing.md` — Syllable-level timing evidence

**Pause timing:**
- `pause-syntax-rhythm.md` — Pause syntax and rhythm
- `pauses.md`, `pauses-2.md` — Pause duration data
- `pauses-classification.md`, `pauses-structural.md`, `pauses-perceptual-thresholds.md` — Pause classification
- `wpm.md`, `wpm-benchmarks.md` — Words-per-minute benchmarks

**Compensation and rhythm:**
- `compensation-mechanism.md` — Phonetic compensation mechanism
- `compensation-model-qa.md` — Q&A on compensation model
- `duration-metrics-classification.md` — Duration metrics classification
- `segmental-temporal-classification.md` — Temporal classification of segments

**Measurement and methodology:**
- `measurement-errors.md` — Inter-transcriber reliability
- `excessive-lengthening.md`, `unnatural-limit.md` — Duration ceilings
- `transition-realization.md` — Vowel transition realization

**Parameter justifications:**
- `basic-accentuation-justification.md` — 50 ms increment justification
- `parameters-justifications.md` — Full parameter justifications
- `durations-again.txt`, `durations-again-2.txt` — Duration consistency checks
- `max-long-vowels.txt` — Maximum vowel duration data

**Bibliography and review:**
- `bibliography-v1.md`, `bibliography-v2.md` — Formatted bibliographies
- `plausible-metrics.md` — Metrics plausibility assessment
- `reference-improvements.md` — Reference improvement suggestions
- `review-corrections.md` — Research notes review

---

## Style Expectations

Write in a cautious scholarly voice. Keep secure claims, probable claims, and speculative claims distinct. Avoid overstating what comparative evidence can demonstrate for Akkadian. The aim is not to eliminate interpretation, but to make the level of certainty visible at every step.

## Practical Default

If there is any doubt about whether a new note is stable enough for the main note stream, put it in `notes/prep/` first.
