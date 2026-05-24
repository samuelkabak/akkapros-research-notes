# Research Notes - Akkadian Prosody Project
## Part K: Article Planning and Argumentation

---

## K-160-Article-Overview

**Domain:** Article / Planning

**WHAT:** The article argues that the standard Akkadian stress model is best understood as a theory of lexical stress eligibility, not a full account of phrasal realization. It then demonstrates, through computational implementation and rhythm metrics, that Akkadian was most likely stress-timed, and proposes a realization algorithm that fills the gap between lexical eligibility and connected speech. The article includes an Appendix A describing the akkapros toolkit (the computational engine behind all reported metrics). The "Data and code" line was removed from the header (not a real submission field). Keywords were revised to: *Akkadian prosody, lexical stress, phrasal realization, rhythm metrics, stress-timing, computational philology*.

**WHY:** The project needed a publishable article that makes two linked claims: (1) a diagnostic claim that the gap between lexical eligibility and phrasal realization can be demonstrated concretely, and (2) a constructive claim that a realization algorithm can be specified, implemented, and evaluated against standard rhythm metrics.

**THUS:** The article is structured to present the quantitative evidence first (metrics demonstration, rhythm classification) and the algorithm second, so that the algorithm is understood as a response to a demonstrated need rather than as a free-standing proposal.

---

## K-161-Article-Structure-Rationale

**Domain:** Article / Planning / Structure

**WHAT:** The article follows this structure:

1. **Introduction** — States the problem: lexical stress rules identify candidates, not phrasal realization.
2. **Lexical Stress and the Phrasal Problem** — Presents the academic model as a candidate set, introduces the Erra diagnostic (29.2% lexical vs. 18.30% realized), and explains why Erra is illustrative but not the main quantitative proof.
3. **Corpus and Metric Framework** — Describes the 6-text corpus (6,261 words, 15,406 syllables) and the cluster of rhythm metrics used (%V, ΔC, ΔV, VarcoC, VarcoV, rPVI-C, nPVI-V).
4. **Metrics Demonstration** — Presents the original stream baseline, the accentuated stream (LOB bi mode), comparison with SOB, and comparison with mono mode.
5. **Why Akkadian Is Unlikely to Be Syllable-Timed** — Structural and metric arguments against syllable-timing.
6. **Why Akkadian Is Unlikely to Be Mora-Timed** — Distinction between moraic phonology and mora-timed rhythm.
7. **Why a Stress-Timed Reading Is the Strongest Remaining Option** — Positive argument for stress-timing, including honest discussion of intermediate VarcoC values.
8. **The Realization Algorithm** — Describes mora modes, accent styles, legal operations, and grouping rules.
9. **Worked Example: Erra 59–62** — Shows the algorithm on a short passage.
10. **From Morae to Millisecond Durations** — Timing model parameters and their empirical grounding.
11. **Practical Consequence: Toward Akkadian TTS** — TTS as a practical outcome, not evidence.
12. **Limitations** — Honest statement of scope and constraints.
13. **Conclusion**

**WHY:** The structure was revised from earlier drafts. The key architectural decision was to move the stress-timed demonstration (sections 4–7) before the algorithm description (section 8). This ensures the reader understands why a realization mechanism is needed before being shown how one works. Earlier drafts (v8) placed the algorithm first, which risked making it seem like a free-standing proposal rather than a response to a demonstrated gap.

**THUS:** The current structure (v9) is: problem → evidence → classification → algorithm → example → timing model → implications. This mirrors the logical flow of the research itself: the metrics were computed first, and the algorithm was designed to produce a stress-timed profile.

---

## K-162-Erra-Diagnostic-Data

**Domain:** Article / Data / Erra

**WHAT:** The Erra diagnostic uses two figures:

- **29.2%** — Manual lexical analysis of *Erra and Išum* Tablet I. Every lexically eligible syllable counted as potentially prominent. This is the "lexical reading" density.
- **18.30%** — Algorithm output (LOB, bi mode) on the same text. The algorithm selects within the traditional candidate set, groups function words with hosts, and resolves construct-state links as single prosodic units.

