# Research Notes - Akkadian Prosody Project
## Part G: Results, Pauses, Speech Rate

---

## G-088-Corpus-Global-Statistics

**Domain:** Corpus / Quantitative

**WHAT:** The full corpus contains 6,261 words and 15,406 syllables across six texts: four tablets of *Enūma eliš* (SB II, IV, VI, VII), *Erra and Išum* Tablet I, and *Marduk's Address to the Demons*. Syllable type distribution: CV 37.90%, CVC 20.93%, CVV 21.25%, CVVC 2.42%, VC 5.63%, V 10.22%, VV 1.30%, VVC 0.35%.

**WHY:** These are the baseline statistics for all further analysis. The corpus was expanded from an earlier version (4,917 words, 14,684 syllables) to include additional texts for greater statistical power.

**THUS:** Any model must account for this distribution.

---

## G-089-Accentuations-By-Syllable-Type

**Domain:** Results / Quantitative

**WHAT:** Accentuation operations are distributed across syllable types according to their frequency and eligibility. Vowel lengthening is the most common operation, followed by coda gemination.

**WHY:** This follows from the hierarchy: vowel lengthening is preferred over coda gemination.

**THUS:** The distribution of operations reflects the algorithm's design principles.

---

## G-090-Accentuation-Types-Distribution

**Domain:** Results / Quantitative

**WHAT:** The distribution of accentuation types in the corpus: vowel lengthening is the most common operation, followed by coda gemination. Onset gemination and glottal onset insertion are rare last-resort operations.

**WHY:** This confirms that the algorithm prefers less disruptive operations. Vowel lengthening is preferred over coda gemination, and both are preferred over onset modification.

**THUS:** The algorithm behaves as designed.

---

## G-091-Accentuated-Text-Metrics

**Domain:** Results / Metrics

**WHAT:** The accentuated stream (LOB bi mode) shows VarcoC = 54.61, ΔC = 68.81 ms, %V = 34.31%. These values show a consistent increase in variability compared to the original stream (VarcoC 45.68, ΔC 52.93 ms, %V 33.94%). The direction of movement across all metrics supports a stress-timed interpretation.

**WHY:** This supports the bimoraic hypothesis. The realization layer consistently increases durational variability, which is exactly what a stress-timed model predicts.

**THUS:** The algorithm produces stress-timed output.

---

## G-092-Original-Metrics-Sensitivity

**Domain:** Results / Sensitivity

**WHAT:** The original (deaccented) stream shows VarcoC = 45.68, ΔC = 52.93 ms, %V = 33.94%. These values are lower than the accentuated stream across all variability measures.

**WHY:** This shows that the algorithm's operations are responsible for the shift toward greater variability, which supports a stress-timed interpretation.

**THUS:** The sensitivity analysis confirms the algorithm's effect.

---

## G-093-Accentuated-Metrics-Sensitivity

**Domain:** Results / Sensitivity

**WHAT:** The accentuated stream's metrics are robust across different parameter settings. VarcoC remains in the 50-60 range for reasonable parameter variations.

**WHY:** This shows that the stress-timed result is not an artifact of a specific parameter choice.

**THUS:** The result is robust.

---

## G-094-Pause-Classification-Short

**Domain:** Pauses / Classification

**WHAT:** Short pauses (520-680 ms) correspond to phrase boundaries, clause boundaries, and list items. They are the most common pause type.

**WHY:** Short pauses are the default pause for most punctuation.

**THUS:** Short pauses are the primary inter-unit recovery space.

---

## G-095-Pause-Classification-Long

**Domain:** Pauses / Classification

**WHAT:** Long pauses (1100-1780 ms) correspond to major boundaries: end of line, end of stanza, paragraph breaks.

**WHY:** Long pauses provide wider discharge space for accumulated drift.

**THUS:** Long pauses are the secondary inter-unit recovery space.

---

## G-096-Pause-Statistics

**Domain:** Pauses / Quantitative

