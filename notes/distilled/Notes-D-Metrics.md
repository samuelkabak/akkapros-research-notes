# Research Notes - Akkadian Prosody Project
## Part D: Rhythm Metrics

---

## D-031-Acoustic-Metrics-Introduction

**Domain:** Metrics / Methodology

**WHAT:** Acoustic metrics (%V, ΔC, VarcoC, nPVI-V, rPVI-C) are standard tools for classifying speech rhythm typology. They measure the variability of vocalic and consonantal intervals in speech (Ramus et al. 1999; Grabe and Low 2002).

**WHY:** These metrics provide a quantitative basis for comparing Akkadian to living languages. They are the standard methodology in rhythm research.

**THUS:** The project uses these metrics to test whether the algorithm's output falls within the stress-timed range.

---

## D-032-%V-Definition

**Domain:** Metrics / Definitions

**WHAT:** %V is the proportion of total utterance time occupied by vocalic intervals. Formula: %V = (sum of vocalic interval durations / total duration) × 100.

**WHY:** %V is a basic measure of rhythm. Stress-timed languages typically have lower %V (around 40-43%) than syllable-timed languages (around 45-51%).

**THUS:** %V provides a first diagnostic for rhythm classification.

---

## D-033-ΔC-Definition

**Domain:** Metrics / Definitions

**WHAT:** ΔC is the standard deviation of consonantal interval durations. It measures how much consonantal intervals vary in length.

**WHY:** Stress-timed languages have higher ΔC because consonant clusters create more variable intervals. Syllable-timed languages have lower ΔC.

**THUS:** ΔC is a key diagnostic. Higher values suggest stress-timing.

---

## D-034-VarcoC-Introduction

**Domain:** Metrics / Definitions

**WHAT:** VarcoC normalizes ΔC by dividing by mean consonantal duration and multiplying by 100. This removes the effect of speech rate.

**WHY:** Raw ΔC is sensitive to speech rate. VarcoC allows comparison across different speaking rates.

**THUS:** VarcoC is the preferred metric for cross-linguistic comparison.

---

## D-035-Reference-Values-Stress-Timed

**Domain:** Metrics / Reference

**WHAT:** Stress-timed languages (English, German, Dutch, Arabic) typically show: %V ≈ 40-43%, ΔC ≈ 60-80 ms, VarcoC ≈ 50-70 (Ramus et al. 1999; Grabe and Low 2002). The article's Table 1 provides specific published values for individual languages: English VarcoC ~70.0, German ~69.0, Dutch ~67.0, Moroccan Arabic ~55.3, Modern Standard Arabic ~49.0.

**WHY:** These values provide the reference range for classifying Akkadian. The broad ranges and specific values are complementary: the ranges establish the general typological space, while the specific values in Table 1 enable direct comparison.

**THUS:** If the algorithm's output falls within this range, it supports the stress-timed hypothesis.

---

## D-036-Reference-Values-Syllable-Timed

**Domain:** Metrics / Reference

**WHAT:** Syllable-timed languages (French, Spanish, Italian) typically show: %V ≈ 45-51%, ΔC ≈ 40-60 ms, VarcoC ≈ 30-50 (Ramus et al. 1999; Grabe and Low 2002).

**WHY:** These values provide the contrasting range.

**THUS:** The algorithm's output should be clearly distinguishable from this range if Akkadian is stress-timed.

---

## D-037-Reference-Values-Mora-Timed

**Domain:** Metrics / Reference

**WHAT:** Mora-timed languages (Japanese) typically show: %V ≈ 40-45%, ΔC ≈ 30-50 ms, VarcoC ≈ 20-40 (Ramus et al. 1999; Grabe and Low 2002).

**WHY:** These values provide a third reference point.

**THUS:** The algorithm's output should be distinguishable from this range as well.

---

## D-038-Arabic-Rhythm-Research

**Domain:** Metrics / Comparative

**WHAT:** Arabic is classified as stress-timed, but internal variation exists across dialects. Western dialects (Moroccan) sound more "staccato" due to vowel deletion increasing consonant clustering. Eastern dialects (Syrian) have a more open rhythm, approaching French in vocalic patterning (Hamdi et al. 2004).

**WHY:** This internal variation strengthens the argument that Semitic languages have a natural tendency toward stress-timing without being monolithic about it. The dialectal range provides a more nuanced comparative picture than a single reference value.

**THUS:** Akkadian's rhythm may fall within the Arabic range, but the comparison must acknowledge dialectal variation. The article's treatment simplifies this picture appropriately for its scope.

---

## D-038b-Rhythm-as-Continuum

**Domain:** Metrics / Theory

**WHAT:** Speech rhythm is not a categorical typology but a continuum. Languages can show mixed characteristics (Ramus et al. 1999; Arvaniti 2009).

**WHY:** The stress/syllable/mora classification is a useful heuristic, not a rigid taxonomy.

**THUS:** The project should report where Akkadian falls on the continuum, not force it into a category.

---

## D-039-Arvaniti-Critique

**Domain:** Metrics / Methodology

**WHAT:** Arvaniti (2009) critiques the acoustic metrics approach. She argues that %V, ΔC, and VarcoC do not directly measure rhythm but rather segmental properties that correlate with rhythm.

**WHY:** This critique is valid but does not invalidate the metrics. They remain useful as comparative tools.

**THUS:** The project acknowledges this limitation. The metrics are used as comparative diagnostics, not as direct measures of rhythm.

---

