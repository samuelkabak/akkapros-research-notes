# Research Notes - Akkadian Prosody Project
## Part L: Parameter Justifications

---

## L-200-Parameter-Justification-Introduction

**Domain:** Parameters / Methodology

**WHAT:** This section documents the empirical grounding for each parameter in the timing model. Each parameter is justified by reference to published phonetic, psycholinguistic, or perceptual research.

**WHY:** The timing model's parameters are not arbitrary. They are conservative choices within empirically attested ranges. This documentation provides the audit trail for each choice.

**THUS:** The parameter justifications support the model's claim to empirical grounding.

---

## L-201-Parameter-Supersession-Note

**Domain:** Parameters / Methodology

**WHAT:** The parameter justifications in this section supersede the earlier, less rigorous justifications in notes 200–230 of the original monolithic research notes. Those earlier notes were written during the exploratory phase of the project, before the timing model was fully developed. They contain preliminary estimates and speculative values that have since been refined.

**WHY:** The project's parameter values evolved as the timing model matured. The earlier notes reflect an earlier stage of understanding. The current notes (231–250) represent the final, empirically grounded values.

**THUS:** For any research use, cite the parameter values and justifications from notes 231–250, not the earlier notes 200–230.

---

## L-202-CVC-Reference-300ms

**Domain:** Parameters / Timing Model

**WHAT:** The CVC reference value of 300 ms is the central timing parameter. It represents the nominal duration of a heavy syllable (CVC, CVV) in the model.

**WHY:** The value 300 ms is grounded in converging evidence:

1. **Compositional interval (286–306 ms):** Sugai (2017) reports that the mora in Japanese has an intrinsic duration of approximately 100 ms. For a bimoraic syllable (CVC or CVV), this gives 2 × 100 = 200 ms. However, the CVC syllable includes a coda consonant that adds closure time. Kozasa (2000) reports that Japanese CVC syllables average approximately 286 ms. Yungdo Yun (1998) reports Korean CVC durations of approximately 306 ms. The range 286–306 ms provides the primary grounding.

2. **Short-pause half-range (300–340 ms):** The short-pause band (600–680 ms) represents the time needed for two prosodic units plus the pause between them. Half of this range (300–340 ms) gives the per-unit duration. The overlap with the compositional interval (300–306 ms) permits a conservative choice.

3. **Conservative selection:** The value 300 ms is chosen as the conservative lower bound of the overlapping range. It is the simplest value that falls within both the compositional interval and the short-pause half-range.

**THUS:** The CVC reference of 300 ms is grounded in converging experimental evidence from three independent sources. It represents a conservative choice within the empirically attested range.

---

## L-203-Basic-Accentuation-Lengthening-50ms

**Domain:** Parameters / Timing Model

**WHAT:** The basic_accentuation_lengthening parameter (50 ms) is the increment added to accentuated syllables in mono mode. In bi mode, the increment is 0.5 × cvc_reference = 150 ms.

**WHY:** The value 50 ms is grounded in three independent lines of evidence:

1. **Just Noticeable Difference (JND) for duration (Cutanda et al. 2019):** The JND for duration discrimination in the sub-second range is approximately 5-10% of the base duration. For a 300 ms base, this gives 15-30 ms. The 50 ms value exceeds this threshold, ensuring perceptual salience.

2. **Minimum perceptible lengthening (Meynadier et al. 2019):** Studies of whispered fricative perception show that listeners can detect duration differences of approximately 40-60 ms. The 50 ms value falls within this range.

3. **Pause perception threshold (Zellner 1994):** The minimum pause duration that listeners perceive as a break is approximately 200-250 ms. The 50 ms increment is well below this threshold, ensuring that accentuation is perceived as prominence, not as a pause.

**THUS:** The 50 ms value is not arbitrary. It is grounded in converging evidence from duration discrimination, phoneme perception, and pause perception research.

---

## L-204-Drift-Tolerance-19ms

**Domain:** Parameters / Timing Model

**WHAT:** The drift_tolerance parameter (19 ms) defines how much cumulative timing mismatch is tolerated before forced resynchronization.

**WHY:** The value 19 ms is derived from the CVC reference:

* CVC reference = 300 ms
* One mora = 150 ms (0.5 × CVC reference)
* Drift tolerance = 19 ms ≈ 150 / 8

The division by 8 is motivated by the observation that timing mismatch in natural speech is typically corrected within 1-2 syllables. The value 19 ms ensures that drift is corrected before it reaches perceptual significance (approximately 20-30 ms, per Cutanda et al. 2019).

**THUS:** The drift tolerance is a principled fraction of the mora duration, ensuring that timing mismatch is corrected before it becomes perceptible.