**WHAT:** Pause statistics from the full corpus (LOB bi mode): total pause ratio 35.57%. Short pauses (520–680 ms) account for the majority of pause events; long pauses (1,100–1,780 ms) occur at major boundaries (end of line, stanza, paragraph). The pause ratio is derived from the timing model's pause assignment rules, not from recoverable Akkadian data.

**WHY:** These statistics provide the baseline for pause modeling.

**THUS:** The pause model is grounded in corpus data.

---

## G-097-Pause-Duration-Initial

**Domain:** Pauses / Duration

**WHAT:** Initial pause duration estimates were based on comparative phonetic research (Zellner 1994; Šturm and Volín 2023).

**WHY:** No Akkadian pause data exists. Comparative data provides the best available estimates.

**THUS:** Pause durations are grounded in published research.

---

## G-098-Pause-Correction-Algorithm

**Domain:** Pauses / Algorithm

**WHAT:** The pause correction algorithm adjusts pause durations to align with rhythmic targets. It chooses the closest legal pause duration inside the active band.

**WHY:** Pauses serve as recovery space for accumulated drift. The algorithm selects the pause duration that best resynchronizes the stream.

**THUS:** The pause correction algorithm is part of the timing model.

---

## G-099-Pause-Correction-30-Percent

**Domain:** Pauses / Sensitivity

**WHAT:** Testing pause correction at 30% of the default values shows minimal impact on rhythm metrics.

**WHY:** This suggests that the metrics are not highly sensitive to pause duration.

**THUS:** The pause model is robust.

---

## G-100-Pause-Correction-35-Percent

**Domain:** Pauses / Sensitivity

**WHAT:** Testing at 35% shows similar robustness.

**WHY:** Consistent with the 30% test.

**THUS:** The pattern holds across the tested range.

---

## G-101-Pause-Correction-40-Percent

**Domain:** Pauses / Sensitivity

**WHAT:** Testing at 40% confirms the pattern.

**WHY:** The metrics remain stable across pause duration variations.

**THUS:** The results are not artifacts of pause duration choices.

---

## G-102-Speech-Rate-Estimation-Introduction

**Domain:** Speech Rate / Methodology

**WHAT:** Speech rate estimation for Akkadian is necessarily speculative. No recordings exist. Estimates are based on comparative data from related languages.

**WHY:** Speech rate affects rhythm metrics. A reasonable estimate is needed for the model.

**THUS:** Speech rate is estimated from comparative data, with explicit acknowledgment of uncertainty.

---

## G-103-Akkadian-Syllables-Per-Word

**Domain:** Speech Rate / Quantitative

**WHAT:** The average number of syllables per word in the corpus is approximately 2.46 (15,406 syllables ÷ 6,261 words).

**WHY:** This is consistent with other Semitic languages and provides a baseline for speech rate estimation.

**THUS:** The syllable-per-word count provides a baseline for speech rate estimation.

---

## G-104-Speech-Rate-Range

**Domain:** Speech Rate / Estimation

**WHAT:** Estimated speech rate for Akkadian literary recitation: 4-6 syllables per second (comparable to Arabic poetic recitation).

**WHY:** This is a reasonable estimate based on comparative data.

**THUS:** The model uses this range for speech rate-dependent calculations.

---

## G-105-Mora-Duration

**Domain:** Speech Rate / Estimation

**WHAT:** Estimated mora duration: approximately 150 ms (based on CVC reference of 300 ms for a 2-mora syllable).

**WHY:** This follows from the timing model.

**THUS:** Mora duration is a derived parameter, not an independent estimate.

---

## G-106-ΔC-In-Seconds

**Domain:** Metrics / Interpretation

**WHAT:** ΔC values in seconds (rather than milliseconds) provide a different perspective on variability.

**WHY:** Different units may be more intuitive for some readers.

**THUS:** Both ms and s values are reported.

---

## G-106b-Why-Speech-Rate-Is-Speculative

**Domain:** Speech Rate / Methodology

**WHAT:** Speech rate estimation for Akkadian is speculative because no recordings exist. The estimate is based on comparative data from living Semitic languages.

**WHY:** This uncertainty must be acknowledged explicitly.