## D-040-Metrics-To-Text-Assumptions

**Domain:** Metrics / Methodology

**WHAT:** Applying acoustic metrics to ancient texts requires assumptions about speech rate, pause duration, and segmental timing. These assumptions are explicit in the model.

**WHY:** Unlike living languages, we cannot record Akkadian speakers. The metrics are computed from the model's output, not from acoustic recordings.

**THUS:** The metrics results are model-dependent. They show what the model predicts, not what was actually spoken. This limitation is acknowledged.

---

## D-041-Initial-Metrics-Results-Preliminary

**Domain:** Metrics / Results

**WHAT:** Initial metrics from the Erra corpus (preliminary, before full corpus analysis) showed promising results. The accentuated stream showed higher VarcoC than the original stream, suggesting that the algorithm increases rhythmic variability.

**WHY:** These preliminary results motivated the full corpus analysis.

**THUS:** The initial results were encouraging but required confirmation from the full corpus.

---

## D-042-Initial-Metrics-Results-Final

**Domain:** Metrics / Results

**WHAT:** Final metrics from the full corpus confirmed the preliminary findings. The accentuated stream consistently shows higher VarcoC and ΔC than the original stream.

**WHY:** This confirms that the algorithm's operations (vowel lengthening, coda gemination) increase consonantal interval variability, moving the output toward the stress-timed range.

**THUS:** The algorithm produces the expected effect on rhythm metrics.

---

## D-043-Confidence-Intervals-Not-Relevant

**Domain:** Metrics / Methodology

**WHAT:** Confidence intervals are not the appropriate uncertainty measure for this model. The model is deterministic, not stochastic. Parameter uncertainty matters more than sampling uncertainty.

**WHY:** The model produces a single output for a given input. Variability comes from parameter choices, not from random sampling.

**THUS:** Sensitivity analysis (testing different parameter values) is more informative than confidence intervals.

---

## D-044-VarcoC-Interpretation

**Domain:** Metrics / Interpretation

**WHAT:** VarcoC values for the accentuated stream fall in the 50-60 range, which is characteristic of stress-timed languages. The original stream shows lower values (40-50), closer to syllable-timed languages.

**WHY:** This suggests that the algorithm's operations push Akkadian from a more syllable-timed baseline toward a stress-timed realization.

**THUS:** The VarcoC results support the stress-timed hypothesis.

---

## D-045-Comparison-To-English

**Domain:** Metrics / Comparative

**WHAT:** English typically shows VarcoC ≈ 50-70. The accentuated Akkadian stream shows VarcoC ≈ 50-60, placing it at the lower end of the English range.

**WHY:** This is a reasonable position for a literary register. Literary speech is typically less variable than conversational speech.

**THUS:** The comparison to English supports the stress-timed interpretation while acknowledging register differences.

---

## D-046-The-Paradox

**Domain:** Metrics / Interpretation

**WHAT:** The original (deaccented) stream shows metrics in the syllable-timed range. The accentuated stream shows metrics in the stress-timed range. This creates a paradox: which one represents Akkadian?

**WHY:** The original stream represents the lexical baseline without prosodic operations. The accentuated stream represents the realized speech with prosodic adjustments. The paradox is resolved by recognizing that both are part of the same system: the baseline provides the raw material, and the operations transform it into stress-timed speech.

**THUS:** The paradox is not a contradiction but a description of the transformation that the algorithm performs.

---

## D-047-What-Academic-Model-Lacks

**Domain:** Academic Model / Gap

**WHAT:** The academic model (Huehnergard 2011, Streck 2022) describes stress placement but not phrasal timing. It does not explain how words are grouped into prosodic units or how prominence is realized in connected speech.

**WHY:** This gap is the motivation for the project. The academic model is incomplete for describing spoken language.

**THUS:** The project fills this gap by providing a computational model of phrasal prosody.

---

## D-048-The-Gap-This-Project-Fills

**Domain:** Project / Contribution

**WHAT:** The project provides a computational model that transforms the academic stress rules into a complete prosody realization algorithm. It adds merge logic, accentuation operations, and a timing model.

**WHY:** This fills the gap between the academic description and any plausible spoken realization.

**THUS:** The project's contribution is a complete, testable model of Akkadian prosody realization.

---

## References

**Arvaniti, Amalia.** "Rhythm, Timing and the Timing of Rhythm." *Phonetica* 66 (2009): 46–63. (Arvaniti 2009)

**Grabe, Esther, and Ee Ling Low.** "Durational Variability in Speech and the Rhythm Class Hypothesis." In *Papers in Laboratory Phonology 7*, edited by Carlos Gussenhoven and Natasha Warner, 515–546. Berlin: Mouton de Gruyter, 2002. (Grabe and Low 2002)

**Hamdi, Rym, et al.** "Durational Variability in Arabic: A Cross-Dialectal Study." *Proceedings of Speech Prosody 2004*, Nara, Japan. (Hamdi et al. 2004)

**Huehnergard, John.** ***A Grammar of Akkadian***. 3rd edition. Winona Lake, IN: Eisenbrauns, 2011. (Huehnergard 2011)

**Ramus, Franck, Marina Nespor, and Jacques Mehler.** "Correlates of Linguistic Rhythm in the Speech Signal." *Cognition* 73 (1999): 265–292. (Ramus et al. 1999)

**Streck, Michael P.** ***Altbabylonisches Lehrbuch***. 4th edition. Wiesbaden: Harrassowitz, 2022. (Streck 2022)