---

## L-205-Consonant-Onset-Anchors

**Domain:** Parameters / Consonants

**WHAT:** Consonant onset durations: closure 70 ms, fricative 90 ms, sonorant 60 ms.

**WHY:** These values are based on cross-linguistic phonetic research (Möbius 2004; Gibson et al. 2013). Onset consonants are typically shorter than coda consonants because they are released into the following vowel. The values represent conservative estimates within the attested range for each class.

**THUS:** Onset anchors are grounded in cross-linguistic phonetic data.

---

## L-206-Consonant-Coda-Anchors

**Domain:** Parameters / Consonants

**WHAT:** Consonant coda durations: closure 100 ms, fricative 120 ms, sonorant 80 ms.

**WHY:** Coda consonants are typically longer than onset consonants because they are unreleased or have longer closure phases. The values are based on cross-linguistic data (Möbius 2004; Gibson et al. 2013).

**THUS:** Coda anchors are grounded in cross-linguistic phonetic data.

---

## L-207-Consonant-Coda-Final-Anchors

**Domain:** Parameters / Consonants

**WHAT:** Consonant coda_final durations: closure 130 ms, fricative 150 ms, sonorant 100 ms.

**WHY:** Pre-pausal codas are typically longer than non-final codas due to final lengthening (Gao and Birkholz 2014). The values represent a 30% increase over the standard coda values.

**THUS:** Coda_final anchors account for pre-pausal lengthening.

---

## L-208-Consonant-Geminate-Anchors

**Domain:** Parameters / Consonants

**WHAT:** Consonant geminate durations: closure 180 ms, fricative 200 ms, sonorant 150 ms.

**WHY:** Geminate consonants are approximately 1.5-2.5 times longer than singletons cross-linguistically (Billington 2015; Möbius 2004). The values represent conservative estimates within this range.

**THUS:** Geminate anchors are grounded in cross-linguistic geminate duration research.

---

## L-209-Consonant-Geminate-Coda-Ratio

**Domain:** Parameters / Consonants

**WHAT:** The geminate_coda_ratio (0.6) determines the coda share of geminate duration in corrective mode.

**WHY:** In corrective mode, the geminate duration is split between coda and onset. The ratio 0.6 means 60% of the geminate duration is assigned to the coda and 40% to the onset. This reflects the observation that the coda phase of a geminate is typically longer than the onset phase (Möbius 2004).

**THUS:** The geminate_coda_ratio reflects the asymmetric duration distribution within geminate consonants.

---

## L-210-Consonant-Perception-Limits

**Domain:** Parameters / Consonants

**WHAT:** Perception limits for consonants define the minimum geminate duration (geminate_min) and maximum gemination duration (gemination_max) for each class:

* Closure: geminate_min 145 ms, gemination_max 260 ms
* Fricative: geminate_min 160 ms, gemination_max 280 ms
* Sonorant: geminate_min 120 ms, gemination_max 230 ms

**WHY:** These limits are based on perceptual research on geminate/singleton discrimination (Billington 2015; Möbius 2004). The geminate_min values represent the minimum duration at which a consonant is perceived as geminate. The gemination_max values represent the maximum duration before the consonant sounds unnatural or distorted.

**THUS:** Perception limits ensure that the model produces perceptually plausible consonant durations.

---

## L-211-Vowel-Short-110ms

**Domain:** Parameters / Vowels

**WHAT:** Short vowel duration: 110 ms.

**WHY:** Cross-linguistic research shows that short vowels average approximately 80-120 ms in natural speech (Tauberer and Evanini 2009; Naeser 1970). The value 110 ms is a conservative estimate within this range.

**THUS:** The short vowel anchor is grounded in cross-linguistic phonetic data.

---

## L-212-Vowel-Long-160ms

**Domain:** Parameters / Vowels

**WHAT:** Long vowel duration: 160 ms.

**WHY:** Long vowels are approximately 1.3-1.8 times longer than short vowels cross-linguistically (Tauberer and Evanini 2009). The ratio 160/110 ≈ 1.45 falls within this range.

**THUS:** The long vowel anchor maintains a phonologically realistic length contrast.

---

## L-213-Vowel-Very-Long-260ms

**Domain:** Parameters / Vowels

**WHAT:** Very long vowel duration: 260 ms.

**WHY:** Very long vowels (circumflex vowels from contraction) are approximately 1.6 times longer than long vowels. The value 260 ms represents the upper end of the long vowel range, appropriate for contracted vowels that may have been phonetically extra-long.

**THUS:** The very long vowel anchor accounts for contracted vowels with potentially extra-long duration.