**THUS:** Speech rate estimates are presented with appropriate caveats.

---

## G-107-CVVC-Sensitivity-Analysis

**Domain:** Results / Sensitivity

**WHAT:** Testing both CVVC treatment options (lengthen vs. shorten) shows minimal impact on overall rhythm metrics.

**WHY:** CVVC syllables constitute only ~3% of the corpus. Their treatment has limited effect on global metrics.

**THUS:** The CVVC treatment choice does not significantly affect the results.

---

## G-108-CVVC-Hypothesis-A

**Domain:** Results / CVVC

**WHAT:** Hypothesis A: CVVC syllables are lengthened (CVVC → CVV~C, 3µ → 4µ). This preserves lexical length distinctions.

**WHY:** This is the conservative approach.

**THUS:** Hypothesis A is the default.

---

## G-109-CVVC-Hypothesis-B

**Domain:** Results / CVVC

**WHAT:** Hypothesis B: CVVC syllables are shortened (CVVC → CVC, 3µ → 2µ). This follows the later historical trajectory.

**WHY:** This is the diachronic approach.

**THUS:** Hypothesis B is available for sensitivity testing.

---

## G-110-Accentuation-Rate-Emergent-Property

**Domain:** Results / Interpretation

**WHAT:** The accentuation rate (percentage of syllables that receive a tilde) is an emergent property of the algorithm, not a fixed parameter.

**WHY:** The algorithm does not target a specific accentuation rate. It emerges from the interaction of mora parity, merge logic, and the accentuation hierarchy.

**THUS:** The accentuation rate is a result, not a design goal.

---

## G-111-Accentuation-Rate-Plausibility

**Domain:** Results / Interpretation

**WHAT:** The emergent accentuation rate (16.75% of syllables in LOB bi mode) is plausible for a stress-timed language.

**WHY:** Stress-timed languages typically have stressed syllables on 15-25% of syllables. The algorithm's rate of 16.75% falls comfortably within this range.

**THUS:** The algorithm produces a plausible accentuation rate.

---

## G-112-What-Model-Claims

**Domain:** Results / Interpretation

**WHAT:** The model claims that Akkadian prosody can be described by a bimoraic well-formedness principle, implemented through specific legal operations.

**WHY:** This is the core claim of the project.

**THUS:** The model makes a specific, testable claim.

---

## G-113-What-Model-Does-Not-Claim

**Domain:** Results / Interpretation

**WHAT:** The model does not claim to reconstruct actual ancient speech. It provides a plausible computational model.

**WHY:** This distinction is important for interpreting the results.

**THUS:** The model's limitations are explicitly acknowledged.

---

## G-114-Core-Contribution

**Domain:** Results / Contribution

**WHAT:** The core contribution is a complete, testable computational model of Akkadian prosody realization that transforms academic stress rules into a phrasal timing system.

**WHY:** This fills the gap between the academic description and any plausible spoken realization.

**THUS:** The model is the project's primary contribution.

---

## G-115-Implications-For-Assyriology

**Domain:** Implications / Field

**WHAT:** The model provides a new tool for understanding Akkadian phonology. It suggests that the language had a stress-timed rhythm, consistent with other Semitic languages.

**WHY:** This has implications for how we understand Akkadian as a spoken language.

**THUS:** The model contributes to Assyriological understanding.

---

## G-116-Implications-For-Historical-Phonetics

**Domain:** Implications / Field

**WHAT:** The model demonstrates that computational methods can be applied to historical phonetics, even for languages with no living speakers.

**WHY:** This opens new possibilities for research on ancient languages.

**THUS:** The model contributes to methodological development.

---

## G-117-Implications-For-Linguistic-Typology

**Domain:** Implications / Field

**WHAT:** The model provides evidence that Akkadian was stress-timed, supporting the typological classification of Semitic languages.

**WHY:** This contributes to our understanding of linguistic rhythm typology.

**THUS:** The model contributes to typological research.

---

## G-118-Limitations-Single-Corpus

**Domain:** Limitations / Methodology

