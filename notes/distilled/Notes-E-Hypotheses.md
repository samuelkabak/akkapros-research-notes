# Research Notes - Akkadian Prosody Project
## Part E: Hypotheses and Algorithm Design

---

## E-049-First-Hypothesis-Even-Compression

**Domain:** Hypothesis / Development

**WHAT:** The first hypothesis was that all syllables should be compressed to equal duration. This would create isochronous rhythm.

**WHY:** This was the simplest possible model. If all syllables had the same duration, rhythm would be perfectly regular.

**THUS:** This hypothesis was tested and failed (see note 050).

---

## E-050-Why-Even-Compression-Failed

**Domain:** Hypothesis / Development

**WHAT:** Even compression failed because it destroyed lexical length distinctions. Short vowels became indistinguishable from long vowels. The output was phonologically implausible.

**WHY:** Akkadian has phonemic vowel length. Compressing all syllables to equal duration neutralizes this contrast. The model would lose information that the language uses to distinguish words.

**THUS:** The model must preserve lexical length distinctions. This became a design constraint.

---

## E-051-Second-Hypothesis-Target-Stressed-Only

**Domain:** Hypothesis / Development

**WHAT:** The second hypothesis was that only stressed syllables should be targeted for adjustment. Unstressed syllables would remain at their lexical durations.

**WHY:** This would preserve lexical length while adding prominence to stressed syllables.

**THUS:** This hypothesis was also insufficient. It did not produce the desired rhythmic effect.

---

## E-052-Third-Hypothesis-Add-Don't-Subtract

**Domain:** Hypothesis / Development

**WHAT:** The third hypothesis was that the model should only add duration, never subtract. This preserves all lexical information.

**WHY:** Subtracting duration would destroy information about lexical length. Adding duration preserves it.

**THUS:** This principle became a core design constraint. The model only adds morae, never removes them.

---

## E-053-Bimoraic-Hypothesis-Source

**Domain:** Hypothesis / Source

**WHAT:** The bimoraic hypothesis emerged from observing the syllable weight distribution. Light syllables (1 mora) and heavy syllables (2 morae) dominate the corpus. The model should aim for even mora counts.

**WHY:** The distribution suggests that Akkadian prefers bimoraic units. This is consistent with stress-timed languages, where feet are typically bimoraic.

**THUS:** The model adopts bimoraic well-formedness as its organizing principle.

---

## E-054-Bimoraic-Hypothesis-Formulation

**Domain:** Hypothesis / Formulation

**WHAT:** The bimoraic hypothesis states that Akkadian prosody aims for even mora counts within prosodic units. When a unit has odd mora count, one mora is added through legal operations.

**WHY:** This is the core hypothesis of the project. It predicts where and when accentuation occurs.

**THUS:** The algorithm implements this hypothesis. It checks mora parity and adds one mora when needed.

---

## E-055-Bimoraic-Hypothesis-Testability

**Domain:** Hypothesis / Methodology

**WHAT:** The bimoraic hypothesis is testable through rhythm metrics. If the hypothesis is correct, the accentuated output should show stress-timed characteristics.

**WHY:** The metrics provide an independent test. They do not depend on the hypothesis.

**THUS:** The metrics results serve as validation of the hypothesis.

---

## E-056-Legal-Operation-Vowel-Lengthening

**Domain:** Algorithm / Operations

**WHAT:** Vowel lengthening applies to syllables containing long vowels: CVV, VV, CVVC, VVC. Effect: 2µ → 3µ (or 3µ → 4µ for CVVC). Notation: V̄ → V̄~ (e.g., ā → ā~).

**WHY:** This operation is phonologically legal because vowel length is phonemic in Akkadian. Lengthening preserves the contrast (short remains short). The operation is already attested in the language through processes like compensatory lengthening.

**THUS:** Vowel lengthening is a primary tool for achieving bimoraic targets. It adds exactly one mora with minimal disruption to lexical identity.

---

## E-057-Legal-Operation-Coda-Gemination

**Domain:** Algorithm / Operations