---

## L-214-Vowel-Short-Final-130ms

**Domain:** Parameters / Vowels

**WHAT:** Short vowel final duration (pre-pausal): 130 ms.

**WHY:** Pre-pausal vowels are typically longer than non-final vowels due to final lengthening (Gao and Birkholz 2014). The value represents an 18% increase over the standard short vowel duration.

**THUS:** The short_final anchor accounts for pre-pausal lengthening.

---

## L-215-Vowel-Long-Final-190ms

**Domain:** Parameters / Vowels

**WHAT:** Long vowel final duration (pre-pausal): 190 ms.

**WHY:** Same rationale as short_final: pre-pausal lengthening applies to long vowels as well. The value represents a 19% increase over the standard long vowel duration.

**THUS:** The long_final anchor accounts for pre-pausal lengthening.

---

## L-216-Vowel-Perception-Limits

**Domain:** Parameters / Vowels

**WHAT:** Perception limits for vowels:

* short_min: 70 ms (minimum duration for a short vowel to be perceived as a vowel)
* long_min: 130 ms (minimum duration for a long vowel to be perceived as long)
* very_long_min: 200 ms (minimum duration for a very long vowel)
* elongation_max: 310 ms (maximum duration before the vowel sounds unnatural)

**WHY:** These limits are based on perceptual research on vowel duration discrimination (Tauberer and Evanini 2009; Naeser 1970). The elongation_max value is constrained by the segmental_ceiling (310 ms).

**THUS:** Perception limits ensure that the model produces perceptually plausible vowel durations.

---

## L-217-Pause-Short-Band

**Domain:** Parameters / Pauses

**WHAT:** Short pause band: min 520 ms, max 680 ms.

**WHY:** The short pause band is based on research on pause duration in read speech (Šturm and Volín 2023; Zellner 1994). Short pauses (phrase-internal) typically range from 400-700 ms. The band 520-680 ms represents a conservative range within this interval.

**THUS:** The short pause band is grounded in pause duration research.

---

## L-218-Pause-Long-Band

**Domain:** Parameters / Pauses

**WHAT:** Long pause band: min 1100 ms, max 1780 ms.

**WHY:** Long pauses (between major units) typically range from 1000-2000 ms (Šturm and Volín 2023; Zellner 1994). The band 1100-1780 ms represents a conservative range within this interval.

**THUS:** The long pause band is grounded in pause duration research.

---

## L-219-Pause-Resync-Band

**Domain:** Parameters / Pauses

**WHAT:** Resync pause band: min 100 ms, max 200 ms.

**WHY:** Resync pauses are short pauses inserted by the drift mechanism to discharge accumulated timing mismatch. The band 100-200 ms is below the perceptual threshold for a break (approximately 200-250 ms, per Zellner 1994), ensuring that resync pauses are not perceived as phrase boundaries.

**THUS:** The resync pause band is below the perceptual threshold for a break.

---

## L-220-Geminate-Policy-Corrective

**Domain:** Parameters / Process Controls

**WHAT:** The geminate_policy is set to "corrective" by default.

**WHY:** In corrective mode, adjacent same-consonant sequences (coda + onset) are corrected to the configured geminate target duration. This ensures consistent geminate realization regardless of how the geminate was created (lexical, assimilatory, or prosodic). The alternative "cumulative" mode would keep coda + onset durations separate, potentially producing inconsistent geminate durations.

**THUS:** Corrective mode ensures consistent geminate realization.

---

## L-221-Accentuation-Distribution-Policy-80-20

**Domain:** Parameters / Process Controls

**WHAT:** The accentuation_distribution_policy is set to "80_20" by default.

**WHY:** When an accentuation operation adds duration, 80% of the added duration is assigned to the accentuated segment and 20% to the adjacent segment. This reflects the observation that prominence is not concentrated entirely on one segment but spreads slightly to adjacent segments (Campbell and Isard 1990).

**THUS:** The 80/20 distribution reflects the phonetic reality of prominence spread.

---

## L-222-Scale-1.0

**Domain:** Parameters / Global

**WHAT:** The scale parameter is set to 1.0 by default.

**WHY:** A scale of 1.0 means no global scaling is applied. Runtime treats 1.0 as a true no-op path, avoiding unnecessary computation. Values other than 1.0 are used for sensitivity analysis or speech rate adjustment.

**THUS:** The default scale of 1.0 is a no-op, preserving the base timing model.

---

## L-223-Segmental-Ceiling-310

**Domain:** Parameters / Global

**WHAT:** The segmental_ceiling is set to 310 ms.

