# Research Notes - Akkadian Prosody Project
## Part H: Implementation — Data Structures, CLI, Pipeline

---

## H-130-Syllable-Class

**Domain:** Algorithm / Implementation / Data Structures

**WHAT:** The Syllable class is the fundamental unit representing a single syllable in the Akkadian text. It stores the syllable's text, type, mora count, and accentuation status.

**WHY:** To apply moraic prosody realization, each syllable must be analyzed individually. The class encapsulates:

* `text`: the syllable string (e.g., "dad")
* `type`: syllable type (CV, CVC, CVV, CVVC, VC, V, VV, VVC)
* `morae`: original mora count
* `accentuated_morae`: mora count after stress realization
* `accentuated_text`: text with tilde markers
* `is_accentuated`: boolean flag
* `accentuation_type`: "lengthen_vowel", "geminate_coda", "geminate_onset", "geminate_glottal"
* `has_circumflex`: boolean for special handling
* `word_idx` and `position_in_word`: for tracking context

**THUS:** The Syllable class provides all necessary information for the accentuation engine to evaluate eligibility and apply operations. It serves as the atomic unit throughout the pipeline.

---

## H-131-Word-Class

**Domain:** Algorithm / Implementation / Data Structures

**WHAT:** The Word class represents a complete lexical word composed of Syllable objects. It tracks the word's moraic structure and manages accentuation attempts.

**WHY:** Words are the primary domain for stress eligibility. The class provides:

* `syllables`: list of Syllable objects
* `morae`: total original mora count
* `accentuated_morae`: total after stress realization
* `needs_accentuation`: boolean (accentuated_morae % 2 == 1)
* `get_accentuation_candidates(style)`: returns list of possible accentuations in priority order
* `get_best_accentuation(style)`: returns highest priority accentuation
* `apply_accentuation(accentuation)`: applies operation to specified syllable
* `get_text()`: returns word with accentuations and syllable dots

**THUS:** The Word class encapsulates all word-level logic, keeping the main accentuation algorithm clean and focused on flow control rather than low-level operations.

---

## H-132-MergedUnit-Class

**Domain:** Algorithm / Implementation / Data Structures

**WHAT:** The MergedUnit class represents a group of words that have been prosodically joined for stress realization purposes. It flattens the component words into a single list of syllables while tracking original word boundaries.

**WHY:** When words cannot be stress-realized independently, they merge with following words. The merged unit must be treated as a single prosodic domain while preserving information about which syllables belong to which original word (critical for legality checks like final gemination).

**THUS:** The MergedUnit class provides methods to check if a syllable is word-final, to find accentuation candidates across the entire unit, and to apply accentuations while respecting word-internal constraints.

---

## H-133-AccentuationEngine-State-Machine

**Domain:** Algorithm / Implementation / Control Flow

**WHAT:** The AccentuationEngine class orchestrates the entire stress realization process. It processes text line by line, tokenizing into words and applying the accentuation algorithm sequentially.

**WHY:** The algorithm must proceed left-to-right, mimicking speech production. For each word:

1. Count morae
2. If even, keep and move to next
3. If odd, attempt internal accentuation per accent model
4. If accentuation succeeds, apply and continue
5. If accentuation fails, merge with following word(s)
6. Count merged unit morae
7. Select accentuation target per accent model
8. Apply accentuation to merged unit
9. Output with merge markers (`_` or `+`)

**THUS:** The AccentuationEngine state machine implements the core logic in a clean, deterministic way, with all edge cases handled through merging and last-resort mechanisms.

---

## H-134-atfparser-CLI

**Domain:** Implementation / CLI / Preprocessing

**WHAT:** `atfparser.py` converts eBL ATF files into clean Akkadian text for the prosody pipeline. It extracts Akkadian from `%n` lines, extracts English translation from `#tr.en:` lines, and normalizes editorial markup.

**WHY:** Raw ATF files contain extensive markup that would interfere with syllabification and stress realization. The parser removes editorial markup while preserving the linguistic content and line structure.

