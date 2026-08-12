# Research Notes - Akkadian Prosody Project
## Part N: Output Regeneration and Accent Style Clarification

---

## N-001-Output-Regeneration-Akkapros-3-2-0

**Domain:** Data / Reproducibility

**WHAT:** The outputs in `outputs/` (full-corpus and Erra and Išum) were regenerated with akkapros 3.2.0 after a bug fix in the prosody engine. The fix (CR-111) makes the last-resort accentuation fallback consistently target the **first** syllable of the word (`word.syllables[0]`) in all five code paths; two paths previously targeted the last syllable (`word.syllables[-1]`), a difference that surfaced only for polysyllabic words.

**WHY:** The bug affected which syllable carries the last-resort mark (onset gemination or glottal onset) in a small number of polysyllabic cases, and therefore the downstream durations and acoustic metrics. Publishing results computed with the uncorrected engine would compromise reproducibility.

**THUS:** All LOB and SOB artifacts were regenerated and are published here. Aggregate quantities are unchanged: 2,580 accentuated syllables (16.75%) in the full-corpus bi stream, 4,989 (32.38%) in mono mode, and 547 (18.30%) for Erra and Išum. The distribution of last-resort types shifted slightly (full corpus bi: C:V 20 -> 18, ʔ:V 13 -> 15), and a few acoustic metrics changed at the second decimal place (e.g. ΔC 68.81 -> 68.82 ms in bi mode; mono ΔC 61.56 -> 61.43 ms, VarcoC 49.85 -> 49.74, rPVI-C 73.05 -> 72.60, nPVI-V 27.04 -> 27.08; bi rPVI-C 78.91 -> 78.90). Pause ratios and merge statistics are unaffected.

---

## N-002-Last-Resort-Targets-First-Syllable

**Domain:** Algorithm / Last Resort

**WHAT:** When no legal accentuation candidate exists and forward/backward merge cannot resolve the unit, the algorithm applies the last resort: gemination of the onset or insertion of a glottal onset, always on the **first** syllable of the word.

**WHY:** This is the phonetically conservative choice: it builds prominence on the initial syllable without altering the phonemic quantity of the word's vowels, and it matches the Semitic pattern in which prominence defaults to the initial syllable when no heavy syllable can attract stress.

**THUS:** The realization section of the study states this rule explicitly: "when no heavy syllable is available to attract stress, prominence defaults to the initial syllable."

---

## N-003-Accent-Style-Clarification

**Domain:** Algorithm / Accent Styles

**WHAT:** The toolkit implements three accent styles. Their status differs:

- **LOB** (Literary Old Babylonian): final superheavy > rightmost non-final heavy > final heavy. Follows literary-register reconstructions (Streck 2022; Izre'el and Cohen 2004). This is the default style of the study.
- **AOB** (Academic Old Babylonian): final superheavy > rightmost non-final heavy, with the initial syllable as the last-resort default. Implements the standard academic description (Huehnergard 2011); in the toolkit it is LOB without the final-heavy rule (akkapros 3.2.0).
- **SOB** (Standard Old Babylonian): rightmost non-final heavy > final heavy > initial syllable. This is a **speculative modeling variant** of the toolkit. No such hierarchy is attested in the academic literature on Standard Old Babylonian; the name must not be read as an established scholarly style.

**WHY:** Earlier versions of the notes attributed the SOB hierarchy to Huehnergard's standard description. That attribution was incorrect: the standard description is implemented as AOB, and SOB is a heuristic used only to probe the behavior of the algorithm when the final syllable can attract stress but superheavy finals are not prioritized.

**THUS:** The study uses only LOB and reports no AOB or SOB results. The distinction between attested styles (LOB, and the standard model behind AOB) and the speculative testing variant (SOB) is now stated explicitly in the notes.

---

## N-004-Section-9-4-Update

**Domain:** Article / Algorithm Description

**WHAT:** The algorithm description in the study (draft, Section 9.4) was updated to align with the corrected engine: the operations of the bi mode are described as *permitted* operations, and the last-resort behavior is stated as first-syllable targeting.

**WHY:** The paragraph had to reflect the corrected behavior of the engine and a terminology that does not overstate the status of the operations.

**THUS:** No change in results is implied beyond the regenerated outputs described in N-001.

---

## Bibliography

- Huehnergard, John. *A Grammar of Akkadian*. 3rd ed. Winona Lake, IN: Eisenbrauns, 2011.
- Izre'el, Shlomo, and Eran Cohen. *Literary Old Babylonian*. Muenchen: LINCOM, 2004.
- Streck, Michael. *Old Babylonian Grammar*. Leiden: Brill, 2022.