**WHY:** The contrast shows that lexical eligibility and phrasal realization are not the same thing. The 29.2% figure is difficult to carry over into any plausible connected recitation. The 18.30% figure is sparser and more hearable as connected speech.

**CAVEAT:** The two figures arise from different counting layers. The manual lexical analysis counts every eligible syllable; the algorithm counts only syllables that receive an actual accentuation operation. The comparison is directional, not perfectly homogeneous.

**THUS:** Erra's role is diagnostic and illustrative, not the main quantitative proof. The headline typological argument rests on the broader corpus.

---

## K-163-Full-Corpus-Metrics-Data

**Domain:** Article / Data / Metrics

**WHAT:** The full corpus metrics are the quantitative core of the article. Key values from the LOB bi mode run:

| Metric | Original | Accentuated | Change |
|--------|----------|-------------|--------|
| %V | 33.94% | 34.31% | +0.37% |
| ΔC | 52.93 ms | 68.81 ms | +15.88 ms |
| ΔV | 39.32 ms | 50.78 ms | +11.46 ms |
| VarcoC | 45.68 | 54.61 | +8.93 |
| VarcoV | 29.97 | 36.69 | +6.72 |
| rPVI-C | 62.27 | 78.91 | +16.64 |
| nPVI-V | 22.72 | 28.98 | +6.26 |

Corpus statistics: 6,261 words, 15,406 syllables, 2,580 accentuated syllables (16.75% rate), 2,453 merged words into 1,108 prosodic units. WPM drops from 63.10 (original) to 60.46 (accentuated).

**WHY:** The strongest evidence is not any single metric value but the consistent direction of movement. Across all variability measures, the accentuated stream shows higher values than the original stream. That is exactly what a stress-timed interpretation predicts. A syllable-timed or mora-timed model would predict the opposite (lower variability after realization).

**THUS:** The direction-of-movement argument is stronger than any single threshold comparison. The VarcoC value of 54.61 falls below canonical stress-timed languages (English ~70–80) but the consistent increase across all metrics supports the stress-timed reading.

---

## K-164-Comparison-With-SOB-And-Mono

**Domain:** Article / Data / Comparison

**WHAT:** Two comparison runs provide additional evidence:

**SOB (Standard Old Babylonian) style:**
- Accentuation rate: 16.75% (same as LOB)
- VarcoC: 45.68 → 55.24
- VarcoV: 29.97 → 36.09
- Nearly identical to LOB. The choice between accent styles does not materially affect rhythm classification.

**Mono mode (no odd-mora gate, 50 ms increment):**
- Accentuation rate: 32.38% (nearly double bi mode)
- VarcoC: 45.68 → 49.85 (smaller increase)
- VarcoV: 29.97 → 31.85 (smaller increase)
- Mono mode accentuates more syllables but with less durational contrast, producing a profile closer to the original stream.

**WHY:** The mono mode comparison is instructive because it shows that the bi-moraic gate is not arbitrary. It is the mechanism that creates the stronger stress-timed signature. Mono mode's higher accentuation rate with smaller variability increase demonstrates that the bi mode's design is doing real work.

**THUS:** The bi mode is the default research model. Mono mode serves as a comparison baseline that validates the bi mode's design choices.

---

## K-165-Rhythm-Classification-Argument

**Domain:** Article / Argumentation / Rhythm

**WHAT:** The article argues for stress-timing by elimination and positive evidence:

**Against syllable-timing:**
- Structural: syncope, closed syllables, long vowels, substantial variation in syllable shape all push against even syllabic pacing.
- Metric: the accentuated stream shows increased variability, not decreased. A syllable-timed realization layer would smooth toward evenness.

**Against mora-timing:**
- Crucial distinction: moraic phonology does not entail mora-timed rhythm. Akkadian counts morae for lexical weight without necessarily equalizing speech at the mora level.
- Structural: heavy use of closed heavy syllables, syncope, restructuring processes resist simple mora-by-mora pacing.

**For stress-timing:**
- Direction-of-movement: all variability metrics increase after realization.
- Structural: the algorithm's operations (vowel lengthening, coda gemination) create durational contrast between prominent and non-prominent syllables.
- Comparative: Semitic languages (Arabic) are stress-timed, providing a family-level expectation.