**WHY:** This value constrains the maximum duration for any individual segment (consonant gemination_max or vowel elongation_max). It is set slightly above the CVC reference (300 ms) to allow for accentuation-related lengthening while preventing unrealistically long segments.

**THUS:** The segmental ceiling prevents unrealistically long segment durations.

---

## L-224-Segmental-Floor-20

**Domain:** Parameters / Global

**WHAT:** The segmental_floor is set to 20 ms.

**WHY:** This value constrains the minimum duration for any individual segment. It is set low enough to allow for short segments (e.g., hiatus realizations at 35 ms, vowel transitions at 25 ms) while preventing zero-duration segments.

**THUS:** The segmental floor prevents zero-duration segments.

---

## L-225-Hiatus-35ms

**Domain:** Parameters / Special Realizations

**WHAT:** The hiatus parameter (closure.special_realization.hiatus) is set to 35 ms.

**WHY:** Hiatus is the short glottal-stop-like realization between adjacent vowels. The value 35 ms is based on cross-linguistic data on glottal stop duration (Möbius 2004). It is short enough to avoid being perceived as a full consonant but long enough to provide a clear syllable boundary.

**THUS:** The hiatus duration provides a minimal syllable boundary marker between adjacent vowels.

---

## L-226-Vowel-Transition-25ms

**Domain:** Parameters / Special Realizations

**WHAT:** The vowel_transition parameter (sonorant.special_realization.vowel_transition) is set to 25 ms.

**WHY:** Vowel transition is the glide-like realization between vowels in a diphthong. The value 25 ms is based on cross-linguistic data on glide duration (Möbius 2004). It is short enough to preserve the diphthongal quality but long enough to provide a smooth transition.

**THUS:** The vowel transition duration provides a smooth glide between diphthong vowels.

---

## References

**Billington, Rosey.** 2015. "Temporal Correlates of Lopit Singleton and Geminate Glides." In *Proceedings of the 18th International Congress of Phonetic Sciences (ICPhS 2015)*. Glasgow, UK. (Billington 2015)

**Campbell, W. N., and S. D. Isard.** 1990. "Segment Durations in a Syllable Frame." Research Paper, University of Edinburgh, Centre for Speech Technology Research. (Campbell and Isard 1990)

**Cutanda, Diana, Daniel Sanabria, and Ángel Correa.** 2019. "Cognitive Entrainment to Isochronous Rhythms Is Independent of Both Sensory Modality and Top-Down Attention." *Psicológica* 40: 62–84. (Cutanda et al. 2019)

**Gao, Yingming, and Peter Birkholz.** 2014. "Speaking Rate Changes Affect Phone Durations Differently for Neutral and Emotional Speech." Research Paper, VocalTractLab, Dresden University of Technology. (Gao and Birkholz 2014)

**Gibson, Mark, et al.** 2013. "Consonant Duration and VOT as a Function of Syllable Complexity and Voicing in a Sub-set of Spanish Clusters." *ISCA Archive*. (Gibson et al. 2013)

**Meynadier, Yohann, S. Dufour, and G. Vercherand.** 2019. "Interaction entre durée et position dans la perception des fricatives voisées chuchotées." *ACL Anthology*. (Meynadier et al. 2019)

**Möbius, Bernd.** 2004. "Corpus-Based Investigations on the Phonetics of Consonant Voicing." *Folia Linguistica* 38 (1-2): 5–26. (Möbius 2004)

**Naeser, Margaret A.** 1970. "Influence of Initial and Final Consonants on Vowel Duration in CVC Syllables." Technical Report No. 130, Wisconsin Research and Development Center for Cognitive Learning, University of Wisconsin, Madison. (Naeser 1970)

**Šturm, Pavel, and Jan Volín.** 2023. "Occurrence and Duration of Pauses in Relation to Speech Tempo and Structural Organization in Two Speech Genres." *Languages* 8: 23. (Šturm and Volín 2023)

**Sugai, Kosuke.** 2017. "Mental Representation of Japanese Mora; Focusing on Its Intrinsic Duration." In *Proceedings of Interspeech 2017*, 1218–1222. Stockholm. (Sugai 2017)

**Tauberer, Joshua, and Keelan Evanini.** 2009. "Intrinsic Vowel Duration and the Post-vocalic Voicing Effect: Some Evidence from Dialects of North American English." In *Proceedings of Interspeech 2009*. Brighton, UK. (Tauberer and Evanini 2009)

**Zellner, Brigitte.** 1994. "Pauses and the Temporal Structure of Speech." In *Fundamentals of Speech Synthesis and Speech Recognition*, edited by Eric Keller, 41–62. Chichester: John Wiley & Sons. (Zellner 1994)