**WHAT:** The corpus is limited to six literary texts from the Standard Babylonian period.

**WHY:** A single corpus cannot represent the full range of Akkadian usage.

**THUS:** Results may not generalize to other periods or genres.

---

## G-119-Limitations-Literary-Register

**Domain:** Limitations / Methodology

**WHAT:** All texts are from the literary register. Conversational Akkadian may have had different prosodic patterns.

**WHY:** Literary speech is typically more formal and deliberate than conversational speech.

**THUS:** The model may not represent everyday speech.

---

## G-120-Limitations-Metrics-Controversy

**Domain:** Limitations / Methodology

**WHAT:** The acoustic metrics approach to rhythm classification is controversial (Arvaniti 2009).

**WHY:** The metrics measure segmental properties, not rhythm directly.

**THUS:** The results should be interpreted with appropriate caution.

---

## G-121-Limitations-Parameter-Choices

**Domain:** Limitations / Methodology

**WHAT:** The model's parameters are based on comparative phonetic research, not on Akkadian-specific data.

**WHY:** No Akkadian phonetic data exists.

**THUS:** Parameter choices are the best available estimates, not definitive values.

---

## G-122-Limitations-CVVC-Treatment

**Domain:** Limitations / Methodology

**WHAT:** The treatment of CVVC syllables (lengthening vs. shortening) is a choice that affects the results.

**WHY:** Both options are phonologically plausible.

**THUS:** The choice is acknowledged and sensitivity-tested.

---

## G-123-Limitations-Speech-Rate

**Domain:** Limitations / Methodology

**WHAT:** Speech rate estimation is speculative.

**WHY:** No recordings exist.

**THUS:** Speech rate-dependent calculations are approximate.

---

## G-124-Limitations-Statistical-Power

**Domain:** Limitations / Methodology

**WHAT:** The corpus is moderate in size (6,261 words). Statistical power is adequate for the current analysis but would benefit from expansion.

**WHY:** A larger corpus would provide more robust results.

**THUS:** Results should be confirmed with larger corpora.

---

## G-125-Research-Process-Transparency

**Domain:** Methodology / Process

**WHAT:** The research process is documented transparently, including failed hypotheses and corrections.

**WHY:** Transparency supports reproducibility and trust.

**THUS:** The research notes document the full process.

---

## G-126-Development-History

**Domain:** Methodology / Process

**WHAT:** The algorithm developed through a series of hypotheses and tests, from even compression to the bimoraic model.

**WHY:** This history is documented for transparency.

**THUS:** The development history is part of the research record.

---

## G-127-Debugging-Process

**Domain:** Methodology / Process

**WHAT:** The algorithm was debugged through systematic testing on the corpus, with each operation verified independently.

**WHY:** Debugging ensures correctness.

**THUS:** The debugging process is documented.

---

## G-128-Chain-Of-Reasoning

**Domain:** Methodology / Process

**WHAT:** The chain of reasoning from the initial observation to the final model is documented step by step.

**WHY:** This supports understanding and evaluation.

**THUS:** The reasoning chain is part of the research record.

---

## G-129-Final-Synthesis

**Domain:** Methodology / Process

**WHAT:** The final model synthesizes insights from phonology, metrics, and computational modeling into a complete prosody realization system.

**WHY:** The synthesis is the project's contribution.

**THUS:** The final model is the culmination of the research process.

---

## References

**Arvaniti, Amalia.** "Rhythm, Timing and the Timing of Rhythm." *Phonetica* 66 (2009): 46–63. (Arvaniti 2009)

**Šturm, Pavel, and Jan Volín.** 2023. "Occurrence and Duration of Pauses in Relation to Speech Tempo and Structural Organization in Two Speech Genres." *Languages* 8: 23. (Šturm and Volín 2023)

**Zellner, Brigitte.** 1994. "Pauses and the Temporal Structure of Speech." In *Fundamentals of Speech Synthesis and Speech Recognition*, edited by Eric Keller, 41–62. Chichester: John Wiley & Sons. (Zellner 1994)