**WHY:** The argument is strongest when presented as cumulative rather than dependent on any single threshold. The VarcoC value of 54.61 is honestly acknowledged as intermediate, but the direction-of-movement argument is stronger than any single threshold.

**THUS:** The article's formulation: "under explicit and comparatively grounded assumptions, Akkadian was most likely stress-timed." This avoids both extremes — neither merely "compatible with" nor falsely claiming recovered acoustic facts.

---

## K-166-Realization-Algorithm-Summary

**Domain:** Article / Algorithm

**WHAT:** The realization algorithm is described in the article after the quantitative demonstration. Key components:

**Mora modes:**
- `bi` mode: accentuation attempted only if prosodic unit has odd mora count. Even units emitted unchanged. Uses forward merge as repair strategy.
- `mono` mode: accentuation attempted regardless of mora parity. No forward merge.

**Accent styles:**
- LOB (Literary Old Babylonian): final superheavy > rightmost non-final heavy > final heavy
- SOB (Standard Old Babylonian): rightmost non-final heavy > final heavy

**Legal operations (always add exactly one mora):**
1. Vowel lengthening — on CVV, VV, CVVC, VVC syllables
2. Coda gemination — on CVC, VC syllables non-final in the active unit
3. Last-resort — geminate onset or add glottal onset

**Grouping rules:**
- Content words resolved independently if possible
- Function words never accented independently; attach forward
- Explicit prosodic links preserved and resolved as group

**WHY:** The algorithm is placed after the metrics demonstration so the reader understands why a realization mechanism is needed before seeing how one works. The algorithm is not presented as a free-standing proposal but as a response to the demonstrated gap between lexical eligibility and phrasal realization.

**THUS:** The algorithm section opens with: "The quantitative demonstration has shown that Akkadian's rhythm profile is most consistent with stress-timing. That conclusion raises a further question. If Akkadian was stress-timed, how was prominence realized in connected speech?"

---

## K-167-Timing-Model-Parameters

**Domain:** Article / Timing Model

**WHAT:** The timing model converts abstract morae into millisecond durations. Key parameters:

**CVC reference:** 300 ms (empirically attested range 286–306 ms, Cutanda et al. 2019)

**Accentuation increments:**
- Bi mode: 150 ms (0.5 × CVC reference), distributed 80/20
- Mono mode: 50 ms, distributed 80/20

**Consonantal durations:**
| Class | Onset | Coda | Geminate |
|-------|-------|------|----------|
| Closure | 89 ms | 87 ms | 175 ms |
| Fricative | 115 ms | 112 ms | 210 ms |
| Sonorant | 105 ms | 100 ms | 190 ms |

**Vocalic durations:**
- Short: 110 ms
- Long: 160 ms
- Very long: 260 ms
- Elongation max: 280 ms

**Pause durations:**
- Short (comma-level): 520–680 ms
- Long (clause-final): 1,100–1,780 ms

**WHY:** These values are grounded in comparative phonetic studies, not recovered from Akkadian. The article treats them as plausible ranges. The parameter justifications are documented in detail in Notes-L-Parameter-Justifications.md.

**THUS:** The timing model section serves two purposes: it explains how the rhythm metrics were computed, and it provides an audit trail for the parameter choices.

---

## K-168-Erra-Worked-Example

**Domain:** Article / Example

**WHAT:** The article uses Erra lines 59–62 as a worked example. The passage shows:

- Function words (*kī*, *ša*, *ana*, *lū*) attaching to following content hosts
- Explicit links (*šakān+kamāri*, *ṣalmāt+qaqqadi*, *būl+šakkan*) preserved as prosodic units
- Accentuation falling on rightmost eligible heavy syllable within each unit

Source transliteration:
```
kī ša nišī dadmē ḫubūršina : elīka imtarṣu
ublam-ma libbaka : ana šakān+kamāri
ṣalmāt+qaqqadi ana šumutti : šumqutu būl+šakkan
lū kakkūka ezzūtu šunū-ma : lillikū idāka
```