**WHAT:** Coda gemination applies to heavy syllables ending in a consonant: CVC, VC (non-final only). Effect: 2µ → 3µ. Notation: C → C~ (e.g., mir → mir~).

**WHY:** This operation is phonologically legal because gemination is phonemic and productive in Akkadian. It appears in n-assimilation (indin → iddin) and t-infix assimilation (iṣtabat → iṣṣabat). Word-final gemination is unattested, so it is prohibited.

**THUS:** Coda gemination is a second primary tool. It adds a mora through consonant length while respecting the constraint against word-final geminates.

---

## E-058-Illegal-Operation-Final-Gemination

**Domain:** Algorithm / Constraints

**WHAT:** Word-final gemination is illegal. A coda consonant in the final syllable of a word cannot be geminated.

**WHY:** Word-final geminates are unattested in Akkadian. The language does not allow them.

**THUS:** The algorithm must check for word-final position before applying coda gemination.

---

## E-059-Illegal-Operation-Short-Vowel-Lengthening

**Domain:** Algorithm / Constraints

**WHAT:** Short vowels cannot be lengthened. This would neutralize the phonemic contrast between short and long vowels.

**WHY:** Vowel length is phonemic in Akkadian. Lengthening a short vowel would destroy lexical information.

**THUS:** Short vowels are protected from lengthening. Only long vowels can be extended.

---

## E-060-Why-Onsets-Cannot-Geminate

**Domain:** Algorithm / Constraints

**WHAT:** Onset gemination is not a primary operation. It is used only as a last resort when no other legal operation is available.

**WHY:** Onset gemination is phonologically marked. It is not attested as a regular process in Akkadian.

**THUS:** Onset gemination is reserved for cases where no other option exists (<1% of corpus).

---

## E-061-Design-Principle-One-Mora

**Domain:** Algorithm / Design

**WHAT:** The algorithm always adds exactly one mora. It never adds more than one.

**WHY:** Adding one mora is sufficient to change parity (odd → even). Adding more would overshoot the target.

**THUS:** The algorithm is conservative. It adds the minimum needed.

---

## E-062-Accentuation-Hierarchy-LOB

**Domain:** Algorithm / Accent Styles

**WHAT:** LOB (Literary Old Babylonian) hierarchy: 1. final superheavy, 2. rightmost non-final heavy, 3. final heavy.

**WHY:** This follows Streck (2022) for literary texts. Final superheavy syllables attract stress regardless of position.

**THUS:** LOB is the default accent style for literary texts.

---

## E-063-Accentuation-Hierarchy-SOB

**Domain:** Algorithm / Accent Styles

**WHAT:** SOB (Standard Old Babylonian) hierarchy: 1. rightmost non-final heavy, 2. final heavy.

**WHY:** This follows Huehnergard (2011) for standard texts. Final superheavy is not prioritized.

**THUS:** SOB is available as an alternative for non-literary texts.

---

## E-064-Accentuation-Hierarchy-AOB

**Domain:** Algorithm / Accent Styles (Discarded)

**WHAT:** AOB (Academic Old Babylonian) was initially considered as a comparison model. It was set aside because it did not provide useful distinctions.

**WHY:** AOB was an experimental option that did not contribute to the research findings.

**THUS:** AOB is documented here for historical completeness but is not used in the current research.

---

## E-065-Rationale-For-Hierarchy

**Domain:** Algorithm / Design

**WHAT:** The hierarchy prioritizes operations that are phonologically least disruptive. Vowel lengthening is preferred over coda gemination, which is preferred over onset gemination.

**WHY:** This follows from the principle of minimal disruption. Operations that preserve lexical identity are preferred.

**THUS:** The hierarchy ensures that the algorithm makes the most conservative choice first.

---

## References

**Huehnergard, John.** ***A Grammar of Akkadian***. 3rd edition. Winona Lake, IN: Eisenbrauns, 2011. (Huehnergard 2011)

**Streck, Michael P.** ***Altbabylonisches Lehrbuch***. 4th edition. Wiesbaden: Harrassowitz, 2022. (Streck 2022)
