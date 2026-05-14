# Notes Directory

This directory contains the research notes for the Akkadian Prosody Project. The notes are organized into three layers: the consolidated bibliography, exploratory working notes (`prep/`), and NotebookLM-generated source summaries (`notebooklm/`).

---

## Directory Structure

```
notes/
├── README.md              # This file
├── bibliography.md        # Consolidated project bibliography
├── prep/                  # Exploratory synthesis and working notes
└── notebooklm/            # NotebookLM-generated source summaries
```

---

## `bibliography.md` — Consolidated Bibliography

All bibliographic references used across the research notes, article drafts, and NotebookLM source summaries, organized by domain in Chicago Author-Date format.

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
| `consonant-duration-note.md` | Consonant duration data note |
| `onset-post_vocalic-parameter-choice.md` | Parameter reduction to onset vs. post-vocalic |
| `phonetizer-algorithm-note.md` | Phonetizer algorithm documentation |
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