Realized output (LOB, bi mode):
```
kī ša nišī dadmē ḫubūršina : elīka imtar´ṣu
ublam´-ma libbaka : ana šakān kamāri
ṣalmāt qaq´qadi ana šumutti : šumqutu būl šak´kan
lū kakkū´ka ezzū´tu šunū-ma : lil´likū idāka
```

**WHY:** The worked example makes the algorithm's behavior visible at the line level. It shows that the model can move from lexical material to a constrained phrasal realization built from operations the language can plausibly sustain.

**THUS:** The example is illustrative, not probative. It shows how the algorithm works, not that it is historically correct.

---

## K-169-TTS-As-Practical-Consequence

**Domain:** Article / TTS

**WHAT:** The TTS section is placed after the main argument and before limitations. It states that without a phrasal model, Akkadian text can be transliterated and syllabified but cannot be driven into a speech pipeline. With the realization engine, the situation changes.

**WHY:** TTS is a practical consequence, not evidence for the model. The article is careful to frame it this way. The section is short and does not claim that a finished Akkadian voice exists.

**THUS:** The TTS section shows why solving the connected-speech problem matters beyond the purely descriptive sphere, without overstating what has been achieved.

---

## K-170-Limitations-Statement

**Domain:** Article / Limitations

**WHAT:** The article states six limitations:

1. Timing values are modeled, not recovered. No direct acoustic evidence exists.
2. Comparative table against published rhythm metrics is included but should be treated as illustrative rather than exhaustive.
3. Erra lexical figure (29.2%) and realized figure (18.30%) arise from different counting layers.
4. Corpus is literary and historically restricted (Standard Babylonian, first millennium).
5. Pause model is grounded in comparative reading studies, not recoverable from Akkadian.
6. The rhythm metrics approach to classification is controversial (Arvaniti 2009), and the results should be interpreted with appropriate caution.

**WHY:** These limitations define the article's scale without erasing its contribution. The article should not claim more than the evidence supports.

**THUS:** The limitations section is placed before the conclusion, so the reader has a clear picture of what the article does and does not claim.

---

## K-171-Article-Evolution

**Domain:** Article / Planning / History

**WHAT:** The article has gone through several structural revisions:

**v5 (prep):** Early draft with algorithm-first structure. The metrics demonstration was placed after the algorithm description. The argument was: "here is the algorithm, here is what it produces, here is how to interpret the results."

**v8:** Refined draft with more detailed metrics and timing model sections. Still algorithm-first. Included extensive parameter justifications and implementation details that were later moved to research notes.

**v9:** Restructured to metrics-first. The key architectural change was moving the stress-timed demonstration before the algorithm description. This ensures the reader understands why a realization mechanism is needed before being shown how one works. Added circumflex vowel clarification in Section 2.1. Cleaned up Erra diagnostic to remove confusing word counts. Added GitHub repository links. Expanded bibliography.

**v10:** Addressed reviewer feedback from journal review. Added comparative Table 1 with Moroccan Arabic and other languages. Corrected circumflex vowel footnote. Added explicit limitations section (6 items). Refined Erra diagnostic wording. Added Arvaniti (2009) critique to limitations. Softened mono-mode conclusion. Corrected *iprus* mora count (3→4 morae). Added writing style review corrections.

**v11:** Applied second-round corrections from content review. Refined comparative table formatting. Corrected minor inconsistencies in metrics reporting.

**WHY:** The v9 restructuring was motivated by the recognition that the algorithm-first structure risked making the proposal seem unmotivated. The metrics-first structure mirrors the actual research process: the metrics were computed first, and the algorithm was designed to produce a stress-timed profile. Subsequent revisions (v10, v11) refined the argumentation, added comparative data, and addressed reviewer concerns without altering the core structure.

**THUS:** The current structure (v11) is the most defensible one. The comparative table has been inserted, and the limitations section has been expanded to six items. Future revisions may add more detailed cross-linguistic comparisons and sensitivity analyses.

---

## K-172-Data-Sources

**Domain:** Article / Data / Sources

**WHAT:** The article draws on the following data sources:

**Corpus texts:**
- *Enūma eliš* SB II, IV, VI, VII (Lambert 2013)
- *Erra and Išum* SB I (Cagni 1969)
- *Marduk's Address to the Demons* (Lambert 1999)

**Metrics output files:**
- `outputs/full-corpus/corpus-lob_metrics.txt` — LOB bi mode
- `outputs/full-corpus/corpus-sob_metrics.txt` — SOB bi mode
- `outputs/full-corpus/corpus-mono-lob_metrics.txt` — LOB mono mode
- `outputs/erra-and-ishum/erra_construct_metrics.txt` — Erra LOB bi mode
- `outputs/erra-and-ishum/erra_construct-mono_metrics.txt` — Erra LOB mono mode

**Configuration files:**
- `outputs/full-corpus.yaml` — Full corpus pipeline configuration
- `outputs/erra-and-ishum.yaml` — Erra pipeline configuration

**WHY:** All data is generated by the akkapros toolkit (v3.0.1) and is reproducible. The configuration files document the exact parameters used for each run.

**THUS:** The article's quantitative claims are auditable. Any researcher can reproduce the metrics by running the toolkit with the same configuration.

---

## K-173-References-Used

**Domain:** Article / References

**WHAT:** The article cites the following works:

- Billington 2015 — Geminate glides in Lopit
- Broselow, Chen, and Huffman 1997 — Syllable weight convergence
- Cagni 1969 — *L'epopea di Erra*
- Cutanda et al. 2019 — Rhythmic anisochrony
- Dellwo 2006 — Rhythm and speech rate
- Gibson et al. 2013 — Stop closure duration
- Grabe and Low 2002 — Durational variability and rhythm class
- Greenstein 1984 — Akkadian stress phonology
- Hayes 1995 — Metrical stress theory
- Huehnergard 2011 — Grammar of Akkadian (3rd ed.)
- Lambert 1999 — Marduk's Address to the Demons
- Lambert 2013 — Babylonian Creation Myths
- Meynadier et al. 2019 — Whispered speech
- Morley and Smith 2022 — Vowel duration modeling
- Naeser 1970 — The American Criterion
- Ramus, Nespor, and Mehler 1999 — Correlates of linguistic rhythm
- Streck 2022 — Old Babylonian Grammar
- Sturm and Volin 2023 — Pause durations in poetry reading
- Sugai 2017 — Perception of mora boundaries
- Zellner 1994 — Pauses and temporal structure of speech

**WHY:** The bibliography covers three domains: (1) Akkadian philology (Cagni, Greenstein, Huehnergard, Lambert, Streck), (2) phonetic and phonological theory (Billington, Broselow, Gibson, Hayes, Morley, Naeser, Sugai), and (3) rhythm metrics and speech timing (Cutanda, Dellwo, Grabe & Low, Meynadier, Ramus, Sturm, Zellner).

**THUS:** The bibliography supports the article's interdisciplinary approach, grounding the computational model in both Assyriological and phonetic research.

---

## K-174-Future-Revisions

**Domain:** Article / Planning / Future

**WHAT:** Several items are planned for future revisions:

1. ~~**Comparative table:** Insert a table comparing Akkadian metrics against published values for English, Dutch, French, Spanish, Japanese, and Arabic.~~ **DONE (v10).** Table 1 now includes Akkadian alongside English, German, Dutch, French, Spanish, Italian, Japanese, Moroccan Arabic, and Modern Standard Arabic.
2. **Sensitivity analysis:** Test the model's sensitivity to parameter variations (e.g., different CVC reference values, different accentuation distribution policies).
3. **Expanded corpus:** Include additional Standard Babylonian texts to increase statistical power.
4. **Diachronic comparison:** Test the model on Old Babylonian texts to see if the rhythm profile changes across periods.
5. **Perceptual evaluation:** Design a listening experiment to test whether the realized output sounds more natural than a flat lexical reading.

**WHY:** The article establishes the framework and the core argument. These revisions would strengthen the empirical foundation and extend the argument's scope.

**THUS:** The current article is a foundation, not a final statement. Future work will refine and extend the analysis.