* `--preserve-case`: keep original case (default lowercases text)
* `--preserve-h`: keep `h/H` unchanged (default maps to ḫ/Ḫ)
* `--append`: append to output files instead of overwriting
* `--strict`: enable strict warning mode

**THUS:** The parser produces clean `*_proc.txt` files ready for syllabification, with line breaks preserved to encode phrasing.

---

## H-135-syllabifier-CLI

**Domain:** Implementation / CLI / Syllabification

**WHAT:** `syllabifier.py` converts cleaned Akkadian text into syllabified form using standard Assyriological rules (Huehnergard 2011). It inserts syllable boundaries (`.`), marks word endings (`¦`), and preserves hyphens and punctuation in brackets.

**WHY:** Syllabification is a prerequisite for mora counting and stress realization. The algorithm must handle edge cases like geminate splitting, diphthong resolution (via glottal stop insertion), and non-Akkadian text in brackets.

* `--merge-hyphen`: merge hyphens into syllable separators
* `--merge-lines`: normalize line breaks (1 newline → space, 2+ → paragraph break)
* `--extra-vowels` / `--extra-consonants`: extend character sets

**THUS:** The syllabifier produces `*_syl.txt` files with explicit syllable structure, ready for the prosody realization engine.

---

## H-136-prosmaker-CLI

**Domain:** Implementation / CLI / Prosody Realization

**WHAT:** `prosmaker.py` applies the moraic prosody realization algorithm to syllabified text. It reads `*_syl.txt` and produces `*_tilde.txt`, the pivot format containing all accentuation decisions explicitly marked with `~`.

**WHY:** This is the core algorithmic engine. It implements the LOB/SOB hierarchies, legal operations, merge logic, and function word handling. Diphthongs are restored automatically after processing. The output `_tilde.txt` is the prosody pivot that records grouping and accentuation decisions for downstream stages.

Key options:
* `--style {lob,sob}`: accent style (default: lob)
* `--mora-mode {bi,mono}`: bimoraic parity gate (bi, default) or academic mono-mode (mono)
* `--relax-last`: allow stress realization propagation before last linked word
* `--test`: run internal tests

The `_tilde.txt` pivot preserves merge provenance: explicit links inherited from input remain `+`, while automatic merges introduced by prosody are serialized as `&`. Diphthong memory markers (`¨`) are preserved so downstream stages can still see the internal syllable boundary.

**THUS:** The prosmaker produces the master pivot format consumed by the phonetizer. It is the third step in the pipeline: atfparser → syllabifier → prosmaker → phonetizer → metrics/printer.

---

## H-136b-phonetizer-CLI

**Domain:** Implementation / CLI / Phonetic Realization

**WHAT:** `phonetizer.py` turns a prosody-realized `*_tilde.txt` file into two finalized phone-row artifacts, `<prefix>_ophone.txt` and `<prefix>_phone.txt`, plus two MBROLA `.pho` artifacts. This is the stage where the prosodic analysis becomes a phonetic one: it decides segmental realization, duration, pause strength, and row-level intonation.

**WHY:** The phonetizer is the central timing engine of the pipeline. It implements a three-pass contract:
1. **Pass 1** builds row structure: which rows exist, where boundaries fall, and what kind of pause has been encountered.
2. **Pass 2** realizes non-zero durations over the prebuilt row streams, using the timing model (cvc_reference, consonant/vowel anchors, drift tolerance, pause bands).
3. **Pass 3** assigns row-level intonation tokens.

The timing split is stream-aware: the accentuated stream (`_phone.txt`) uses `cvc_reference` in bimoraic mode and `0.5 × cvc_reference` in monomoraic mode, while the original stream (`_ophone.txt`) always uses `0.5 × cvc_reference`.

Key options:
* `--geminate-policy {corrective,cumulative}`: override geminate handling
* `--accentuation-distribution-policy {100_0,...,70_30}`: override accent distribution
* `--drift-tolerance <int>`: override drift tolerance
* `-t/--option KEY=VALUE`: override any config-backed runtime path
* `--conf <file>`: load shared grouped config

The phonetizer is the canonical owner of the `phonetize` config section, including `phonetize.process.timing_model.durations.*` (scale, segmental_ceiling, segmental_floor, cvc_reference, consonant/vowel/pause parameters) and `phonetize.process.intonation.*` (f0, stress, question, statement, exclamation, continuation presets).

**THUS:** The phonetizer is the fourth step in the pipeline and produces the authoritative phonetic artifacts consumed by metricalc and printer. It is the stage where the timing model is actually applied to produce millisecond durations.

---

## H-137-metricalc-CLI

**Domain:** Implementation / CLI / Metrics

**WHAT:** `metricalc.py` computes rhythmic and structural metrics from paired phonetizer artifacts (`_ophone.txt` and `_phone.txt`). It outputs human-readable tables and JSON formats.

**WHY:** The active metrics contract is phone-driven. Metricalc reads the realized durations from the phonetizer artifacts directly, rather than reconstructing rhythm from the prosody pivot. This means the reported rhythm metrics describe the actual phone-row timing model used by the toolkit.

The stage computes the full indicator set for both original and accentuated streams:
* `%V`, `%C`: proportion of vocalic and consonantal intervals
* `meanV`, `meanC`: average interval durations
* `ΔV`, `ΔC`: raw variability (standard deviation)
* `VarcoV`, `VarcoC`: rate-normalized variability
* `rPVI-C`, `nPVI-V`: pairwise variability indices

Pause intervals remain in the denominator for `%V` and `%C` but are excluded from `mean`, `Δ`, `Varco`, and PVI calculations.

The stage also reports structural inventory (syllable counts, word counts, mora statistics, merge statistics, accentuation statistics, prominence statistics) and the phonetizer unit-drift summary consumed from front matter.

Key options:
* `--table`, `--json`: output formats
* `--input-list`: batch processing
* `--ophone <file>`: explicit original-stream path

**THUS:** The metrics calculator provides quantitative validation of the algorithm and enables cross-linguistic comparison. It is the fifth step in the pipeline, consuming the phonetizer's realized phone rows.

---

## H-138-printer-CLI

**Domain:** Implementation / CLI / Formatting

**WHAT:** `printer.py` converts phonetizer-owned phone rows (`*_phone.txt` and matching `*_ophone.txt`) into user-facing reading outputs: acute-accented text, bold-marked Markdown, IPA transcription, and XAR practical orthography.

**WHY:** Different audiences need different representations. Scholars need acute accents for compact notation; readers need bold for visual inspection; phoneticians need IPA. The printer now consumes the phonetizer's downstream artifacts directly, not the `_tilde.txt` pivot.

Key options:
* `--acute`, `--bold`, `--ipa`, `--xar`: output selectors
* `--ipa-proto-semitic {preserve,replace}`: pharyngeal mapping
* `--circ-hiatus`: speculative mode splitting circumflex vowels
* `--print-merger`: show visible merge connector `‿`

MBROLA `.pho` export is no longer owned by the printer. Use `phonetizer.py` or `fullprosmaker.py` to produce MBROLA artifacts from the phonetize stage.

**THUS:** The printer makes the algorithm's output accessible to diverse users and applications. It is the final stage in the pipeline, consuming the phonetizer's phone-row artifacts.

---

## H-139-fullprosmaker-CLI

**Domain:** Implementation / CLI / Pipeline

**WHAT:** `fullprosmaker.py` runs the complete pipeline in one command: syllabification → prosody realization → phonetization → metrics → printing. It centralizes shared options and writes all selected outputs in a single reproducible run.

**WHY:** Users should not need to run five separate tools for standard processing. The full pipeline ensures consistency and reduces error. For most research use, this is the recommended entry point.

Pipeline stages:
1. Syllabify: `*_proc.txt` → `*_syl.txt`
2. Prosody: `*_syl.txt` → `*_tilde.txt`
3. Phonetize: `*_tilde.txt` → `*_ophone.txt`, `*_phone.txt`, `*_ombrola.pho`, `*_mbrola.pho`
4. Metrics: `_ophone.txt` + `_phone.txt` → table/json
5. Print: `_ophone.txt` + `_phone.txt` → accent outputs

Key options:
* `--prosody-style {lob,sob}`: accent style
* `--mora-mode {bi,mono}`: mora mode
* `--prosody-relax-last`: relaxed linker behavior
* `--phonetize-accentuation-distribution-policy`: override accent distribution
* `--phonetize-drift-tolerance <int>`: override drift tolerance
* `-t/--option KEY=VALUE`: override any config-backed path
* `--metrics-table`, `--metrics-json`: metrics output selection
* `--print-acute`, `--print-bold`, `--print-ipa`, `--print-xar`: print output selection

**THUS:** The fullprosmaker is the primary entry point for end-to-end processing, suitable for both single-file analysis and batch corpus work. It keeps stage contracts aligned across the full pipeline.

---

## H-140-phoneprep-CLI

**Domain:** Implementation / CLI / TTS Preparation

**WHAT:** `phoneprep.py` generates optimized recording scripts for MBROLA diphone voice creation. It produces a human-readable script, machine-readable sidecars (manifest, diphone list, word list), and an interactive HTML recording assistant.

**WHY:** Building a custom MBROLA voice requires recording every possible diphone. The script maximizes coverage with minimal recording burden by using a rhythmic pattern that enables automatic segmentation.

* `--coverage`: target per-diphone coverage (1-4, default 3)
* `--with-html-recording-helper`: create interactive recording assistant
* `--two-batch-emphatic`: create plain and mixed batches

**THUS:** phoneprep bridges the gap between computational phonology and speech synthesis, providing everything needed to record and segment a complete diphone database.

---

## H-141-Pipeline-Data-Flow

**Domain:** Implementation / Pipeline

**WHAT:** The akkapros pipeline processes Akkadian text through five sequential stages, each producing artifacts consumed by the next stage:

1. **ATF Parser** (`atfparser.py`): `*.atf` → `*_proc.txt`
   - Extracts Akkadian text from eBL ATF files
   - Normalizes editorial markup

2. **Syllabifier** (`syllabifier.py`): `*_proc.txt` → `*_syl.txt`
   - Inserts syllable boundaries and word-ending markers
   - Handles diphthong resolution and punctuation

3. **Prosmaker** (`prosmaker.py`): `*_syl.txt` → `*_tilde.txt`
   - Applies moraic prosody realization algorithm
   - Produces the prosody pivot with accentuation markers

4. **Phonetizer** (`phonetizer.py`): `*_tilde.txt` → `*_ophone.txt`, `*_phone.txt`, `*_ombrola.pho`, `*_mbrola.pho`
   - Builds finalized phone-row artifacts with millisecond durations
   - Applies the timing model (anchors, drift, pause bands)
   - Assigns intonation contours

5. **Metrics** (`metricalc.py`): `*_ophone.txt` + `*_phone.txt` → `*_metrics.txt`, `*_metrics.json`
   - Computes rhythmic and structural metrics from realized durations
   - Reports interval metrics, drift summary, structural inventory

6. **Printer** (`printer.py`): `*_ophone.txt` + `*_phone.txt` → accent outputs
   - Generates user-facing reading formats (acute, bold, IPA, XAR)

**WHY:** The pipeline architecture ensures that each stage has a clear input contract and produces well-defined artifacts. The phonetizer is the central stage: it transforms abstract prosodic decisions into concrete phonetic realizations that can be measured and compared. The `_ophone.txt` and `_phone.txt` artifacts are the authoritative downstream analysis artifacts, consumed by both metricalc and printer.

**THUS:** The pipeline is designed for reproducibility and transparency. Each stage can be run independently for debugging, or the entire pipeline can be run with a single `fullprosmaker.py` command for production use.

---

## References

**Huehnergard, John.** ***A Grammar of Akkadian***. 3rd edition. Winona Lake, IN: Eisenbrauns, 2011. (Huehnergard 2011)
