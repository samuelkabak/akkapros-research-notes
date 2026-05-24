# Research Notes - Akkadian Prosody Project

## 001-Auditory-Intuition

**Domain:** Foundational / Motivation

**WHAT:** When European scholars recite Akkadian, the language sounds rhythmless. Arabic speakers produce recitations that feel closer to natural speech.

**WHY:** Personal observation while listening to recordings of scholarly recitations. Native speaker intuition from a related Semitic language detects a missing pulse. The standard pronunciation taught in universities lacks the natural organization that all living languages possess (Huehnergard 2011 describes the rules but not the flow).

**THUS:** There is a gap between the phonological description and any plausible spoken realization. The academic model describes stress placement but not phrasal timing. This gap needs to be identified and possibly filled.

---

## 002-Gap-In-Scholarship

**Domain:** Foundational / Problem Statement
**WHAT:** The user-facing YAML should no longer force one exposed `hiatus` value to cover the whole vowel-to-vowel transition domain. The parameter space now needs two values: a strict `hiatus` floor for onsetless or bare VV passage, and a second `vowel_transition` value for stronger diphthong-like or glide-like passage.
**WHAT:** Assyriological grammars describe stress rules in detail, but applying these rules mechanically does not produce language that could be spoken fluently.
**WHY:** The earlier `70 ms` setting did useful work as a compact placeholder, but it conflated two distinct objects. The newly assembled source review on vowels and transitions makes that visible. The intrinsic transition evidence points to a very short vocoid-internal passage around `11 ms`, whereas lexical glides sit far higher, around `93-97 ms` (Liu 2022; Billington 2015). A single `70 ms` value therefore behaves more like a reduced sonorant proxy than like true hiatus. After several rounds of comparison, the cleaner solution is to split the row. The strict `hiatus` anchor can be kept near the intrinsic transition floor, rounded to `12 ms`, while a second parameter can represent the stronger vowel-to-vowel passage that remains clearly below lexical glide duration. Taking the midpoint between `11 ms` and `93 ms` yields about `52 ms`, which is a defensible compact default for `vowel_transition`.
**WHY:** Comparison with living Semitic languages (Arabic) shows that something essential is missing. The grammars provide rules for isolated words but nothing for connected speech (Greenstein 1984 discusses syllable structure but not phrasal timing).
**THUS:** PROPOSED MODEL: Replace the old single value with `hiatus = 12 ms` and `vowel_transition = 52 ms`. The first is a narrow modeling anchor for onsetless entry or bare VV passage. The second is the working value for stronger diphthong-like transition. Neither should be mistaken for a directly measured Akkadian segment, but the two-value model is methodologically clearer than the old overloaded `70 ms` proxy.
**THUS:** The academic model is incomplete. It describes where stress could fall, not how it was realized in actual speech. A complete model needs a mechanism for phrasal timing.

---

## 003-Personal-Motivation

**Domain:** Foundational / Context

**WHAT:** The investigator's native familiarity with Arabic provided an internal metric for what natural speech should sound like.

**WHY:** This is not an abstract linguistic question but a perceptual one. The ear detects a problem even when the mind cannot yet name it.

**THUS:** The research is grounded in authentic linguistic intuition, not just theoretical speculation.

---

## 004-Akkadian-Consonant-Inventory

**Domain:** Phonology / Segments

**WHAT:** Akkadian has a full set of consonants with IPA values. These include stops (b, d, g, k, p, q, ṭ), fricatives (s, z, š, ḫ, ḥ), sonorants (l, m, n, r), glottals (ʾ, ʿ), and glides (w, y). The emphatics are q, ṣ, ṭ (Buccellati 1997).

**WHY:** The phonetic realization of emphatics is debated. They may be ejective or pharyngealized. This uncertainty matters for IPA rendering but does not affect moraic computation.

**THUS:** Any prosodic model must account for these consonants and their effects on adjacent vowels.

---

## 004b-Cuneiform-Writing-Conventions

**Domain:** Orthography / Writing System

**WHAT:** Akkadian is written in cuneiform, a logo-syllabic script where signs can represent words (logograms) or syllables (phonograms). The writing system does not consistently mark vowel length, gemination, or stress. Plene writing (extra vowel signs) occasionally indicates length or prominence, but its use is inconsistent.

**WHY:** Understanding the orthographic conventions is essential for interpreting the corpus data. The eBL transcriptions normalize cuneiform into a standard transliteration that marks vowel length (macron/circumflex) and distinguishes consonants. However, the underlying cuneiform leaves much phonetic detail ambiguous. Buccellati (1997) stresses how difficult it is to establish a phonemic inventory for ancient Semitic languages from graphemic documentation alone. This ambiguity is therefore both a limitation and an opportunity: it means the writing system does not contradict the prosodic model, but it also cannot directly confirm it (Huehnergard 2011, §1.4; Buccellati 1997; Streck 2022, §1.3).

**THUS:** Any prosodic reconstruction must acknowledge that we are working from transliterated texts, not direct phonetic records. The model's assumptions must be explicit, and its results must be compatible with what the orthography does tell us (e.g., phonemic length distinctions, syllable structure constraints).

---

## 005-Akkadian-Vowel-Inventory

**Domain:** Phonology / Segments

**WHAT:** Akkadian has short vowels (a, e, i, u = 1 mora), long vowels (ā, ē, ī, ū = 2 morae), and circumflex vowels (â, ê, î, û = 2 morae) from contraction (Huehnergard 2011).

**WHY:** Scholars debate whether macron and circumflex vowels differed phonetically. The orthography distinguishes them, but the phonetic reality is unknown.

**THUS:** Orthographic distinctions do not necessarily reflect spoken distinctions. This uncertainty must be acknowledged in any reconstruction.

---

## 006-Diphthong-Contraction

**Domain:** Phonology / Historical Change

**WHAT:** Historical diphthongs (*ay, *aw) contracted to long vowels (ê, ô) in Old Babylonian (Huehnergard 2011; Buccellati 1996).

**WHY:** This removed diphthongs from the inventory and increased the proportion of long vowels. It affected the overall syllable structure of the language.

**THUS:** Diphthongs are rare in Old Babylonian texts. When they appear across morpheme boundaries, they need special handling in syllabification.

---

## 007-Vowel-Syncope

**Domain:** Phonology / Processes

**WHAT:** Unstressed short vowels in open syllables delete under certain conditions. Example: napištum → napšātum (Greenstein 1984; Buccellati 1996).

**WHY:** This is not random deletion. It is a systematic process that reduces the number of light syllables. Buccellati (1996) also notes vowel elision before endings in forms such as ipparis + u > ipparsū, which shows that Akkadian actively manages syllable weight and surface phonotactics.

**THUS:** Syncope shows that Akkadian phonology already contains mechanisms for adjusting moraic structure. This supports the idea that similar operations could be used for rhythm.

---

## 008-Syncope-Blocking-Conditions

**Domain:** Phonology / Constraints

**WHAT:** Syncope is blocked if it would create a tri-consonantal cluster, especially with a guttural. Example: iḫarriš is attested, not iḫrš (Greenstein 1984).

**WHY:** The language avoids phonotactic violations. It manages syllable structure actively.

**THUS:** Any prosodic model must respect these constraints. Operations that would create illegal clusters are prohibited.

---

## 009-Anaptyxis

**Domain:** Phonology / Processes

**WHAT:** When syncope would create an illegal cluster, a vowel is inserted instead. Example: šarrum from šar-r-m (Greenstein 1984).

**WHY:** Accentuation strategies are already present in the phonology. The language has native mechanisms for adjusting syllable structure.

**THUS:** The toolkit's operations (vowel lengthening, gemination) are not invented. They are grounded in existing Akkadian phonological processes.

---

## 010-Geers-Law

**Domain:** Phonology / Constraints

**WHAT:** Two emphatic consonants cannot co-occur in a root. If a root would etymologically contain two emphatics, one dissimilates to its plain counterpart (Geers 1945; Buccellati 1997).

**WHY:** This is evidence of articulatory ease prioritizing rapid production. The language avoids difficult sequences.

**THUS:** Phonological constraints shape the lexicon. Any prosodic model must operate within these natural limits.

---

## 011-N-Assimilation

**Domain:** Phonology / Processes

**WHAT:** The consonant *n* assimilates completely to a following consonant, resulting in gemination. Example: indin → iddin (Huehnergard 2011).

**WHY:** Gemination is a native process. It is available as a phonetic resource.

**THUS:** Gemination can be used as an operation in the prosodic model. It is already attested in the language.

---

## 012-T-Infix-Assimilation

**Domain:** Phonology / Processes

**WHAT:** The infix -t- in verbal stems assimilates to preceding dentals or sibilants, resulting in gemination. Example: iṣtabat → iṣṣabat (Huehnergard 2011).

**WHY:** Gemination is productive across different morphological contexts. It is a regular part of the phonology.

**THUS:** Gemination is a well-attested, productive process. It can be used systematically in the model.

---

## 013-Sandhi-Assimilation

**Domain:** Phonology / Connected Speech

**WHAT:** Consonants assimilate across word boundaries for ease of pronunciation. Example: in pīm → im pīm (Huehnergard 2011).

**WHY:** Sandhi is active. The language does not treat word boundaries as absolute barriers.

**THUS:** Word boundaries can be crossed for prosodic purposes. Merging words in the algorithm reflects natural speech behavior.

---

## 014-Gemination-As-Resource

**Domain:** Phonology / Processes

**WHAT:** Geminated consonants are phonologically distinct from singletons. They are common in the lexicon (Huehnergard 2011).

**WHY:** Gemination is available as a phonetic resource. The language already uses it for morphological and phonological purposes.

**THUS:** Adding morae through gemination is phonologically legal. It builds on an existing contrast.

---

## 015-Word-Boundary-Constraints

**Domain:** Phonology / Syllable Structure

**WHAT:** Consonant clusters are not permitted at word boundaries. A prothetic vowel breaks initial clusters. An epenthetic case vowel breaks final clusters (Greenstein 1984).

**WHY:** The language actively manages syllable margins. It avoids illegal structures at edges.

**THUS:** The model must respect these constraints. Final gemination is illegal because word-final geminates are unattested.

---

## 016-Tri-Consonantal-Clusters-Forbidden

**Domain:** Phonology / Syllable Structure

**WHAT:** Three consonants in a row are not allowed. They are resolved by inserting an anaptyctic vowel. The maximum is CC across a syllable boundary (Greenstein 1984).

**WHY:** This is a hard constraint on Akkadian phonotactics. It shapes all phonological processes.

**THUS:** Any prosodic operation must avoid creating illegal clusters. This becomes a boundary condition for the algorithm.

---

## 017-CVVC-Syllables-Status

**Domain:** Phonology / Syllable Types

**WHAT:** CVVC (superheavy) syllables exist in Old Babylonian but are restricted. In later dialects, they disappear. They are either shortened to CVC or restructured (Greenstein 1984, Huehnergard 2011).

**WHY:** This is evidence of instability. CVVC syllables are a marked category. Their diachronic loss suggests pressure to eliminate trimoraic structures.

**THUS:** The choice between preserving or shortening CVVC syllables is not arbitrary. Preserving them (through lengthening) avoids information loss about lexical length distinctions. Shortening them would follow the later historical trajectory but would lose the contrast between CV̄C and CVC. The algorithm adopts the conservative approach: preserve length unless evidence suggests otherwise.

---

## 018-CVVC-Diachronic-Pathway

**Domain:** Phonology / Historical Change / Algorithm

**WHAT:** The historical loss of CVVC syllables in later dialects suggests that the language was under pressure to eliminate trimoraic syllables. This pressure might reflect a preference for bimoraic units in speech rhythm.

**WHY:** Two pathways are possible for handling CVVC syllables algorithmically:

* Lengthen (conservative): CVVC → CVV~C (3µ → 4µ). This preserves lexical length distinctions and avoids information loss about the original long vowel.
* Shorten (diachronic): CVVC → CVC (3µ → 2µ). This follows the later historical development but neutralizes the contrast between CV̄C and CVC.

**THUS:** The algorithm adopts the lengthening approach for Old Babylonian texts. This is the more conservative choice: it preserves the phonemic length distinction and avoids discarding information that may have been prosodically relevant. The shortening option remains available for sensitivity testing or for application to later dialects where the historical loss had already occurred.

---

## 018b-Corpus-Selection-Criteria

**Domain:** Corpus / Methodology

**WHAT:** The corpus consists of three Standard Babylonian literary texts: Enūma Eliš (tablets II, IV, VI, VII), Erra and Išum (tablet I), and Marduk's Address to the Demons. These were selected for specific reasons.

**WHY:**

* Enūma Eliš is the Babylonian creation epic, a well-preserved literary text with consistent orthography and clear line structure. Tablets II, IV, VI, VII were chosen because they contain connected narrative passages suitable for prosodic analysis.
* Erra and Išum (Tablet I) is a mythological poem with varied metrical structures and a mix of dialogue and narrative. It provides a different register from the epic style.
* Marduk's Address to the Demons is an incantation text with formulaic repetitions and ritual language. It represents a third genre, allowing cross-genre comparison.

All texts are from the Standard Babylonian period (ca. 1000–600 BCE), ensuring linguistic consistency. The transcriptions are taken from the Electronic Babylonian Library (eBL), which provides normalized, machine-readable versions of standard editions (Lambert 2013 for Enūma Eliš; Cagni 1969 for Erra; Lambert 1999 for Marduk's Address).

**THUS:** The corpus is small but representative of three major literary genres. Future work should expand to letters, legal documents, and administrative texts to test the model on non-literary registers.

---

## 019-Syllable-Structure-Statistics-Preliminary

**Domain:** Corpus / Quantitative

**WHAT:** The syllable weight distribution in the corpus shows a near balance between light and heavy syllables. Light syllables (1 mora: CV, V) constitute approximately 43% of the corpus. Heavy syllables (2 morae: CVC, CVV, VC, VV) constitute approximately 49%. Superheavy syllables (3 morae: CVVC, VVC) constitute approximately 3%. This shows that Akkadian privileges long syllables, with heavy syllables actually outnumbering light ones.

**WHY:** Historical processes such as vowel syncope, elision of glides, and loss of Proto-Semitic pharyngeals (Huehnergard 2011) increased the proportion of closed and long-vowel syllables over time. These processes transformed the original syllable balance, making heavy syllables more frequent than in the earlier stages of the language.

**THUS:** The strong balance between light and heavy syllables cannot be discarded in any prosodic model. It is a fundamental characteristic of Akkadian phonology. Any account of stress and rhythm must operate within this distribution, where heavy syllables are actually more common than light ones.

---

## 020-Syllable-Structure-Statistics-Final

**Domain:** Corpus / Quantitative

**WHAT:** Final syllable counts from the full corpus (4,917 words, 14,684 syllables): CV 35.69%, CVC 22.02%, CVV 21.53%, CVVC 2.54%, VC 6.01%, V 7.03%, VV 1.32%, VVC 0.03%.

**WHY:** These proportions represent the actual distribution in Standard Babylonian literary texts. They are the baseline for all further analysis.

**THUS:** Any model must account for this distribution. The frequency of each syllable type determines how often different operations will apply.

---

## 021-Syllable-Weight-Distribution

**Domain:** Corpus / Quantitative

**WHAT:** Light syllables (CV, V) = ~43% of the corpus. Heavy syllables (CVC, VC, CVV, VV) = ~54%. Superheavy syllables (CVVC, VVC) = ~3%.

**WHY:** This distribution shows that Akkadian has a mix of light and heavy syllables. The language has resources for both types.

**THUS:** The bimoraic target (even mora counts) will require adjusting both light and heavy syllables. Light syllables cannot be lengthened (would neutralize contrast), so they must be grouped or merged.

---

## 022-Moraic-Theory-Foundation

**Domain:** Phonology / Theory

**WHAT:** Hayes (1995) provides the theoretical grounding for moraic phonology. Morae are weight units. Light syllables have one, heavy have two, superheavy have three. Kager (2009) reinforces the same bimoraic logic for Arabic stress, where a single light syllable does not form a foot by itself.

**WHY:** This framework is standard in metrical stress theory. It applies to Akkadian as described by Huehnergard (2011) and others, and it fits a broader Semitic comparison in which bimoraic footing remains a central generalization (Hayes 1995; Kager 2009).

**THUS:** The model adopts the moraic framework. Syllable weight is measured in morae. Stress falls on heavy syllables.

---

## 023-Huehnergard-Stress-Rules

**Domain:** Academic Model / Description

**WHAT:** Huehnergard (2011) presents the standard stress rules. Stress falls on the rightmost heavy syllable. If no heavy exists, stress defaults to the first syllable.

**WHY:** This is the established description in Assyriological grammars. It is based on patterns observed in cuneiform texts.

**THUS:** These rules provide the candidate set. They tell us where stress could fall in isolated words, but not how it works in connected speech.

---

## 024-Streck-Literary-Rule

**Domain:** Academic Model / Literary Register

**WHAT:** Streck (2022) updates the analysis for Literary Old Babylonian. Final syllables with circumflex vowels attract stress regardless of position. This is a special rule for the literary register.

**WHY:** Literary texts show special treatment of circumflex finals. This may reflect a different prosodic tradition or a more deliberate style.

**THUS:** The model must include both Standard and Literary options. The LOB hierarchy (final superheavy → rightmost non-final heavy → final heavy) captures the literary pattern.

---

## 025-Academic-Model-As-Candidate-Set

**Domain:** Academic Model / Interpretation

**WHAT:** The academic model does not tell us which syllables ARE prominent, but which syllables CAN BE prominent. It provides a candidate set, not a realization.

**WHY:** This insight emerged from comparing the rules to actual speech patterns. Fixed positions cannot by themselves produce the variable timing of stress-timed languages.

**THUS:** The model needs a selection mechanism. Something else must choose among candidates in connected speech. This selection mechanism is what the project aims to model.

---

## 026-Stress-Eligibility-vs-Realization

**Domain:** Academic Model / Quantitative

**WHAT:** The number of stressed syllables in Akkadian predicted by the academic model (Huehnergard 2011) appears too high for natural connected speech.

**WHY:** The academic stress model predicts that every word other than function words and nouns in construct state has exactly one stressed syllable. A manual count of stressable words [S] in the Erra corpus gives:

* Total words: 1,015
* Stressable words [S]: 817 (80.5% of all words)
* Total syllables: 2,798
* Stressed syllables according to the academic model: 817 (one per stressable word)
* Percentage of stressed syllables: 817 / 2,798 × 100 = 29.2%

**THUS:** Applying the academic model strictly would result in prominence on approximately 29% of all syllables. This is likely too high for natural speech. In stress-timed languages, stressed syllables serve as processing cues for word boundaries. This system requires a sufficient number of unstressed syllables to create the characteristic rhythm. A prominence rate of 29% leaves relatively little room for the compression and reduction of unstressed material that defines natural stress-timing.

---

## 027-Stress-Eligibility-By-Type

**Domain:** Academic Model / Quantitative

**WHAT:** Heavy syllables (CVC, CVV, CVVC, VC, VV, VVC) are 100% eligible. Light syllables (CV, V) are 0% eligible.

**WHY:** This follows from the moraic definition of stress. Stress requires weight. Light syllables have no weight to attract stress.

**THUS:** The eligibility pattern is clear and principled. Heavy syllables are the only candidates.

---

## 027b-Stress-Eligibility-and-Word-Boundaries

**Domain:** Academic Model / Phonology

**WHAT:** Stress eligibility under the academic model operates within word boundaries, not across them. Each word is an independent domain for stress assignment, regardless of its syntactic or prosodic context.

**WHY:** This follows from the standard description in grammars (Huehnergard 2011, Streck 2022). Words in isolation or in sequence are treated the same way: the rightmost heavy syllable within that word receives stress. Function words and construct nouns may lose their stress, but the rule applies to the lexical word itself before any post-lexical processes.

**THUS:** The academic model provides a candidate set at the word level. The prosody realization model must then select among these candidates at the phrase level, merging words and adjusting prominence to achieve rhythmic coherence. The two operate at different levels of representation: lexical (academic) and phrasal (realization).

---

## 028-The-84-Percent-Red-Herring

**Domain:** Academic Model / Correction

**WHAT:** An early calculation mistakenly gave 84% stressed words. This was based on counting words, not syllables. When corrected to syllables, the proportion is 33.2%.

**WHY:** The error was caught and corrected. Counting words gave a misleading impression of how many syllables actually bear stress.

**THUS:** The correct figure (33.2%) is entirely plausible. It means about one-third of syllables are stress-eligible.

---

## 029-Plene-Spelling-Evidence

**Domain:** Orthography / Phonetics

**WHAT:** Cuneiform occasionally writes an extra vowel sign (plene spelling) in positions that correspond to stress. This is independent evidence that some candidates were actually prominent (Huehnergard 2011).

**WHY:** Plene spellings sometimes align with predicted stress positions. This suggests that scribes occasionally marked prominence.

**THUS:** The academic model has some phonetic support. But the inconsistency of plene spelling is also significant.

---

## 030-Plene-Spelling-Inconsistency

**Domain:** Orthography / Phonetics

**WHAT:** Plene spelling is not used consistently. This suggests that it marks something variable. It may mark phonetic prominence (which varies with speech rate and context) rather than lexical length.

**WHY:** If plene marked lexical length, it would be consistent. The inconsistency points to a variable factor. Prominence in connected speech is variable.

**THUS:** Plene spelling may reflect the output of the selection mechanism. It could be evidence for the model, not against it.

---

## 031-Acoustic-Metrics-Introduction

**Domain:** Rhythm / Measurement

**WHAT:** Ramus, Nespor, and Mehler (1999) introduced a framework for measuring speech rhythm. They used %V (proportion of vocalic intervals) and ΔC (standard deviation of consonantal intervals).

**WHY:** These metrics classify languages into rhythmic types. Stress-timed, syllable-timed, and mora-timed languages occupy different regions of the %V-ΔC plane (Ramus et al. 1999, White and Mattys 2007).

**THUS:** The same metrics can be applied to Akkadian texts. They provide a quantitative way to test rhythmic hypotheses.

---

## 032-%V-Definition

**Domain:** Rhythm / Measurement

**WHAT:** %V = (total duration of vocalic intervals) / (total duration of speech) × 100. It measures the proportion of vocalic material in the speech stream (Ramus et al. 1999). The value is expressed as a percentage.

**WHY:** This metric distinguishes language types. Stress-timed languages have lower %V. Syllable-timed languages have higher %V.

**THUS:** %V can be computed from written text using morae as duration proxies. Pauses must be accounted for separately to make the values comparable to measurements from living languages.

---

## 033-ΔC-Definition

**invalid note - superseded by note 162**

**Domain:** Rhythm / Measurement

**WHAT:** ΔC = standard deviation of consonantal interval durations. It measures the variability of consonant spacing (Ramus et al. 1999). The value is expressed in seconds (or in morae when used as a proxy).

**WHY:** Low ΔC means consonants are evenly spaced. This is characteristic of syllable-timed or mora-timed languages. High ΔC means consonants are unevenly spaced. This is characteristic of stress-timed languages.

**THUS:** ΔC reveals the rhythm mechanism. When measured in morae, it provides a language-internal measure of variability that is independent of absolute timing.

---

## 034-VarcoC-Introduction

**invalid note - superseded by note 163**

**Domain:** Rhythm / Measurement

**WHAT:** Dellwo (2006) introduced VarcoC = (ΔC / mean interval) × 100. This rate-normalized version allows comparison across different speech tempos. VarcoC is a unitless percentage.

**WHY:** Raw ΔC is affected by speech rate. VarcoC removes this effect. It is a robust classifier across languages (White and Mattys 2007).

**THUS:** VarcoC is the key metric for rhythmic classification. It allows direct comparison between Akkadian and living languages without requiring speech rate assumptions. Its unitless nature makes it ideal for cross-linguistic typology.

---

## 035-Reference-Values-Stress-Timed

**Domain:** Rhythm / Typology

**WHAT:** English VarcoC ranges 70-80. German ranges 70-80. Dutch ranges 68-78 (Ramus et al. 1999, Dellwo 2006, White and Mattys 2007).

**WHY:** These ranges provide a baseline for stress-timed classification.

**THUS:** If Akkadian's VarcoC falls in this range, it patterns with stress-timed languages.

---

## 036-Reference-Values-Syllable-Timed

**Domain:** Rhythm / Typology

**WHAT:** French VarcoC ranges 50-55. Spanish ranges 50-55. Italian ranges 50-55 (Ramus et al. 1999, White and Mattys 2007).

**WHY:** These ranges provide a baseline for syllable-timed classification.

**THUS:** If Akkadian's VarcoC falls in this range, it would pattern with syllable-timed languages.

---

## 037-Reference-Values-Mora-Timed

**Domain:** Rhythm / Typology

**WHAT:** Japanese ΔC is approximately 37. This corresponds to a very low VarcoC (Ramus et al. 1999).

**WHY:** Japanese is the prototypical mora-timed language. Its consonant spacing is highly regular.

**THUS:** If Akkadian's VarcoC were very low, it might be mora-timed. This is not the case.

---

## 038-Arabic-Rhythm-Research

**Domain:** Rhythm / Comparative

**WHAT:** Research on Arabic dialects shows that they cluster around the stress-timed end of the continuum, though with real internal variation. Hamdi et al. (2004) show that Western dialects such as Moroccan Arabic sound more "staccato" or "jerky," largely because vowel deletion increases consonant clustering, whereas Eastern dialects such as Syrian Arabic have a more open rhythm, in some respects approaching French in vocalic patterning.

**WHY:** Arabic is a living Semitic language with an unbroken tradition of spoken use across millennia. Unlike Akkadian, which is known only from written texts, Arabic provides direct evidence of how a Semitic language can be rhythmically organized in natural speech. The broad tendency of both Western and Eastern dialects toward stress-timed patterning, despite their different surface textures, suggests that this may be a durable possibility within Semitic prosody rather than an isolated modern development (Hamdi et al. 2004).

**THUS:** The shared Semitic roots between Arabic dialects and Akkadian do not prove that Akkadian patterned identically. They do, however, make a stress-timed interpretation more plausible. The Arabic evidence therefore functions as comparative support for the metrics-based classification, not as a direct historical demonstration.

---

## 038b-Rhythm-as-Continuum

**Domain:** Rhythm / Theory

**WHAT:** The traditional division of languages into discrete rhythm classes (stress-timed, syllable-timed, mora-timed) has been challenged by research showing that rhythm is better understood as a continuum (Grabe and Low 2002). Languages may show mixed properties depending on speech rate, style, and individual variation.

**WHY:** Grabe and Low (2002) introduced the Pairwise Variability Index (PVI) to measure rhythmic differences along a continuum rather than in discrete categories. Their work shows that languages traditionally classified as syllable-timed (e.g., Spanish) can show stress-timed properties in certain contexts, and vice versa. Arvaniti (2012) further argues that the metrics themselves are sensitive to methodological choices and that cross-linguistic differences are often smaller than previously claimed.

**THUS:** The classification of Akkadian as "stress-timed" should not be taken as an absolute label but as a position on a continuum. The VarcoC value of 69.09 places it toward the stress-timed end, overlapping with Dutch and approaching English. This is a meaningful finding, but it does not imply that Akkadian had all the properties of English. The goal is compatibility, not identity.

---

## 039-Arvaniti-Critique

**Domain:** Rhythm / Methodology

**WHAT:** Arvaniti (2012) critiqued rhythm metrics. She argued that metrics show substantial inter-speaker variation and are sensitive to methodological choices. Cross-linguistic differences are often statistically non-significant.

**WHY:** This critique must be acknowledged. Rhythm classes are tendencies, not absolutes. Individual variation exists within every language.

**THUS:** The model must present results with confidence intervals. It must acknowledge the limitations of the approach. The goal is compatibility, not proof.

---

## 040-Metrics-To-Text-Assumptions

**Domain:** Rhythm / Methodology

**WHAT:** Applying acoustic metrics to written text requires assumptions. We assume that morae correspond to durational units. We assume that consonantal intervals can be measured in moraic distance. We assume that pauses can be estimated (Ramus et al. 1999).

**WHY:** These assumptions are standard in historical phonetics. They are necessary when absolute timing is unknown.

**THUS:** The assumptions must be explicit. Different assumptions would yield different numbers. The contribution is to show that under plausible assumptions, Akkadian patterns with stress-timed languages.

---

## 041-Initial-Metrics-Results-Preliminary

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Corpus / Quantitative / Methodology

**WHAT:** Initial metrics on a small sample gave %V ≈ 80%, ΔC ≈ 0.68, VarcoC ≈ 68. However, %V = 80% is far greater than measured values for living languages reported by Ramus et al. (1999) and Dellwo (2006), where stress-timed languages typically show %V between 40-45%.

**WHY:** The metrics %V, ΔC, and VarcoC are observations of speech, not written text. Goldman-Eisler (1968) showed that pauses can occupy roughly 30% to 40% of total utterance time in spontaneous speech. The raw metrics computed directly from written text count only vocalic and consonantal segments, ignoring pause time entirely. This inflates %V because the denominator (total time) is missing the pause contribution.

**THUS:** To make the metrics comparable to living languages, a corrected %V must be computed that includes pause time. Using 35% as a reference pause ratio (median estimate from cross-linguistic studies), the corrected %V becomes approximately 80% × (1 - 0.35) = 52%. Sensitivity analysis should be performed across the plausible range of 30% to 40% pause ratios to ensure the classification is robust.

---

## 042-Initial-Metrics-Results-Final

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Corpus / Quantitative

**WHAT:** Final metrics on the original corpus (4,917 words, 14,684 syllables): %V (pause-excluded) 79.90%, %V (35% pauses) 59.18%, ΔC 0.6917 morae, MeanC 1.0012 morae, VarcoC 69.09.

**WHY:** These numbers are the actual results from the full corpus. They are reliable and reproducible.

**THUS:** They provide the baseline for all further analysis. Akkadian's structure is compatible with stress-timing.

---

## 043-Confidence-Intervals-Not-Relevant

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Statistics / Methodology

**WHAT:** Confidence intervals are sometimes used to assess the reliability of metrics. However, for this corpus, they add little value.

**WHY:** The corpus contains 4,917 words and 14,684 syllables—a substantial sample. The key variables affecting the metrics are not statistical noise but systematic choices: the pause ratio (30-40%) and the treatment of CVVC syllables. Sensitivity analysis has been performed on both. VarcoC, the primary classification metric, is independent of speech rate and remains stable across the plausible range of pause assumptions.

**THUS:** Confidence intervals are not reported. The focus is on sensitivity analysis of the assumptions that actually matter, rather than statistical uncertainty about the sample itself.

---

## 044-VarcoC-Interpretation

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Rhythm / Interpretation

**WHAT:** Akkadian's VarcoC (69.09) places it in the lower end of the stress-timed range. The 95% CI overlaps English and Dutch ranges.

**WHY:** This is an empirical finding. It does not depend on any accentuation model. The original text already shows the signature of stress-timing.

**THUS:** Akkadian was likely a stress-timed language. This is not a hypothesis but a deduction from the data, using methods validated on living languages.

---

## 045-Comparison-To-English

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Rhythm / Interpretation

**WHAT:** Statistical comparison shows Akkadian's VarcoC is not significantly different from English. The 95% CI overlaps the English range (70-80).

**WHY:** This strengthens the stress-timing claim. Akkadian patterns with stress-timed languages, not syllable-timed ones.

**THUS:** The classification is robust. It does not depend on fine-tuning or special assumptions.

---

## 046-The-Paradox

**Domain:** Problem / Contradiction

**WHAT:** Metrics show Akkadian is compatible with stress-timing. The academic model gives fixed stress positions. But fixed positions alone cannot produce the variable timing that stress-timing requires.

**WHY:** Stress-timed languages require stressed syllables at roughly equal intervals. Unstressed material compresses or expands between them. Fixed lexical stress positions cannot produce this effect alone (Ramus et al. 1999).

**THUS:** Something is missing from the model. There must be a mechanism that adjusts timing between fixed peaks without moving the peaks themselves.

---

## 047-What-Academic-Model-Lacks

**Domain:** Problem / Gap

**WHAT:** The academic model tells us where stress could go, but not how it works in connected speech. It has no component for phrasal timing.

**WHY:** This is not a criticism of the model. It simply addresses a different question. The grammars describe lexical stress, not speech rhythm.

**THUS:** A complete model needs a candidate set (provided), a selection mechanism (missing), phonetic operations (missing), and a timing target (missing).

---

## 048-The-Gap-This-Project-Fills

**Domain:** Problem / Solution

**WHAT:** This project supplies the missing components. It proposes a selection mechanism, phonetic operations, and a timing target. All are grounded in Akkadian phonology.

**WHY:** The gap must be filled to connect lexical descriptions to plausible speech. Without these components, the model is incomplete.

**THUS:** The project aims to show that a coherent rhythmic system can be built from the lexical stress rules. This is one possible hypothesis, not a reconstruction.

---

## 049-First-Hypothesis-Even-Compression

**Domain:** Algorithm / Failed Attempt

**WHAT:** First attempt: distribute compression evenly across all short vowels to achieve isochrony. Result: VarcoC went out of range.

**WHY:** The hypothesis was arbitrary. It was not grounded in any linguistic principle. Short vowels are not all equal.

**THUS:** This approach failed. Treating all short vowels uniformly ignores syllable structure and stress. A more principled approach is needed.

---

## 050-Why-Even-Compression-Failed

**Domain:** Algorithm / Failed Attempt

**WHAT:** Short vowels are not all equal. Some are in positions where compression is natural (unstressed open syllables). Others are not.

**WHY:** The linguistic context matters. Syllable structure and stress status affect how a vowel behaves.

**THUS:** Any successful model must target specific syllables. The academic stress rules provide a principled way to identify candidates.

---

## 051-Second-Hypothesis-Target-Stressed-Only

**Domain:** Algorithm / Failed Attempt

**WHAT:** Second attempt: lengthen stressed syllables, leave others unchanged. Result: not enough adjustment. VarcoC barely moved.

**WHY:** A stress-timed language needs both compression of unstressed material and expansion of stressed material. Lengthening alone is insufficient.

**THUS:** The model needs operations in both directions. But shortening is problematic because it would neutralize lexical contrasts.

---

## 052-Third-Hypothesis-Add-Don't-Subtract

**Domain:** Algorithm / Insight

**WHAT:** Instead of reducing short vowels (which would destroy contrasts), lengthen long vowels and geminate consonants to achieve even mora counts.

**WHY:** This preserves lexical identity while adding weight. Short vowels remain short. Long vowels remain long. The language already has vowel lengthening and gemination as native processes.

**THUS:** The symmetric approach is promising. It adds morae rather than subtracting. It uses operations already present in Akkadian phonology.

---

## 053-Bimoraic-Hypothesis-Source

**Domain:** Algorithm / Inspiration

**WHAT:** Observation from Levantine Arabic: CVC syllables function as rhythmic units. In connected speech, syllables tend to group into bimoraic chunks.

**WHY:** CVC = 2 morae. This is the most common heavy syllable type across languages. The bimoraic foot is a widespread metrical tendency (Hayes 1995), and Kager (2009) notes that in Arabic a single light syllable does not form a foot by itself, which supports the broader Semitic plausibility of bimoraic grouping.

**THUS:** Hypothesis: Akkadian rhythm is organized around bimoraic units. Phrases should have even mora counts. Local sequences should tend toward bimoraic grouping.

---

## 054-Bimoraic-Hypothesis-Formulation

**Domain:** Algorithm / Core Principle

**WHAT:** Each prosodic unit (word or group of linked words) should contain an even number of morae. When a unit has an odd mora count, exactly one mora is added to a stress-eligible syllable within that unit.

**WHY:** This extends cross-linguistic observations about prosodic minimality. Just as words tend toward bimoraic minimality, phrases tend toward bimoraic regularity.

**THUS:** The bimoraic target becomes the organizing principle. It provides a clear, testable goal for the algorithm.

---

## 055-Bimoraic-Hypothesis-Testability

**Domain:** Algorithm / Prediction

**WHAT:** If the hypothesis is correct, prosodically realized text should show: even mora counts at phrase level, VarcoC in stress-timed range, and plausible distribution of operations by syllable type.

**WHY:** These are concrete, testable predictions. They can be verified against corpus data.

**THUS:** The hypothesis is scientific. It can be confirmed or falsified by empirical testing.

---

## 056-Legal-Operation-Vowel-Lengthening

**Domain:** Algorithm / Operations

**WHAT:** Vowel lengthening applies to syllables containing long vowels: CVV, VV, CVVC, VVC. Effect: 2µ → 3µ (or 3µ → 4µ for CVVC). Notation: V̄ → V̄~ (e.g., ā → ā~).

**WHY:** This operation is phonologically legal. Vowel length is phonemic. Lengthening preserves the contrast (short remains short). The operation is already attested in the language (Huehnergard 2011).

**THUS:** Vowel lengthening is a primary tool for achieving bimoraic targets.

---

## 057-Legal-Operation-Coda-Gemination

**Domain:** Algorithm / Operations

**WHAT:** Coda gemination applies to heavy syllables ending in a consonant: CVC, VC (non-final only). Effect: 2µ → 3µ. Notation: C → C~ (e.g., mir → mir~).

**WHY:** This operation is phonologically legal. Gemination is phonemic and productive. It appears in assimilations and paradigms (Huehnergard 2011). Word-final gemination is unattested, so it is prohibited.

**THUS:** Coda gemination is a second primary tool. It adds a mora through consonant length.

---

## 058-Illegal-Operation-Final-Gemination

**Domain:** Algorithm / Constraints

**WHAT:** CVC at word end cannot be geminated. Reason: word-final geminates are unattested in Akkadian phonotactics (Greenstein 1984).

**WHY:** Creating them would introduce an illegal structure. The language actively avoids this.

**THUS:** The model must respect this constraint. Final CVC syllables are ineligible for gemination.

---

## 059-Illegal-Operation-Short-Vowel-Lengthening

**Domain:** Algorithm / Constraints

**WHAT:** CV (1µ) cannot become CVV (2µ). Reason: Akkadian has phonemic vowel length. Lengthening a short vowel would neutralize this contrast. It would create lexical ambiguity.

**WHY:** This would destroy a fundamental phonological distinction. Minimal pairs like šar (king) vs. šār (wind) would be confused.

**THUS:** Light syllables cannot be prosodically realized directly. They must be handled through merging.

---

## 060-Why-Onsets-Cannot-Geminate

**Domain:** Algorithm / Constraints

**WHAT:** Gemination in Akkadian affects coda consonants. Onset consonants belong to the following syllable. They are not available for lengthening without resyllabification.

**WHY:** Resyllabification would change syllable structure in ways not attested in the language. It would create novel patterns.

**THUS:** Onset gemination is a last resort only. It is used when no other option exists.

---

## 061-Design-Principle-One-Mora

**Domain:** Algorithm / Principles

**WHAT:** Each operation adds exactly one mora. This is a design principle, not an empirical finding.

**WHY:** Adding exactly one mora minimizes disruption to lexical identity. It is the smallest possible adjustment.

**THUS:** The algorithm is conservative. It changes the structure as little as possible while achieving the bimoraic target.

---

## 062-Accentuation-Hierarchy-LOB

**Domain:** Algorithm / Selection

**WHAT:** LOB (Literary Old Babylonian) priority: 1) final superheavy (including circumflex finals), 2) rightmost non-final heavy, 3) final heavy (Streck 2022).

**WHY:** This follows attested stress rules for the literary register. Literary texts show special treatment of superheavy finals.

**THUS:** The LOB model is appropriate for literary texts. It respects the special status of circumflex finals.

---

## 063-Accentuation-Hierarchy-SOB

**Domain:** Algorithm / Selection

**WHAT:** SOB (Standard Old Babylonian) priority: 1) rightmost non-final heavy, 2) final heavy.

**WHY:** This follows Huehnergard's standard description. It avoids word-final operations when possible.

**THUS:** The SOB model is appropriate for general texts. It is the baseline for comparison.

---

## 064-Accentuation-Hierarchy-AOB

**Domain:** Algorithm / Selection

**WHAT:** AOB (Academic Old Babylonian) was initially considered as a comparison model with priority hierarchy: 1) final superheavy, 2) rightmost non-final heavy, 3) first syllable.

**WHY:** This hierarchy was proposed to compare the academic stress model directly against the proposed stress realization models (LOB and SOB). The idea was to test whether the traditional academic description of stress placement could serve as a selection mechanism for phrasal prominence. However, without any direct evidence for how Akkadian stress was actually realized, such a comparison becomes speculative. The key question is not which hierarchy is "correct," but whether the academic model as a whole is complete—it describes lexical stress positions but provides no mechanism for phrasal timing.

**THUS:** Comparing different hierarchies is less relevant than validating the core insight: the academic model is incomplete. The focus should remain on demonstrating that a stress realization mechanism is necessary, and that the proposed LOB/SOB models offer one plausible way to fill that gap. The AOB model adds little to this argument and is set aside.

---

## 065-Rationale-For-Hierarchy

**Domain:** Algorithm / Principles

**WHAT:** The hierarchy respects attested stress patterns, avoids illegal operations, follows academic preferences when possible, and provides a deterministic selection mechanism.

**WHY:** Each of these principles is important. Respecting attested patterns grounds the model in scholarship. Avoiding illegal operations ensures phonological plausibility. Determinism ensures reproducibility.

**THUS:** The hierarchy is principled, not arbitrary. It can be defended on multiple grounds.

---

## 066-Merge-Logic-Why-Needed

**Domain:** Algorithm / Merging

**WHAT:** When a word has odd morae and cannot be prosodically realized internally, it must combine with following words to find a stress realization target.

**WHY:** Light syllables cannot be prosodically realized directly. Final CVC syllables cannot be geminated. Some words have no eligible syllable.

**THUS:** Merging is necessary to handle these cases. It mimics natural speech where words run together.

---

## 067-Merge-Left-To-Right

**Domain:** Algorithm / Merging

**WHAT:** The algorithm proceeds through the text sequentially, never looking back. This mimics speech production. Decisions are made online, not with perfect foresight.

**WHY:** Speakers do not plan entire utterances in advance. They make decisions as they go.

**THUS:** The left-to-right strategy is psychologically plausible. It models real-time production.

---

## 068-Merge-Forward

**Domain:** Algorithm / Merging

**WHAT:** Merge with following words until the merged unit is even or a legal stress realization candidate appears. If successful, output with merge marker.

**WHY:** Forward merging is the default strategy. It follows the natural direction of speech.

**THUS:** The algorithm prioritizes forward merging. It only looks back when forward is impossible.

---

## 069-Merge-Backward

**Domain:** Algorithm / Merging

**WHAT:** Backward merge is used when trailing function words occur before punctuation and need a content host. The algorithm may roll back prior stress realizations and rebuild a larger unit.

**WHY:** Function words cannot stand alone. They must attach to content words. At boundaries, forward merging is impossible.

**THUS:** Backward merging handles edge cases. It ensures function words are properly integrated.

---

## 070-Merge-Termination-Guarantee

**Domain:** Algorithm / Merging

**WHAT:** The algorithm always terminates because each operation adds exactly one mora, and the total number of morae is finite. In practice, merges of up to 3 words suffice.

**WHY:** This guarantees that the algorithm will not loop indefinitely. It is computationally safe.

**THUS:** The implementation is reliable. It can process any input without getting stuck.

---

## 071-Explicit-Plus-Linking

**Domain:** Algorithm / Merging

**WHAT:** The input `+` is treated as an explicit instruction that the linked sequence forms one mandatory prosodic unit.

**WHY:** Some sequences (construct chains, certain compounds) must be treated as units. The `+` marker allows the user to specify this.

**THUS:** The algorithm respects explicit linking. It overrides default behavior when instructed.

---

## 072-Explicit-Plus-Strict-Mode

**Domain:** Algorithm / Merging

**WHAT:** In strict mode (default, `only_last=True`), only the last linked word is eligible for stress realization.

**WHY:** This preserves the integrity of construct chains. The first elements are phonologically dependent on the last.

**THUS:** The default behavior respects the prosodic structure of construct states.

---

## 073-Explicit-Plus-Relaxed-Mode

**Domain:** Algorithm / Merging

**WHAT:** In relaxed mode (`--prosody-relax-last`, `only_last=False`), stress realization may propagate right-to-left across the linked chain.

**WHY:** Some sequences may allow more flexibility. The relaxed mode tests this possibility.

**THUS:** The option exists for experimentation. The default is the more conservative choice.

---

## 074-Function-Word-Behavior

**Domain:** Algorithm / Merging

**WHAT:** Function words are not stress-realized independently. Consecutive function words are grouped. When followed by content, they attach forward. If stranded, they attach backward.

**WHY:** Function words in stress-timed languages are cliticized. They share a single stress unit with adjacent content words.

**THUS:** This enforces clitic-like prosodic dependence. It reflects how function words behave in natural speech.

---

## 075-Function-Word-Inventory

**Domain:** Algorithm / Merging

**WHAT:** Function words include prepositions (ana, ina, ištu, itti, eli), negative particles (ul, ula, lā), the determinative-relative pronoun (ša), coordinating conjunctions (u, ū, lū), and independent personal pronouns (anāku, atta, šū, etc.).

**WHY:** These categories are standard in Assyriological descriptions (Huehnergard 2011, Buccellati 1996).

**THUS:** The inventory is philologically grounded. It reflects the actual grammar of the language.

---

## 076-Diphthong-Processing-Problem

**Domain:** Algorithm / Diphthongs

**WHAT:** Diphthongs exist in the eBL corpus and must be handled. But syllabification and stress realization need a consonant-vowel alternating structure. Diphthongs (VV) break this pattern.

**WHY:** The moraic algorithm expects CV, CVC, CVV, etc. Adjacent vowels are ambiguous for syllable parsing.

**THUS:** A solution is needed. Diphthongs must be processed in a way that allows the algorithm to work.

---

## 077-Diphthong-Processing-Solution

**Domain:** Algorithm / Diphthongs

**WHAT:** Insert a temporary hiatus consonant (glottal stop) during processing. Then restore the diphthong after stress realization.

**WHY:** This creates unambiguous syllable boundaries for the algorithm. Glottal stop is the most neutral consonant. It does not affect vowel quality.

**THUS:** The split-restore pipeline works. It keeps computation explicit while allowing diphthongal surface output.

---

## 078-Diphthong-Constraint

**Domain:** Phonology / Constraints

**WHAT:** Akkadian phonotactics impose a constraint on sequences of contiguous vowels: when two vowels come into contact (typically due to the loss of a separating consonant such as a laryngeal or glide), the first vowel must be short, even if it was originally long (Huehnergard 2011, Lesson 6.1(c)).

**WHY:** This rule is explicitly stated in Huehnergard's grammar: "an original long ē or ī that remains as the first vowel in most such sequences is shortened." The phonetic rationale is that "a long vowel does not usually occur immediately before another vowel" in Akkadian. This explains forms like rabiam (great, acc.) from underlying rabī + am, where the long ī is shortened to i, rather than the expected rabīam. Izre'el and Cohen (2004) confirm this as a morphophonemic rule: "When two long vowels come in sequence, the first is usually interpreted as short." Buccellati (1996) adds that long vowels generally do not occur in environments where they would create impermissible syllabic structures.

**THUS:** Any prosodic model that adds length to a vowel in a diphthongal sequence must respect this constraint. If the stress realization algorithm elongates the first vowel of a diphthong, it would violate a fundamental phonotactic rule. Therefore, when elongation is required in such contexts, the length must be moved to the second vowel, or the operation must be blocked entirely.

---

## 079-Diphthong-Restoration-Rules

**Domain:** Algorithm / Diphthongs

**WHAT:** Restoration rules must account for vowel quality (short/long/circumflex), whether the second vowel carries a tilde, and interactions where circumflex forms take precedence.

**WHY:** Different combinations yield different outputs. The mapping is not trivial. Rules must be ordered correctly to avoid shadowing.

**THUS:** A comprehensive restoration table is needed. It must be generated systematically and applied in the correct order.

---

## 080-Diphthong-Same-Base-Rules

**Domain:** Orthography / Phonology / Algorithm

**WHAT:** In Akkadian, the circumflex (â, ê, î, û) is a transcription marker used specifically to indicate a long vowel that resulted from vowel contraction. This process is intimately tied to the disappearance of Proto-Semitic consonants (laryngeals, pharyngeals, and the semi-vowels w and y). When one of these consonants stood between two vowels, its elision left those vowels contiguous. In Old Babylonian, these pairs of contiguous vowels typically merged into a single long vowel, which is marked by the circumflex (Huehnergard 2011, Izre'el and Cohen 2004).

**WHY:** This historical process explains the behavior of same-base vowel pairs (a+a, i+i, etc.) in the diphthong restoration algorithm. The circumflex represents a contraction of two vowels into one, preserving a memory of the original sequence. The restoration rules must account for this:

* `a.ʾā~` → `ā` (short + long~ → long without tilde): When a short vowel is followed by a long vowel with a tilde, the result is a simple long vowel (macron). The tilde is absorbed because the second vowel already carries length.
* `ā.ʾâ~` → `â~` (long + circ~ → circ with tilde): When a long vowel is followed by a circumflex with a tilde, the result is a circumflex with a tilde, preserving the historical contraction marker.
* `a.ʾa` → `â` (short+short → circumflex): When two short vowels contract, the result is a circumflex, reflecting the historical process of vowel contraction after consonantal elision.

**THUS:** The restoration rules must respect this historical phonology. The circumflex is not just a variant of the macron—it carries specific information about the origin of the vowel. The algorithm must preserve this distinction when restoring diphthongs from their split representations. The same-base rules are derived from these historical patterns and must be applied consistently.

---

## 081-Diphthong-Different-Base-Rules

**Domain:** Orthography / Phonology / Algorithm

**WHAT:** When two vowels of different bases come into contact (typically due to the elision of a separating consonant), Akkadian phonology imposes specific constraints on how they combine. Unlike same-base pairs which may contract into a single vowel marked with a circumflex, different-base pairs (such as u + a, a + i, etc.) may form true diphthongs or remain as sequences with specific length restrictions (Huehnergard 2011, Izre'el and Cohen 2004).

**WHY:** The historical process of consonantal elision created vowel sequences across morpheme boundaries. While many such sequences eventually contracted into single vowels, others resisted full contraction and preserved their diphthongal character. Crucially, as established in note 078, the first vowel in such sequences must be short, even if it was originally long. This constraint governs the restoration rules for different-base pairs:

* `u.ʾā~` → `uā~` (short u + long~ a → uā~): The short u remains short, the long a retains its length and tilde, forming a diphthong.
* `ū.ʾā~` → `uā` (long ū + long~ a → uā): The long ū is shortened to u (per the first-vowel shortening constraint), and the long a retains its length but loses the tilde because the combined form already has two morae.
* `u.ʾa` → `ua` (short u + short a → ua): Two short vowels form a simple diphthong with no length marking.

**THUS:** The restoration algorithm must respect both the vowel quality and the length constraints. When the first vowel is long, it must be shortened before combining with the second vowel. The tilde (representing added length from stress realization) must be preserved on the second vowel when appropriate. These rules ensure that the restored diphthongs reflect both the historical phonology of Akkadian and the prosodic modifications introduced by the algorithm.

---

## 082-Diphthong-Restoration-Ordering

**Domain:** Algorithm / Diphthongs

**WHAT:** Patterns where the second vowel has a tilde must be applied first. Otherwise, shorter patterns would match incorrectly.

**WHY:** This ensures that tilde markers are preserved appropriately. The order is critical for correct output.

**THUS:** The restoration table must be carefully ordered. Second-tilde patterns come first.

---

## 083-Worked-Example-First-Line-Transliteration

**Domain:** Algorithm / Illustration

**WHAT:** The first line of Enuma Elish Tablet II in transliteration: ukappit-ma : tiāmtu pitiqša.

**WHY:** This is a representative sample from the corpus. It illustrates all key phenomena.

**THUS:** It can be used to demonstrate the algorithm step by step.

---

## 084-Worked-Example-Syllabification

**Domain:** Algorithm / Illustration

**WHAT:** Syllabified form: u·kap·pit-ma : ti·ʾā·m·tu pi·tiq·ša. Mora counts: u(1) + kap(2) + pit(2) + ma(1) = 6µ; ti(1) + ʾām(3) + tu(1) = 5µ; pi(1) + tiq(2) + ša(1) = 4µ.

**WHY:** This shows the input to the prosody realization algorithm. Odd mora words need adjustment.

**THUS:** The algorithm will target tiāmtu (5µ odd) for stress realization.

---

## 085-Worked-Example-First-Line-Enuma-Elish

**Domain:** Algorithm / Illustration

**WHAT:** The first line of Enuma Elish Tablet II (L_I.2_Poem_of_Creation_SB_II) provides a clear illustration of the algorithm. Original: "ukappit-ma : tiāmtu pitiqša". Syllabified: "u·kap·pit-ma : ti·ʾām·tu pi·tiq·ša". Accentuated: "u·kap·pit-ma : ti·ʾā~·m·tu pi·tiq·ša".

**WHY:** tiāmtu has one eligible syllable: ʾām (superheavy). Under LOB, final superheavy is priority 1. ʾām is lengthened: ʾām → ʾā~m (4µ). New total: 1+4+1 = 6µ even.

**THUS:** This example demonstrates the core operation: selecting a stress-eligible syllable according to the hierarchy and adding exactly one mora through vowel lengthening. It connects to the full ten-line worked example (note 087).

---

## 086-Worked-Example-Final-Output

**Domain:** Algorithm / Illustration

**WHAT:** Final pivot format: u·kap·pit-ma : ti·ʾā~·m·tu pi·tiq·ša. Acute output: ukappit-ma : tiʾā´mtu pitiqša. Bold output: ukappit-ma : tiʾām tu pitiqša. IPA output: u.kap.pit-ma | ti.ˈʔaːːm.tu.pi.tiq.ʃa.

**WHY:** Each format serves a different purpose. The pivot format is the master. Acute and bold are for reading. IPA is for phonetic analysis.

**THUS:** The worked example demonstrates that the algorithm produces coherent output. It can be verified by inspection.

---

## 087-Worked-Example-All-Lines

**Domain:** Algorithm / Illustration / Paper

**WHAT:** The first ten lines of Enuma Elish Tablet II are a valid candidate to include in the paper as a worked example.

**WHY:** We need a small sample text to illustrate the stress realization algorithm. The first ten lines of Enuma Elish Tablet II are ideal because:

* They contain no broken lines or lacunae—all words are intact and readable
* The passage includes a comprehensive range of realization cases: word-internal accentuations, coda gemination, function-word attachment, construct linking, and last-resort operations
* The text is long enough to show patterns across multiple lines, but short enough to present in full
* Readers can see the algorithm applied consistently to connected text, not just isolated words

**THUS:** Use these ten lines in the article as the primary worked example. Present the original transliteration, the syllabified input, the prosody-realized pivot format, and the final outputs (acute, bold, IPA). The goal is not to analyze their metrics, but to help the reader understand how the algorithm works through a concrete, real-world example. The visual pattern of bolded or accented syllables will make the rhythmic structure immediately apparent.

---

## 088-Corpus-Global-Statistics

**Domain:** Corpus / Quantitative

**WHAT:** The full corpus contains 4,917 words and 14,684 syllables. Of these, 2,001 syllables are prominent (13.63%). 2,453 words participate in merging (49.9%), forming 1,108 units with average size 2.21 words.

**WHY:** These numbers emerge from the data. They are not designed parameters. The prominence rate falls within the plausible range for stress-timed languages.

**THUS:** The model produces quantitatively reasonable outputs. The merge statistics show that prosodic restructuring is extensive, as expected in connected speech.

---

## 089-Accentuations-By-Syllable-Type

**Domain:** Corpus / Quantitative

**WHAT:** CV syllables are almost never prominent (only 4 cases). CVC syllables become prominent in 21.6% of cases. CVV syllables become prominent in 30.0% of cases. VC syllables become prominent in 16.8% of cases. Superheavy syllables are often prominent (44.8% of CVVC, 75% of VVC).

**WHY:** This distribution follows from the design principles. CV syllables cannot be lengthened. Heavy syllables are eligible. Superheavy syllables are marked and often require adjustment.

**THUS:** The distribution is principled and interpretable. It reflects the underlying phonology.

---

## 090-Accentuation-Types-Distribution

**Domain:** Corpus / Quantitative

**WHAT:** Vowel lengthening is the most common operation (applied to CVV and CVVC syllables). Coda gemination is the second most common (applied to CVC and VC). Onset gemination is extremely rare (4 cases). Glottal gemination is not observed.

**WHY:** This follows from the frequency of syllable types. CVV and CVC are common. Onset gemination is a last resort.

**THUS:** The distribution is natural. It reflects the structure of the language.

---

## 091-Accentuated-Text-Metrics

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Corpus / Quantitative

**WHAT:** After stress realization, %V (pause-excluded) is 74.43%. %V (35% pauses) is 55.14%. ΔC is 0.7822 morae. MeanC is 1.1068 morae. VarcoC is 70.67.

**WHY:** VarcoC remains firmly in the stress-timed range. %V moves closer to the English range. Both changes are in the expected direction.

**THUS:** The prosodically realized text remains compatible with stress-timing. The algorithm does not distort the rhythmic classification.

---

## 092-Original-Metrics-Sensitivity

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Metrics / Pauses

**WHAT:** %V for the original text varies with pause ratio: 30% pauses → 61.46%, 35% pauses → 59.18%, 40% pauses → 57.07%.

**WHY:** This shows the effect of pause assumptions. The exact pause ratio is unknown, so sensitivity analysis is necessary.

**THUS:** The range of plausible values is reported. The core conclusion (stress-timing) is robust across this range.

---

## 093-Accentuated-Metrics-Sensitivity

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Metrics / Pauses

**WHAT:** %V for the accentuated text varies with pause ratio: 30% pauses → 57.26%, 35% pauses → 55.14%, 40% pauses → 53.17%.

**WHY:** This shows the effect of pause assumptions on the accentuated text. The values are consistently lower than the original.

**THUS:** The accentuation reduces %V, moving it closer to the English range. This is in the expected direction.

---

## 094-Pause-Classification-Short

**Domain:** Metrics / Pauses

**WHAT:** Short pauses include: , ; : — … ( ) « » “ ” ‘ ’ " ' – / \ & † ‡ |. Standalone ellipsis is short when it appears as missing-text punctuation.

**WHY:** These are defined in the metrics module. They represent intra-phrase boundaries.

**THUS:** The classification is explicit and reproducible.

---

## 095-Pause-Classification-Long

**Domain:** Metrics / Pauses

**WHAT:** Long pauses include: . ? ! [ ] { } < > * + (when acting as punctuation). Hyphen acting as punctuation (not surrounded by words) is long. Word-attached ellipsis is long.

**WHY:** These are defined in the metrics module. They represent phrase-final boundaries.

**THUS:** The classification is explicit and reproducible.

---

## 096-Pause-Statistics

**Domain:** Metrics / Pauses

**WHAT:** Short pauses per syllable: 0.053. Long pauses per syllable: 0.076. Total pauses per syllable: 0.128. Total boundaries: 3,228. Pauseable boundaries: 1,883. Short pauseable: 772. Long pauseable: 1,111.

**WHY:** These numbers come from the corpus. They quantify the pause structure of the texts.

**THUS:** They provide a baseline for pause modeling and speech rate estimation.

---

## 097-Pause-Duration-Initial

**Domain:** Metrics / Pauses

**WHAT:** Initial short pause duration (30% ratio): 0.179 s. Initial long pause duration (30% ratio): 0.358 s. Initial short pause duration (35% ratio): 0.209 s. Initial long pause duration (35% ratio): 0.418 s. Initial short pause duration (40% ratio): 0.239 s. Initial long pause duration (40% ratio): 0.478 s.

**WHY:** These are computed from the pause ratio and weights. They represent the initial allocation before correction.

**THUS:** They provide the baseline for pause correction.

---

## 098-Pause-Correction-Algorithm

**Domain:** Metrics / Pauses

**WHAT:** The pause correction algorithm aligns all pauses with the bimoraic rhythm. Short pauses are set to the nearest multiple of 2 morae. Long pauses are adjusted to preserve the total pause time, with some rounded up and some rounded down.

**WHY:** It would be inconsistent to align words to multiples of 2 morae while allowing pauses to have arbitrary durations like 1.5 or 2.3 morae. The entire temporal structure—both speech and silence—should reflect the same rhythmic organization. Short pauses, which occur more frequently, are kept identical in duration to create a regular beat. Long pauses are adjusted as needed, but the overall average respects the configured pause ratio while ensuring that every pause, individually, aligns with the 2-mora rhythm.

**THUS:** The corrected short pause duration is a fixed multiple of 2 morae. Long pauses vary to maintain the total pause budget, but each is also a multiple of 2 morae. This ensures that the entire utterance, including its silent intervals, is rhythmically coherent.

---

## 099-Pause-Correction-30-Percent

**Domain:** Metrics / Pauses

**WHAT:** At 30% pause ratio: initial short 0.179 s → corrected short 0.206 s (+0.027). Initial long 0.358 s → corrected long 0.340 s (-0.018). Corrected long:short ratio 1.7.

**WHY:** The correction aligns short pauses with the bimoraic rhythm (multiple of 2 morae). Long pauses adjust to maintain total pause time.

**THUS:** The corrected values are used for speech rate estimation.

---

## 100-Pause-Correction-35-Percent

**Domain:** Metrics / Pauses

**WHAT:** At 35% pause ratio: initial short 0.209 s → corrected short 0.191 s (-0.018). Initial long 0.418 s → corrected long 0.431 s (+0.013). Corrected long:short ratio 2.3.

**WHY:** The correction aligns short pauses with the bimoraic rhythm. Long pauses adjust to maintain total pause time.

**THUS:** The corrected values are used for speech rate estimation.

---

## 101-Pause-Correction-40-Percent

**Domain:** Metrics / Pauses

**WHAT:** At 40% pause ratio: initial short 0.239 s → corrected short 0.235 s (-0.004). Initial long 0.478 s → corrected long 0.481 s (+0.003). Corrected long:short ratio 2.0.

**WHY:** The correction aligns short pauses with the bimoraic rhythm. Long pauses adjust to maintain total pause time.

**THUS:** The corrected values are used for speech rate estimation.

---

## 102-Speech-Rate-Estimation-Introduction

**Domain:** Speculative / Illustration

**WHAT:** Information rate constancy suggests that languages may transmit information at broadly comparable rates despite differing syllable rates (Pellegrino et al. 2011). As a rough heuristic, this places many languages in the vicinity of 3-4 words per second, even when syllables per second differ.

**WHY:** This provides a cautious basis for estimating speech rate when absolute timing is unknown. The claim is not that Akkadian shared the same rate exactly, but that cross-linguistic regularities in information flow make a rough estimate less arbitrary than choosing a number in isolation.

**THUS:** Speech rate can be estimated from word count and syllable count, with assumptions.

---

## 103-Akkadian-Syllables-Per-Word

**Domain:** Speculative / Quantitative

**WHAT:** From the corpus: 14,684 syllables / 4,917 words = 2.99 syllables per word.

**WHY:** This is a direct count from the data. It is not an assumption.

**THUS:** It provides a baseline for speech rate estimation.

---

## 104-Speech-Rate-Range

**Domain:** Speculative / Estimation

**WHAT:** Assuming 165 words per minute (mid-range for English prose): SPS = (165/60) × 2.99 = 8.2 syllables per second. With 30-40% pause ratio, articulation rate would be 11.7-13.7 syllables per second.

**WHY:** These figures are purely illustrative. They depend on assumptions borrowed from modern languages.

**THUS:** They are not reconstructions. They give a sense of scale but should not be mistaken for facts.

---

## 105-Mora-Duration

**Domain:** Speculative / Estimation

**WHAT:** At 8.2 SPS, syllable duration = 0.122 s. Mean morae per syllable (accentuated) = 2.479. Mora duration = 0.122 / 2.479 = 0.049 s (49 ms). At 11.7 SPS, mora duration = 0.034 s (34 ms). At 13.7 SPS, mora duration = 0.029 s (29 ms).

**WHY:** These are derived from the speech rate estimates. They are speculative.

**THUS:** They provide a sense of temporal scale but are not reliable reconstructions.

---

## 106-ΔC-In-Seconds

**Domain:** Speculative / Estimation / Methodology

**WHAT:** The ΔC metric, when expressed in seconds rather than morae, would allow direct comparison with measurements from living languages. Using the estimated parameters from the metrics output, original text (WPM: 165, pause ratio: 35%, mora duration: 0.049 s/mora), ΔC_sec = ΔC × mora duration = 0.6917 × 0.049 = 0.0338 s (33.8 ms).

**WHY:** This value is lower than the 64–80 ms range reported for English by Ramus et al. (1999). However, such a direct comparison is methodologically problematic. Akkadian's ΔC is measured in morae, not seconds, and the conversion to seconds depends entirely on assumed speech rate and mora duration. The numbers used here are extrapolated from modern language averages and are not reliable reconstructions.

**THUS:** Rather than treating this as a failed comparison, it highlights an important research direction: speech rate estimation for Akkadian. The average words-per-minute in modern languages translates to a relatively stable information rate. By assuming an average of ~3 words per second (a cross-linguistic norm) and that the pauses are 35% of the speech, we can extrapolate to syllables per second for Akkadian based on its mean syllables per word (2.986 from the corpus). From this, mora duration can be computed, and ΔC_sec can be derived. The result (33.8 ms) is presented not as a finding, but as an illustration of how such an estimate could be made if speech rate were known. This underscores the speculative nature of any temporal reconstruction for ancient languages.

---

## 106b-Why-Speech-Rate-Is-Speculative

**Domain:** Methodology / Limitations

**WHAT:** Any attempt to convert mora-based metrics to absolute time (seconds) requires assumptions about speech rate that cannot be directly verified for Akkadian.

**WHY:** Speech rate varies within and across languages based on speaker, genre, emotional state, and countless other factors. Even for living languages, reported rates vary widely: English reading rates range from 150 to 200 words per minute depending on the study (Tauroza and Allison 1990). For a dead language with no native speakers, any single rate is an arbitrary choice.

**THUS:** The ΔC-in-seconds calculation (26.6 ms) is presented not as a finding but as an illustration of what would be possible if speech rate were known. It does not affect the core argument, which relies on rate-independent metrics (VarcoC) and relative comparisons within the moraic framework. Readers are cautioned against treating these numbers as reconstructions.

---

## 107-CVVC-Sensitivity-Analysis

**Domain:** Corpus / Validation

**WHAT:** Two treatments of CVVC syllables were tested: lengthen (3µ → 4µ) or shorten (3µ → 2µ). Both yield stress-timed VarcoC. The difference (0.1) is well within the 95% CI.

**WHY:** This shows that the rhythmic classification is robust. It does not depend on the CVVC treatment.

**THUS:** The choice of treatment does not affect the main conclusion. Hypothesis A (lengthen) was chosen as more conservative for Old Babylonian.

---

## 108-CVVC-Hypothesis-A

**Domain:** Corpus / Validation

**WHAT:** Hypothesis A (lengthen): CVVC → CVV~C (3µ → 4µ). This preserves lexical length distinctions and is more conservative for Old Babylonian.

**WHY:** CVVC syllables were historically unstable, but in the Old Babylonian period they were still present. Lengthening respects the synchronic state.

**THUS:** This hypothesis is the default for the main analysis.

---

## 109-CVVC-Hypothesis-B

**Domain:** Corpus / Validation

**WHAT:** Hypothesis B (shorten): CVVC → CVC (3µ → 2µ). This follows the later historical development. It may be more appropriate for later dialects.

**WHY:** CVVC syllables disappeared in later Akkadian. Shortening reflects this diachronic trend.

**THUS:** This hypothesis is tested for sensitivity analysis. It may be relevant for different periods.

---

## 110-Accentuation-Rate-Emergent-Property

**Domain:** Algorithm / Interpretation

**WHAT:** The 13.63% prominence rate is not a designed parameter. It emerges from the interaction of syllable type distribution, word boundaries, rules, and merge logic.

**WHY:** This is important. The rate is not tuned. It is a consequence of the model's structure.

**THUS:** The rate provides indirect validation. It falls within a plausible range for stress-timed languages.

---

## 111-Accentuation-Rate-Plausibility

**Domain:** Algorithm / Interpretation

**WHAT:** Stress-timed languages typically realize 15-20% of syllables as prominent. Akkadian's 13.63% is at the lower end but still plausible.

**WHY:** Cross-linguistic comparison supports this range. The rate is not an outlier.

**THUS:** The model's output is quantitatively reasonable. This strengthens its plausibility.

---

## 112-What-Model-Claims

**Domain:** Meta / Scope

**WHAT:** The model claims: 1) Akkadian's structure is compatible with stress-timing. 2) The academic model provides a candidate set. 3) Some mechanism must select among candidates in connected speech. 4) The proposed mechanism uses phonologically legal operations. 5) The output is internally coherent and testable. 6) The prominence rate emerges from the data.

**WHY:** Each claim is defensible within its scope. The model does not overreach.

**THUS:** The claims are modest but significant. They show that a coherent system can be built from the lexical rules.

---

## 113-What-Model-Does-Not-Claim

**Domain:** Meta / Scope

**WHAT:** The model does not claim: 1) This is the only possible mechanism. 2) Every prominent syllable was phonetically prominent. 3) The exact 13.63% rate is historically correct. 4) The CVVC treatment is historically correct. 5) Speech rate can be reliably reconstructed. 6) Akkadian was stress-timed—only that its structure is compatible.

**WHY:** These limitations are explicitly stated. They prevent misinterpretation of the results.

**THUS:** The model is presented as a hypothesis, not a reconstruction. It invites testing and refinement.

---

## 114-Core-Contribution

**Domain:** Meta / Synthesis

**WHAT:** The model shows that a rhythmically coherent output can be generated from the academic stress rules using operations that are phonetically plausible and philologically grounded.

**WHY:** This bridges the gap between writing and speech. The academic model describes writing and meter. This model describes one possible speech realization.

**THUS:** The contribution is to show that the gap can be filled, not to claim that this is how it was actually filled.

---

## 115-Implications-For-Assyriology

**Domain:** Implications / Field

**WHAT:** The academic stress model is not wrong—it is incomplete. It provides the candidate set. Plene spelling may mark phonetic prominence, not lexical length. Syncope can be reanalyzed as a stress realization strategy.

**WHY:** These reinterpretations follow from the model. They offer new perspectives on old data.

**THUS:** The model has implications beyond its immediate claims. It suggests new ways of thinking about familiar phenomena.

---

## 116-Implications-For-Historical-Phonetics

**Domain:** Implications / Field

**WHAT:** Quantitative methods can generate testable hypotheses about ancient prosody. Metrics designed for acoustic signals can be adapted to written text with explicit assumptions. Multiple hypotheses are possible; the goal is constraint, not unique solution.

**WHY:** This demonstrates a methodological approach. It can be applied to other ancient languages.

**THUS:** The model contributes to historical phonetics as a field. It shows what is possible with careful assumptions.

---

## 117-Implications-For-Linguistic-Typology

**Domain:** Implications / Field

**WHAT:** Akkadian represents a transitional type: stress-timed but with preserved lexical weight and moderate closed syllable frequency. The model shows how a language could evolve from mora-timing to stress-timing.

**WHY:** This adds to our understanding of rhythmic typology. It shows that categories are not discrete.

**THUS:** The model contributes to theoretical linguistics. It provides data for typological comparison.

---

## 118-Limitations-Single-Corpus

**Domain:** Limitations / Scope

**WHAT:** Results are based on three texts from the Standard Babylonian literary corpus. Verification on other genres and periods would strengthen the conclusions.

**WHY:** Different texts might yield different results. The model should be tested more broadly.

**THUS:** This is a limitation of the current study. Future work should expand the corpus.

---

## 119-Limitations-Literary-Register

**Domain:** Limitations / Scope

**WHAT:** Literary recitation may differ from colloquial speech. The model is proposed for the former. Its applicability to the latter is unknown.

**WHY:** Literary texts may have special prosodic conventions. Colloquial speech might be different.

**THUS:** The model is explicitly limited to literary texts. It does not claim to represent everyday speech.

---

## 120-Limitations-Metrics-Controversy

**Domain:** Limitations / Methodology

**WHAT:** The application of acoustic metrics to written text is not uncontroversial. The assumptions have been made explicit.

**WHY:** Different assumptions would yield different numbers. The goal is to show that under plausible assumptions, Akkadian patterns with stress-timed languages.

**THUS:** The limitations are acknowledged. The model does not overclaim.

---

## 121-Limitations-Parameter-Choices

**Domain:** Limitations / Methodology

**WHAT:** Different rules (different hierarchy, different legal/illegal definitions) would yield different results. The code invites experimentation.

**WHY:** The model is one implementation among many. It is not the only possible one.

**THUS:** The parameters are choices, not truths. Others can test alternative choices.

---

## 122-Limitations-CVVC-Treatment

**Domain:** Limitations / Methodology

**WHAT:** The choice to lengthen CVVC syllables is not empirically settled. Shortening would also be plausible, especially for later dialects.

**WHY:** CVVC syllables were historically unstable. Both treatments have historical support.

**THUS:** The choice is acknowledged as a decision, not a fact. Sensitivity analysis shows it does not affect classification.

---

## 123-Limitations-Speech-Rate

**Domain:** Limitations / Methodology

**WHAT:** Speech rate cannot be reliably reconstructed. Estimates are speculative and depend on assumptions.

**WHY:** We have no recordings of ancient speech. Any rate is an informed guess.

**THUS:** Speech rate estimates are presented as illustrations, not findings. They do not affect the core argument.

---

## 124-Limitations-Statistical-Power

**Domain:** Limitations / Methodology

**WHAT:** Larger corpora would enable more robust comparisons. The current corpus is substantial but not exhaustive.

**WHY:** Statistical power increases with sample size. More texts would strengthen confidence in the results.

**THUS:** This is an area for future work. Expanding the corpus is a priority.

---

## 125-Research-Process-Transparency

**Domain:** Meta / Documentation

**WHAT:** The research process is documented to allow replication and critique. All code is provided in the appendices. Key decision points are recorded.

**WHY:** Transparency is essential for scientific credibility. Others should be able to verify the work.

**THUS:** The project follows open science principles. It invites scrutiny and improvement.

---

## 126-Development-History

**Domain:** Meta / Documentation

**WHAT:** The algorithm was developed through extensive trial and error. Key decision points included syllabification rules, legal vs. illegal operations, the accentuation hierarchy, and merge logic.

**WHY:** This history is documented to show the evolution of the ideas. It provides context for the final decisions.

**THUS:** The research process is transparent. Others can see how the model developed.

---

## 127-Debugging-Process

**Domain:** Meta / Documentation

**WHAT:** The algorithm was tested on a 4-line, 27-word, 20-syllable sample with 100% accuracy before full corpus application.

**WHY:** Small-sample validation built confidence before scaling. It ensured the implementation was correct.

**THUS:** The model was validated incrementally. This reduced the risk of errors in the full corpus run.

---

## 128-Chain-Of-Reasoning

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Meta / Synthesis

**WHAT:** The chain of reasoning: 1) Auditory intuition → something wrong. 2) Analysis → academic model has no rhythm. 3) Metrics → Akkadian is compatible with stress-timing. 4) Failed attempts → arbitrary compression fails. 5) Arabic insight → CVC as rhythmic unit. 6) Symmetry → add, don't subtract. 7) Academic model → provides candidate set. 8) Rules → legal operations, hierarchy. 9) Merge → handles cross-word cases. 10) Implementation → working algorithm. 11) Results → 13.63% prominence rate, coherent metrics. 12) Sensitivity → CVVC choice doesn't affect classification. 13) Conclusion → academic model describes writing; this model describes one possible speech realization.

**WHY:** This logical flow is transparent. Each step follows from the previous one.

**THUS:** The argument is coherent and defensible. It builds from observation to hypothesis to test.

---

## 129-Final-Synthesis

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Meta / Conclusion

**WHAT:** When European scholars recite Akkadian, it sounds rhythmless. The academic stress model provides no mechanism for phrasal timing. Yet acoustic metrics show Akkadian's structure is compatible with stress-timing. This paradox requires a solution. The proposed algorithm adds exactly one mora to selected syllables through vowel lengthening or gemination, following a hierarchy based on attested stress rules. It affects 13.63% of syllables—a rate that emerges from the data. The model works: it produces a rhythmically coherent output from the academic rules using operations grounded in Akkadian phonology.

**WHY:** The academic model is not wrong—it describes where stress could go. This model describes how it might have worked in connected speech.

**THUS:** The gap between writing and speech can be filled. This is one possible way to fill it. The code is open for testing and refinement.

---

## 130-Speech-Rhythm-Typology-Introduction

**Domain:** Rhythm / Theory

**WHAT:** The Rhythm Class Hypothesis traditionally divides languages into stress-timed, syllable-timed, and mora-timed categories (Ramus et al. 1999, Nazzi and Ramus 2003).

**WHY:** This framework provides a way to classify languages based on their temporal structure.

**THUS:** It can be applied to Akkadian to determine its rhythmic type.

---

## 131-Stress-Timed-Characteristics

**Domain:** Rhythm / Theory

**WHAT:** Stress-timed languages show alternation between strong and weak syllables and typically display comparatively high consonantal variability. English commonly falls in the VarcoC range of roughly 70-80, with Dutch close behind (White and Mattys 2007).

**WHY:** These characteristics produce high ΔC and VarcoC values and give a practical comparative baseline for identifying the stress-timed end of the rhythm continuum.

**THUS:** If Akkadian shows high VarcoC, it may be stress-timed.

---

## 132-Syllable-Timed-Characteristics

**Domain:** Rhythm / Theory

**WHAT:** Syllable-timed languages have syllables of approximately equal duration with relatively limited reduction and lower consonantal variability. French and Spanish, for example, are commonly reported around VarcoC values of roughly 50-55 (White and Mattys 2007).

**WHY:** These characteristics produce lower ΔC and VarcoC values and therefore provide the principal comparison set for testing whether Akkadian is too variable to belong near the syllable-timed end.

**THUS:** If Akkadian showed low VarcoC, it would be syllable-timed. It does not.

---

## 133-Mora-Timed-Characteristics

**Domain:** Rhythm / Theory

**WHAT:** Mora-timed languages base rhythm on the mora, a unit smaller than the syllable. Japanese is the prototypical example (Ramus et al. 1999, Sugai 2017).

**WHY:** Mora-timing produces very regular consonant spacing and very low ΔC.

**THUS:** Akkadian's high VarcoC rules out mora-timing.

---

## 134-Entrainment-Research

**Domain:** Rhythm / Cognitive

**WHAT:** Rhythmic entrainment is the automatic synchronization with external temporal regularities. Benefits are maintained even with deviations up to 50 ms (Cutanda et al. 2019).

**WHY:** This shows that listeners tolerate some variability. Perfect isochrony is not required.

**THUS:** The model does not need to achieve perfect timing. Approximate isochrony is sufficient.

---

## 135-Infant-Rhythm-Perception

**Domain:** Rhythm / Cognitive

**WHAT:** Newborns can discriminate languages of different rhythmic classes but fail to distinguish those within the same class (Nazzi and Ramus 2003). Between birth and 5 months, infants shift to focusing on their native language's rhythm.

**WHY:** This shows that rhythm is a fundamental perceptual category. It is acquired early.

**THUS:** Akkadian's rhythmic classification has implications for how it might have been perceived by native speakers.

---

## 136-Language-Impairment-Rhythm

**Domain:** Rhythm / Clinical

**WHAT:** Children with language impairment are slower and less isochronous during internal rhythm generation. Their performance normalizes with an external rhythmic model (Georgiadou et al., no date).

**WHY:** This shows that rhythm deficits are linked to language impairment. Rhythm is integral to language processing.

**THUS:** The model's focus on rhythm is linguistically and cognitively motivated.

---

## 137-Dyslexia-Rhythm-Deficit

**Domain:** Rhythm / Clinical

**WHAT:** Developmental dyslexia is characterized as a temporal sampling deficit. Dyslexic adolescents show larger synchronization error during slow-paced rhythmic tasks (Rossi et al. 2023).

**WHY:** This further links rhythm processing to language abilities.

**THUS:** The study of rhythm in ancient languages connects to broader research on language and cognition.

---

## 138-Memorization-Rhythm-Connection

**Domain:** Rhythm / Comparative / Oral Culture

**WHAT:** Rhythmic speech helps memorize knowledge in oral cultures. In societies where writing is restricted to a small elite, the transmission and preservation of knowledge require additional cognitive supports to aid recall. Rhythm, meter, and formulaic patterns serve as these supports in poetry, ritual speech, and common discourse.

**WHY:** Research on oral traditions across cultures demonstrates that rhythm is a fundamental mnemonic device. Marcel Jousse, the 20th-century French anthropologist, identified what he called "rhythmo-mnemonic expression" as a universal feature of oral cultures, where knowledge is encoded in rhythmic, formulaic patterns that make it transmissible across generations without writing. His work on "The Oral Style" documents how gesture, rhythm, and formulaic structures function as a "living press" for the preservation of cultural memory.

**THUS:** Poetry and formal prose in oral cultures must carry strong rhythmic structures in order to consolidate information exchange and diffusion. The rhythm compensates for the lack of written support, enabling memorization, transmission, and faithful reproduction of texts across generations. This cross-cultural evidence suggests that any ancient text transmitted orally—including Akkadian literature—would likely have been shaped by similar rhythmic constraints.

---

## 139-Phonological-Processes-Summary

**Domain:** Phonology / Synthesis

**WHAT:** Akkadian has numerous native processes that involve adjusting moraic structure: syncope, anaptyxis, assimilation, gemination, and vowel lengthening.

**WHY:** These processes show that the language already has the phonological resources needed for the model.

**THUS:** The model's operations are grounded in actual Akkadian phonology, not invented for the purpose.

---

## 140-Syllable-Structure-Constraints-Summary

**Domain:** Phonology / Synthesis

**WHAT:** Akkadian syllable structure is constrained: no complex onsets, no complex codas, no tri-consonantal clusters, no word-final geminates.

**WHY:** These constraints shape all phonological processes. They must be respected by any model.

**THUS:** The model's illegal operations are defined by these constraints. This ensures phonological plausibility.

---

## 141-Academic-Model-Summary

**Domain:** Academic Model / Synthesis

**WHAT:** The academic stress model (Huehnergard 2011; Streck 2022) provides a candidate set based on syllable weight. It describes lexical stress in isolated words.

**WHY:** This is the established description. It is philologically grounded and widely accepted, and it remains consistent with broader grammatical treatments of Akkadian phonology and stress domains (Buccellati 1996).

**THUS:** It serves as the foundation for the prosody realization model. The model extends it, does not replace it.

---

## 142-Metrics-Summary

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Metrics / Synthesis

**WHAT:** Metrics computed from the corpus show that Akkadian's structure is compatible with stress-timing (VarcoC = 69.09). After prosody realization, VarcoC = 70.67, remaining in the stress-timed range.

**WHY:** This empirical finding is independent of the model. It provides the motivation for the model.

**THUS:** The model is grounded in data. It addresses a real phenomenon, not a theoretical artifact.

---

## 143-Algorithm-Summary

**Domain:** Algorithm / Synthesis

**WHAT:** The algorithm selects stress-eligible syllables using the LOB/SOB hierarchy, adds exactly one mora through vowel lengthening or coda gemination, merges words when necessary, and respects all phonological constraints.

**WHY:** This provides a deterministic, testable mechanism for phrasal timing.

**THUS:** The algorithm fills the gap identified in the academic model. It shows one possible way stress could have been realized in connected speech.

---

## 144-Results-Summary

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Corpus / Synthesis

**WHAT:** The algorithm affects 13.63% of syllables. Nearly half of all words participate in prosodic merging. The prosodically realized text yields VarcoC = 70.67, remaining in the stress-timed range.

**WHY:** These results emerge from the data. They are not designed parameters.

**THUS:** The model produces quantitatively reasonable outputs. It is internally coherent and testable.

---

## 145-Sensitivity-Summary

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Corpus / Synthesis

**WHAT:** Sensitivity analysis shows that the CVVC treatment does not affect the rhythmic classification. Pause ratio assumptions affect %V but not VarcoC.

**WHY:** This strengthens confidence in the core conclusion. The stress-timing result is robust.

**THUS:** The model's main finding is reliable. It does not depend on fine-tuned parameters.

---

## 146-Scope-Summary

**Domain:** Meta / Synthesis

**WHAT:** The model is limited to literary Old Babylonian texts. It does not claim to represent colloquial speech or later dialects. It presents one possible hypothesis, not a reconstruction.

**WHY:** These limitations are explicitly stated. They prevent overinterpretation.

**THUS:** The model is presented responsibly. It invites testing and refinement, not blind acceptance.

---

## 147-Implications-Summary

**Domain:** Meta / Synthesis

**WHAT:** The model has implications for Assyriology, historical phonetics, and linguistic typology. It suggests new ways of thinking about plene spelling, syncope, and rhythmic classification.

**WHY:** These implications follow from the model's assumptions and results.

**THUS:** The model contributes beyond its immediate claims. It opens new avenues for research.

---

## 148-Open-Questions

**Domain:** Meta / Future

**WHAT:** Would other accent hierarchies yield different results? How would the model perform on other genres (letters, royal inscriptions)? Could the operations be applied to other Semitic languages?

**WHY:** These questions remain open. They point to future work.

**THUS:** The model is not the final word. It is a starting point for further investigation.

---

## 149-Future-Work-Expanded-Corpus

**Domain:** Future / Research

**WHAT:** The model should be tested on other Akkadian texts: Gilgamesh, Code of Hammurabi, royal inscriptions, letters, administrative documents.

**WHY:** Different genres may have different prosodic structures. Testing broadly would validate or refine the model.

**THUS:** Expanding the corpus is a priority for future research.

---

## 150-Future-Work-Dialectal-Variation

**Domain:** Future / Research

**WHAT:** Akkadian had dialectal variation (Old Assyrian, Old Babylonian, Standard Babylonian, Neo-Assyrian, Neo-Babylonian). The model should be tested on different dialects.

**WHY:** Prosody may have varied across dialects and time periods. The model's assumptions may need adjustment.

**THUS:** Dialectal comparison is an important direction for future work.

---

## 151-Future-Work-Colloquial-Speech

**Domain:** Future / Research

**WHAT:** The model is based on literary texts. Colloquial speech may have been different. How could we model it with no direct evidence?

**WHY:** This is a fundamental limitation. We have no recordings of everyday Akkadian speech.

**THUS:** The model remains speculative for colloquial registers. It is explicitly limited to literary texts.

---

## 152-Future-Work-TTS-Integration

**Domain:** Future / Application

**WHAT:** The IPA output could be fed to a speech synthesizer to produce audible Akkadian. This would test the model's perceptual plausibility.

**WHY:** Native speakers of related languages could evaluate the synthesized speech. Does it sound natural?

**THUS:** TTS integration is a promising direction for validation.

---

## 153-Future-Work-Experimental-Testing

**Domain:** Future / Research

**WHAT:** Native speakers of Arabic and Hebrew could be asked to evaluate the prosodically realized texts. Does the rhythm feel natural to speakers of related languages?

**WHY:** This would provide perceptual validation. It would test whether the model produces plausible Semitic rhythm.

**THUS:** Experimental testing is a long-term goal.

---

## 154-Future-Work-Alternative-Hierarchies

**Domain:** Future / Research

**WHAT:** Other accent hierarchies could be tested. The current LOB and SOB models are two possibilities. Others may exist.

**WHY:** The choice of hierarchy affects the output. Different hierarchies might yield different results.

**THUS:** Exploring alternative hierarchies is important for understanding the model's sensitivity.

---

## 155-Future-Work-Operation-Variants

**Domain:** Future / Research

**WHAT:** Other operations could be considered. Could syncope be used prosodically? Could anaptyxis be used to add morae?

**WHY:** The current operations are conservative. Other possibilities may exist.

**THUS:** Exploring alternative operations is a direction for future work.

---

## 156-Future-Work-Merge-Strategies

**Domain:** Future / Research

**WHAT:** Other merge strategies could be tested. The current left-to-right forward merge is one possibility. Could optimal merging improve results?

**WHY:** Merge logic affects the output. Different strategies might yield different prominence rates.

**THUS:** Exploring alternative merge strategies is a direction for future work.

---

## 157-Future-Work-Pause-Modeling

**Domain:** Future / Research

**WHAT:** Pause modeling could be refined. The current correction to multiples of 2 morae is a first step. Could more sophisticated pause models improve speech rate estimates?

**WHY:** Pauses are an important part of speech rhythm. Better modeling would improve the IPA output.

**THUS:** Refining pause modeling is a direction for future work.

---

## 158-Future-Work-Statistical-Analysis

**Domain:** Future / Research

**WHAT:** More sophisticated statistical analysis could be applied. Mixed-effects models could account for word-level and text-level variation.

**WHY:** This would provide stronger inference about the model's predictions.

**THUS:** Advanced statistical analysis is a direction for future work.

---

## 159-Future-Work-Open-Source-Development

**Domain:** Future / Application

**WHAT:** The code is open source and available on GitHub. Others can use it, test it, and contribute to it.

**WHY:** Open science principles encourage collaboration and improvement.

**THUS:** The project invites community involvement. It is not a closed, finished product.

---

## 160-Summary-of-Key-Contributions

**computed metrics are revised - note to be reviewed against new metrics**

**Domain:** Meta / Conclusion

**WHAT:** This research makes several interconnected contributions to Assyriology, historical phonetics, and computational linguistics:

1. **Empirical finding:** Acoustic metrics applied to a corpus of 4,917 words show that Akkadian's phonological structure is compatible with stress-timing (VarcoC = 69.09).

2. **Theoretical reframing:** The academic stress model (Huehnergard, Streck) is reinterpreted as providing a candidate set of stress-eligible positions, not a full account of phrasal realization.

3. **Computational model:** A prosody realization algorithm selects among these candidates using phonologically legal operations (vowel lengthening, coda gemination) to achieve bimoraic alignment at the phrase level.

4. **Quantitative validation:** The algorithm produces a prominence rate of 13.63%, which emerges from the data and falls within the plausible range for stress-timed languages. VarcoC after realization (70.67) remains in the stress-timed range.

5. **Open implementation:** The code is publicly available, allowing others to test, critique, and extend the model.

**WHY:** Each contribution builds on the previous one, creating a coherent argument from observation to implementation.

**THUS:** The project demonstrates that a rhythmically coherent prosodic system can be built from the lexical stress rules of Akkadian. It does not claim to reconstruct ancient speech, but shows that such a reconstruction is possible under plausible assumptions. The work invites further testing on other texts, dialects, and languages.

---

## 161-Vowel-Coloring

**Domain:** Phonetics / Phonology

**WHAT:** Emphatic consonants in Semitic languages are produced with a secondary pharyngeal constriction that retracts the tongue body, lowering the second formant (F2) of adjacent vowels (Hermes 2018; Almomany 2026). This process, known as vowel coloring or emphasis spread, systematically shifts plain vowels to backed allophones: /a/ → /ɑ/, /i/ → /ɨ/, /u/ → /ʉ/ (Hermes 2018; Almomany 2026). The same written vowel (e.g., alif) is pronounced differently depending on the preceding consonant (Hermes 2018).

**WHY:** Vowel coloring is a predictable phonological process that must be accounted for in phonetic transcription, speech synthesis, and text-to-speech systems (Almomany 2026). Failure to apply these rules results in unnatural or incorrect pronunciation.

**THUS:** Speech processing software handling Semitic languages must implement vowel backing rules triggered by emphatic consonants (q, ṣ, ṭ) to generate accurate phonetic output (Hermes 2018). The acoustic correlate—lowered F2—serves as a measurable benchmark for verification (Almomany 2026).

---

## 162-Corrected-Interval-Definitions

**Domain:** Metrics / Methodology

**WHAT:** In rhythm metrics, vocalic intervals are defined as vowels or sequences of contiguous vowels, while consonantal intervals are sequences of one or more contiguous consonants (Patel and Daniele 2003). Patel and Daniele (2003) also make clear that nPVI is applied to successive vocalic intervals as a relative measure of duration variability. The relevant quantity is the physical duration of the interval itself, measured in milliseconds, and not the spacing between consonants (White and Mattys in press). Earlier project notes misread distC as the vowel-filled gap between consonants. That interpretation is incorrect.

**WHY:** This correction changes the computational basis of ΔC, ΔV, VarcoC, VarcoV, and nPVI-V. Metrics derived from consonant spacing are not directly comparable to the Ramus-Dellwo tradition, because that literature explicitly measures interval duration from the acoustic signal rather than inter-consonantal distance (Ramus 2002). Visual analysis of waveforms and spectrograms is required to accurately segment these building blocks of rhythm (White and Mattys in press).

**THUS:** Any earlier note or draft section that used the old definition must be treated as obsolete until the metrics are recomputed with true vocalic and consonantal intervals.

---

## 163-Extended-Rhythm-Indicator-Set

**Domain:** Metrics / Comparative Framework

**WHAT:** The revised quantitative argument should use a cluster of indicators rather than a single preferred metric. The working set for v5 is: ΔC, %V, ΔV, VarcoV, nPVI-V, rPVI-C, and VarcoC (White and Mattys in press).

**WHY:** Different indicators capture different structural consequences of rhythmic organization. %V tracks the share of vocalic material, ΔC and VarcoC capture consonantal interval variability resulting from phonotactic permissiveness (Ramus, Nespor, and Mehler 1999). Metrics like ΔV, VarcoV, and nPVI-V capture vocalic variability and sequential alternation, which are highly sensitive to vowel reduction (Grabe and Low 2002). A stress-timed argument is stronger when several indicators converge because metrics like VarcoC may be less discriminant once rate-normalized (Dellwo 2006).

**THUS:** The article should compare Akkadian against published language profiles across the whole indicator set and should avoid presenting VarcoC alone as decisive.

---

## 164-Comparative-Interpretation-of-Indicators

**Domain:** Metrics / Interpretation

**WHAT:** Published rhythm studies suggest that stress-timed languages tend to combine lower %V (approx. 38%) with higher consonantal and vocalic variability, whereas syllable-timed languages tend toward higher %V (approx. 45-48%) and lower variability (White and Mattys in press). Mora-timed languages, such as Japanese, show still greater regularity and isochronicity based on the mora unit rather than the syllable. Sugai (2017) is especially useful here because it links Japanese mora timing to a mental durational threshold of about 250 ms, underscoring how differently a mora-based rhythm is organized. VarcoC on its own is often a weak discriminator; the relation between %V, VarcoV, and nPVI-V may be more informative in identifying the "Morse code" vs. "machine gun" feel of different rhythms (Patel and Daniele 2003).

**WHY:** The extended comparison weakens any argument that rests on one threshold alone, as rhythm is increasingly viewed as a gradient continuum rather than discrete classes (Hamdi et al. 2004). It also allows a stronger cumulative claim if Akkadian aligns with stress-timed profiles across several dimensions and diverges clearly from syllable-timed and mora-timed comparanda (Ramus, Nespor, and Mehler 1999).

**THUS:** The revised article should argue comparatively and cumulatively: Akkadian is most plausibly stress-timed if its updated profile groups with stress-timed languages across several indicators, not merely one.

---

## 165-Provisional-Status-of-Recomputed-Metrics

**Domain:** Metrics / Drafting Status

**WHAT:** The project's earlier metric outputs are no longer evidential because they were generated from an incorrect understanding of interval structure. The next article draft must therefore treat all updated metric values as pending until the program is rerun.

**WHY:** A preparatory manuscript is still needed before the rerun is complete. The safest solution is to preserve the argument's structure while replacing invalid numbers with explicit placeholders. The current working assumption is that the updated results will remain broadly similar in typological orientation—aligning with stress-timed languages like English or Dutch—but that assumption has not yet been verified numerically (White and Mattys in press).

**THUS:** The article should contain placeholder tables for all recomputed indicators, should avoid citing legacy values as findings, and should label the expected stress-timed profile as provisional until the new outputs are available.

---

## 166-Full-Corpus-Numbers-Discipline

**Domain:** Article Strategy / Quantitative Argument

**WHAT:** The Erra and Išum run and the full-corpus run must be kept analytically distinct. Erra is best used as a lexical diagnostic and as a worked example; the full corpus should carry the article's headline quantitative claims.

**WHY:** Mixing the two datasets makes the manuscript harder to follow and weakens the force of the evidence. The Erra figure of 29.2% matters because it shows how a lexical reading of the academic model can overgenerate prominence. The cross-linguistic rhythm argument, however, should rest on the broader corpus.

**THUS:** The revised draft should present the Erra numbers early and then move decisively to the full corpus for the central metric comparison.

---

## 167-Demonstration-Order-for-v5

**Domain:** Article Strategy / Argument Structure

**WHAT:** The article's core demonstration should proceed by elimination and then positive comparison: first show that Akkadian does not pattern like a syllable-timed language (e.g., French or Spanish), then show that it does not pattern like a mora-timed language (e.g., Japanese), and only then argue that a stress-timed reading is the most plausible remaining option (Patel and Daniele 2003; White and Mattys in press).

**WHY:** This order makes the argument sharper. It prevents the realization algorithm from looking like the source of the classification and turns the quantitative section, utilizing metrics like %V and ΔC, into an independent pressure point for rhythmic categorization (Ramus, Nespor, and Mehler 1999; Hamdi et al. 2004).

**THUS:** The v5 draft should reorganize the middle sections around this sequence before presenting the realization algorithm.

---

## 168-Terminology-Accentuation-Not-Repair

**Domain:** Article Style / Terminology

**WHAT:** When the algorithm modifies a prosodic domain, the operation should be described as accentuation, prosodic realization, or accentual adjustment, not as repair (Patel and Daniele 2003).

**WHY:** The word repair imports a defect-correction model that is not intended here. The article is not claiming that odd mora counts are broken forms; rather, it describes how duration, pitch, and intensity create structured patterns in speech (Patel and Daniele 2003). It is describing how connected-speech accentuation may have been realized acoustically (Hamdi et al. 2004).

**THUS:** The revised article should replace repair language with terminology that is consistent with accentuation and connected-speech realization.

---

## 169-Qualified-Strong-Claim

**Domain:** Argument / Thesis

**WHAT:** The main claim of the revised article should be stronger than bare compatibility yet still hedged. Under explicit and coherent assumptions, Akkadian was most likely stress-timed (White and Mattys in press).

**WHY:** The stronger formulation is warranted only if the revised comparative argument holds across the expanded indicator set, including vocalic and consonantal variability metrics (White and Mattys in press). Because rhythmic typology is increasingly viewed as a gradient continuum rather than a strictly categorical system, the wording must stay probabilistic and clinal rather than absolute (Hamdi et al. 2004). It remains a historical inference based on acoustic correlates rather than a certainty (Ramus, Dupoux, and Mehler 2003).

**THUS:** The article should replace overly weak formulations where the argument is cumulative and should avoid categorical statements where the evidence remains indirect.

---

## 170-Rhythm-Metrics-Computation-Protocol

**Domain:** Metrics / Computation / Methodology

**WHAT:** The recomputation of rhythm metrics should follow the Ramus-Dellwo and Grabe-Low traditions as closely as the data permit. Vocalic intervals are contiguous runs of vowels, consonantal intervals are contiguous runs of consonants, and pauses must be treated as a separate interval type rather than collapsed into either class (Ramus, Nespor, and Mehler 1999; Grabe and Low 2002; Patel and Daniele 2003).

**WHY:** The methodological point is not trivial. Pauses are excluded from the dispersion and PVI calculations because they are not vocalic or consonantal intervals in the relevant sense, but they remain part of total utterance duration when %V is computed. If pauses are omitted from the denominator, %V is artificially inflated; if they are inserted into Δ or PVI calculations, the variability measures cease to be comparable with published work.

**THUS:** The computational pipeline should begin from an ordered sequence of typed intervals, minimally `V`, `C`, and `P`, with durations measured in milliseconds. All downstream metrics should be derived from that sequence under explicit pause-handling rules.

---

## 171-Rhythm-Metrics-Formula-Set

**Domain:** Metrics / Computation / Formulas

**WHAT:** The revised implementation should compute the full indicator set from the same interval list: %V, %C, meanV, meanC, ΔV, ΔC, VarcoV, VarcoC, rPVI-C, and nPVI-V. In practical terms, ΔV and ΔC are standard deviations over vocalic and consonantal interval durations; VarcoV and VarcoC divide those dispersions by the corresponding mean and multiply by 100; rPVI-C averages the absolute difference between adjacent consonantal intervals; nPVI-V normalizes the difference between adjacent vocalic intervals by their local mean before averaging and multiplying by 100 (Dellwo 2006; Grabe and Low 2002; Patel and Daniele 2003).

Using the notation below, the formulas may be written explicitly in TeX form. Let $V_1, \dots, V_m$ be the durations of the vocalic intervals, $C_1, \dots, C_n$ the durations of the consonantal intervals, and let

$$
T = \sum_{i=1}^{m} V_i + \sum_{j=1}^{n} C_j + \sum_{k=1}^{p} P_k
$$

be the total utterance duration, where the $P_k$ are pauses. Then:

$$
\%V = 100 \times \frac{\sum_{i=1}^{m} V_i}{T}
$$

$$
\%C = 100 \times \frac{\sum_{j=1}^{n} C_j}{T}
$$

$$
\mathrm{meanV} = \frac{1}{m} \sum_{i=1}^{m} V_i
$$

$$
\mathrm{meanC} = \frac{1}{n} \sum_{j=1}^{n} C_j
$$

$$
\Delta V = \sqrt{\frac{1}{m} \sum_{i=1}^{m} \left(V_i - \mathrm{meanV}\right)^2}
$$

$$
\Delta C = \sqrt{\frac{1}{n} \sum_{j=1}^{n} \left(C_j - \mathrm{meanC}\right)^2}
$$

$$
\mathrm{VarcoV} = 100 \times \frac{\Delta V}{\mathrm{meanV}}
$$

$$
\mathrm{VarcoC} = 100 \times \frac{\Delta C}{\mathrm{meanC}}
$$

$$
\mathrm{rPVI\text{-}C} = \frac{1}{n-1} \sum_{j=1}^{n-1} \left|C_j - C_{j+1}\right|
$$

$$
\mathrm{nPVI\text{-}V} = 100 \times \frac{1}{m-1} \sum_{i=1}^{m-1} \left| \frac{V_i - V_{i+1}}{\left(V_i + V_{i+1}\right)/2} \right|
$$

These formulas assume that pauses contribute to $T$ for the percentage metrics but do not enter directly into the $V$- and $C$-based dispersion and PVI calculations.

**WHY:** These metrics do not all capture the same property. Raw dispersion preserves absolute variability, Varco metrics reduce speech-rate effects, and the PVI family tracks sequential alternation between neighboring intervals. Using the whole cluster therefore gives a firmer basis for typological comparison than any single threshold can provide.

**THUS:** Recomputed Akkadian metrics should be reported as a bundle, with one shared input representation and one documented formula set, so that later reruns remain directly comparable.

---

## 172-Python-Reference-Implementation-for-Rhythm-Metrics

**Domain:** Metrics / Computation / Python

**WHAT:** A compact Python reference implementation can make the assumptions of the metric computation fully inspectable. The following function assumes an ordered list of `(type, duration)` pairs, where `type` is `"V"`, `"C"`, or `"P"`, and `duration` is measured in milliseconds:

```python
import math


def compute_rhythm_metrics(intervals):
	"""Compute rhythm metrics from an ordered list of (type, duration_ms) pairs."""
	v_durations = [duration for interval_type, duration in intervals if interval_type == "V"]
	c_durations = [duration for interval_type, duration in intervals if interval_type == "C"]
	total_duration = sum(duration for _, duration in intervals)

	def population_stddev(durations):
		if len(durations) < 2:
			return 0.0
		mean = sum(durations) / len(durations)
		variance = sum((value - mean) ** 2 for value in durations) / len(durations)
		return math.sqrt(variance)

	mean_v = sum(v_durations) / len(v_durations) if v_durations else 0.0
	mean_c = sum(c_durations) / len(c_durations) if c_durations else 0.0
	delta_v = population_stddev(v_durations)
	delta_c = population_stddev(c_durations)

	percent_v = (sum(v_durations) / total_duration) * 100 if total_duration else 0.0
	percent_c = (sum(c_durations) / total_duration) * 100 if total_duration else 0.0

	varco_v = (delta_v / mean_v) * 100 if mean_v else 0.0
	varco_c = (delta_c / mean_c) * 100 if mean_c else 0.0

	rpvi_c = 0.0
	if len(c_durations) > 1:
		rpvi_c = sum(
			abs(c_durations[index] - c_durations[index + 1])
			for index in range(len(c_durations) - 1)
		) / (len(c_durations) - 1)

	npvi_v = 0.0
	if len(v_durations) > 1:
		normalized_differences = []
		for index in range(len(v_durations) - 1):
			first = v_durations[index]
			second = v_durations[index + 1]
			pair_mean = (first + second) / 2
			if pair_mean:
				normalized_differences.append(abs((first - second) / pair_mean))
		if normalized_differences:
			npvi_v = 100 * (sum(normalized_differences) / len(normalized_differences))

	return {
		"%V": percent_v,
		"%C": percent_c,
		"meanV": mean_v,
		"meanC": mean_c,
		"ΔV": delta_v,
		"ΔC": delta_c,
		"VarcoV": varco_v,
		"VarcoC": varco_c,
		"rPVI-C": rpvi_c,
		"nPVI-V": npvi_v,
	}


sample_intervals = [("V", 150), ("C", 120), ("P", 100), ("C", 45), ("V", 245)]
results = compute_rhythm_metrics(sample_intervals)

for key, value in results.items():
	print(f"{key}: {value:.2f}")
```

**WHY:** A reference implementation does more than save time. It fixes the operational meaning of the notes: pauses contribute to total duration for %V and %C, but only true vocalic and consonantal intervals feed Δ, Varco, and PVI calculations. That distinction is easy to state abstractly and easy to mishandle in code.

**THUS:** Future reruns of the Akkadian corpus should document any deviation from this implementation, especially in interval extraction, pause treatment, or the choice between population and sample dispersion.

---

## 173-Ordered-Interval-Input-Requirement

**Domain:** Metrics / Computation / Data Preparation

**WHAT:** The metric function presupposes an ordered interval stream rather than a bag of durations. A sequence such as `[("V", 150), ("C", 120), ("P", 100), ("C", 45), ("V", 245)]` preserves the temporal order needed for rPVI-C and nPVI-V, while also preserving pause placement for the %V denominator.

**WHY:** This requirement matters because PVI metrics are sequential by definition. Once durations are detached from order, the alternation structure disappears and the resulting values no longer correspond to the published formulas. The interval stream is therefore the real primary data structure for recomputed rhythm analysis.

**THUS:** The revised pipeline should export ordered interval lists before aggregation. Summary tables should be derived from that representation, not computed from already-collapsed totals.

---

## 174-Article-Must-Show-Algorithm-Step-by-Step

**Domain:** Article Strategy / Exposition

**WHAT:** The article must present the realization algorithm explicitly and step by step. If the article argues that Akkadian connected speech required a realization mechanism, the reader must be shown how that mechanism operates on actual text rather than being asked to infer it from outputs alone.

**WHY:** At present the project makes a strong methodological claim: lexical stress description is not enough, and prosody must be reconstructed through a constrained sequence of accentual operations. That claim is incomplete if the paper reports results without making the procedure legible. The argument is computational, philological, and phonological at once. Its internal steps therefore belong in the article, not only in the software.

**THUS:** The revised paper should include a compact algorithm section with an ordered procedure, a worked example, and an explanation of why each operation is permitted and each excluded operation is disallowed.

---

## 175-Algorithm-Section-Should-Use-Worked-Lines

**Domain:** Article Strategy / Demonstration

**WHAT:** The clearest way to present the algorithm is to walk the reader through a short Akkadian passage line by line: transliteration, syllabification, mora count, stress-eligible target selection, legal accentual operation, and final prosodic output.

**WHY:** A prose summary of the rules is not enough. The algorithm is easiest to understand when the reader can watch it move from lexical representation to realized phrasing. The Enuma Elish lines already used in the notes are well suited to this because they include word-internal accentuation, linking, and pause structure in a compact space.

**THUS:** The article should reserve one section for a worked algorithmic derivation before turning to broader quantitative interpretation.

---

## 176-Plausible-Duration-Approach

**Domain:** Metrics / Methodology / Framework

**WHAT:** A second, complementary demonstration can proceed from Akkadian transliteration to a sequence of plausible consonantal, vocalic, and pause durations in milliseconds, from which %C, meanC, ΔC, VarcoC, rPVI-C, %V, meanV, ΔV, VarcoV, and nPVI-V may be computed (Ramus, Nespor, and Mehler 1999; Dellwo 2006; White and Mattys 2007).

**WHY:** This approach addresses a real weakness in the earlier presentation. Morae are structurally indispensable in Akkadian grammar, but they remain abstract units. Interval metrics, by contrast, are defined on physical duration. Assigning phonetically plausible durations provides a bridge between the moraic description in the grammars and the acoustic categories used in rhythm typology.

**THUS:** PROPOSED MODEL: The new approach is promising, provided it is framed as a plausibility model anchored in comparative phonetics rather than as a direct recovery of ancient timings.

---

## 177-Plausible-Durations-Are-Heuristic-Not-Reconstruction

**Domain:** Metrics / Methodology / Caution

**WHAT:** Millisecond values assigned to Akkadian intervals must be treated as heuristic realizations, not as reconstructed acoustic facts (Ramus, Nespor, and Mehler 1999; White and Mattys 2007; Sugai 2017).

**WHY:** The sources in the bibliography can justify plausible ranges, thresholds, and proportional relations, but they cannot identify one uniquely correct duration for Akkadian consonants, vowels, or pauses. The evidential strength lies in constrained plausibility: if Akkadian receives durations that are phonetically reasonable and typologically grounded, the resulting rhythm profile can be tested comparatively. It does not follow that the assigned milliseconds reproduce how a Babylonian speaker actually sounded.

**THUS:** PROPOSED MODEL: The article should consistently speak of plausible duration assignment, modeled realization, or calibrated heuristic timing, and should avoid language that suggests direct acoustic reconstruction.

---

## 178-Consonant-Duration-Assumptions-Are-Sufficiently-Sourced

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** The current bibliography is sufficient to justify plausible consonantal interval assumptions, especially if the model distinguishes three broad timing classes: closure consonants, fricatives, and sonorants (Hankamer, Lahiri, and Koreman 1989; Yungdo Yun 2022; Howell and Rosen 1983; Billington 2015; Gibson et al. 2013; Kavitskaya 2001).

**WHY:** Hankamer, Lahiri, and Koreman provide a useful contrast between singleton and geminate stop closures, while Yun offers independent evidence that stop duration varies by position. The later review of the non-stop evidence showed that a single continuant class is too coarse: fricatives occupy time through sustained noise, whereas sonorants and glides are organized more by murmur and transition. Buccellati and Huehnergard identify the relevant Akkadian consonant classes, and the comparative phonetic literature makes it possible to reduce them to three acoustic timing classes without pretending to recover Akkadian milliseconds directly.

**THUS:** PROPOSED MODEL: The article may build consonantal timing assumptions from comparative phonetics so long as it presents them as analogical constraints rather than language-specific measurements. In practice, closure consonants may receive firmer defaults, fricatives may be modeled as a distinct heavier non-closure class, and sonorants may remain broader or be tested by sensitivity analysis rather than fixed as one exact value.

---

## 179-Vowel-Duration-Assumptions-Are-Sufficiently-Sourced

**Domain:** Metrics / Assumptions / Vowels

**WHAT:** The current bibliography is also sufficient to justify plausible vocalic interval assumptions for short and long vowels, provided that the baseline is taken from quantity-sensitive comparanda rather than stress-timed reduction-prone materials (Sugai 2017; Kozasa 2002; Jia, Mori, and Kasuya).

**WHY:** Sugai, Jia, and Kozasa provide evidence that quantity-sensitive systems distinguish shorter and longer vocalic durations in ways that can be expressed in milliseconds and tied back to moraic perception. These studies do not give Akkadian values, but they do offer credible comparative anchors for assigning distinct duration bands to short and long vowels in a modeled realization. The stricter review of the vowel evidence also showed that English and related stress-timed materials should not supply the central baseline, because compressed unstressed vowels would pull the short-vowel defaults downward.

**THUS:** PROPOSED MODEL: A vowel-duration model can be defended if it works with ranges or ratios and if it is presented as a comparative calibration rather than as a direct historical measurement. For a stricter central baseline, the present evidence supports short vowels around 75-95 ms and long vowels around 145-180 ms, while broader outer envelopes should remain available for sensitivity testing.

---

## 180-Pause-Assumptions-Are-Sufficiently-Sourced

**Domain:** Metrics / Assumptions / Pauses

**WHAT:** The current bibliography is sufficient to justify pause thresholds and pause proportions for a modeled Akkadian recitation (Goldman-Eisler 1968; Lin 2021; Anjarningsih 2024; Bae 2020; Tavakoli 2015).

**WHY:** Goldman-Eisler supports the broader claim that pauses may occupy roughly 30-40% of total utterance time, while Anjarningsih, Bae, Tavakoli, and Lin provide more specific support for pause thresholds and for the perceptual relevance of punctuation-shaped pauses. Taken together, these sources justify both a minimum pause threshold and a plausible range for the share of silence in an utterance.

**THUS:** PROPOSED MODEL: Pause modeling can be defended with the sources already in the bibliography, provided the article presents multiple tested values rather than a single untouchable default.

---

## 181-Main-Source-Gap-Is-Compensation-Effect-Specificity

**Domain:** Bibliography / Assessment / Caution

**WHAT:** The current bibliography is sufficient to support compensation as a plausible timing principle in the modeled realization, but not to establish one exact quantitative compensation law for Akkadian (Sugai 2017; Jia, Mori, and Kasuya; Kozasa 2002; Kavitskaya 2001).

**WHY:** Sugai, Jia, and Kozasa already show that quantity-sensitive timing depends on the relation between segment duration, moraic parsing, and speech rate. That is enough to justify a model in which consonant and vowel durations are not treated as wholly independent. What the bibliography does not provide is direct Akkadian phonetic measurement or a uniquely determined compensation coefficient. The evidentially safe position is therefore comparative and heuristic rather than absolute.

**THUS:** PROPOSED MODEL: The article may invoke compensation as a plausible timing logic and may test it across bounded settings, but it should not present one exact compensation value as if it were directly attested for Akkadian.

---

## 181b-Syllable-And-Rime-Intervals-Are-The-Better-Modeling-Level

**Domain:** Metrics / Methodology / Interval Model

**WHAT:** For the present software and article, the more defensible timing parameters are whole syllable or rime intervals rather than isolated consonant durations (Sugai 2017; Morley and Smith 2022; Asu and Nolan 2006; Pellegrino, Coupe, and Marsico 2011).

**WHY:** The comparative review showed that the strongest usable claim is not that every consonant type has one recoverable duration, but that weight and timing are better modeled at the level of larger intervals such as `CV`, `CVC`, `CVV`, and possibly `CVVC`. Segment durations remain relevant because they bound the admissible space, but the compensation logic of the model operates on larger rhythmic domains.

**THUS:** PROPOSED MODEL: The main model should be parameterized primarily by light, heavy, and superheavy interval classes, while consonant and vowel durations remain the empirical grounding layer rather than the sole program inputs.

---

## 181c-Interval-Targets-Are-Compositionally-Grounded-Heuristics

**Domain:** Metrics / Methodology / Interval Model / Caution

**WHAT:** The millisecond targets used by the program are heuristic, but they are not arbitrary. They should be derived from empirically plausible segmental ranges and then recast as interval targets (Yungdo Yun 2022; Hankamer, Lahiri, and Koreman 1989; Sugai 2017; Kozasa 2002).

**WHY:** The empirical discussion makes a two-level model necessary. At one level, onsets, codas, and vowels provide compositional envelopes. At another, the model selects central targets inside or across those envelopes so that compensation can be tested. This means the software values are neither pure inventions nor direct historical measurements.

**THUS:** PROPOSED MODEL: The article and software documentation should describe the interval values as compositionally grounded heuristics or calibrated interval targets, not as recovered Akkadian acoustic constants.

---

## 181d-Light-Heavy-And-Superheavy-Targets-Can-Be-Specified-Cautiously

**Domain:** Metrics / Assumptions / Interval Model

**WHAT:** A cautious first interval model may begin from three timing classes: light `CV/#V`, heavy `CVC/CVV`, and superheavy `CVVC`, with further mappings treated as exploratory (Hayes 1995; Kager 2009; Greenstein 1984; Huehnergard 2011; Sugai 2017; Kozasa 2002).

**WHY:** The discussion of the source material supports the architectural move to interval classes more strongly than it supports any single exact value. Even so, a first parameterization can be constrained by composition. A broad `CV` interval built from plausible onset plus short-vowel ranges centers near 200 ms. A common heavy target near 320 ms is more strongly supported from the `CVC` side than from the raw arithmetic midpoint of `CVV`, which is why it should be treated as a compensated common target rather than as a simple compositional mean. A superheavy interval is best treated as an expanded value whose base may lie near twice the light interval, though the evidence here remains weaker.

**THUS:** PROPOSED MODEL: For software purposes, a defensible first scheme is `K1 ≈ 200 ms` for light intervals, `K2 ≈ 320 ms` for heavy intervals, and `K3_base ≈ 400 ms` for superheavy intervals, all explicitly marked as baseline parameters for sensitivity testing rather than as direct phonetic reconstructions.

---

## 181e-Word-Level-Delta-Is-The-Safest-Interpretation-Of-Superheavy-Adjustment

**Domain:** Metrics / Assumptions / Compensation / Interval Model

**WHAT:** Any extra term added to the superheavy interval should be interpreted as a word-level or word-group compensation adjustment rather than as a directly measured consonantal pause (Morley and Smith 2022; Kavitskaya 2001).

**WHY:** The comparative discussion of phasing and apparent acoustic duration makes it safer to model the extra duration as a higher-level compensation factor than as a discrete hidden segment. This is especially important for `CVVC`, where the evidence for one fixed third-mora duration remains weak but the need for bounded rhythmic adjustment remains plausible.

**THUS:** PROPOSED MODEL: The program may implement `K3 = K3_base + delta`, where `delta` helps the realized word or word group approach the relevant rhythmic grid, but the article should avoid presenting `delta` as a directly attested Akkadian interval.

---

## 181f-Exploratory-Mappings-Beyond-The-Core-Three-Classes-Must-Remain-Optional

**Domain:** Metrics / Assumptions / Interval Model / Constraints

**WHAT:** Mappings such as `C:V` and `ʔ:V` with the heavy class, or `CVV:` and `CVC:` with the superheavy class, may be explored, but they should not be treated as hard defaults (Hayes 1995; Kager 2009; Huehnergard 2011; Greenstein 1984).

**WHY:** These equivalences are structurally plausible within the emerging interval model, but the current evidence base supports them less securely than the core classes `CV/#V`, `CVC/CVV`, and `CVVC`. Folding them into the default system too early would blur the distinction between well-grounded and exploratory assumptions.

**THUS:** PROPOSED MODEL: The software may allow these mappings as optional settings, while the article should keep them explicitly exploratory unless later evidence strengthens them.

---

## 181g-Fixed-Syllable-Targets-Alone-Are-Not-A-Realistic-Speech-Model

**Domain:** Metrics / Methodology / Interval Model / Realism

**WHAT:** A model that assigns near-fixed durations to syllable classes such as `CV`, `CVC`, and `CVV` is too rigid to represent natural Semitic speech on its own (Hamdi et al. 2004; Kager 2009; Hayes 1995).

**WHY:** Native-speaker intuition from Arabic points in exactly this direction. At the smaller scale, forms such as `laba` and `kal`, or `kaba` and `kal`, need not have the same duration: the heavier or more segmentally complex form may indeed be longer. But once an additional syllable is added, the relation changes. Pairs such as `kabaka` and `lakna` may converge toward a similar overall word duration even though their internal syllable structures differ. The extra syllabic material in the first form does not force the word to become proportionally longer. Instead, duration is redistributed across the word, with compression in some portions and expansion in others. This suggests that rhythmic equalization operates above the isolated syllable and cannot be captured adequately by a model that simply sums fixed light, heavy, and superheavy targets.

**THUS:** PROPOSED MODEL: The interval classes should be retained as heuristic anchors, but the realistic timing model must allow substantial word-level redistribution. In practice, the software should treat syllable-class values as attractors or starting points inside a larger prosodic-word timing model, not as durations that are expected to surface unchanged in running speech.

---

## 181h-Prosodic-Word-Timing-Is-More-Realistic-Than-Syllable-Summing

**Domain:** Metrics / Assumptions / Compensation / Interval Model

**WHAT:** The more realistic target for the model is not exact syllable-by-syllable isochrony, but bounded equalization at the level of the prosodic word or word group (Hamdi et al. 2004; Morley and Smith 2022; Pellegrino, Coupe, and Marsico 2011).

**WHY:** The empirical and comparative material already suggested that compensation is relational. The Arabic intuition strengthens that point by showing that speakers may preserve a comparable overall word duration across structurally different forms once additional syllables are present. What remains stable is therefore more likely to be the larger rhythmic package than the duration of each syllable taken separately. Syllable classes still matter, but as internal contributors to a higher-order temporal organization.

**THUS:** PROPOSED MODEL: The software model should be reformulated so that `K1`, `K2`, and `K3` function as internal weighting anchors, while the final adjustment is computed over the whole prosodic word or linked word group. This is more realistic than expecting each `CV`, `CVC`, or `CVVC` token to realize a near-fixed duration in isolation.

---

## 181i-Intersyllabic-Rearticulation-May-Be-Part-Of-The-Timing-Mechanism

**Domain:** Metrics / Assumptions / Compensation / Timing Mechanism

**WHAT:** One plausible reason why words with different internal structures can converge in total duration is that the effective timing domain includes not only the syllable nuclei and codas, but also the rearticulation span between syllables (Kavitskaya 2001; Morley and Smith 2022).

**WHY:** The Arabic examples suggest that the timing difference between simpler and more complex forms is not constant across word sizes. A heavier monosyllabic or disyllabic form may be longer in isolation, yet that advantage may shrink once another syllable is added. This is easier to understand if part of the relevant temporal material lies in the transition from one syllable to the next: release, overlap, gestural rephasing, and preparation for the following onset. In such a model, the added syllable does not contribute only its own vowel and consonants. It also changes how neighboring material is timed.

**THUS:** PROPOSED MODEL: The current project should keep two linked explanations open: compensation in a broad sense and an intersyllabic rearticulation timespan in a narrower phonetic sense. For modeling purposes, the safest choice is to treat both as higher-order timing contributions that operate across syllable boundaries rather than to force all duration into the syllables taken one by one.

---

## 181j-Bimoraic-Equivalence-Requires-A-Boundary-Placeholder-When-Segment-Sums-Differ

**Domain:** Metrics / Assumptions / Compensation / Timing Mechanism

**WHAT:** A bimoraic or heavy-syllable model cannot be stated only in terms of raw segment sums if equally weighted forms differ in their realized segmental duration. In such cases, the model needs a boundary placeholder `p` that belongs to the timing domain even when it is not represented as an independent segment (Hayes 1995; Kager 2009; Kavitskaya 2001; Morley and Smith 2022).

**WHY:** The contrast between forms like `kab` and `kana` makes the problem explicit. If the model expects comparable weight or timing behavior, yet `len(kab) != len(kana)` when only the overt segments are counted, then the equality cannot be rescued by syllable labels alone. A further timespan has to be recognized. The most plausible candidates are precisely the ones suggested by the phonetic discussion: prolongation of the coda in fricative-like cases, an articulatory switching interval when the vocal tract moves from one consonantal posture to another, or a pause-like edge interval at word end. Under that interpretation, the relevant equality is not simply `len(kab) = len(kana)`, but rather `len(kab) + len(p) = len(kana)` whenever the timing system assigns them to the same higher-order rhythmic slot.

**THUS:** PROPOSED MODEL: The current project should not identify bimoraic equivalence with bare segment counting. The better formulation is that a weighted form may include an additional boundary contribution `p`, where `p` is a placeholder for coda prolongation, articulatory switching, or edge timing. This keeps the bimoraic logic viable while making the timing model more realistic.

---

## 181k-The-Placeholder-p-Should-Be-Treated-As-An-Effective-Timing-Contribution

**Domain:** Metrics / Assumptions / Compensation / Interval Model

**WHAT:** The placeholder `p` is best treated as an effective timing contribution rather than as one narrowly defined phonetic object (Kavitskaya 2001; Morley and Smith 2022).

**WHY:** The available evidence does not justify one rigid interpretation. In some contexts `p` may surface as audible consonantal prolongation, especially with fricative-like codas. In others it may be better understood as a switch time between articulatory postures, especially across stop-sonorant or comparable transitions. At word edge it may be realized as a short terminal hold or pause-like release interval. What matters for the model is not that every instance of `p` has the same phonetic shape, but that these different realizations may fill the same structural timing function.

**THUS:** PROPOSED MODEL: The software and article should define `p` as an effective boundary timing term. Its phonetic realization may vary by consonant class, syllable structure, and word position, but its modeling role is stable: it allows forms with different overt segment sums to converge toward the same rhythmic target.

---

## 182-Illustrative-Passage-Cannot-Carry-The-Main-Claim

**Domain:** Article Strategy / Quantitative Argument

**WHAT:** A five-line illustrative passage is suitable for demonstrating the method, but not for establishing the article's main typological claim.

**WHY:** A hand-picked passage can show that the method works and that its resulting durations yield interpretable metrics. It cannot, by itself, establish that Akkadian as a language was stress-timed. The danger is selection bias: a short passage may look rhythmically persuasive while failing to represent the corpus more broadly.

**THUS:** The short passage should function as a demonstration case. The headline claim about stress-timed Akkadian must still depend on a larger corpus or on a clearly labeled secondary test set.

---

## 183-New-Demonstration-Should-Combine-Algorithm-and-Metrics

**Domain:** Article Strategy / Demonstration

**WHAT:** The strongest revised demonstration would combine two layers: first, a transparent step-by-step account of the realization algorithm on a short text; second, a plausible-duration assignment for that same text that produces the full interval-based metric suite.

**WHY:** The two demonstrations answer different objections. The stepwise algorithm shows how prosody is reconstructed. The plausible-duration model shows how that reconstructed output can be brought into the acoustic metric framework used in rhythm typology. Used together, they tighten the link between philology, phonology, and quantitative comparison.

**THUS:** The revised article should not choose between algorithmic exposition and metric demonstration. It should stage them sequentially and make each carry a distinct argumentative burden.

---

## 184-Bibliography-Is-Sufficient-For-Valid-Assumptions

**Domain:** Bibliography / Assessment

**WHAT:** The bibliography is now sufficient to support valid assumptions for a plausible-duration approach to Akkadian rhythm.

**WHY:** The relevant source types are present: Akkadian phonology and stress (Huehnergard, Streck, Buccellati, Greenstein), rhythm metrics and comparative baselines (Ramus, Dellwo, Grabe and Low, Patel and Daniele, White and Mattys, Hamdi), pause studies (Goldman-Eisler, Lin, Anjarningsih, Tavakoli, Bae), information-rate calibration (Pellegrino et al.), and quantity-sensitive duration studies (Sugai, Jia, Kozasa, Hankamer, Yun). That is enough to build empirically constrained assumptions even though no source gives Akkadian milliseconds directly.

**THUS:** The article can move forward with the new approach without waiting for a fundamentally new bibliographic base. What it must preserve is methodological modesty and explicit sensitivity testing.

---

## 185-Full-Corpus-Metrics-Must-Carry-The-Claim

**Domain:** Article Strategy / Quantitative Argument

**WHAT:** The decisive metric argument should be run on the full corpus of roughly 5,000 words, not on the short illustrative passage alone.

**WHY:** A corpus of that size is large enough to carry the article's main quantitative claim in a way that a five-line demonstration cannot. The short passage remains useful because it makes the procedure visible. The corpus is what gives the argument typological weight.

**THUS:** The article should compute the interval-based metrics on the full corpus and use the worked passage only as a transparent demonstration of method.

---

## 186-Onset-Duration-Should-Be-Bounded-By-Human-Articulation

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** Consonant durations should be modeled within phonetically plausible human ranges and should respect at least the three-way distinction among closure consonants, fricatives, and sonorants.

**WHY:** This part of the timing model is not primarily cultural. It is constrained by human articulation. Closure consonants such as stops consume time through an actual oral or glottal closure, fricatives consume time through sustained noise, and sonorants distribute duration through murmur or transition. The strength of the argument lies less in one exact millisecond assignment than in preserving these structural distinctions and excluding implausible values.

**THUS:** The article should justify consonant durations as belonging to human articulatory ranges, assign firmer defaults to closure consonants, and test fricative and sonorant values within broader admissible ranges rather than pretending to know one exact ancient value for every consonant subtype.

---

## 187-Consonant-Vowel-Compensation-Is-The-Relevant-Claim

**Domain:** Metrics / Assumptions / Compensation

**WHAT:** The relevant compensation claim is that consonant and vowel durations may trade off within a rhythmic domain so that added weight or prominence does not force every affected unit to become proportionally longer.

**WHY:** This is the real methodological value of compensation for the project. It supports a timing model in which vowel elongation and constrained consonantal lengthening are not treated as arbitrary additions, but as ways of redistributing duration inside a moraic or syllabic structure. Within a CV or CVV domain, a longer consonantal onset may be balanced by a shorter vowel; across adjacent mora-bearing positions, added consonantal weight may likewise be absorbed without producing unlimited durational growth.

**THUS:** The duration model should allow bounded redistribution of timing across the relevant rhythmic domain rather than assigning fixed independent values to consonant and vowel with no interaction.

---

## 188-Compensation-Should-Be-Tested-As-A-Range-Not-A-Dogma

**Domain:** Metrics / Methodology / Sensitivity

**WHAT:** If consonant-vowel compensation is built into the timing model, it should be implemented as a tunable range or parameter rather than as an all-or-nothing rule.

**WHY:** The comparative literature suggests that compensation exists, but the degree of compensation varies across languages, structures, and speaking rates. For Akkadian, the safest claim is therefore not that compensation must take one exact form, but that some degree of trade-off between consonant duration and following vowel duration is phonetically plausible and should be tested.

**THUS:** The article should report sensitivity tests across plausible compensation settings and ask whether the resulting rhythm profile remains stable.

---

## 188b-Kavitskaya-Improves-Compensation-Grounding-But-Not-Calibration

**Domain:** Metrics / Assumptions / Compensation / Evidence Assessment

**WHAT:** Kavitskaya improves the grounding of the project's compensation logic by showing that compensatory lengthening can arise from the acoustic reinterpretation of transitional or consonantal material, but she does not supply a uniquely calibratable compensation coefficient for Akkadian.

**WHY:** This is the precise gain from the source. It helps show that the project's vowel lengthening and consonant-sensitive timing adjustments belong to a phonetically intelligible family of mechanisms rather than to an ad hoc engineering device. At the same time, her data come from comparative phonetics and diachrony, not from Akkadian recordings or from a single normalized metric that could be transferred mechanically into the model. The source therefore strengthens plausibility without dissolving the need for bounded testing and methodological caution.

**THUS:** The article may cite compensation as a better grounded comparative principle than before, but it should continue to implement compensation as a range-tested heuristic rather than as an exact recovered law of Akkadian timing.

---

## 189-Model-Uncertainty-Matters-More-Than-Sampling-Uncertainty

**Domain:** Metrics / Methodology / Uncertainty

**WHAT:** For the present project, the main uncertainty is not ordinary sampling error but model uncertainty. The critical question is how much the rhythm metrics change when the assumed durations for consonants, vowels, pauses, and compensation are varied within plausible bounds.

**WHY:** A corpus of roughly 5,000 words is large enough that the dominant source of uncertainty is unlikely to be random fluctuation in the sample itself. What matters more is the choice of timing assumptions. If those assumptions move the metrics substantially, a narrow confidence interval around one fixed model would give a false sense of precision.

**THUS:** The article should treat assumption sensitivity as the primary robustness problem and should use sampling-based uncertainty measures, if at all, only as a secondary supplement.

---

## 190-Confidence-Intervals-Are-Secondary-Not-Primary

**Domain:** Metrics / Methodology / Uncertainty

**WHAT:** Classical confidence intervals should not be the primary uncertainty device for the plausible-duration model.

**WHY:** A confidence interval answers the question of how stable a metric is under repeated sampling once the model has already been fixed. That is not the project's main epistemic problem. The real issue comes earlier: whether the chosen timing model is itself sufficiently grounded and whether the central claim survives alternative plausible settings.

**THUS:** If confidence intervals are used at all, they should appear only after a baseline timing model has been fixed and should be clearly distinguished from the more important analysis of assumption sensitivity.

---

## 191-Local-Sensitivity-Should-Use-Normalized-Partial-Derivatives

**Domain:** Metrics / Methodology / Sensitivity

**WHAT:** The first stage of robustness analysis should use local sensitivity, ideally in normalized form. For a metric $M$ and a parameter $\theta_i$, the relevant quantity is the local elasticity: $S_i = \frac{\partial M}{\partial \theta_i}\frac{\theta_i}{M}$.

**WHY:** Raw partial derivatives are difficult to compare across parameters measured on different scales. A normalized derivative shows how strongly a metric responds, in proportional terms, to a proportional change in one parameter near the baseline setting. This makes it possible to rank assumptions by importance.

**THUS:** The article should use normalized local sensitivity to identify which timing assumptions matter most before attempting broader robustness exploration.

---

## 192-Local-Derivatives-Should-Be-Estimated-By-Finite-Differences

**Domain:** Metrics / Methodology / Sensitivity

**WHAT:** In practice, the local partial derivatives should be estimated numerically by finite differences rather than derived analytically from the full metric engine.

**WHY:** The metric calculations are complex and involve ordered interval data, compensation settings, and thresholded pause rules. A central finite-difference approximation around the baseline is therefore the most transparent solution. It is also easy to replicate computationally.

**THUS:** The baseline analysis should perturb one parameter at a time by a small positive and negative step, recompute the metrics, and estimate the local derivative from the resulting change.

---

## 193-Global-Bounded-Robustness-Should-Use-Admissible-Space-Not-Priors

**Domain:** Metrics / Methodology / Robustness

**WHAT:** After local sensitivity has identified the important parameters, the broader robustness analysis should evaluate the metrics over an admissible parameter space rather than over an assumed probability distribution.

**WHY:** The current bibliography supports plausible bounds and ordering constraints better than it supports precise probability distributions. If one were to assign normal, uniform, or other priors to the duration parameters without strong empirical backing, the analysis would become harder to defend. A bounded admissible space avoids that problem by asking what happens anywhere within the region justified by the sources.

**THUS:** The main robustness analysis should be deterministic and bounded: define the admissible space, evaluate the metrics within it, and inspect the resulting range and classification stability.

---

## 194-Parameter-Tuples-Must-Be-Validated-Before-Metric-Computation

**Domain:** Metrics / Methodology / Constraints

**WHAT:** Every candidate parameter tuple must be validated against the system constraints before the metric function is computed.

**WHY:** The admissible space is not a naive rectangular box. Some parameter combinations are linguistically or phonetically impossible even if each parameter, taken separately, lies within its own numerical range. At minimum, the model must preserve the ordering short vowel < long vowel < very long vowel whenever the third category is used; singleton closure consonant < geminate closure consonant; singleton continuant < geminate continuant whenever continuant gemination is modeled; and short pause < long pause with the short pause remaining above the pause threshold. Positional relations must also be respected where the model uses them, such as coda stop duration not exceeding onset or intervocalic stop duration. In addition, no tuple may license prosodic operations that violate Akkadian phonotactics, including illegal diphthong handling or illicit singleton gemination with lexical side effects.

**THUS:** The computational procedure should first test whether a tuple satisfies the full set of ordering, positional, and structural constraints. Only valid tuples should be passed to the metric engine, and the constraint list should be reported explicitly so that the admissible space is reproducible.

---

## 195-Robustness-Should-Be-Reported-As-Envelope-And-Threshold-Crossing

**Domain:** Metrics / Methodology / Reporting

**WHAT:** The results of the bounded robustness analysis should be reported as a robustness envelope and as threshold-crossing tests. For each metric, the key quantities are its minimum and maximum over the admissible parameter space, along with whether the metric ever crosses the relevant typological boundary.

**WHY:** This reporting format answers the real methodological question. It shows not only how much the metric can move under grounded assumptions, but also whether those movements ever force a change in typological interpretation. That is more informative than a single baseline number and more defensible than an arbitrary probabilistic summary.

**THUS:** The article should report metric envelopes and explicitly state whether the stress-timed interpretation survives throughout the admissible space or fails only at edge cases.

---

## 196-Monte-Carlo-Is-Unnecessary-Without-Defensible-Distributions

**Domain:** Metrics / Methodology / Caution

**WHAT:** Monte Carlo simulation is unnecessary at the current stage unless defensible parameter distributions can be justified from the literature.

**WHY:** A non-uniform distribution would require empirically grounded means, variances, or other shape parameters that are not currently available for modeled Akkadian durations. A uniform distribution would not solve the problem, because it only disguises unsupported assumptions as neutrality. In this context, bounded deterministic exploration is methodologically cleaner.

**THUS:** The project should prefer constrained sensitivity and bounded robustness analysis over Monte Carlo until a stronger empirical basis for parameter likelihoods exists.

---

## 197-First-Implementation-Should-Use-Core-Supported-Parameters

**Domain:** Metrics / Modeling Strategy

**WHAT:** The first implementation of the plausible-duration model should be built from the strongest supported parameter classes: stop closure and stop gemination, short versus long vowels, short versus long pauses, and a bounded compensation setting.

**WHY:** These are the parts of the timing model for which the present bibliography provides the clearest comparative support. Hankamer and Yun support the core stop-duration assumptions; Sugai, Jia, and Kozasa support the vocalic quantity contrast; Goldman-Eisler, Lin, Anjarningsih, and Bae support pause thresholds and pause tiers. A defensible first model should rest on these firmest components before adding finer distinctions.

**THUS:** The initial article argument and the first software implementation should treat these core parameters as the baseline model, while postponing weaker refinements to bounded sensitivity analysis.

---

## 198-Pause-Ratio-Should-Be-Observed-Not-Allocated

**Domain:** Metrics / Pauses / Methodology / Correction

**WHAT:** The global `pause_ratio` should no longer be used to allocate individual pause durations. It should instead be treated as an observed or benchmark value computed after the phonetizer has realized the actual pause rows.

**WHY:** The architecture of the program has changed. Pauses are now realized individually in the phonetizer, where they interact with the drift state and with pause-class constraints. The older logic in which a global pause budget was distributed over punctuation counts belonged to an earlier stage of the project. Once row-level pause realization exists, a top-down pause-allocation formula becomes redundant and methodologically misleading.

**THUS:** The research argument should no longer defend pause modeling through sensitivity around a global pause budget. It should defend row-level pause realization and use pause ratio only as a verification surface.

---

## 199-Legacy-Pause-Allocation-Block-Is-Now-Misleading

**Domain:** Metrics / Pauses / Implementation / Correction

**WHAT:** The `Pause duration allocation` block in the current metrics output is now a legacy artifact rather than a faithful summary of the active timing model.

**WHY:** That block still derives average short and long pause durations from a global pause share and punctuation weights, then applies a correction step. But the active metrics model is already documented as phone-driven, and the phonetizer already finalizes row durations with drift handling. The block therefore describes an inherited heuristic rather than the actual realized pause rows.

**THUS:** Future metrics reporting should replace that section with realized pause statistics computed directly from phone rows.

---

## 200-Project-Short-Pause-Excludes-Micro-Pauses

**Domain:** Pauses / Terminology / Literature Mapping

**WHAT:** The project's effective `short` punctuation pause does not include the sub-perceptual or compression-driven very short silences that some pause literature also labels short.

**WHY:** The newer bibliography distinguishes between very short silences associated with articulatory compression and the longer punctuation-relevant pauses that help structure speech for the listener. For the present project, only the latter are useful for modeling punctuation-driven reading rhythm. Keeping both under one label would blur the model and overstate what the punctuation layer is trying to represent.

**THUS:** The methods discussion should state explicitly that the project discards micro-pause categories and uses `short` only for the punctuation-relevant shorter tier.

---

## 201-Long-Pause-Adequacy-Is-Defined-By-Drift-Reset

**Domain:** Pauses / Timing Model / Constraints

**WHAT:** A long-pause range is adequate only if it remains compatible with full drift reset at clause-final or equivalent boundaries.

**WHY:** In the current phonetizer logic, short pauses may leave residual drift, but long pauses must return the running drift reserve to zero. This means that the long-pause band cannot be chosen only for literary or phonetic plausibility in the abstract. It must also satisfy a functional solver requirement.

**THUS:** Long-pause defaults and long-pause validation should be judged against both comparative reading evidence and the requirement of complete drift cancellation.

---

## 198-Parameter-Statuses-Must-Be-Separated

**Domain:** Metrics / Methodology / Parameterization

**WHAT:** The duration model must distinguish among core defaults, contextual adjustments, and exploratory sensitivity-only parameters.

**WHY:** The empirical material does not support every value equally. Some parameters are robust enough to function as defaults; others are justified only in marked contexts; still others remain exploratory because the evidence is heterogeneous or indirect. If these statuses are mixed, the resulting model becomes harder to defend and harder to interpret.

**THUS:** Every published parameter table and every article discussion of modeled timing should explicitly label whether a value is core, contextual, or exploratory.

---

## 199-Full-Consonant-Classification-Should-Be-Collapsed-For-Timing

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** The full phonological inventory of Akkadian consonants may be preserved descriptively, but the first timing model should collapse that inventory into three broad timing classes: closure consonants, fricatives, and sonorants.

**WHY:** The empirical discussion showed that a simple closure-versus-continuant split hides a major numerical separation inside the non-closure domain. Fricatives occupy time through sustained noise and tend to be durationally heavier than sonorants, which occupy time through murmur or transitions. The most defensible reduction therefore passes through the fuller consonant system and then groups segments by how they occupy time acoustically.

**THUS:** The published research notes should describe the full consonant system philologically, but the first duration model should parameterize it through the three-class reduction.

---

## 200-Closure-Consonants-Define-The-Firmest-Timing-Class

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** Oral stops form the model's firmest closure-consonant class because they contain the clearest silent closure interval between attack and release.

**WHY:** This class is the strongest consonantal timing category in the present bibliography. Yun provides comparative evidence for positional stop duration, Hankamer, Lahiri, and Koreman provide the clearest singleton-versus-geminate contrast, and Buccellati and Huehnergard identify the relevant Akkadian consonants philologically. In the current conservative version of the model, `ʾ` is returned to the stop row rather than treated as a separate weak-transition subclass. That choice reinforces the main point: closure consonants remain the firmest consonantal baseline in the modeled realization.

**THUS:** Closure consonants may receive firmer default ranges, positional asymmetries, and gemination assumptions than any other consonant class in the first implementation.

---

## 201-Fricatives-And-Sonorants-Should-Be-Separated

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** Fricatives should be separated from sonorants in the timing model rather than merged into one broad continuant class.

**WHY:** Although both fricatives and sonorants lack a silent stop closure, they do not pattern together numerically. Fricatives occupy time through sustained noise and appear durationally heavier, whereas sonorants and glides are organized more by murmur and transition. For a model that aims to generate isochrony, this numerical segregation matters more than the simple shared absence of closure.

**THUS:** The first model should distinguish at least three consonantal timing classes: closure, fricative, and sonorant.

---

## 202-Consonant-Timing-Should-Be-Modeled-By-Three-Acoustic-Classes

**Domain:** Metrics / Assumptions / Consonants / Vowels

**WHAT:** The most relevant consonantal timing parameter for vowel allocation is not merely closure versus non-closure, but a three-way contrast among closure, frication, and sonorant transition.

**WHY:** A closure onset delays vowel unfolding through occlusion, a fricative onset occupies time through turbulent noise, and a sonorant onset occupies time through murmur or transition. These are different low-level physical realities and they leave different amounts of time available to the following vowel. The discussion of the numerical evidence showed that a three-class contrast is more informative for modeled timing than a binary opposition.

**THUS:** Compensation settings and vowel allocation should be keyed first to the closure-fricative-sonorant contrast rather than to either a binary split or a highly granular consonant taxonomy.

---

## 203-Stop-Gemination-Provides-The-Core-Consonantal-Multiplier

**Domain:** Metrics / Assumptions / Gemination

**WHAT:** The singleton-to-geminate relation for stops is the best-supported consonantal multiplier in the present model.

**WHY:** Hankamer, Lahiri, and Koreman provide the clearest comparative evidence that stop gemination is primarily cued by closure duration and that geminate stops are substantially longer than singletons. This makes the stop-gemination relation the strongest direct anchor for adding consonantal weight in the modeled realization.

**THUS:** The first implementation may use stop gemination as the core consonantal multiplier, provided that the article presents it as a comparative constraint rather than as a direct Akkadian measurement.

---

## 204-Fricative-And-Sonorant-Lengthening-Should-Remain-Exploratory

**Domain:** Metrics / Assumptions / Gemination

**WHAT:** Lengthening of fricatives and sonorants, if modeled, should remain exploratory rather than be assigned the same fixed multiplier as stop gemination.

**WHY:** The comparative evidence for non-stop consonant lengthening is less secure and less uniform than the evidence for stop closure. The numerical discussion now justifies separating fricatives from sonorants, but it still does not justify one exact gemination multiplier for either class. Akkadian philology allows held or protracted consonantal articulation, yet the low-level measurements remain less secure than the stop-based statistics.

**THUS:** Fricative and sonorant lengthening may be explored in sensitivity analysis, but neither should serve as a hard default gemination multiplier in the first published parameterization.

---

## 205-Very-Long-Vowel-Is-Contextual-Not-Lexical

**Domain:** Metrics / Assumptions / Vowels

**WHAT:** A very long vowel should not be treated as a third stable lexical length class in the Akkadian duration model.

**WHY:** The present evidence supports a strong short-versus-long distinction, but not a separate lexical inventory of ordinary very long vowels. Kozasa shows that markedly extended vowel duration can arise under specific prosodic conditions, while Buccellati and Izre'el and Cohen do not establish a stable third phonemic length category for Akkadian. The safest conclusion is therefore that overlong duration belongs to contextual realization rather than to the lexical base system.

**THUS:** The published research notes should define the base vowel inventory as short and long, with very long duration treated only as a contextual adjustment layer.

---

## 206-Very-Long-Vowel-Needs-Contextual-Trigger

**Domain:** Metrics / Assumptions / Vowels / Constraints

**WHAT:** If very long vowel duration is modeled at all, it must be activated only by marked contexts such as phrase-finality, verse-finality, or exceptional prominence.

**WHY:** A contextual trigger is what separates ordinary long-vowel realization from prosodically induced extension. Huehnergard and Izre'el and Cohen support the idea that marked lengthening may arise in special positions or expressive settings, but not that such values should populate the baseline inventory.

**THUS:** Very long values must be treated as context-sensitive additions to the model, not as ordinary defaults available everywhere.

---

## 207-Pause-Evidence-Has-Three-Distinct-Functions

**Domain:** Metrics / Assumptions / Pauses

**WHAT:** Pause evidence in the model should be separated into three functions: threshold evidence, baseline duration evidence, and upper-bound caution.

**WHY:** The pause literature does not support one single number for every purpose. Goldman-Eisler helps justify the global share of silence, Lin supports perceptual baselines for punctuation-shaped pauses, and Anjarningsih and Bae clarify thresholding, clause-level tiering, and the practical importance of pause placement. Treating these as three distinct functions is methodologically cleaner than collapsing them into a single average.

**THUS:** The pause model should assign different sources to different tasks and should present threshold, baseline, and upper bound as separate layers of justification.

---

## 208-Initial-Pause-Defaults-Are-Defensible

**Domain:** Metrics / Assumptions / Pauses

**WHAT:** A defensible first pause model may use a functional floor around 250 ms, a short-pause baseline around 600-680 ms, a long-pause range around 1200-1780 ms, and a total silence share of roughly 30-40%.

**WHY:** These values are the most stable cross-sections of the current pause evidence. They combine a perceptual threshold, a naturalness baseline for shorter punctuation pauses, a higher range for clause-boundary pauses, and a global ceiling on how much of the utterance may be silent without becoming rhythmically distorted.

**THUS:** The article may present these values as the initial pause defaults for bounded testing, while still allowing sensitivity analysis across the justified range.

---

## 209-Compensation-Belongs-To-The-Same-Mechanistic-Family

**Domain:** Metrics / Assumptions / Compensation

**WHAT:** The Akkadian duration model need not be identical to the compensation patterns described in quantity-sensitive modern languages in order to belong to the same mechanistic family of durational redistribution.

**WHY:** The comparative literature shows that segment durations within rhythmic domains are relational rather than wholly independent. Sugai, Jia, and Kozasa are sufficient to show that moraic and quantity-sensitive timing can involve redistribution of duration across neighboring components. That does not prove that Akkadian implemented the same mechanism in the same way, but it does show that the project's timing logic is not phonetically unthinkable.

**THUS:** The article may describe the model as belonging to the same family of timing mechanisms as comparative compensation models, while avoiding claims of direct identity.

---

## 210-Vowel-Lengthening-Is-Compatible-With-Compensation-Logic

**Domain:** Metrics / Assumptions / Compensation / Vowels

**WHAT:** Prosodic lengthening of already long vowels is compatible with compensation-like timing logic because it redistributes duration within a bounded rhythmic structure without neutralizing the short-versus-long lexical contrast.

**WHY:** The project's choice to lengthen only vowels that are already long was motivated by phonological caution, but it also fits the broader comparative idea that prominence may be realized durationally inside a quantity-sensitive system. In this respect the model's vowel lengthening is better understood as a bounded redistribution of rhythmic weight than as an arbitrary insertion of time.

**THUS:** The article may present vowel lengthening as compatible with compensation logic, while still describing it as a modeled Akkadian realization rather than as a directly attested phonetic fact.

---

## 211-Consonant-Suite-Gemination-Is-Compatible-With-Inter-Domain-Redistribution

**Domain:** Metrics / Assumptions / Compensation / Gemination

**WHAT:** Geminating a consonant inside a consonant sequence, rather than a singleton, is compatible with a broader inter-domain redistribution of rhythmic weight.

**WHY:** This operation adds weight while minimizing lexical side effects and keeps the adjustment inside structures that can plausibly bear extra consonantal duration. The discussion of the empirical and philological material showed that such a move should not be treated as identical to the mechanisms described for modern languages, but it can be justified as belonging to the same broader family of redistributive timing strategies.

**THUS:** The article may discuss consonant-suite gemination as a comparative family resemblance rather than as a direct phonetic equivalence.

---

## 212-Published-Research-Notes-Must-Exclude-Weak-Citation-Carriers

**Domain:** Bibliography / Methodology / Publication

**WHAT:** Claims in the published research notes should be stated only through sources anchored in the bibliography, not through weak citation carriers or temporary extraction files.

**WHY:** The research notes are intended to shadow the article and to stand as a publishable analytical record. If a claim depends only on a secondary citation chain, a temporary summary file, or an undocumented carrier rather than on a source already anchored in the bibliography, that claim is not yet ready to function as part of the article's public evidential base.

**THUS:** Empirical findings harvested from temporary files must be reframed through the existing bibliography or omitted until the relevant source is formally integrated.

---

## 213-Empirical-Extraction-Files-Are-Preparatory-Not-Final

**Domain:** Research Method / Documentation

**WHAT:** Temporary empirical extraction files are useful for harvesting distinctions, ranges, and questions, but the authoritative analytical formulation must reside in the research notes.

**WHY:** The extraction files are working instruments. They preserve intermediate searching and sorting, whereas the research notes preserve the stabilized findings, the project-specific interpretation, and the final relation between evidence and argument. Since the article must be licensed by the research notes, that second stage cannot remain implicit.

**THUS:** Every empirical point that matters to the article or the software should be copied into the research notes in cleaned WHAT/WHY/THUS form.

---

## 214-Model-Ready-Parameter-Tables-Must-Expose-Status-And-Bounds

**Domain:** Metrics / Methodology / Parameterization

**WHAT:** Any model-ready parameter table should report at least a minimum, a default, a maximum, and an evidential status for each parameter.

**WHY:** Both the article and the software need to distinguish strong defaults from contextual adjustments and exploratory settings. A bare list of values is insufficient because it hides which parameters are well grounded, which are only conditionally active, and which are present solely for sensitivity analysis.

**THUS:** The next formal parameter table should expose numeric bounds together with evidential status so that the modeled duration space is reproducible and interpretable.

---

## 215-Contextual-Activation-Rules-Are-Part-Of-Admissibility

**Domain:** Metrics / Methodology / Constraints

**WHAT:** Admissibility depends not only on numeric inequalities but also on contextual activation rules.

**WHY:** Some values or operations are legal only in marked circumstances. Very long vowels require contextual triggers, pause values depend on punctuation tier and discourse position, and consonantal lengthening strategies are constrained by Akkadian phonotactics and by the need to avoid lexical side effects. A tuple can therefore be numerically ordered yet still invalid if it activates a contextual value in the wrong environment.

**THUS:** The admissible parameter space must encode both numeric ordering and context-sensitive activation rules before metric computation begins.

---

## 216-Philological-Consonant-Inventory-Must-Precede-Timing-Reduction

**Domain:** Phonology / Metrics / Consonants

**WHAT:** The timing model must begin from the full Akkadian consonant inventory before reducing it to computational classes. At minimum, the inventory relevant to the present model includes stops and glottal closure /b, d, g, p, t, k, ṭ, q, ʾ/ and continuants /s, z, š, ḫ, ṣ, m, n, l, r, w, y/.

**WHY:** The computational model should not replace philology with abstraction. Buccellati and Huehnergard define the consonantal structure of Akkadian at the grammatical level; only after that inventory is established can one justify collapsing segments into broader timing classes. Without the philological layer, the numerical model would become an arbitrary engineering shortcut.

**THUS:** Every later reduction to closure versus continuant classes must be understood as a timing simplification built on top of the full Akkadian consonant inventory, not as a replacement for it.

---

## 217-Closure-Consonant-Measurements-Provide-The-Low-Level-Baseline

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** The strongest low-level consonantal measurements currently available for the model are the closure-based statistics for stops. Comparative measurements indicate roughly 108 ms for onset stop closure, 113 ms for intervocalic stop closure, and 103 ms for coda stop closure, while singleton stop closures cluster around about 67-70 ms and geminate stop closures around about 187-202 ms.

**WHY:** Yun provides positional measurements showing that stop closure duration is longest intervocalically, slightly shorter in onset position, and shortest in coda position. Hankamer, Lahiri, and Koreman provide the clearest singleton-versus-geminate contrast, with gemination primarily cued by longer closure duration. These values are not Akkadian recordings, but they supply the best empirical baseline for the physical time occupied by closure consonants.

**THUS:** The first numerical model should take stop closure as its main consonantal anchor and should preserve both positional asymmetry and the singleton-versus-geminate distinction in milliseconds.

---

## 218-Closure-Consonant-Perceptual-Thresholds-Matter-For-Gemination

**Domain:** Metrics / Assumptions / Consonants / Perception

**WHAT:** Comparative evidence suggests a perceptual threshold structure for stop gemination: closures shorter than about 100 ms tend to be identified as singletons, whereas closures longer than about 180 ms tend to be heard as geminates.

**WHY:** The numerical model is not only about production-like durations but also about perceptual plausibility. Hankamer, Lahiri, and Koreman show that gemination is not a vague continuum; it has perceptual consequences tied to closure length. This matters directly to any Akkadian model that uses consonantal weight as a realization strategy.

**THUS:** Any modeled geminate closure should remain clearly on the geminate side of the comparative perceptual boundary, and any modeled singleton closure should remain clearly below it.

---

## 219-Fricative-Class-Has-Distinct-Millisecond-Behavior

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** Fricatives constitute a distinct timing class because they occupy duration through sustained friction noise and appear numerically heavier than both closure consonants and sonorants (Howell and Rosen 1983; Morley and Smith 2022).

**WHY:** The extracted measurements no longer justify one secure isolated onset value for fricatives. What they do justify is a consistent heavier-than-stop pattern: fricatives add duration relative to comparable stops, and final fricatives are longer than final stops in directly relevant comparative data. This numerical segregation still matters for any isochrony-oriented model, even though the exact fricative figures remain less normalized than the stop data.

**THUS:** PROPOSED MODEL: The research notes should preserve fricatives as a separate timing class and should model them with their own weaker and more contextual millisecond band rather than burying them inside a generic continuant class.

---

## 220-Sonorant-Class-Has-Distinct-Millisecond-Behavior

**Domain:** Metrics / Assumptions / Consonants

**WHAT:** Sonorants, including nasals, liquids, and glides, constitute a distinct timing class because they realize duration through murmur or transition and cluster below the fricative range.

**WHY:** The extracted evidence indicates that sonorants and glides are not numerically equivalent to fricatives. Their timing is governed less by sustained noise than by transitional or resonant material, which makes their typical millisecond contribution different from that of fricatives even though both lack full closure. For a quantitative model, that difference is large enough to require a separate class.

**THUS:** Sonorants should be modeled as a class distinct from both closure consonants and fricatives, with their own admissible millisecond range and their own sensitivity treatment.

---

## 220b-Kavitskaya-Strengthens-The-Sonorant-Transition-Basis

**Domain:** Metrics / Assumptions / Consonants / Evidence Assessment

**WHAT:** Kavitskaya strengthens the evidential basis for treating glides and at least some liquids as a timing class distinct from both stops and fricatives because she supplies comparative evidence that vowel-to-sonorant transitions are often substantially longer than vowel-to-stop transitions.

**WHY:** This matters because the earlier sonorant class was supported mainly by general phonetic description and mixed transition evidence. Kavitskaya gives a clearer comparative anchor for the claim that sonorants and glides occupy time through murmur and transition rather than through silent closure or sustained frication. The gain is not that Akkadian now has directly attested millisecond values, but that the lower non-closure class is no longer only an abstract residue once fricatives are separated out.

**THUS:** The three-class consonant baseline is now more secure on its sonorant side. Closure consonants remain the firmest class, fricatives remain numerically heavier, and sonorants/glides now have a better comparative justification as a distinct lighter non-closure class.

---

## 221-Three-Class-Consonant-Baseline-Should-Be-Stated-Explicitly

**Domain:** Metrics / Methodology / Parameterization

**WHAT:** The first consonantal baseline should be stated explicitly as a three-class system: closure consonants at about 67-113 ms depending on position, fricatives as a heavier non-closure range supported mainly by relative excess over comparable stops and by final-position fricative values, and sonorants/glides in a lower non-closure range represented by transition- and murmur-based values (Howell and Rosen 1983; Morley and Smith 2022; Billington 2015; Gibson et al. 2013; Kavitskaya 2001).

**WHY:** A three-class system is the minimal segregation that respects the current numerical evidence. A two-class system understates the difference between fricatives and sonorants, while a highly detailed consonant-by-consonant taxonomy would exceed the present evidential strength. The three-class baseline therefore balances numerical realism with methodological restraint.

**THUS:** The article and the software should replace the earlier two-class consonant timing model with a three-class baseline, while continuing to mark fricative and sonorant values as less firmly anchored than the stop-based closure class.

---

## 222-Weakness-Of-NonStop-Consonant-Data-Is-A-Weakness-Of-Comparability

**Domain:** Metrics / Methodology / Consonants

**WHAT:** The weakness of the fricative and sonorant classes does not consist in a total absence of data, but in the fact that their measurements are less comparable, less uniform, and less directly mapped to the same acoustic cue than the closure data.

**WHY:** Stop timing is anchored by one dominant physical quantity, closure duration, which is measured across positional contexts and across the singleton-geminate contrast. By contrast, the non-stop domain mixes different kinds of evidence: fricative duration may be reported as noise duration or onset duration; sonorants may be described by murmur duration, transition length, or transition-to-steady-state ratio; glides are often represented by categorical thresholds rather than stable default durations. This means the numerical evidence is real but not equally normalized across the three classes.

**THUS:** The model may and should retain the three-class consonant system, but it must state openly that closure values are the firmest anchors, whereas fricative and sonorant values are class-level aggregations built from less uniform measurements.

---

## 223-Consonant-Timing-Table-Must-Aggregate-What-Is-Actually-Available

**Domain:** Metrics / Methodology / Consonants / Parameterization

**WHAT:** The consonantal basis of the numerical model should be stated in one explicit table that aggregates the available measurements by timing class and by situation when such distinctions are available (Hankamer, Lahiri, and Koreman 1989; Yungdo Yun 2022; Howell and Rosen 1983; Billington 2015; Gibson et al. 2013; Kavitskaya 2001).

The current publishable aggregation may be stated as follows:

| Timing class | Physical cue | Situation | Consonant measurement in ms | Short vowel baseline | Long vowel baseline | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Closure consonants | Silent closure | Singleton stop baseline | about 67-70 ms | about 75-95 ms | about 145-180 ms | strong |
| Closure consonants | Silent closure | Onset stop closure | about 108 ms | about 75-95 ms | about 145-180 ms | strong |
| Closure consonants | Silent closure | Intervocalic stop closure | about 113 ms | about 75-95 ms | about 145-180 ms | strong |
| Closure consonants | Silent closure | Coda stop closure | about 103 ms | about 75-95 ms | about 145-180 ms | strong |
| Closure consonants | Silent closure | Geminate stop closure | about 187-202 ms | about 75-95 ms | about 145-180 ms | strong |
| Fricatives | Continuous noise | Final fricative excess over comparable stops | about 15-29 ms above comparable final stops; implied final band about 118-132 ms against the 103 ms stop-coda anchor | about 75-95 ms | about 145-180 ms | moderate-to-weak |
| Sonorants | Murmur / transition | Liquid-sonorant onset anchor with broader sonorant comparison band | liquids about 89 ms in singleton onset; broader sonorant onset space about 69-97 ms when liquids, nasals, and glides are combined | about 75-95 ms | about 145-180 ms | weak-to-moderate |
| Glides | Transition | Glide thresholds | about 40-100 ms transition space | about 75-95 ms | about 145-180 ms | weak |

The singleton stop baseline is smaller than the positional stop values because it comes from a different but still comparable question. It reflects singleton stop closure in contrast with geminate closure in Turkish and Bengali, where the relevant comparison is singleton versus geminate (Hankamer, Lahiri, and Koreman 1989), whereas the onset, intervocalic, and coda values come from positional stop closure in Korean (Yungdo Yun 2022). The smaller singleton baseline is therefore not an error. It is a cross-linguistic singleton anchor, not a positional onset default.

**WHY:** A model that aims to generate isochrony cannot ignore the numerical separation between closure, fricative, and sonorant timing (Hankamer, Lahiri, and Koreman 1989; Yungdo Yun 2022; Howell and Rosen 1983; Morley and Smith 2022; Billington 2015; Gibson et al. 2013; Kavitskaya 2001). At the same time, it must not pretend that every class is supported by equally normalized data. The sonorant side is now somewhat better grounded for onset behavior because singleton liquids give one clearer anchor, but it still lacks a matched cross-position sonorant series. The right methodological response is therefore to expose the whole table, keep the available distinctions, and mark the weaker zones openly instead of collapsing them out of existence.

**THUS:** PROPOSED MODEL: The article and the software may adopt this aggregated consonant table as the initial basis for modeling, provided that fricative and sonorant values are explicitly presented as weaker class-level assumptions rather than as settled constants.

---

## 223b-Perceptual-Threshold-Table-Should-Be-Stated-Explicitly

**Domain:** Metrics / Assumptions / Thresholds / Perception

**WHAT:** The publishable timing notes should state one compact threshold table for the two strongest perceptual boundaries currently available: stop singleton versus geminate, and one mora versus two morae in vowel-bearing intervals (Hankamer, Lahiri, and Koreman 1989; Kosuke Sugai 2017).

The current publishable threshold table may be stated as follows:

| Contrast | Secure shorter side | Boundary region | Secure longer side | Status |
| :--- | :--- | :--- | :--- | :--- |
| Stop singleton vs geminate | less than about 100 ms | about 100-180 ms | greater than about 180 ms | strong |
| One-mora vs two-mora vowel-bearing interval | less than about 210 ms | about 250-270 ms | greater than about 330 ms | moderate-to-strong |

**WHY:** The consonant threshold is anchored in stop closure perception, where listeners identify intervals below about 100 ms as singleton-like and intervals above about 180 ms as geminate-like (Hankamer, Lahiri, and Koreman 1989). The vocalic threshold is anchored in Sugai's mora-perception work, which places the most important second-mora boundary around 250-270 ms and makes it useful to distinguish safer shorter and longer sides on either side of that boundary (Kosuke Sugai 2017).

**THUS:** PROPOSED MODEL: The article and the software should treat these values as perceptual anchors rather than as ordinary production means. They define where the timing model begins to approach categorical interpretation, not where every ordinary token must fall.

---

## 224-Short-And-Long-Vowel-Measurements-Define-The-Base-Vocalic-System

**Domain:** Metrics / Assumptions / Vowels

**WHAT:** The base vocalic timing system for the model should be defined by short vowels of roughly 60-100 ms and long vowels of roughly 120-200 ms, with an observed long-to-short ratio commonly falling between about 1.65 and 1.93 depending on speech conditions.

**WHY:** Sugai, Jia, and Kozasa together provide the strongest comparative grounding for a quantity-sensitive vocalic system in milliseconds. The important point is not a single exact value but a stable quantitative contrast between shorter and longer vowels, large enough to map onto moraic perception while remaining within realistic speech timing.

**THUS:** The first numerical model should treat short and long vowels as the base vocalic classes and should encode both their millisecond ranges and their ratio structure explicitly.

---

## 225-Moraic-Perception-Requires-A-Quantitative-Vocalic-Boundary

**Domain:** Metrics / Assumptions / Vowels / Perception

**WHAT:** Comparative quantity-sensitive timing supports a perceptual boundary for a second mora around 250-270 ms.

**WHY:** Sugai is especially important because it does not merely report raw durations; it connects duration to moraic parsing. This gives the project a bridge between low-level milliseconds and higher-level rhythmic interpretation. A vowel or vowel-bearing sequence that approaches this region is no longer just longer in a vague sense; it approaches the perceptual territory of bimoraic weight.

**THUS:** The vocalic part of the model should be read not only as a table of durations but as a table of durations interpreted through moraic thresholds.

---

## 226-Very-Long-Vowel-Measurements-Belong-To-Contextual-Realization

**Domain:** Metrics / Assumptions / Vowels / Context

**WHAT:** Very long vowel realizations may reach roughly 200-240+ ms or a ratio around 2.42 times the short-vowel baseline, but these values belong to contextual realization rather than to the lexical inventory.

**WHY:** Kozasa shows that markedly extended vowel duration can arise under specific prosodic conditions, especially where durational contrast must carry more of the functional load. The philological evidence from Akkadian supports marked lengthening in special positions, but not an ordinary third lexical vowel length category. The numerical fact and the philological interpretation must therefore be kept together.

**THUS:** The algorithm may use very long values only under contextual activation rules such as finality or exceptional prominence, never as part of the ordinary base inventory.

---

## 226b-Very-Long-Vowel-Confidence-Is-Contextual-Not-Basal

**Domain:** Metrics / Assumptions / Vowels / Confidence

**WHAT:** Confidence in very long vowels around 200-240+ ms is moderate when they are treated as contextual realizations, low when they are treated as lexical defaults, and stronger when they are treated as a pre-threshold zone below clear second-mora categorization (Morley and Smith 2022; Sugai 2017; Rossi, Smit, and Rathcke 2023).

**WHY:** The source base points in three directions at once. Morley and Smith show that vowels at or above about 200 ms are relatively infrequent in ordinary conversational speech, which makes the band too rare for an unmarked lexical baseline. At the same time, controlled production and rhythmic test settings regularly enter this region, so the band is phonetically real rather than speculative (Morley and Smith 2022; Rossi, Smit, and Rathcke 2023). Sugai then clarifies its interpretive role: because the isolated second-mora boundary lies around 250-270 ms, the 200-240 ms region is best treated as pre-boundary territory, close to phonological ambiguity but not yet securely on the two-mora side (Sugai 2017).

**THUS:** PROPOSED MODEL: Very long vowels should be retained with an explicit confidence label. They are defensible as contextual realizations triggered by finality, prominence, or stylized delivery, but they should not be treated as part of the ordinary vowel inventory or as high-confidence default production values.

---

## 227-Pause-Measurements-Must-Combine-Threshold-Baseline-And-Ceiling

**Domain:** Metrics / Assumptions / Pauses

**WHAT:** The pause model should combine four explicit numerical layers: a functional floor around 250 ms, a short-pause baseline around 600-680 ms, a long-pause range around 1200-1780 ms, and an upper caution around 1900 ms for natural modeled realization.

**WHY:** Different pause numbers answer different questions. Anjarningsih supports the functional threshold and the longer clause-boundary tier, Lin supplies a naturalness-oriented short baseline around 600 ms, and the higher pathological values provide a caution against mechanically overextending silence. Without this layered interpretation, pause timing becomes either too vague or too rigid.

**THUS:** The algorithm should encode pause timing as a hierarchy of floor, baseline, long tier, and ceiling rather than as one fixed number for all silent intervals.

---

## 228-Global-Silence-Share-Is-Part-Of-The-Physical-Model

**Domain:** Metrics / Assumptions / Pauses / Utterance Structure

**WHAT:** The total share of silence in modeled recitation should remain in the broad vicinity of 30-40% of utterance time.

**WHY:** Goldman-Eisler provides the key argument that silence is not extraneous noise outside the rhythm model; it is part of utterance timing. This matters because a model can assign locally plausible pauses yet still distort the whole rhythm if silence occupies too little or too much of the total duration.

**THUS:** The numerical model must check not only individual pause durations but also the total silent share of the utterance as a global constraint.

---

## 229-First-Baseline-Parameter-Set-Can-Be-Stated-Explicitly

**Domain:** Metrics / Methodology / Parameterization

**WHAT:** A defensible first baseline parameterization can now be stated explicitly as follows: closure-stop singleton about 67-113 ms depending on position, closure-stop geminate about 187-202 ms, fricatives as a heavier non-closure class but with only weaker contextual timing anchors at present, sonorants and glides as a lighter non-closure class, short vowels about 60-100 ms, long vowels about 120-200 ms, contextual very long vowels about 200-240+ ms only under marked conditions, short pauses about 600-680 ms, long pauses about 1200-1780 ms, pause floor about 250 ms, and total silence about 30-40% of utterance time.

**WHY:** This is the point at which high philological structure and low-level measurement meet. The phonological inventory and Akkadian constraints determine what may be lengthened, where, and why; the empirical measurements determine the physical scale on which those operations may be modeled. The new numerical segregation among fricatives and sonorants strengthens the consonantal side of the model by preventing the non-closure domain from being treated as one undifferentiated block.

**THUS:** The research notes now contain a publishable baseline numerical model that can serve both the article and the rewritten metric computation pipeline, provided that each value remains tied to its evidential status and contextual limits.

---

## 229b-CVC-May-Be-Centered-In-The-Low-300-ms-Heavy-Range

**Domain:** Metrics / Assumptions / Syllables / Heavy Class

**WHAT:** The heavy syllable type `CVC` may be grounded most cautiously in the compositional interval `286-306 ms`. If the runtime also has to remain compatible with the empirically grounded short-pause region `600-680 ms`, then halving that pause region yields `300-340 ms`, and the empirical overlap lies at `300-306 ms`. A value such as `305 ms` may therefore serve as a conservative scalar runtime control without being presented as a directly measured historical constant (Morley and Smith 2022; Sugai 2017; Yungdo Yun 2022; Kozasa 2002).

**WHY:** The strongest segmental composition currently available puts a stop-based `CVC` near that zone. If the onset closure is about 108 ms, the short vowel about 75-95 ms, and the coda stop about 103 ms, the resulting closed syllable falls around 286-306 ms before any higher-order compensation is added (Yungdo Yun 2022; Sugai 2017; Kozasa 2002). Sugai's `tan`-type perception data then provide an important upper-side anchor: the one-mora to two-mora region centers around 250-270 ms, and one-mora interpretations become scarce once the relevant interval exceeds about 310 ms (Sugai 2017). Morley and Smith, conversely, show that ordinary conversational CVC tokens may be much shorter than controlled timing values, which is why conversational medians should not be taken as the modeling target (Morley and Smith 2022).

**THUS:** PROPOSED MODEL: The `CVC` side of the heavy class should be grounded openly as `286-306 ms`. When one scalar runtime control is needed and compatibility with the empirical short-pause region is desired, a value inside the overlap `300-306 ms`, such as `305 ms`, is methodologically safer than a value chosen from the midpoint alone.

---

## 229c-One-Complete-Millisecond-Picture-Should-Be-Stated-Explicitly

**Domain:** Metrics / Methodology / Parameterization / Summary Table

**WHAT:** The project should state one complete model-facing picture of durations in milliseconds, covering four consonant classes, two vowel classes, two pause classes, and the two main perceptual threshold tables now supported by the bibliography (Hankamer, Lahiri, and Koreman 1989; Yungdo Yun 2022; Howell and Rosen 1983; Billington 2015; Gibson et al. 2013; Kavitskaya 2001; Sugai 2017; Kozasa 2002; Goldman-Eisler 1968; Lin 2021; Anjarningsih 2024).

The current complete summary may be stated as follows:

| Domain | Class | Members or cue | Grounded duration in ms | Status |
| :--- | :--- | :--- | :--- | :--- |
| Consonants | Transitions | internal `˙` for zero onset or strict hiatus, internal `¨` for stronger vowel transition only | onset floor about 40 ms; broader transition space up to about 100 ms; optional glottalized stress proxy about 187-202 ms only if forced | weak as direct measurement, but usable as modeling marker |
| Consonants | Closures | `b`, `d`, `g`, `k`, `p`, `t`, `ṭ`, `q`, `ʾ` | singleton and positional closure about 67-113 ms; geminate stop closure about 187-202 ms | strong |
| Consonants | Fricatives | `s`, `z`, `š`, `ṣ`, `ḥ`, `ḫ`, `ʿ` | no secure unified onset value yet; final fricatives about 15-29 ms longer than comparable final stops, implying a contextual final band about 118-132 ms | moderate-to-weak |
| Consonants | Liquide / Nasal / Glide | `l`, `r`, `m`, `n`, `w`, `y` | liquids about 89 ms in singleton onset; broader onset comparison space about 69-97 ms when nasals and lexical glides are included; lexical glides about 163-167 ms under gemination | weak-to-moderate |
| Vowels | Short | `a`, `e`, `i`, `u` | about 75-95 ms as filtered central baseline for natural production | strong as production baseline |
| Vowels | Long | `ā`, `ē`, `ī`, `ū`, `â`, `ê`, `î`, `û` | about 145-180 ms as filtered central baseline for natural production | strong as production baseline |
| Vowels | Very long / contextual | marked extension of long vowels | about 200-240+ ms under marked conditions only | moderate as contextual realization; low as lexical default |
| Pauses | Short | punctuation-scale pause | about 600-680 ms, with pause floor around 250 ms | moderate |
| Pauses | Long | major boundary pause | about 1200-1780 ms | moderate |

The main threshold table may be restated alongside it:

| Contrast | Secure shorter side | Boundary region | Secure longer side | Status |
| :--- | :--- | :--- | :--- | :--- |
| Stop singleton vs geminate | less than about 100 ms | about 100-180 ms | greater than about 180 ms | strong |
| One-mora vs two-mora vowel-bearing interval | less than about 210 ms | about 250-270 ms | greater than about 330 ms | moderate-to-strong |

**WHY:** The project now has enough comparative material to state one explicit duration picture, but not enough to pretend that every row is equally normalized. Closure and vowel anchors remain the strongest parts of the system. The vowel rows are especially secure if they are understood as production baselines for natural timing, not as perceptual thresholds and not as laboratory elongation targets. The Transition row is weaker in a different way: it is now deliberately narrow and serves mainly as the marker for zero onset and hiatus-like passage. Returning `ʾ` to closures and `ʿ ḥ` to fricatives keeps the main model closer to traditional classification and avoids making the article depend on a weakly grounded microclassification. Lexical `w` and `y` still belong mainly with the Liquide / Nasal / Glide class unless reduced to a very short transition-like realization. Fricatives, liquids, nasals, glides, and pauses are still usable, but they must retain wider tolerances and clearer evidential marking. Stating the whole picture in one place makes the relation between secure anchors and weaker contextual defaults visible.

The confidence judgment for vowels may be stated explicitly: the short-vowel band around 75-95 ms and the long-vowel band around 145-180 ms are high-confidence comparative defaults for modeled production, because they align with conversational short-vowel behavior and with produced long-vowel values in quantity-sensitive systems, even though the perceptual second-mora boundary lies much higher, around 250-270 ms in isolated vowel-bearing intervals (Morley and Smith 2022; Sugai 2017; Kozasa 2002). By contrast, the very-long-vowel band around 200-240+ ms has only contextual confidence: it is phonetically real under marked conditions and close to the perceptual ambiguity zone, but it is too rare and too condition-dependent to serve as an ordinary lexical default (Morley and Smith 2022; Sugai 2017; Rossi, Smit, and Rathcke 2023).

**THUS:** PROPOSED MODEL: The article and software documentation should use this complete picture as the reference summary for duration defaults and thresholds, while continuing to treat the weaker consonant and pause classes as contextual ranges rather than fixed historical values.

---

## 229d-Two-Stage-Model-Architecture-Makes-The-Argument-Stronger

**Domain:** Metrics / Methodology / Research Design

**WHAT:** The duration model is strongest when it is presented as a two-stage architecture: first, a grounded `CVC`-based millisecond hypothesis for rhythm metrics; second, a separate accentual realization layer testing a bimoraic pacing proposal (White and Mattys 2007; Sugai 2017).

**WHY:** These two tasks are related but not identical. The first stage assigns plausible durations to transliterated Akkadian so that `%V`, `DeltaC`, `DeltaV`, `VarcoV`, `nPVI-V`, `rPVI-C`, and `VarcoC` can be computed. The strongest current anchor for that stage is the heavy syllable itself. Published comparative work supports the more general claim that syllables are more robust timing units than isolated segments and that rhythmic classification is sensitive to heavier syllable structure and interval organization (Pellegrino, Coupé, and Marsico 2011; White and Mattys 2007). The second stage then asks whether a separate prosodic realization algorithm can move selected structures toward an even-moraic pacing hypothesis. Keeping these layers distinct prevents the article from appearing to claim that one single model simultaneously proves both rhythm classification and accentual realization.

**THUS:** PROPOSED MODEL: The article should present the first computation as a `CVC`-anchored metric-calibration hypothesis and the second as a prosodic-realization hypothesis built on top of it.

---

## 229e-Heavy-Syllable-Targets-Should-Be-Treated-As-Attractor-Ranges

**Domain:** Metrics / Methodology / Parameterization / Caution

**WHAT:** The heavy syllable target centered near 310 ms is better treated as an attractor range than as an exact surface value (Sugai 2017; Yungdo Yun 2022; Kozasa 2002).

**WHY:** Speech timing is not precise to the millisecond, and the current comparative evidence does not justify such precision for Akkadian. A bounded heavy range such as roughly 295-325 ms preserves the grounding of the stop-based `CVC` calculation while avoiding false exactness. It also makes it easier to reject outputs that would force short or long vowels outside the admissible vocalic bands.

**THUS:** PROPOSED MODEL: The software should use central values such as 310 ms as attractors inside admissible ranges rather than as rigid targets that every output must realize exactly.

---

## 229e2-Cvc-Timing-Is-The-Best-Grounded-Foundation-For-The-Isochrony-Hypothesis

**Domain:** Metrics / Methodology / Parameterization / Foundation

**WHAT:** The current model should be framed as resting on the `CVC` syllable, or more precisely the heavy syllable interval, as its best grounded temporal foundation. Bimoraic pacing should then be presented as a derived hypothesis built on that foundation rather than as the primary starting premise.

**WHY:** This reframing improves the evidential order of the argument. The sources do not justify strict isochrony in the strong sense, and they do not warrant the claim that every heavy syllable has one universal duration. They do, however, support three narrower points. First, larger intervals such as the syllable are more stable objects of comparison than isolated segments, which makes them better anchors for a timing model of a language with no direct acoustic record (Pellegrino, Coupé, and Marsico 2011). Second, phonological and phonetic work on syllable weight converges on the heavy `CVC` pattern as a robust timing and parsing unit: `CVC` is categorically heavy in moraic theory, coda loss is often compensated within the same weight domain, and coda presence contributes measurably to perceived weight and stress behavior (Hayes 1989; Broselow, Chen, and Huffman 1997; Ryan 2014). Third, rhythmic typology work suggests that heavier closed-syllable structure contributes directly to the interval profile associated with stress-timed rhythm, which makes the `CVC` anchor relevant not only to metrical theory but also to the metrics the project is actually computing (White and Mattys 2007).

This is a stronger position than saying simply that the model is bimoraic because such a model is convenient or typologically familiar. The `CVC` interval is the comparatively grounded part. Bimoraicity enters one step later as an interpretation of why that interval behaves as it does and as a guide for second-stage accentual realization. The derivational order should therefore remain explicit. `CVC` supplies the base time unit. `CVV` synchronizes with that same heavy unit as the first vocalic counterpart. `CV` and `CVVC` are then derived from that anchored base as the lighter and heavier extensions of the same timing system. The article may therefore claim that the model begins from the most defensible interval-level anchor available and only then tests whether a bimoraic pacing analysis helps explain or regularize the resulting timing picture.

**THUS:** PROPOSED MODEL: Reframe the project so that `CVC` timing is the primary foundation of the interval model, while bimoraic realization remains a secondary, testable hypothesis built upon that foundation.

---

## 229e3-New-Cvc-Sources-Strengthen-The-Foundation-But-Do-Not-License-Overstatement

**Domain:** Metrics / Methodology / Bibliography / Caution

**WHAT:** The newer `CVC`-focused source review strengthens the foundation of the model, but it should be used to support a careful interval-based claim rather than a stronger claim of absolute or universal heavy-syllable isochrony.

**WHY:** The newer materials improve the argument in two ways. They reinforce the idea that `CVC` functions as a stable unit of weight in both phonological theory and rhythmic perception, and they clarify that the coda is not merely an appended consonant but part of the timing domain of the heavy syllable (Hayes 1989; Broselow, Chen, and Huffman 1997; Ryan 2014). They also make it easier to frame the model around heavier interval structure rather than around isolated segmental timing. For the article-facing notes, however, only the published sources that can be quoted directly should carry the argument. Temporary extraction files, page-index summaries, and weakly normalized comparative numbers should not be treated as quotable authorities in their own right. The secure gain is therefore conceptual and architectural rather than the discovery of one new decisive millisecond constant.

**THUS:** PROPOSED MODEL: Use the newer `CVC` materials to strengthen the argument that the interval model should begin from the heavy syllable, but keep the article's phrasing hedged: the evidence supports `CVC` as the best grounded foundation for the model's isochrony hypothesis, not as proof of strict or universal syllable isochrony.

---

## 229e4-Vc-Rhyme-Is-The-Load-Bearing-Domain-Of-Heavy-Syllable-Catch-Up

**Domain:** Metrics / Methodology / Parameterization / Rhyme

**WHAT:** Inside the heavy-syllable foundation, the load-bearing subinterval is best treated as the rhyme, especially `VC` in `CVC`. That is the domain in which accentual catch-up and local isochrony repair should be described.

**WHY:** This formulation fits both the syllable inventory and the timing problem. Akkadian syllables reduce to `CV`, `CVC`, `CVV`, and `CVVC`. The onset still contributes duration and therefore still matters for consonantal interval metrics. But the part of the syllable that carries weight is the nucleus-plus-coda domain. Moraic phonology already locates heaviness there, and phonetic work on syllable weight likewise shows that the coda contributes to the same weight-bearing unit rather than standing outside it as a purely appended segment (Hayes 1989; Broselow, Chen, and Huffman 1997; Ryan 2014). For the present model, this means that in `CVC` the second mora should not be identified with the coda alone. It is better understood as a shared `VC` domain in which timing may be redistributed between vowel and coda during repair or accentuation.

This is also the cleaner way to describe local compensation. If the model needs a heavy syllable to catch up rhythmically, it should not be said that the final consonant alone absorbs the added time. The stronger claim is that the `VC` rhyme absorbs the adjustment, with the exact distribution constrained by the consonant and vowel timing parameters. That allows the model to preserve both the heavy-syllable anchor and the observed fact that coda-bearing weight is not merely consonantal addition on top of an unchanged nucleus. By contrast, `CVV` synchronizes with the same heavy target through the vocalic domain. In that sense, `CVC` grounds the heavy time unit, while `CVV` is the first synchronized counterpart rather than a separate foundation.

**THUS:** PROPOSED MODEL: Keep `CVC` as the syllable-level anchor of the computation layer, but describe the internal catch-up and accent-bearing domain as `VC` rather than as the coda alone.

---

## 229f-Range-Based-Attractors-Reduce-The-Circularity-Problem

**Domain:** Metrics / Methodology / Validation

**WHAT:** The circularity problem in deriving vowel durations from syllable targets is reduced if syllable values are treated as bounded attractors and vowel ranges are treated as admissibility constraints rather than as independent confirmation.

**WHY:** A rigid target asks the derived vowels to validate the very quantity from which they were derived. A bounded target changes the logic. The vowel bands do not prove the target from outside. They filter a permitted region and exclude outputs that would violate the independently grounded short and long vowel ranges. That is still a constrained model, but it is methodologically cleaner than presenting the result as a closed self-confirming system.

**THUS:** PROPOSED MODEL: The article should describe vowel-range checks as admissibility constraints on the syllable model, not as wholly independent verification.

---

## 229g-A-Fuller-Consonant-Table-May-Extend-The-Minimal-Model

**Domain:** Metrics / Methodology / Parameterization / Extension

**WHAT:** The minimal five-parameter model may be extended to a fuller consonant table whenever the user wishes to activate positional detail or inferred ratio-based defaults.

**WHY:** The present evidence does not support every onset, intervocalic, coda, and geminate cell equally across all consonant classes. Even so, the software need not be restricted to the minimal collapse forever. Stronger classes, especially stops, already justify positional distinction, and weaker classes may be extended by cautious ratio-based inference so long as inferred cells remain explicitly marked as less direct than measured ones.

**THUS:** PROPOSED MODEL: The project should preserve both layers: a minimal computation model for robust default use and an optional fuller table for sensitivity analysis and later refinement.

---

## 229h-Bootstrap-Parameter-Tables-Must-Distinguish-Empirical-And-Inferred-Cells

**Domain:** Metrics / Methodology / Parameterization / Bootstrap

**WHAT:** A bootstrap parameter table for the duration model should distinguish empirical cells from inferred cells explicitly, and should state the completion rule used for any missing consonant-position values.

**WHY:** The current evidence is uneven. Stops provide the clearest onset, intervocalic, coda, and geminate series. Fricatives are best grounded by additive excess over comparable stops. Liquids, nasals, glides, and hiatus-like transitions are real parts of the timing model, but their measurements are patchier and should not be displayed as though every cell were directly observed. The hiatus row in particular must be interpreted narrowly if it is meant to model zero onset and diphthong transition rather than full lexical glide duration. A parameter table that marks `not available`, then fills gaps through declared delta or ratio rules, is methodologically clearer than one that silently homogenizes the evidence.

**THUS:** PROPOSED MODEL: The default bootstrap table should prefer constant-delta completion where additive evidence exists, especially for fricatives relative to stops, while retaining ratio-based completion only as an exploratory alternative for sensitivity analysis.

---

## 229i-Delta-Based-Completion-Is-Preferable-For-The-Current-Consonant-Table

**Domain:** Metrics / Methodology / Parameterization / Inference Rules

**WHAT:** For the present consonant bootstrap, delta-based completion is preferable to ratio-based completion.

**WHY:** The best currently available inter-class relation is additive. Morley and Smith show that fricatives contribute about 28.83 ms more than comparable stops, and final fricatives are about 15-29 ms longer than comparable final stops. That supports an additive completion rule more directly than a multiplicative one. Stop positional asymmetry likewise yields usable small offsets from onset to intervocalic and coda position. Ratio-based completion remains possible, but it is less directly anchored by the present evidence.

**THUS:** PROPOSED MODEL: The main bootstrap should use delta-based inferred cells as the default completion method, with ratio-based cells preserved as optional alternative settings rather than as coequal defaults.

---

## 229j-Raw-Source-Values-And-Reduction-Techniques-Must-Precede-Final-Parameters

**Domain:** Metrics / Methodology / Parameterization / Documentation

**WHAT:** A defendable duration note must show the raw comparative values and the reduction technique before it states a final modeled parameter.

**WHY:** The current consonant evidence is cross-linguistic, mixes different acoustic quantities, and often combines direct values with contextual offsets. Under those conditions, a bare final number hides too much. The reader needs to see which values were actually observed, whether they were closure durations, full segment durations, transition spans, or contextual deltas, and then how the model reduced them by direct carry-over, median-like selection, structural minimum, contextual delta, or functional override.

**THUS:** Every future bootstrap table should display source values first, then the reduction method, and only then the chosen parameter.

---

## 229k-The-Full-Table-Is-The-Evidential-Layer-And-The-Simplified-Model-Is-Derived-From-It

**Domain:** Metrics / Methodology / Parameterization / Model Design

**WHAT:** The full consonant table and the simplified five-parameter model must not compete with one another. The full table is the evidential layer; the simplified model is a later engineering reduction derived from it.

**WHY:** A simplified model is defensible only if the fuller table shows either small positional spread or uncertainty large enough to justify collapse. If the fuller table exhibits large systematic positional differences, then the simplification would erase real structure. If, however, the fuller table shows only minor asymmetry, such as stop closure values around `103-113 ms`, then a rounded non-geminate default can be justified as a practical approximation for software. In the present table, the simplified defaults remain fairly close to the fuller non-geminate rows: `110 ms` for stops diverges by only about `0.9-6.8%` from the stop cells, and `140 ms` for fricatives diverges by about `1.4-6.1%` from the current fricative cells. For corpus-scale indicator computation, that level of simplification is small enough to be methodologically tolerable, provided that the fuller table remains visible as the evidential layer.

**THUS:** The project should first finalize the fuller table, then derive the five-parameter model from it by explicit collapse and rounding rules rather than by independent choice.

---

## 229k2-Simplification-Is-A-Computational-Collapse-Not-A-Claim-That-Classes-Are-Phonetically-Identical

**Domain:** Metrics / Methodology / Parameterization / Computation

**WHAT:** The simplified five-parameter model should be presented as a computational collapse for robust corpus-wide metric extraction, not as a claim that each consonant class is phonetically uniform across positions.

**WHY:** The next stage of the project is to compute time indicators across the full corpus of about five thousand words. For that task, a compact parameter set is useful because it stabilizes implementation and keeps the metric pipeline transparent. Yet the simplification should not be mistaken for phonetic identity. The fuller table preserves positional and evidential nuance, while the simplified layer supplies stable defaults whose divergence from the fuller non-geminate rows remains limited. The collapse is therefore best understood as an engineering reduction in the service of reproducible measurement, not as a strong phonetic claim about Akkadian articulation.

**THUS:** The public notes may use the simplified model for corpus-scale computation, while continuing to cite the fuller table whenever the argument turns from engineering convenience to evidential precision.

---

## 229l-Delta-Should-Track-Structural-Minimum-Not-Just-Class-Average

**Domain:** Metrics / Methodology / Parameterization / Inference Rules

**WHAT:** When the duration model uses inter-class delta, that delta should track structural minimum articulation time rather than merely the average of full lexical segment durations.

**WHY:** The model is trying to estimate how much time a class minimally occupies inside a timed interval. For fricatives, the additional turbulent interval over stops already appears as a positive contextual delta. For liquids, nasals, and glides, the relevant structural minimum may be lower than the common full lexical singleton durations, because compressed liquids and transition-like realizations show that the class can be realized more quickly than a naive average of lexical values would suggest.

**THUS:** Delta-based inference should be retained, but it must be interpreted as a structural-minimum hypothesis rather than as a hidden averaging device.

---

## 229m-Transitions-Should-Remain-A-Narrow-Functional-Row

**Domain:** Metrics / Methodology / Parameterization / Special Cases

**WHAT:** The Transition row should remain a narrow functional row for the internal markers `˙` and `¨`. In the current notation, `˙` marks zero onset or strict hiatus, while `¨` marks the stronger vowel-transition case. The row should not expand into a separate phonological superclass for rare back or pharyngeal consonants.

**WHY:** The narrow row is easier to defend. Zero onset and strict hiatus behave like a short transition floor, while stronger vowel transition behaves more like a glide-like passage. The upper value is therefore supported only by glide-like proxy evidence, not by merging the internal marker `¨` with lexical glides as a phonological class. By contrast, promoting `ʾ ʿ ḥ` into dedicated weak subclasses would create a reviewer-facing distinction that is only weakly grounded and probably unnecessary, especially since these consonants are rare enough that assigning them to their parent stop or fricative classes is unlikely to distort the global metrics materially.

**THUS:** The parameter table should keep the row explicit, but should interpret it narrowly as internal `˙ = 12 ms` for onsetless entry or strict hiatus and internal `¨ = 52 ms` for stronger vowel transition, with any glottalized stress realization treated as an optional processing rule rather than as the default geminate value of a phonological class. These markers belong to internal processing only. They are not user-facing output symbols.

---

## 229n-Weak-Stop-And-Weak-Fricative-Subclasses-Should-Remain-Exploratory

**Domain:** Metrics / Methodology / Parameterization / Caution

**WHAT:** Weak-stop and weak-fricative subclasses may be useful for local experimentation, but they should remain exploratory rather than article-facing defaults.

**WHY:** A reduction-based microclassification such as weak stops `{ ¨, ʾ }` and weak fricatives `{ ʿ, ḥ }` is conceptually intelligible, but the present evidence base does not ground it strongly enough to make it central to the published argument. Because these consonants are rare and historically recessive, treating them as members of their parent classes is unlikely to distort `DeltaC` materially, whereas promoting them to separate default subclasses would create a disproportionate methodological burden.

**THUS:** The main notes should keep the conservative arrangement, while local testing may still explore parameters such as `reduct_weak_stop` and `reduct_weak_fricative`.

---

## 229o-Stressed-Initial-VC-Should-Be-Realized-Primarily-Through-Vowel-Expansion

**Domain:** Metrics / Accentuation / Parameterization / Special Cases

**WHAT:** When a word begins with `VC` and that initial syllable is stressed, the preferred realization is not a geminated transition `˙:VC`, but `˙ + V+ + C`, where the vowel is expanded beyond ordinary short-vowel duration without reaching the full `VV` band.

**WHY:** The onsetless initial syllable still needs a phonological interpretation for both academic description and the accentuation algorithm, but a geminated hiatus marker overstates the role of the weak onset slot. Expanding the vowel instead preserves the fact that the syllable is onsetless while still giving stress a measurable temporal effect. The Transition class therefore remains necessary for classifying onsetless entry, even if stressed initial `VC` is no longer realized as transition gemination.

**THUS:** The algorithm may still represent initial `VC` structurally as `˙VC`, but stressed initial `VC` should preferably surface as `˙ + V+ + C` rather than `˙:VC`. By contrast, the internal marker `¨` should be reserved for the stronger vowel-transition case.

---

## 229p-User-Visible-Yaml-Should-Contain-Only-Exposed-Parameters

**Domain:** Metrics / Methodology / Parameterization / Configuration

**WHAT:** The user-visible YAML configuration should contain only parameters that the user may legitimately change for metric computation. Internal symbols, parser markers, fixed punctuation classes, and algorithm-internal constants should remain hardcoded rather than being exposed as editable data.

**WHY:** This point is methodological rather than bibliographic. A configuration file becomes less transparent when it mixes empirical inputs with constants that are not meant to vary. The empirical side of the present model concerns consonant durations, vowel durations, pause durations, pause ratio, and a small number of perceptual thresholds. By contrast, symbols such as the prosodic marker, the onsetless placeholder, or strong versus weak pause markers belong to the internal grammar of the program. Exposing them in the same file would blur the distinction between evidence-bearing data and implementation constants.

**THUS:** PROPOSED MODEL: The YAML should be treated as a user-adjustable empirical input layer only. Anything that is not meant to be tuned by users should remain outside it.

---

## 229q-Hiatus-In-Yaml-Should-Be-A-Compact-Duration-Proxy

**Domain:** Metrics / Methodology / Parameterization / Zero Onset

**WHAT:** The user-facing YAML should not expose the internal symbols themselves. Internally, the current model uses `˙` for onsetless entry or strict hiatus and `¨` for stronger vowel transition, but the YAML should expose only the durations attached to those internal markers, not the symbols.

**WHY:** The comparative evidence supports a narrow transition discussion for onsetless entry and hiatus-like passage, but the internal grammar now distinguishes two cases rather than one. The internal marker `˙` carries the strict hiatus value `12 ms`, while `¨` carries the stronger vowel-transition value `52 ms`. Because these are internal processing symbols rather than user-facing characters, exposing the symbols themselves in the configuration would blur the distinction between model data and internal grammar. What belongs in the YAML is the duration system, not the symbolic encoding.

**THUS:** PROPOSED MODEL: Keep only the durations in the YAML, namely `hiatus = 12 ms` and `vowel_transition = 52 ms`, and document separately in the notes that the internal processor encodes those values with `˙` and `¨` respectively. This makes the symbolic distinction available for implementation without turning it into user-facing output.

---

## 229r-Geminate-Durations-In-Yaml-Should-Be-Visible-But-Secondary

**Domain:** Metrics / Methodology / Parameterization / Gemination

**WHAT:** Geminate durations may be stored in the user-facing YAML, but they should be treated as secondary, model-facing summary values rather than as primary empirical anchors. Their role is to make the active reasoning visible and to allow comparison against derived or additive alternatives.

**WHY:** The strongest direct geminate evidence concerns stop closure, where comparative studies place singleton-like closure below about `100 ms` and geminate-like closure above about `180 ms`, with production values around `187-202 ms` for stop geminates (Hankamer, Lahiri, and Koreman 1989). A single YAML value such as `194.5 ms` is therefore only a compact summary of an attested band, not a new measured fact. For fricatives the situation is weaker still, but the active configuration now prefers `279 ms` rather than the older `284 ms`, because the exposed row has been regularized around the additive cap `137 + 142` instead of around a separate protraction estimate. For the sonorant row, the current `163 ms` anchor is no longer just a structural doubling. It is tied to the clearer glide-geminate comparison around `163-167 ms`, while the lower side of the row is already carried by the ordinary onset and coda anchors. Storing these values can still be useful because it keeps the reasoning legible inside the active configuration file. But the evidential rank of the three rows remains unequal, and the YAML comments should make that visible.

**THUS:** PROPOSED MODEL: The YAML may keep explicit geminate values for practical transparency, provided that they are interpreted correctly: closure geminate as a summary of an attested range, fricative geminate as a capped additive target in a weakly grounded row, and sonorant geminate as a direct glide-facing anchor rather than as a mechanical doubling. These entries should remain explanatory and secondary, and they should be paired with class-specific geminate perception floors rather than treated as self-sufficient facts. For closures, that floor should be placed near the >`180 ms` side of the stop contrast, not mechanically at the lowest produced geminate token `187 ms`.

---

## 229s-The-Cvc-Entry-In-Yaml-Should-Be-Only-The-Grounded-Closed-Syllable-Range

**Domain:** Metrics / Methodology / Parameterization / Syllables

**WHAT:** The YAML should contain only the grounded `CVC` range `286-306 ms` in the syllable row. If the file stores a broader `310 ms` ceiling, that ceiling must be segmental only. It must not redefine `CVC`, and it must not be allowed to absorb the pause rows.

**WHY:** The grounded part of the current evidence is compositional. If onset stop closure is about `108 ms`, short vowel duration about `75-95 ms`, and coda stop closure about `103 ms`, then the closed syllable falls around `286-306 ms` before any higher-order compensation is added (Yungdo Yun 2022; Sugai 2017; Kozasa 2002). Earlier discussion of a value near `310 ms` was a model-facing extrapolation, not a directly grounded `CVC` input. The more recent ceiling discussion clarified that `310 ms` belongs only to the broader segmental domain, where it functions as a natural upper limit for vowel and consonant durations. It should therefore be stored separately from the grounded `CVC` row.

**THUS:** PROPOSED MODEL: Keep `CVC` in the YAML only as the grounded empirical closed-syllable band. If `310 ms` is stored, it should appear only as `segmental_ceiling`, clearly scoped to vowels and consonants, with no effect on the distinct `CVC` and pause entries.

---

## 229t-Pause-Yaml-Should-Keep-Empirical-Durations-And-Ratio-But-Not-Algorithmic-Pause-Controls

**Domain:** Metrics / Methodology / Parameterization / Pauses

**WHAT:** The user-facing YAML should keep empirical pause durations and the overall silence ratio, but it should not expose pause classification rules, pause floor, or long-pause weighting as though they were equivalent empirical inputs.

**WHY:** The present source base grounds short pauses around `600-680 ms`, long pauses around `1200-1780 ms`, and total silence share around `30-40%` of utterance time (Goldman-Eisler 1968; Lin 2021; Anjarningsih 2024; Bae 2020; Tavakoli 2015). By contrast, a pause floor around `250 ms` is a functional threshold used in broader modeling discussion, punctuation classification belongs to the internal parser, and long-pause weighting is an allocation device inside the algorithm rather than a directly grounded empirical constant. These belong to different methodological levels and should not be conflated.

**THUS:** PROPOSED MODEL: In the YAML, retain pause durations and pause ratio as exposed empirical settings. Keep pause floor, punctuation classes, and weighting logic out of the user-visible empirical data file.

---

## 229u-Threshold-Yaml-Should-Store-Anchors-Not-Redundant-Boundary-Duplicates

**Domain:** Metrics / Methodology / Parameterization / Thresholds

**WHAT:** The user-facing YAML should stop exposing the duration system through one broad threshold layer. The revised configuration should instead expose category anchors and class-specific `perception_limits`: vowel anchors plus floors and contextual maximum, consonant anchors plus geminate thresholds, and one broad segmental ceiling that remains separate from pauses and `CVC`.

**WHY:** The deeper source review changed the question. The issue is no longer how to preserve one more threshold band in the YAML. The issue is how to represent the exact anchor values and lower or upper bounds that the working model actually needs. For vowels, the current anchored values are `short = 85 ms`, `long = 160 ms`, and `very_long = 220 ms`. Once those anchors are accepted, the most coherent category floors are `40 ms` for realized short nuclei, `122.5 ms` for the onset of long-vowel treatment, and `190.0 ms` for the onset of very-long treatment, with ordinary contextual extension capped at about `240 ms`. These are not universal psychophysical boundaries. They are model-facing category limits derived from the retained anchors and from the broader review of contextual overlength.

For consonants, the same review showed that one global singleton-versus-geminate split is too coarse. The stop literature still supports a broad singleton versus geminate contrast below about `100 ms` and above about `180 ms`, but the active model now treats ordinary onset and coda anchors as the hard singleton-side pillars of one speaker model. The newer fricative and gemination notes also show that the useful exposed limits are class-specific, but they matter chiefly on the geminate side. Closure geminate perception should begin around `180 ms` rather than at the lowest produced token in the `187-202 ms` band. Fricative geminate floor may stay in the weaker `152-166 ms` region. Sonorant geminate floor may likewise stay in the lower `152 ms` region. This does not turn those thresholds into universal laws. It means only that class-specific geminate limits are methodologically cleaner than one global split, while separate exposed singleton-minimum parameters add little once onset and coda anchors are already treated as hard pillars.

The same review also affects the non-threshold parts of the file. The transition domain now has two exposed values inside the consonant block because the model distinguishes strict hiatus from stronger vowel passage. The old `realization_tolerance` layer proved less clear than the newer anchor-and-limit structure, because the active computational question is not how much arbitrary deviation to allow, but where the segment ceases to count as the same phonological category. Floors and maxima answer that question more directly than one undifferentiated tolerance budget.

The pause rows require a final clarification of scope. The current long-pause interval `1200-1780 ms` remains a broad comparative range anchored in Lin's lower synthesis value and Anjarningsih's clause-boundary average (Lin et al. 2021; Anjarningsih 2024). The short-pause row, however, should likewise remain grounded in comparative pause evidence rather than being presented as though it had been measured from `cvc_reference` itself. A safer formulation is that the active band remains `600-680 ms`, while the runtime chooses a preferred reset target `610 ms` because `cvc_reference = 305 ms` lies inside the empirical overlap zone. Neither pause row should be absorbed into the segmental ceiling logic. By the same token, the broader `310 ms` ceiling should be read only as `segmental_ceiling`, that is, as a natural upper limit for vowels and consonants, not as a synonym for heavy `CVC` or for pause duration.

**THUS:** PROPOSED MODEL: Remove the old front-facing threshold logic from the YAML. Expose instead consonant and vowel anchors together with only the `perception_limits` that remain operationally useful, plus `segmental_ceiling = 310 ms` for the segmental domain alone. Keep stating openly which values are direct empirical anchors, which are active geminate thresholds, and which are broader contextual ceilings.

---

## 229v-Parameter-Refinement-Was-A-Research-Task-Not-A-One-Step-Guess

**Domain:** Metrics / Methodology / Research Process / Article Preparation

**WHAT:** The refinement of the timing parameters should be documented in the research notes and prep notes as a substantive unit of scholarly work. The present values were not chosen by impressionistic preference and should not be presented as though they emerged fully formed in one pass.

**WHY:** The parameter discussion required repeated comparison of unlike materials: natural production, laboratory hyper-articulation, perceptual categorization, syllable-compositional reasoning, and class-specific consonant evidence. Several earlier simplifications proved usable as placeholders but methodologically unsatisfactory once the evidence base thickened. This is especially clear in three places. First, the old `hiatus = 70 ms` worked as a practical proxy, but it collapsed true hiatus and stronger vowel transition into one number. Second, the old `two_morae_split = 222-286 ms` was serviceable as a broad moraic envelope, but it did not answer the narrower question of where the model should place the switch from `V` to `VV`. Third, the old `gemination_split = 142-163 ms` obscured manner differences that became increasingly visible as glide and fricative evidence was reviewed. The work therefore consisted not only in gathering numbers, but also in deciding which numbers belonged to production anchors, which belonged to perceptual discussion, and which could legitimately become exposed defaults.

The article will benefit from making this labor visible. Reviewers are more likely to trust the final parameter skeleton if they can see that it emerged from iterative reduction, rejection of overbroad thresholds, abandonment of misleading tolerance language, and explicit separation of evidence types. The notes should therefore preserve the trail of adjustment rather than retroactively flattening it into a single neat table.

**THUS:** PROPOSED MODEL: Treat parameter refinement as an evidential workflow in its own right. The notes should state that the current YAML skeleton is the result of repeated source analysis, failed or provisional threshold designs, and explicit model-cleaning decisions, not of unexplained intuition.

---

## 229w-Phonetizer-Must-Describe-Transition-Markers-As-Human-Realized-Phonemes

**Domain:** Phonetizer / Realization / Methodology / Transition Markers

**WHAT:** In the phonetizer layer, `hiatus` and `vowel_transition` should be described as actual phonetic realizations that a human speaker could produce, not merely as abstract timing gaps or interval labels. The model should therefore present `hiatus` as a light glottal stop and `vowel_transition` as a light glide, with stressed cases handed off to the fuller geminate rows.

**WHY:** The current empirical picture no longer supports treating these entries as one generic transition domain. The hiatus evidence points to a real but very brief glottal event, around `18 ms`, which is better described as a weak glottal stop or onset than as a silent separator. The transition evidence likewise points to a very brief glide-like articulatory movement, around `11 ms`, which should be phonetically interpretable as a weak [j] or [w] depending on the local vowel context. Campos-Astorkiza's discussion of identifiability and Yang Liu's account of intrinsic glide duration both suggest that the relevant issue is not whether some abstract interval exists, but how audible and segment-like the movement becomes in a given environment. Woolridge's hiatus-resolution material strengthens the same point, since weak glides arise precisely as humanly produced repairs of adjacent vowels.

This matters for exposition. A timing file may store compact values, but a phonetizer must tell the user what is actually being pronounced. If it speaks only of transitions, it risks collapsing articulatory substance into duration bookkeeping. At the same time, the description must remain cautious. In high-front contexts, a weak [j] may verge on heavy coarticulation or perceived lengthening; in rounded or back contexts, a weak [w] may be more detectable. The phonetizer should still name the output as a glide realization, because the model now assumes a pronounceable human event rather than a purely empty boundary.

The same logic applies to stress. A stressed hiatus should not be described as a slightly stretched weak onset. It is better analyzed as a fully featured geminated glottal stop under closure control. A stressed vowel transition likewise should not be described as an enlarged weak glide, but as a geminated glide under sonorant control. That interpretive split is exactly why the YAML now stores the two values under `closure.special_realization` and `sonorant.special_realization` rather than as free-standing transition parameters.

**THUS:** PROPOSED MODEL: The phonetizer should state explicitly that `closure.special_realization.hiatus` is realized as a light glottal stop in weak position and as a geminated glottal stop under stress, while `sonorant.special_realization.vowel_transition` is realized as a light glide, typically [j] or [w] according to vowel context, and as a geminated glide under stress. This keeps the human-facing phonetic description aligned with the current timing architecture.

---

## 229x-Phonetizer-Should-Use-Stable-Anchors-Bounded-Running-Drift-And-Strict-Short-Pause-Reset

**Domain:** Phonetizer / Timing Model / Pause Logic / Configuration

**WHAT:** The phonetizer timing model should now be read as a stability-first system. Ordinary segment anchors remain the default realizations for a given speaker, small timing mismatch is carried forward in a bounded running drift, short pauses are used as strict reset points by default, and the older `cvc_syllable.min/max` control should be replaced in the runtime configuration by one scalar `cvc_reference`.

**WHY:** The earlier attempt to force each syllable to match a local mora target by reshaping segment durations created a phonetic problem. It implied that one speaker would keep changing ordinary singleton and ordinary vowel durations from syllable to syllable simply to satisfy an abstract local equality. That is methodologically weak. The newer interpretation is more realistic. Stable segment anchors carry the ordinary speech burden; bounded running drift allows short-range recovery of isochrony; wider range intervention is reserved for stronger boundaries; and pauses provide the main discharge space.

This also clarifies the role of the heavy-syllable parameter. The grounded stop-based `CVC` evidence still matters, but it is better represented operationally by one explicit control value chosen inside the empirical overlap rather than by a live `min/max` band or by a round surrogate. The compositional interval `286-306 ms` from Sugai, Kozasa, and Yungdo Yun therefore remains the primary grounding, while the comparative short-pause region `600-680 ms` gives a half-range `300-340 ms`. The overlap `300-306 ms` permits a conservative choice such as `cvc_reference = 305 ms`. That control value then defines a preferred reset point `2 * cvc_reference = 610 ms` inside the runtime, while the short-pause band itself remains the empirical `600-680 ms` range. Because both pause timing and syllable timing vary with articulation rate and speaking speed, the paper should treat these values as grounded intervals and conservative control choices, not as rigid physical constants. The drift limit should still be small enough to remain below the tightest ordinary segment corridor and close to the lower empirical error scale. The sonorant onset-to-coda corridor `89 -> 70 ms` leaves only `19 ms` of ordinary adjustment room, while the verification and segmentation notes repeatedly place smaller duration discrepancy scales around `12-16 ms`. For that reason, `drift_tolerance = 12 ms` may still remain the better current default than `20 ms`, but it does not define the pause band itself.

The resulting hierarchy is clearer than the older one. Segment anchors remain the stable emitted defaults. Floors and ceilings protect phonological categories. `cvc_reference` remains a global timing reference rather than an exact local target for every syllable, even though its value is now chosen conservatively from the empirical overlap between the grounded `CVC` interval and the halved short-pause region. Short pauses serve as rhythmic reset points, but their band should still be described as the empirical `600-680 ms` range, not as a directly measured multiple of heavy timing. Long pauses remain broader comparative intervals and may discharge drift fully without difficulty; where aligned realization is wanted, the best default is the admissible multiple nearest the long-pause band center, with ties resolved downward. This change also explains why the phonetizer should expose `short_pause_policy: strict` and `drift_tolerance` in the process block rather than bury those behaviors in runtime code alone.

**THUS:** PROPOSED MODEL: Replace runtime `cvc_syllable.min/max` with `cvc_reference = 305 ms`; add `phonetize.process.short_pause_policy = strict` and `phonetize.process.drift_tolerance = 12 ms`; interpret short pause as a strict reset operation inside the empirically grounded band `600-680 ms`, with preferred runtime target `610 ms`; keep long pause at `1200-1780 ms`, with aligned default realization chosen by the admissible multiple nearest band center and ties resolved downward; and describe the phonetizer as a stability-first system with bounded running drift rather than as a syllable-by-syllable exact mora matcher.

---
## 230-Parameter-Justification-Overview

**Domain:** Timing Model / Parameter Grounding

**WHAT:** The timing parameters in `local-only/default.yaml` are not arbitrary. Each numeric value is grounded in published phonetic, psycholinguistic, or perceptual research. This note provides an overview of the justification structure; subsequent notes (231–249) detail each parameter individually.

**WHY:** The model's credibility depends on explicit, auditable parameter choices. Without source grounding, the timing values would be indistinguishable from free parameters. The justifications assembled in `local-only/latest-paper-findings/parameters-justifications.md` and `local-only/latest-paper-findings/basic_accentuation_justification.md` provide the empirical anchor for each value.

**THUS:** The parameter set is defensible as a constrained model, not a free fit. Each value sits inside an empirically attested range from comparative phonetic research. The model does not claim to recover Akkadian speech, but it does claim that its timing assumptions are compatible with what is known about human speech production and perception.

---

## 231-Parameter-Justification-Segmental-Ceiling

**Domain:** Timing Model / Global Constraints

**WHAT:** `segmental_ceiling: 310` ms. This is the upper ordinary duration for any single vowel or consonant segment. It serves as a validation ceiling for class-local consonant gemination maxima and the vowel elongation max.

**WHY:** Japanese perceptual studies (Sugai 2017) show that reaction times for stimuli longer than ~310 ms cease to correlate with duration, suggesting the brain no longer processes the sound as a standard linguistic unit. This provides a principled upper bound: segments exceeding 310 ms enter a different perceptual regime and should not be treated as ordinary phonetic material.

**THUS:** The ceiling is grounded in perceptual processing limits, not arbitrary selection. It prevents the model from generating segments that would be perceived as non-linguistic.

---

## 232-Parameter-Justification-Segmental-Floor

**Domain:** Timing Model / Global Constraints

**WHAT:** `segmental_floor: 20` ms. This is the global validation floor for vowel minima, consonant anchors and minima, and the hiatus and vowel-transition special realizations. It is validation-only, not a runtime timing control.

**WHY:** In artificial speech compression research (Gao and Birkholz 2014), a modeling floor of ~20 ms is used to maintain phone intelligibility. Below this threshold, segments become too short for reliable perception and the phone identity degrades.

**THUS:** The floor ensures that no segment falls below the minimum duration required for perceptual identification. It is a safety boundary, not an active timing control.

---

## 233-Parameter-Justification-CVC-Reference

**Domain:** Timing Model / Central Reference

**WHAT:** `cvc_reference: 300` ms. This is the central heavy-syllable timing reference used by accentuation and pause alignment. It sits inside the empirically grounded CVC interval of 286–306 ms (Cutanda et al. 2019).

**WHY:** Cutanda et al. (2019) established that the CVC syllable duration of ~300 ms is a baseline interval for rhythmic entrainment and isochrony deviation tests. The value 300 ms is chosen conservatively from the empirical overlap between the grounded CVC interval and the halved short-pause region (600–680 ms → half-range 300–340 ms). The overlap 300–306 ms permits a conservative choice.

**THUS:** The CVC reference is not a free parameter. It is anchored in comparative phonetic evidence for heavy syllable duration and serves as the computational heartbeat of the timing model: accentuation adds 0.5 × cvc_reference (150 ms) in bi mode, and pause alignment uses integer multiples of this value.

---

## 234-Parameter-Justification-Drift-Tolerance

**Domain:** Timing Model / Stability Control

**WHAT:** `drift_tolerance: 19` ms. This is the maximum local timing mismatch tolerated before the algorithm must intervene. It is subject to the global duration scale: effective value = round(drift_tolerance × scale) when scale ≠ 1.0.

**WHY:** The drift limit must be small enough to remain below the tightest ordinary segment corridor. The sonorant onset-to-coda corridor (89 → 70 ms) leaves only ~19 ms of ordinary adjustment room. Verification and segmentation notes place smaller duration discrepancy scales around 12–16 ms. The value 19 ms is therefore a conservative upper bound that keeps drift below the narrowest natural segment corridor.

**THUS:** Drift tolerance defines how much cumulative timing error the system can absorb before forced resynchronization. It is a stability parameter, not a phonetic claim. The value 19 ms ensures that drift never exceeds the smallest phonologically relevant durational contrast.

---

## 235-Parameter-Justification-Basic-Accentuation-Lengthening

**Domain:** Timing Model / Mono Mode

**WHAT:** `basic_accentuation_lengthening: 50` ms. This is the additional duration attributed to accentuated syllables in mono mora mode. Unlike bi mode where accentuation adds one mora (0.5 × cvc_reference = 150 ms), mono mode uses this smaller configurable elongation.

**WHY:** The 50 ms value is grounded in three independent lines of evidence (assembled in `local-only/latest-paper-findings/basic_accentuation_justification.md`):

1. **Rhythmic anisochrony (Cutanda et al. 2019):** 50 ms is a standard increment used to test perception of timing deviations in entrainment experiments. Rhythms were produced where 50 ms was randomly added or subtracted to a 300 ms baseline interval.

2. **Whispered speech processing (Meynadier et al. 2019):** In whispered speech, listeners require an additional ~50 ms processing window to resolve voicing ambiguity when standard acoustic cues (vocal fold vibration) are absent.

3. **Keller-Zellner synthesis algorithm (Zellner 1994):** The algorithm assumes an empirical minimum of 50 ms for durational adjustments in normal and slow speech, and applies a 50 ms reduction rule for single-word constituents.

Additionally, Ryan (2014) uses a 50 ms increment as a theoretical benchmark for Weber's Law in syllable weight perception: adding one coda consonant of 50 ms to a 100 ms syllable increases duration by 50%, illustrating why initial duration additions are more perceptually significant than subsequent ones.

**THUS:** The 50 ms value is not arbitrary. It is supported by converging evidence from three independent research domains: experimental rhythm research, perceptual phonetics, and speech synthesis. This triple grounding makes it a defensible default for the mono mode elongation parameter.

---

## 236-Parameter-Justification-Closure-Onset

**Domain:** Timing Model / Consonants / Closure

**WHAT:** `closure.onset: 89` ms. Default onset closure (stop) duration.

**WHY:** This matches the pooled mean for word-initial voiceless stops in Standard Spanish (Gibson et al. 2013). Stops provide the firmest timing class because their acoustic boundaries are the most clearly defined: closure duration is directly measurable from the silence interval before the release burst.

**THUS:** The onset closure value is a direct comparative anchor. It is not a free parameter but a measurement drawn from cross-linguistic stop production data.

---

## 237-Parameter-Justification-Closure-Coda

**Domain:** Timing Model / Consonants / Closure

**WHAT:** `closure.coda: 87` ms. Default post-vocalic closure (stop) duration.

**WHY:** Word-final stop measurements range from ~46 ms (Morley and Smith 2022) to ~81 ms (Gibson et al. 2013). The value 87 ms is at the upper end of this range, reflecting the fact that coda stops in careful reading (the relevant register for literary recitation) tend toward longer durations.

**THUS:** The coda value is defensible as a conservative upper estimate for careful literary reading. It is not the lowest measured token but a plausible value for the register being modeled.

---

## 238-Parameter-Justification-Closure-Geminate

**Domain:** Timing Model / Consonants / Closure

**WHAT:** `closure.geminate: 175` ms. Default geminate closure target.

**WHY:** Derived from adding a standard moraic increase of ~120 ms (Sugai 2017) to a singleton baseline of ~55 ms. The resulting 175 ms falls within the empirically attested geminate stop range and is consistent with the perceptual threshold for geminate identification.

**THUS:** The geminate value is a summary point for the attested stop-geminate band. It is not the only possible value but a defensible central estimate.

---

## 239-Parameter-Justification-Closure-Perception-Limits

**Domain:** Timing Model / Consonants / Closure

**WHAT:** `closure.perception_limits.geminate_min: 145` ms; `gemination_max: 260` ms.

**WHY:** The 145 ms minimum reflects the high-end mean of a single mora (Broselow et al. 1997). Below this threshold, a stop is not perceived as phonologically long. The 260 ms maximum corresponds to the 50% identification threshold for Japanese mora boundaries (Sugai 2017). Above this ceiling, the segment enters a different perceptual regime.

**THUS:** These perceptual limits define the legal runtime window for geminate stops. They are grounded in perceptual experiments, not arbitrary boundaries.

---

## 240-Parameter-Justification-Fricative-Onset

**Domain:** Timing Model / Consonants / Fricative

**WHAT:** `fricative.onset: 115` ms. Default onset fricative duration.

**WHY:** Based on whispered speech research (Meynadier et al. 2019) where initial fricative boundaries are measured between 114 ms and 119 ms. The value 115 ms is a conservative choice within this range.

**THUS:** The fricative onset value is grounded in direct phonetic measurement, though the evidence base is narrower than for stops. Fricatives are inherently noisier segments with less clearly defined acoustic boundaries.

---

## 241-Parameter-Justification-Fricative-Geminate

**Domain:** Timing Model / Consonants / Fricative

**WHAT:** `fricative.geminate: 210` ms. Default geminate fricative target.

**WHY:** While the threshold for geminate perception is ~166 ms (Sugai 2017), the target value accounts for the inherent manner lengthening of fricatives compared to stops. Fricatives require longer duration to be perceived as geminate because their continuous noise spectrum provides less salient boundary cues than stop closures.

**THUS:** The fricative geminate value is exploratory. It is based on the current onset + post-vocalic row and should be treated as a working hypothesis rather than a firmly established measurement.

---

## 242-Parameter-Justification-Sonorant-Onset

**Domain:** Timing Model / Consonants / Sonorant

**WHAT:** `sonorant.onset: 105` ms. Default onset sonorant duration.

**WHY:** Grounded in word-initial liquid (/l/) measurements of ~89 ms (Gibson et al. 2013). The value 105 ms accounts for the fact that sonorants (including nasals and glides) have inherently longer duration than stops due to their continuous voicing and less abrupt acoustic onset.

**THUS:** The sonorant onset value is set from the clearer singleton liquid onset anchor, with a modest upward adjustment for the broader sonorant class.

---

## 243-Parameter-Justification-Sonorant-Geminate

**Domain:** Timing Model / Consonants / Sonorant

**WHAT:** `sonorant.geminate: 190` ms. Default geminate sonorant target.

**WHY:** Grounded in the absolute duration of geminate palatal glides in Lopit (Billington 2015), which average ~167 ms but reach ~201 ms at one standard deviation. The value 190 ms is a midpoint estimate that accounts for the broader sonorant class while remaining within the attested geminate range.

**THUS:** The sonorant geminate value is set from direct glide geminate evidence, with the caveat that Lopit is a Nilotic language, not a Semitic one. The cross-linguistic comparison is defensible as a first approximation but should be refined with Semitic-specific data if available.

---

## 244-Parameter-Justification-Vowel-Short

**Domain:** Timing Model / Vowels

**WHAT:** `vowels.short: 110` ms. Default short-vowel duration.

**WHY:** Matches the median "short" response in whispered speech (Meynadier et al. 2019). Short vowels in production studies consistently fall in the 100–120 ms range across languages, making 110 ms a defensible central estimate.

**THUS:** The short vowel value is a production anchor from the retained short-vowel baseline. It is not the lowest measured token but a plausible central value for careful reading.

---

## 245-Parameter-Justification-Vowel-Long

**Domain:** Timing Model / Vowels

**WHAT:** `vowels.long: 160` ms. Default long-vowel duration.

**WHY:** Matches the statistical intercept for vowel duration models of ~160.1 ms (Morley and Smith 2022). Long vowels are consistently measured at approximately 1.5× the duration of short vowels across languages, and 160 ms satisfies this ratio relative to the 110 ms short vowel anchor.

**THUS:** The long vowel value is a production anchor from the retained long-vowel baseline. It maintains the phonologically required short/long contrast while staying within empirically attested ranges.

---

## 246-Parameter-Justification-Vowel-Very-Long

**Domain:** Timing Model / Vowels

**WHAT:** `vowels.very_long: 260` ms. Default very-long vowel duration.

**WHY:** Matches the Japanese threshold range for "long" identification at 250–270 ms (Sugai 2017). Very long vowels in Akkadian arise from contraction (circumflex vowels) or from contextual extension. The value 260 ms is a midpoint within this range.

**THUS:** The very long vowel value is a contextual extension anchor, not an ordinary lexical default. It represents the upper end of the phonologically relevant vowel duration range.

---

## 247-Parameter-Justification-Vowel-Elongation-Max

**Domain:** Timing Model / Vowels

**WHAT:** `vowels.perception_limits.elongation_max: 280` ms.

**WHY:** Based on the average duration of syllable nuclei before voiced stops, recorded at ~280 ms (Naeser 1970). This is the upper contextual bound for vowel extension. Ordinary non-accentual long-vowel recovery stops at very_long_min − 1, but post-accent cleanup on accent-bearing CVV: and CVV:C syllables may use this wider legality ceiling.

**THUS:** The elongation max is grounded in pre-voiced stop lengthening, a well-attested cross-linguistic phenomenon. It provides a principled upper bound for vowel duration in the model.

---

## 248-Parameter-Justification-Pause-Resync

**Domain:** Timing Model / Pauses

**WHAT:** `pauses.resync.min: 100` ms; `resync.max: 200` ms. Default resync-pause band for non-punctuation recovery gaps.

**WHY:** This range is defined by the acoustic detection floor of ~100 ms (Wan et al. 2024) and the boundary for "intended" pauses of ~200 ms (Sturm and Volin 2023). Below 100 ms, a silence is not reliably perceived as a pause. Above 200 ms, the silence is perceived as a deliberate break rather than a timing adjustment.

**THUS:** The resync band occupies the perceptual gap between unintentional silence and deliberate pausing. It allows the algorithm to insert micro-pauses for drift correction without creating perceptually salient breaks.

---

## 249-Parameter-Justification-Pause-Short

**Domain:** Timing Model / Pauses

**WHAT:** `pauses.short.min: 520` ms; `short.max: 680` ms. Default short-pause band for comma-level punctuation.

**WHY:** Grounded in the mean silent pause duration in interviews of ~520 ms (Zellner 1994) and paced rhythms at 1.5 Hz (~671 ms) (Rathcke et al. 2023). The range 520–680 ms captures the typical duration of a short, phrase-internal pause in careful reading.

**THUS:** The short-pause band is empirically grounded in reading studies. Rhythmic alignment remains possible when at least one integer multiple N × cvc_reference falls inside this band without redefining the empirical range.

---

## 250-Parameter-Justification-Pause-Long

**Domain:** Timing Model / Pauses

**WHAT:** `pauses.long.min: 1100` ms; `long.max: 1780` ms. Default long-pause band for clause-final punctuation.

**WHY:** The lower bound matches the mean for major unit pauses in poetry of ~1144 ms (Sturm and Volin 2023). The upper tail accounts for extreme planning pauses reaching ~1320 ms or higher (Zellner 1994). The range 1100–1780 ms captures the full spectrum of clause-boundary pauses in careful reading.

**THUS:** The long-pause band is a broad comparative interval. If rhythmic alignment is used, the best default is the admissible multiple of cvc_reference nearest the band center, with ties resolved downward.

---

## 251-Draft8-Content-Not-In-Article-Mono-Mode-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) contains a detailed description of mono mode behavior that was not carried into the final article. Specifically, the draft explains that mono mode uses a configurable 50 ms accentuation increment (basic_accentuation_lengthening) rather than the bi-mode increment of 0.5 × cvc_reference (150 ms). The draft also notes that mono mode does not use forward merge as a repair strategy.

**WHY:** The article's Section 7.4 ("Comparison with Mono Mode") retains the essential comparison: mono mode produces a higher accentuation rate (32.38%) but a smaller increase in variability (VarcoC rises to only 49.85 vs. 54.61 for bi mode). However, the article does not explain why 50 ms was chosen as the mono mode increment, nor does it detail the three independent lines of evidence (Cutanda et al. 2019; Meynadier et al. 2019; Zellner 1994) that justify this value.

**THUS:** The parameter justification for basic_accentuation_lengthening (see note 235) fills this gap. The article's comparative argument is strengthened by noting that the 50 ms value is not arbitrary but grounded in converging experimental evidence.

---

## 252-Draft8-Content-Not-In-Article-CVC-Reference-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) states that the CVC reference value of 300 ms falls within the empirically attested range of 286–306 ms (Cutanda et al. 2019). However, the draft does not explain the full reasoning chain: that the compositional interval 286–306 ms from Sugai, Kozasa, and Yungdo Yun provides the primary grounding, while the comparative short-pause region 600–680 ms gives a half-range of 300–340 ms, and the overlap 300–306 ms permits a conservative choice.

**WHY:** The article simplifies this to a single sentence for readability. The full reasoning is preserved in the research notes (note 233) and in the `local-only/default.yaml` comments.

**THUS:** The article's claim that the timing values are "grounded in published phonetic research" is accurate but compressed. The detailed justification chain is available in the research notes for readers who want to audit the parameter choices.

---

## 253-Draft8-Content-Not-In-Article-Drift-Tolerance-Rationale

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention drift_tolerance at all. This parameter controls how much cumulative timing mismatch the phonetizer tolerates before forced resynchronization. The draft's Section 6 describes the timing model at a high level (CVC reference, accentuation increments, consonant/vowel/pause durations) but omits the stability-control mechanism.

**WHY:** Drift tolerance is an implementation detail that belongs in the software documentation rather than the article. The article's audience (linguists and Assyriologists) needs to understand the timing assumptions, not the error-correction algorithm.

**THUS:** The omission is appropriate for the article's scope. The drift tolerance parameter is documented in the research notes (note 234) and in the `local-only/default.yaml` comments for implementers.

---

## 254-Draft8-Content-Not-In-Article-Accentuation-Distribution-Policy

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) states that accentuation duration is distributed according to an 80/20 policy: 80% on the accentuated segment and 20% on the adjacent segment. However, the draft does not explain that this policy is configurable (accentuation_distribution_policy) with allowed values including 100_0, 95_05, 90_10, 85_15, 80_20, 75_25, and 70_30.

**WHY:** The article presents the 80/20 split as the default behavior, which is accurate. The full set of configurable options is an implementation detail that would distract from the article's argument.

**THUS:** The article's treatment is appropriate. The configurable policy is documented in `local-only/default.yaml` for users who want to experiment with different distribution ratios.

---

## 255-Draft8-Content-Not-In-Article-Geminate-Policy

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions geminate durations but does not explain the geminate_policy parameter (cumulative vs. corrective). In cumulative mode, the phonetizer keeps coda duration + onset duration instead of correcting to the configured geminate target. In corrective mode, the sequence is corrected to the configured geminate target.

**WHY:** The geminate policy is a software implementation choice that affects how adjacent same-consonant sequences are handled. The article's audience does not need to know this level of implementation detail.

**THUS:** The omission is appropriate. The geminate policy is documented in `local-only/default.yaml` for implementers.

---

## 256-Draft8-Content-Not-In-Article-Scale-Parameter

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the scale parameter (default: 1.0). This global multiplier applies to all numeric duration leaves when different from 1.0. Runtime treats 1.0 as a true no-op path.

**WHY:** The scale parameter is a convenience feature for sensitivity analysis and speech rate adjustment. It is not part of the core timing model and would add unnecessary complexity to the article's exposition.

**THUS:** The omission is appropriate. The scale parameter is documented in `local-only/default.yaml` for advanced users who want to test the model at different speech rates.

---

## 257-Draft8-Content-Not-In-Article-Coda-Final-Parameters

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the coda_final parameters for consonants (closure.coda_final, fricative.coda_final, sonorant.coda_final). These are pre-pausal final durations used only when the next realized unit is a punctuation-owned short or long pause.

**WHY:** The article simplifies the timing model by presenting only the basic onset/coda/geminate values. The coda_final distinction is a refinement for pause-adjacent positions that would add complexity without changing the article's core argument.

**THUS:** The omission is appropriate. The coda_final parameters are documented in `local-only/default.yaml` for users who want precise pause-adjacent timing.

---

## 258-Draft8-Content-Not-In-Article-Vowel-Final-Parameters

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the short_final and long_final vowel parameters. These are pre-pausal final vowel durations used only when the next realized unit is a punctuation-owned short or long pause.

**WHY:** Same rationale as coda_final: the article simplifies by presenting only the basic vowel durations. The final variants are a refinement for pause-adjacent positions.

**THUS:** The omission is appropriate. The vowel final parameters are documented in `local-only/default.yaml` for users who need precise pause-adjacent timing.

---

## 259-Draft8-Content-Not-In-Article-Perception-Limits-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions perceptual limits for geminate stops (145 ms minimum, 260 ms maximum) but does not discuss the full set of perception_limits for all consonant classes and vowels. The `local-only/default.yaml` defines geminate_min and gemination_max for each consonant class (closure, fricative, sonorant), plus short_min, long_min, very_long_min, and elongation_max for vowels.

**WHY:** The article uses the stop geminate limits as an illustrative example, which is sufficient for its argument. The full set of perceptual limits is an implementation detail that would overwhelm the article's exposition.

**THUS:** The article's selective treatment is appropriate. The complete perception limits are documented in `local-only/default.yaml` and in the parameter justification notes (notes 236–250).

---

## 260-Draft8-Content-Not-In-Article-Hiatus-And-Vowel-Transition

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the hiatus parameter (closure.special_realization.hiatus: 35 ms) or the vowel_transition parameter (sonorant.special_realization.vowel_transition: 25 ms). These are special realizations for vowel-to-vowel transitions: hiatus for unstressed light glottal-stop realization between adjacent vowels, and vowel_transition for diphthong-internal or glide-like VV transition.

**WHY:** These are fine-grained phonetic details that matter for the phonetizer implementation but are not central to the article's argument about rhythm typology.

**THUS:** The omission is appropriate. The special realization parameters are documented in `local-only/default.yaml` for implementers.

---

## 261-Draft8-Content-Not-In-Article-Intonation-Presets

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the intonation presets (f0, stress, question, statement, exclamation, continuation) defined in `local-only/default.yaml`. These control the baseline speaker pitch and intonation contours used for emitted .pho rows.

**WHY:** The article's scope is rhythm typology, not intonation. Intonation presets are relevant for TTS integration (Section 11) but are not part of the rhythm metrics argument.

**THUS:** The omission is appropriate. Intonation presets are documented in `local-only/default.yaml` for TTS implementers.

---

## 262-Draft8-Content-Not-In-Article-Experimental-Features

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the allow_experimental flag or the experimental features it guards (limit_emphatic_coloring, enable_resync_pause). These are software development features that control access to unfinished or unvalidated functionality.

**WHY:** Experimental features are a software engineering concern, not a research finding. The article presents the stable, validated model.

**THUS:** The omission is appropriate. Experimental features are documented in `local-only/default.yaml` for developers.

---

## 263-Draft8-Content-Not-In-Article-Metrics-Output-Options

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the metrics output options (table, json) or the print output options (acute, bold, ipa, circ_hiatus, xar, print_merger) defined in `local-only/default.yaml`. These control what output files the toolkit generates.

**WHY:** Output format options are a software usability concern, not part of the research argument. The article presents the metrics results, not the software interface.

**THUS:** The omission is appropriate. Output options are documented in `local-only/default.yaml` for users of the toolkit.

---

## 264-Draft8-Content-Not-In-Article-ATF-Parse-Options

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the ATF parsing options (remove_hyphens, preserve_case, preserve_h) or the syllabifier options (extra_vowels, extra_consonants, merge_hyphen, merge_lines, etc.) defined in `local-only/default.yaml`.

**WHY:** These are preprocessing options that affect how input texts are parsed. They are relevant for users of the toolkit but not for the article's argument about prosody.

**THUS:** The omission is appropriate. Preprocessing options are documented in `local-only/default.yaml` for toolkit users.

---

## 265-Draft8-Content-Not-In-Article-IPA-Proto-Semitic-Policy

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the ipa_proto_semitic parameter (print.process.ipa_proto_semitic: "preserve"). This controls whether IPA output preserves the Old Akkadian distinction or uses the Old Babylonian merger.

**WHY:** This is a philological detail relevant for IPA rendering but not for the rhythm metrics argument.

**THUS:** The omission is appropriate. The IPA policy is documented in `local-only/default.yaml` for users who need IPA output.

---

## 266-Draft8-Content-Not-In-Article-Common-Run-Options

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the common run options (prefix, outdir, quiet, no_console, log, log_append) defined in `local-only/default.yaml`. These control file output and logging behavior.

**WHY:** These are software configuration options with no bearing on the research argument.

**THUS:** The omission is appropriate. Common run options are documented in `local-only/default.yaml` for toolkit users.

---

## 267-Draft8-Content-Not-In-Article-Relax-Last-Option

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions explicit plus linking (Section 4.5) but does not explain the relax_last option (prosody.process.relax_last: false). In strict mode (default), only the last linked word is eligible for stress realization. In relaxed mode, stress realization may propagate right-to-left across the linked chain.

**WHY:** The article presents the default behavior (strict mode) which is sufficient for its argument. The relaxed mode is an experimental option for users who want to test alternative linking behaviors.

**THUS:** The omission is appropriate. The relax_last option is documented in `local-only/default.yaml` and in the research notes (notes 072–073).

---

## 268-Draft8-Content-Not-In-Article-Function-Word-Inventory-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions function words (Section 4.5) but does not provide the full inventory. The `local-only/default.yaml` does not define a function word inventory (it is hardcoded in the software). The research notes (note 075) list the inventory: prepositions (ana, ina, ištu, itti, eli), negative particles (ul, ula, lā), determinative-relative pronoun (ša), coordinating conjunctions (u, ū, lū), and independent personal pronouns (anāku, atta, šū, etc.).

**WHY:** The article's description ("function words are never accented as independent units") is sufficient for its argument. The full inventory is a software implementation detail.

**THUS:** The omission is appropriate. The function word inventory is documented in the research notes for implementers.

---

## 269-Draft8-Content-Not-In-Article-CVVC-Treatment-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions CVVC syllables (Section 2.1) but does not explain the two possible algorithmic pathways: lengthen (conservative: CVVC → CVV~C, 3µ → 4µ) or shorten (diachronic: CVVC → CVC, 3µ → 2µ). The research notes (note 018) document both pathways.

**WHY:** The article adopts the lengthening approach without discussing alternatives, which is appropriate for its scope. The alternative pathway is documented in the research notes for sensitivity testing.

**THUS:** The omission is appropriate. The CVVC treatment detail is preserved in the research notes.

---

## 270-Draft8-Content-Not-In-Article-Diphthong-Processing-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention diphthong processing at all. The research notes (notes 076–082) document the diphthong processing algorithm: insert a temporary hiatus consonant (glottal stop) during processing, then restore the diphthong after stress realization.

**WHY:** Diphthong processing is a preprocessing step that does not affect the article's argument about rhythm typology. The article's corpus may not contain significant diphthong material.

**THUS:** The omission is appropriate. Diphthong processing is documented in the research notes for implementers.

---

## 271-Draft8-Content-Not-In-Article-Merge-Logic-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) describes merge logic at a high level (Section 4.5) but does not detail the merge termination guarantee, the left-to-right processing strategy, or the backward merge mechanism for trailing function words. The research notes (notes 066–070) document these details.

**WHY:** The article's high-level description is sufficient for its argument. The algorithmic details are preserved in the research notes for implementers.

**THUS:** The omission is appropriate. The merge logic details are documented in the research notes.

---

## 272-Draft8-Content-Not-In-Article-Accent-Style-AOB

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions LOB and SOB accent styles but does not mention AOB (Academic Old Babylonian), which was initially considered as a comparison model. The research notes (note 064) document AOB and explain why it was set aside.

**WHY:** The article correctly focuses on the two styles that are actually used in the research. AOB was a discarded experimental option.

**THUS:** The omission is appropriate. The AOB discussion is preserved in the research notes for historical documentation.

---

## 273-Draft8-Content-Not-In-Article-84-Percent-Red-Herring

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not mention the early calculation error that mistakenly gave 84% stressed words. The research notes (note 028) document this error and its correction.

**WHY:** The article presents the correct figure (29.2% for Erra) without discussing the earlier mistake. This is appropriate for a polished research article.

**THUS:** The omission is appropriate. The error and correction are documented in the research notes for transparency.

---

## 274-Draft8-Content-Not-In-Article-Plene-Spelling-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) does not discuss plene spelling evidence in detail. The research notes (notes 029–030) document that plene spelling occasionally aligns with predicted stress positions but is used inconsistently, suggesting it may mark variable phonetic prominence rather than lexical length.

**WHY:** The article's argument does not depend on orthographic evidence. The plene spelling discussion is a supporting observation, not a core claim.

**THUS:** The omission is appropriate. The plene spelling analysis is preserved in the research notes.

---

## 501-Syllable-Class

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

## 275-Draft8-Content-Not-In-Article-Arabic-Rhythm-Comparative-Detail

**Domain:** Article / Draft 8 / Omitted Content

**WHAT:** The article draft (v8) mentions Arabic rhythm research (Section 8) but does not detail the internal variation across Arabic dialects. The research notes (note 038) document that Western dialects such as Moroccan Arabic sound more "staccato" or "jerky," largely because vowel deletion increases consonant clustering, whereas Eastern dialects such as Syrian Arabic have a more open rhythm, in some respects approaching French in vocalic patterning (Hamdi et al. 2004).

**WHY:** The article uses Arabic as comparative support for the stress-timed interpretation but simplifies the picture by not discussing dialectal variation. The full picture is more nuanced: Arabic dialects span a range from strongly stress-timed (Moroccan) to more mixed (Syrian), and this internal variation actually strengthens the argument that Semitic languages have a natural tendency toward stress-timing without being monolithic about it.

**THUS:** The article's treatment is appropriate for its scope. The dialectal detail is preserved in the research notes for readers who want a more nuanced comparative picture.

---


## 502-Word-Class

**Domain:** Algorithm / Implementation / Data Structures

**WHAT:** The Word class represents a complete lexical word composed of Syllable objects. It tracks the word's moraic structure and manages accentuation attempts.

**WHY:** Words are the primary domain for stress eligibility. The class provides:

* `syllables`: list of Syllable objects
* `morae`: total original mora count
* `accentuated_morae`: total after stress realization
* `needs_accentuation`: boolean (accentuated_morae % 2 == 1)
* `get_accentuation_caaccentuationndidates(style)`: returns list of possible accentuations in priority order
* `get_best_accentuation(style)`: returns highest priority accentuation
* `apply_accentuation(accentuation)`: applies operation to specified syllable
* `get_text()`: returns word with accentuations and syllable dots

**THUS:** The Word class encapsulates all word-level logic, keeping the main accentuation algorithm clean and focused on flow control rather than low-level operations.

---

## 503-MergedUnit-Class

**Domain:** Algorithm / Implementation / Data Structures

**WHAT:** The MergedUnit class represents a group of words that have been prosodically joined for stress realization purposes. It flattens the component words into a single list of syllables while tracking original word boundaries.

**WHY:** When words cannot be stress-realized independently, they merge with following words. The merged unit must be treated as a single prosodic domain while preserving information about which syllables belong to which original word (critical for legality checks like final gemination).

**THUS:** The MergedUnit class provides methods to check if a syllable is word-final, to find accentuation candidates across the entire unit, and to apply accentuations while respecting word-internal constraints.

---

## 504-AccentuationEngine-State-Machine

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

## 505-Legal-Operation-Vowel-Lengthening

**Domain:** Algorithm / Operations

**WHAT:** Vowel lengthening applies to syllables containing long vowels: CVV, VV, CVVC, VVC. Effect: 2µ → 3µ (or 3µ → 4µ for CVVC). Notation: V̄ → V̄~ (e.g., ā → ā~).

**WHY:** This operation is phonologically legal because vowel length is phonemic in Akkadian. Lengthening preserves the contrast (short remains short). The operation is already attested in the language through processes like compensatory lengthening.

**THUS:** Vowel lengthening is a primary tool for achieving bimoraic targets. It adds exactly one mora with minimal disruption to lexical identity.

---

## 506-Legal-Operation-Coda-Gemination

**Domain:** Algorithm / Operations

**WHAT:** Coda gemination applies to heavy syllables ending in a consonant: CVC, VC (non-final only). Effect: 2µ → 3µ. Notation: C → C~ (e.g., mir → mir~).

**WHY:** This operation is phonologically legal because gemination is phonemic and productive in Akkadian. It appears in n-assimilation (indin → iddin) and t-infix assimilation (iṣtabat → iṣṣabat). Word-final gemination is unattested, so it is prohibited.

**THUS:** Coda gemination is a second primary tool. It adds a mora through consonant length while respecting the constraint against word-final geminates.

---

## 506b-Accentuated-Cvc-Should-Be-Timed-As-A-Trimoraic-Syllable-Not-As-A-Full-Lexical-Geminate

**Domain:** Algorithm / Operations / Phonetic Interpretation

**WHAT:** When a `CVC` syllable is accentuated and represented algorithmically through coda gemination (`CVC:`), the phonetic target should not be a full lexical geminate consonant copied mechanically from the consonant-duration table. The relevant target is instead the total duration of an approximately trimoraic syllable, that is, the original heavy syllable plus one mora, with the added time distributed between the short vowel and the coda consonant.

**WHY:** This distinction matters because lexical gemination and accentual coda prolongation are not the same phenomenon. Lexical gemination is part of the segmental structure of the word and should continue to use the empirical geminate durations of the consonant classes. Accentual `CVC:` is different. Its function is to satisfy the prosodic requirement of adding one mora to the syllable while preserving lexical vowel length. If one were to force the coda alone to equal the full lexical geminate target in every accentuated `CVC`, the result would overstate the consonant and obscure the syllabic nature of the operation. A more realistic interpretation is that the syllable as a whole approaches a trimoraic duration, while the vowel may expand somewhat but remain within the short-vowel range, and the coda carries the remaining prosodic prolongation.

**THUS:** PROPOSED MODEL: The algorithm may continue to use `geminate_coda` as its operational label, but the realization model should interpret `CVC:` as a syllable-level timing target rather than as a mandatory full lexical geminate consonant. In practice, the added mora should be distributed across `V` and coda `C` in such a way that lexical short-vowel identity is preserved while the total syllable duration approaches a three-mora equivalent.

---

## 507-Last-Resort-Onset-Gemination

**Domain:** Algorithm / Operations

**WHAT:** When no legal accentuation candidate exists, onset gemination is used as a last resort. For consonant-initial syllables: C~V (e.g., ka → k~a). For vowel-initial syllables: ~V (e.g., a → ~a), representing a geminated glottal stop.

**WHY:** This operation is rare (<1% of corpus) and used only when all other options fail. It adds exactly one mora without lengthening the vowel, thus preserving lexical length contrasts. The geminated glottal stop is the most neutral consonant, affecting vowel quality minimally.

**THUS:** Onset gemination provides a safety net for the algorithm, ensuring that every unit can achieve an even mora count even in the most constrained environments.

---

## 508-Merge-Forward

**Domain:** Algorithm / Merging

**WHAT:** When a word cannot be stress-realized internally, it merges with following words until a accentuation candidate is found or the merged unit becomes even. The algorithm proceeds left-to-right, never looking back.

**WHY:** This mimics the online nature of speech production. Speakers do not plan entire utterances in advance; they make decisions incrementally. Forward merging is the default strategy.

**THUS:** The algorithm prioritizes forward merging, only looking back when forward is impossible (e.g., at punctuation boundaries). This yields psychologically plausible outputs.

---

## 509-Merge-Backward

**Domain:** Algorithm / Merging

**WHAT:** Backward merge is used when trailing function words occur before punctuation and need a content host. The algorithm may roll back prior stress realizations and rebuild a larger unit including the preceding content word plus trailing function words.

**WHY:** Function words cannot stand alone. At boundaries, forward merging is impossible. Backward merging ensures that even stranded function words are properly integrated into the prosodic structure.

**THUS:** Backward merging handles edge cases, ensuring the algorithm can process any input regardless of punctuation placement.

---

## 510-Explicit-Plus-Linking

**Domain:** Algorithm / Merging

**WHAT:** The input `+` is treated as an explicit instruction that the linked sequence forms one mandatory prosodic unit. In strict mode (default, `only_last=True`), only the last linked word is eligible for stress realization. In relaxed mode (`--prosody-relax-last`), stress realization may propagate right-to-left across the linked chain.

**WHY:** Some sequences (construct chains, certain compounds) must be treated as units. The `+` marker allows the user to specify this. The strict mode preserves the integrity of construct chains; the relaxed mode tests alternative groupings.

**THUS:** The algorithm respects explicit linking, overriding default behavior when instructed. The option exists for experimentation, with the conservative strict mode as the default.

---

## 511-Function-Word-Inventory

**Domain:** Algorithm / Merging

**WHAT:** Function words cannot be stress-realized independently. They must attach to adjacent content words. The inventory includes:

* Prepositions: ana, ina, ištu, itti, eli
* Negative particles: ul, ula, lā
* Determinative-relative pronoun: ša
* Coordinating conjunctions: u, ū, lū
* Independent personal pronouns: anāku, nīnu, atta, atti, attunu, attina, šū, šī, šunu, šina

**WHY:** These categories are standard in Assyriological descriptions (Huehnergard 2011, Buccellati 1996). Function words in stress-timed languages are cliticized, sharing a single stress unit with adjacent content words.

**THUS:** The algorithm treats function words specially, merging them forward when possible and backward when stranded. This enforces clitic-like prosodic dependence, reflecting natural speech behavior.

---

## 512-atfparser-CLI

**Domain:** Implementation / CLI / Preprocessing

**WHAT:** `atfparser.py` converts eBL ATF files into clean Akkadian text for the prosody pipeline. It extracts Akkadian from `%n` lines, extracts English translation from `#tr.en:` lines, and normalizes editorial markup.

**WHY:** Raw ATF files contain extensive markup that would interfere with syllabification and stress realization. The parser removes editorial markup while preserving the linguistic content and line structure.

* `--preserve-case`: keep original case (default lowercases text)
* `--preserve-h`: keep `h/H` unchanged (default maps to ḫ/Ḫ)
* `--append`: append to output files instead of overwriting
* `--strict`: enable strict warning mode

**THUS:** The parser produces clean `*_proc.txt` files ready for syllabification, with line breaks preserved to encode phrasing.

---

## 513-syllabifier-CLI

**Domain:** Implementation / CLI / Syllabification

**WHAT:** `syllabifier.py` converts cleaned Akkadian text into syllabified form using standard Assyriological rules (Huehnergard 2011). It inserts syllable boundaries (`.`), marks word endings (`¦`), and preserves hyphens and punctuation in brackets.

**WHY:** Syllabification is a prerequisite for mora counting and stress realization. The algorithm must handle edge cases like geminate splitting, diphthong resolution (via glottal stop insertion), and non-Akkadian text in brackets.

* `--merge-hyphen`: merge hyphens into syllable separators
* `--merge-lines`: normalize line breaks (1 newline → space, 2+ → paragraph break)
* `--extra-vowels` / `--extra-consonants`: extend character sets

**THUS:** The syllabifier produces `*_syl.txt` files with explicit syllable structure, ready for the prosody realization engine.

---

## 514-prosmaker-CLI

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
## 514b-phonetizer-CLI

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
## 515-metricalc-CLI

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
## 516-printer-CLI

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
## 517-fullprosmaker-CLI

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
## 518-phoneprep-CLI

**Domain:** Implementation / CLI / TTS Preparation

**WHAT:** `phoneprep.py` generates optimized recording scripts for MBROLA diphone voice creation. It produces a human-readable script, machine-readable sidecars (manifest, diphone list, word list), and an interactive HTML recording assistant.

**WHY:** Building a custom MBROLA voice requires recording every possible diphone. The script maximizes coverage with minimal recording burden by using a rhythmic pattern that enables automatic segmentation.

* `--coverage`: target per-diphone coverage (1-4, default 3)
* `--with-html-recording-helper`: create interactive recording assistant
* `--two-batch-emphatic`: create plain and mixed batches

**THUS:** phoneprep bridges the gap between computational phonology and speech synthesis, providing everything needed to record and segment a complete diphone database.
## 528-Phonetizer-Timing-Model

**Domain:** Implementation / Timing Model

**WHAT:** The phonetizer timing model is a stability-first system organized around a heavy-syllable reference (`cvc_reference`) and a bounded running drift. Ordinary segment anchors remain the default realizations; small timing mismatch is carried forward in a bounded running drift; short pauses serve as strict reset points; long pauses provide wider discharge space.

**WHY:** The timing model operates through a three-pass solver:
1. **Phase 1** builds row structure from the `_tilde.txt` input, classifying each symbol as segment, accent mark, separator, or pause.
2. **Phase 2** realizes durations using the timing model: consonant anchors (closure, fricative, sonorant), vowel anchors (short, long, very long), pause bands (short, long, resync), and drift management.
3. **Phase 3** assigns intonation tokens.

The active synchronization basis is stream-aware:
* Accentuated stream with `mora_mode = bi`: `cvc_reference`
* Accentuated stream with `mora_mode = mono`: `0.5 × cvc_reference`
* Original stream (`_ophone.txt`): `0.5 × cvc_reference`

Nominal non-accentuated targets:
* `CV = 0.5 × cvc_reference`
* `CVC = 1.0 × cvc_reference`
* `CVV = 1.0 × cvc_reference`
* `CVVC = 1.5 × cvc_reference`

Accentuated shapes add exactly `0.5 × cvc_reference` beyond the matching non-accentuated target.

**THUS:** The phonetizer timing model is the computational heart of the toolkit. It transforms abstract prosodic decisions into concrete millisecond durations, enabling quantitative rhythm analysis through metricalc.
## 529-Phonetizer-Drift-Mechanism

**Domain:** Implementation / Timing Model / Drift

**WHAT:** The phonetizer carries one signed running value, `drift_cursor`, that tracks cumulative timing mismatch. Negative drift means the stream is ahead of the beat; positive drift means it is behind. Synchronization is modulo the active synchronization basis.

**WHY:** Drift management is essential for realistic timing. Rather than forcing every syllable to match an exact target, the model allows bounded mismatch to accumulate and discharges it at prosodic boundaries.

Key behaviors:
* **Drift folding**: After a completed prosodic unit (`F` boundary), drift is folded to the nearest equivalent beat branch modulo the synchronization basis.
* **Long-vowel recovery**: Non-accented long vowels may be adjusted within `long_min .. very_long_min - 1` when drift exceeds `drift_tolerance`.
* **Accent-bearing recovery**: `CVV:` and `CVV:C` syllables apply accentuation first, then post-accent cleanup may run without the ordinary tolerance gate.
* **Resync pauses**: At eligible `F` boundaries, the solver may insert one non-punctuation resync pause (100-200 ms default band) to discharge drift exactly.
* **Short pauses**: Chosen from the short-pause band (520-680 ms) to bring drift as close to zero as the band allows.
* **Long pauses**: Chosen from the long-pause band (1100-1780 ms); usually discharge drift fully.

The drift tolerance parameter (`drift_tolerance: 19` ms) defines how much cumulative timing mismatch is tolerated before forced resynchronization. It is subject to the global duration scale.

**THUS:** The drift mechanism is what makes the timing model realistic. It allows the system to maintain overall rhythmic coherence without forcing every individual syllable to match an exact target.
## 530-Confwriter-CLI

**Domain:** Implementation / CLI / Configuration

**WHAT:** `confwriter.py` is the schema-driven editor for the package-wide YAML config file. It works with full YAML-path keys and a small set of operations: `--set`, `--get`, `--list`, `--unset`, `--set-default`, and `--verify`.

**WHY:** The config file controls recurring options for all pipeline stages. Confwriter provides a programmatic interface for creating, updating, and verifying config files without manual YAML editing.

Key operations:
* `--set KEY=VALUE`: set one key (repeatable)
* `--get KEY`: print one effective value
* `--list [SUBSTRING]`: print schema-backed key inventory
* `--unset KEY`: write null for one key
* `--set-default KEY`: write schema default explicitly
* `--verify`: run shared phonetize semantic verification

The `--verify` operation runs the same shared semantic verification layer used by standalone phonetizer preflight, checking enum-like process-policy values, positive integer timing leaves, ordering constraints, and pause-band compatibility.

**THUS:** Confwriter is the recommended way to manage configuration files. It validates both key paths and values against the canonical schema before any file is modified.
## 531-Configuration-Structure

**Domain:** Implementation / Configuration

**WHAT:** The package-wide YAML configuration has a hierarchical structure with top-level sections: `common`, `atfparse`, `syllabify`, `prosody`, `phonetize`, `metrics`, and `print`. Override precedence is: `-t/--option` path override > dedicated CLI flag > YAML config value > built-in default.

**WHY:** The grouped config structure allows users to specify all pipeline options in one file and run with `--conf FILE`. Each stage section owns its relevant options:

* `common.run`: shared output naming (prefix, outdir, quiet, log)
* `prosody.process`: style, mora_mode, relax_last
* `phonetize.process`: timing_model (durations, geminate_policy, accentuation_distribution_policy, drift_tolerance), intonation (f0, stress, question, statement, exclamation, continuation), allow_experimental
* `metrics.run`: json, table
* `print.run`: acute, bold, ipa, xar, ipa_proto_semitic

The `phonetize` section is the largest and most important, owning the timing model parameters that control the phonetic realization: `durations.scale`, `durations.segmental_ceiling`, `durations.segmental_floor`, `durations.cvc_reference`, `durations.consonants.*`, `durations.vowels.*`, `durations.pauses.*`.

**THUS:** The configuration structure mirrors the pipeline architecture. Each stage owns its parameters, and the grouped config file provides a single point of control for reproducible runs.
## 532-Default-YAML-Parameters

**Domain:** Implementation / Configuration / Timing Model

**WHAT:** The default YAML (`configs/default.yaml`) defines the complete timing model parameterization. Key parameters include:

**Global:**
* `durations.scale: 1.0` — global multiplier for all numeric duration leaves
* `durations.segmental_ceiling: 310` — validation ceiling for consonant gemination_max and vowel elongation_max
* `durations.segmental_floor: 20` — validation floor for vowel minima, consonant anchors
* `durations.cvc_reference: 300` — central heavy-syllable timing reference

**Consonants (closure, fricative, sonorant):**
* `onset`, `coda`, `coda_final` — positional anchors
* `geminate` — geminate target
* `geminate_coda_ratio` — corrective-only coda share
* `perception_limits.geminate_min`, `gemination_max` — class-local perceptual bounds

**Vowels:**
* `short: 110`, `long: 160`, `very_long: 260` — duration anchors
* `short_final`, `long_final` — pre-pausal final anchors
* `perception_limits.short_min`, `long_min`, `very_long_min`, `elongation_max` — perceptual bounds

**Pauses:**
* `short.min: 520`, `short.max: 680` — short-pause band
* `long.min: 1100`, `long.max: 1780` — long-pause band
* `resync.min: 100`, `resync.max: 200` — resync-pause band

**Process controls:**
* `geminate_policy: corrective` — same-consonant handling
* `accentuation_distribution_policy: 80_20` — primary/adjacent ratio
* `drift_tolerance: 19` — maximum tolerated timing mismatch

**WHY:** Each parameter is grounded in published phonetic, psycholinguistic, or perceptual research (see notes 231–250 for detailed justifications). The default values represent conservative choices within empirically attested ranges.

**THUS:** The default YAML provides a complete, defensible timing model that can be used directly for research or adjusted for sensitivity analysis.
## 533-Phonetizer-Phone-Row-Format

**Domain:** Implementation / Data Format

**WHAT:** The phonetizer emits phone rows in a twelve-field pipe-delimited format:

```
label|category|type|length|position|boundary|accent|realization|duration|drift|intonation|text
```

Example:
```
SUD|C|F|S|O|N|F|SU|0137|+000|M0C|ṣ
AYA|V|L|S|N|F|F|AA|0110|+023|M0C|a
MEN|S|M|S|S|N|P|MP|0064|+000|M0C| 
ZEN|S|S|L|S|N|P|ZP|1525|+000|L2C|<EOL>
```

**WHY:** This format is the authoritative downstream analysis artifact. It carries all information needed for metrics computation and printer output: segment identity, timing class, position in syllable, boundary type, accentuation status, realized duration in milliseconds, drift token, intonation contour, and source text.

Key fields:
* `category`: C (consonant), V (vowel), S (silence)
* `type`: consonant subclass (H=hiatus, T=transition, C=closure, F=fricative, S=sonorant); vowel height (L=low, M=mid, H=high); pause type (Q=question, E=exclamation, S=statement, C=continuation, I=internal, M=resync)
* `position`: O (onset), C (coda), N (nucleus), S (silence)
* `boundary`: N (none), I (internal), E (enclitic), L (internal merge), X (explicit merge), F (prosodic unit end)
* `accent`: A (accentuated), F (flat), P (pause)
* `duration`: zero-padded milliseconds
* `drift`: signed beat-offset token (+000, -023, +023)
* `intonation`: row-level pitch-shape token (M0C, H2C, L2C, R1L, etc.)

**THUS:** The phone-row format is the canonical representation of the phonetizer's output. It is the input contract for both metricalc and printer.
## 534-Phonetizer-Config-Ownership

**Domain:** Implementation / Configuration / Phonetizer

**WHAT:** The phonetizer is the canonical owner of the top-level `phonetize` config section. This includes:

**Process controls:**
* `phonetize.process.allow_experimental`: must be true to enable experimental features
* `phonetize.process.intonation.*`: f0, stress, question, statement, exclamation, continuation presets
* `phonetize.process.timing_model.geminate_policy`: corrective or cumulative
* `phonetize.process.timing_model.accentuation_distribution_policy`: 100_0 through 70_30
* `phonetize.process.timing_model.drift_tolerance`: maximum tolerated timing mismatch

**Timing model durations:**
* `phonetize.process.timing_model.durations.scale`: global multiplier
* `phonetize.process.timing_model.durations.segmental_ceiling`: validation ceiling
* `phonetize.process.timing_model.durations.segmental_floor`: validation floor
* `phonetize.process.timing_model.durations.cvc_reference`: central timing reference
* `phonetize.process.timing_model.durations.consonants.<class>.*`: class-specific anchors
* `phonetize.process.timing_model.durations.vowels.*`: vowel anchors and perception limits
* `phonetize.process.timing_model.durations.pauses.*`: pause bands

**No longer user-configurable:**
* `phonetize.process.timing_model.short_pause_policy`: fixed internally
* `phonetize.process.timing_model.drift_policy`: fixed internally
* `phonetize.process.timing_model.speech`: removed from active contract

**WHY:** Clear config ownership ensures that each stage controls its own parameters. The phonetizer's config section is the largest because the timing model is the most complex part of the pipeline. Runtime overrides use the same canonical paths via `-t/--option KEY=VALUE`.

**THUS:** The phonetize config section is the authoritative source for all timing model parameters. Changes to these parameters affect the phonetizer output and, through it, the metrics and printer outputs.
## 535-Pipeline-Data-Flow

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
## 536-Phonetizer-Semantic-Verification

**Domain:** Implementation / Validation

**WHAT:** Before runtime realization begins, the phonetizer runs a shared semantic verification layer against the effective config. This preflight checks:

* Enum-like process-policy values (geminate_policy, accentuation_distribution_policy)
* Positive integer timing leaves
* Validation-only segmental_floor lower bounds for vowel minima, consonant anchors, and hiatus/transition special realizations
* Class-local consonant gemination_max ordering and segmental_ceiling checks
* Consonant and vowel ordering constraints
* Pause-band ordering
* Short- and long-pause compatibility against active synchronization bases derived from cvc_reference
* Non-negative integer requirement for drift_tolerance
* Experimental-feature guard: limit_emphatic_coloring or enable_resync_pause requires allow_experimental: true

**WHY:** Semantic verification catches configuration errors before runtime, preventing the generation of invalid phone-row artifacts. The same verification layer is used by `confwriter --verify`, ensuring consistency between config editing and runtime execution.

**THUS:** The verification layer is a safety net that ensures the timing model is internally consistent before any processing begins. It reports blocking failures and warning-only conditions distinctly.
## 537-Phonetizer-Unit-Drift-Reporting

**Domain:** Implementation / Diagnostics

**WHAT:** The phonetizer reports a unit-drift summary in the front matter of each emitted phone-row artifact. This includes:

* `metadata.data.phonetize.unit_drift.max`, `mean`, `stddev`, `current`, `label`
* `unit_drift_extension_count`, `unit_drift_extension_rate`
* `max_unit_drift_extension`
* `syllable_count`, `pause_count`, `resync_pause_count`, `total_unit_count`
* `non_accented_long_vowel_count`, `left_as_is_non_accented_long_vowel_count`, `drift_tolerance_effect`
* `inserted_resync_pause_count`, `eligible_resync_pause_count`, `resync_pause_insertion_rate`
* `pause_with_residual_drift_count`, `pause_with_residual_drift_rate`
* `duration_scale`

**WHY:** These diagnostics allow researchers to audit the timing model's behavior at the corpus level. They answer questions like: How often does drift exceed tolerance? How often are resync pauses inserted? What is the average drift magnitude? This information is essential

---

## 515-metricalc-CLI

**Domain:** Implementation / CLI / Metrics

**WHAT:** `metricalc.py` computes rhythmic and structural metrics from prosody-realized text (`*_tilde.txt`). It outputs human-readable tables, JSON, and CSV formats.

**WHY:** Metrics are essential for validating the algorithm and comparing Akkadian to living languages. The calculator computes syllable distributions, mora statistics, acoustic metrics (%V, ΔC, VarcoC), merge statistics, and pause metrics.

* `--table`, `--json`, `--csv`: output formats
* `--wpm`, `--pause-ratio`, `--long-punct-weight`: speech parameters
* `--input-list`: batch processing

**THUS:** The metrics calculator provides quantitative validation of the algorithm and enables cross-linguistic comparison.

---

## 516-printer-CLI

**Domain:** Implementation / CLI / Formatting

**WHAT:** `printer.py` converts the pivot format (`*_tilde.txt`) into multiple user-facing outputs: acute-accented text, bold-marked Markdown, IPA transcription, XAR practical orthography, and MBROLA-ready formats.

**WHY:** Different audiences need different representations. Scholars need acute accents for compact notation; readers need bold for visual inspection; phoneticians need IPA; speech synthesis needs MBROLA format.

* `--acute`, `--bold`, `--ipa`, `--xar`, `--mbrola`: output selectors
* `--ipa-proto-semitic {preserve,replace}`: pharyngeal mapping
* `--circ-hiatus`: speculative mode splitting circumflex vowels

**THUS:** The printer makes the algorithm's output accessible to diverse users and applications.

---

## 517-fullprosmaker-CLI

**Domain:** Implementation / CLI / Pipeline

**WHAT:** `fullprosmaker.py` runs the complete pipeline in one command: syllabification → prosody realization → metrics → printing. It centralizes shared options and writes all selected outputs in a single run.

**WHY:** Users should not need to run four separate tools for standard processing. The full pipeline ensures consistency and reduces error.

* Stage-specific prefixes: `--syl-merge-hyphens`, `--prosody-style`, `--metrics-wpm`, `--print-ipa`
* `--test-all`: run all built-in tests

**THUS:** The fullprosmaker is the primary entry point for end-to-end processing, suitable for both single-file analysis and batch corpus work.

---

## 518-phoneprep-CLI

**Domain:** Implementation / CLI / TTS Preparation

**WHAT:** `phoneprep.py` generates optimized recording scripts for MBROLA diphone voice creation. It produces a human-readable script, machine-readable sidecars (manifest, diphone list, word list), and an interactive HTML recording assistant.

**WHY:** Building a custom MBROLA voice requires recording every possible diphone. The script maximizes coverage with minimal recording burden by using a rhythmic pattern that enables automatic segmentation.

* `--coverage`: target per-diphone coverage (1-4, default 3)
* `--with-html-recording-helper`: create interactive recording assistant
* `--two-batch-emphatic`: create plain and mixed batches

**THUS:** phoneprep bridges the gap between computational phonology and speech synthesis, providing everything needed to record and segment a complete diphone database.

---

## 519-MBROLA-Overview

**Domain:** TTS / Speech Synthesis

**WHAT:** MBROLA (Multilingual BLAISE Articulatory Speech Synthesizer) is a diphone concatenation synthesizer. It requires a voice database of diphone samples, each with marked start, middle, and end sample numbers (Dutoit et al. 1996).

**WHY:** Creating a custom MBROLA voice for Akkadian would allow synthesized speech based on the prosody-realized texts. This would provide an audible test of the algorithm's perceptual plausibility.

**THUS:** The project includes tools for generating the necessary recording materials and segmentation data, laying the foundation for future voice development.

---

## 520-Diphone-Recording-Pattern

**Domain:** TTS / Recording Script Design

**WHAT:** The key innovation enabling automatic segmentation is the rhythmic pattern: `_ V C C V C C V C _`. This pattern covers all diphone types in a single template:

* `_-V`: silence to vowel
* `V-C`: vowel to consonant (3 occurrences)
* `C-C`: consonant cluster (2 occurrences)
* `C-V`: consonant to vowel (2 occurrences)
* `C-_`: consonant to silence

**WHY:** With 5 consonants and 2 vowels, this pattern generates 9 diphones per word. A randomized script of 160 words ensures each CC pair appears 6-7 times, providing ample coverage.

**THUS:** The rhythmic pattern makes automatic segmentation possible by creating predictable acoustic events: silence at boundaries, high-amplitude vowel peaks, and characteristic low-amplitude consonant clusters.

---

## 521-Diphone-Inventory-Calculation

**Domain:** TTS / Phonetics

**WHAT:** For a simplified inventory of 5 consonants (k, s, m, b, j) and 2 vowels (a, u), the complete diphone inventory includes:

* V-C: 10 diphones (2 vowels × 5 consonants)
* C-V: 10 diphones (5 consonants × 2 vowels)
* C-C: 25 diphones (5 × 5)
* V-V: 4 diphones (2 × 2)
* Boundaries ( _-C, C-_, _-V, V-_ ): 14 diphones

Total: 63 diphones

**WHY:** This manageable size demonstrates the feasibility of the approach. For the full Akkadian inventory, the numbers scale accordingly, but the same principles apply.

**THUS:** The diphone inventory calculation provides a clear target for recording coverage, ensuring that all necessary transitions are captured.

---

## 522-Randomized-Recording-Script

**Domain:** TTS / Recording Script

**WHAT:** The recording script randomizes word order to prevent list fatigue. If every word started with the same pattern, articulation would become unnatural. Randomization ensures both vowels appear as V1, V2, V3, and all consonants appear in all positions.

**WHY:** Natural pronunciation requires variety. A randomized script produces more consistent, natural-sounding recordings across the 160-word corpus.

**THUS:** The script is organized into 8 blocks of 20 words each, with built-in breaks to manage vocal fatigue during recording sessions.

---

## 523-Recording-Protocol

**Domain:** TTS / Recording

**WHAT:** The recording protocol specifies:

* Technical parameters: 16 kHz, 16-bit, mono, WAV format
* Speaking guidelines: natural pace, 1-second pause before and after each word
* Session structure: 4 sessions of 2 blocks each, with 5-minute breaks
* File naming: `diphone_recording_YYYYMMDD.wav`

**WHY:** Consistent recording conditions are essential for successful automatic segmentation. The 1-second silences provide clear word boundaries, and the technical specifications match MBROLA requirements.

**THUS:** The protocol ensures high-quality, consistent recordings suitable for downstream processing.

---

## 524-Automatic-Segmentation-Strategy

**Domain:** TTS / Signal Processing

**WHAT:** The rhythmic pattern enables automatic segmentation through predictable acoustic events:

1. Silence detection identifies word boundaries
2. Vowel peaks (high amplitude, periodic structure) locate V1, V2, V3
3. Phoneme boundaries are placed midway between vowel peaks
4. Diphone segments are extracted based on the pattern positions

**WHY:** Manual segmentation of hundreds of diphones is tedious and error-prone. Automatic segmentation makes the process scalable and reproducible.

**THUS:** The segmentation strategy turns a challenging manual task into an automated process, making custom voice creation feasible for a single researcher.

---

## 525-HTML-Recording-Assistant

**Domain:** TTS / User Interface

**WHAT:** The HTML recording assistant provides an interactive interface for guided recording sessions. It displays words one at a time, logs events, and ensures consistent naming and timing.

Key features:
* Keyboard controls: Space (start/stop chunk), Right Arrow (accept word), Left Arrow (repeat word)
* WAV naming: `<prefix>_NNN.wav` with zero-padded indices
* Event logging: timestamps, word indices, accepted counts, errors
* Copy Log function for segmentation manifest

**WHY:** A structured recording process reduces errors and produces the metadata needed for automatic segmentation. The assistant enforces the protocol and creates a complete audit trail.

**THUS:** The HTML assistant makes the recording process accessible to non-experts while ensuring the quality and consistency required for downstream processing.

---

## 526-MBROLATOR-Workflow

**Domain:** TTS / Voice Building

**WHAT:** Once recordings and segmentation are complete, the MBROLATOR toolset builds the final MBROLA voice:

1. Prepare data: 16-bit, 16kHz diphone WAV files and segmentation (`.seg`) file
2. Compile MBROLATOR tools (AnaMBE, Resynthesis)
3. Generate parameter files (`.mbe` with FrameLength and FrameShift)
4. Run analysis (generate_make.pl and make)
5. Build database (database_build)
6. Test voice (mbrola test.pho test.wav)

**WHY:** MBROLATOR is the standard toolset for creating MBROLA voices. Following this workflow ensures compatibility with the MBROLA synthesizer.

**THUS:** The complete pipeline from phoneprep through segmentation to MBROLATOR provides a clear path from linguistic analysis to audible speech synthesis.

---

## 527-Future-TTS-Integration

**Domain:** TTS / Roadmap

**WHAT:** The current implementation provides the foundation for future TTS integration. The IPA output from the printer can be fed to a speech synthesizer once a voice is built.

**WHY:** An audible Akkadian voice would allow perceptual testing of the prosody realization algorithm. Native speakers of related languages could evaluate whether the synthesized speech sounds natural.

**THUS:** TTS integration is a long-term goal that will provide external validation of the model and make Akkadian accessible to new audiences.

---

## References

**Alqahtani, Mufleh Salem M.** 2020. "The Phonological Opacity of Local Compensatory Lengthening in Modern Colloquial Persian: A Stratal Optimality Theoretic Approach." *SKASE Journal of Theoretical Linguistics* 17 (5): 2–26.
**Anjarningsih, Harwintha Y.** "A Preliminary Study on Characterizing Syntactic Processing and Pause Patterns in Bilingual English." Indonesia: Center of Language Development, Institut Agama Islam Negeri Madura, 2024. (Anjarningsih 2024)
**Ashby, Michael.** 2021. "A Prague School Psycholinguist in London? The Life and Career of Frieda Goldman-Eisler (1907–1982)." In *Proceedings of the 4th International Workshop on the History of Speech Communication Research (HSCR 2021)*, 11–20. Prague.
**Asu, Eva Liina, and Francis Nolan.** 2006. "Estonian Rhythm and the Pairwise Variability Index." *Proceedings of Speech Prosody 2006*.
**Bae, Rebecca.** "The Effects of Pausing on Comprehensibility." Master's thesis, Iowa State University, 2015. (Bae 2015)
**Best, Catherine T.** 1994. "The Emergence of Native-Language Phonological Influences in Infants: A Perceptual Assimilation Model." *Developmental Speech Perception* 167: 233–277.
**Billington, Rosey.** 2015. "Temporal Correlates of Lopit Singleton and Geminate Glides." In *Proceedings of the 18th International Congress of Phonetic Sciences (ICPhS 2015)*. Glasgow, UK.
**Botinis, Antonis, Marios Fourakis, and Irini Prinou.** 1999. "Prosodic Effects on Segmental Durations in Greek." In *Proceedings of the 14th International Congress of Phonetic Sciences (ICPhS 1999)*, 595–598. San Francisco.
**Broselow, Ellen, Su-I Chen, and Marie Huffman.** 1997. "Syllable Weight: Convergence of Phonology and Phonetics." *Phonology* 14 (1): 47–82.
**Buccellati, Giorgio. "Akkadian."** In *The Semitic Languages*, edited by Robert Hetzron, 69–99. London: Routledge, 1997. (Buccellati 1997)
**Cagni, Luigi.** ***L'epopea di Erra***. Studi Semitici 34. Rome: Istituto di Studi del Vicino Oriente, 1969. (Cagni 1969)
**Campbell, W. N., and S. D. Isard.** 1990. "Segment Durations in a Syllable Frame." Research Paper, University of Edinburgh, Centre for Speech Technology Research.
**Campos-Astorkiza, Rebeka.** 2005. "What Drives Compensatory Lengthening? Beyond Moraic Conservation." Research Paper, The Ohio State University, Department of Linguistics.
**Caplice, Richard, with Daniel Snell.** ***Introduction to Akkadian***. 4th edition. Rome: Editrice Pontificio Istituto Biblico, 2002. (Caplice & Snell 2002)
**Cutanda, Diana, Daniel Sanabria, and Ángel Correa.** 2019. "Cognitive Entrainment to Isochronous Rhythms Is Independent of Both Sensory Modality and Top-Down Attention." *Psicológica* 40: 62–84. doi:10.2478/psicolj-2019-0005.
**Dediu, Dan, Scott R. Moisik, S. Lin, and Steven Moran.** 2021. "Dental Fricatives: Patterning, Evolution, and Factors Affecting a Rare Class of Speech Sounds." In *Words, Bones, Genes, Tools*, 147–175. Kerns Verlag Tübingen.
**El Zarka, Dina. "Arabic Intonation."** In *The Oxford Handbook of Arabic Linguistics*, edited by [Editor Name], 2017. (El Zarka 2017)
**Gao, Yingming, and Peter Birkholz.** 2014. "Speaking Rate Changes Affect Phone Durations Differently for Neutral and Emotional Speech." Research Paper, VocalTractLab, Dresden University of Technology.
**Gendrot, Cédric, Martine Adda-Decker, and Yaru Wu.** 2012. "Comparing Journalistic and Spontaneous Speech: Prosodic and Spectral Analysis." *ISCA Archive*.
**Gibson, Mark, Ana María Fernández Planas, Adamantios Gafos, and Emily Remirez.** 2013. "Consonant Duration and VOT as a Function of Syllable Complexity and Voicing in a Sub-set of Spanish Clusters." *ISCA Archive*.
**Gustafson-Čapková, Sofia, and Beáta Megyesi.** 2001. "A Comparative Study of Pauses in Dialogues and Read Speech." In *Eurospeech 2001 - Scandinavia*, 931–934. Stockholm.
**Hayes, Bruce.** 1989. "Compensatory Lengthening in Moraic Phonology." *Linguistic Inquiry* 20 (2): 253–306.
**Hozjan, Vladimir, and Zdravko Kacic.** 2002. "Objective Analysis of Emotional Speech for English and Slovenian Interface Emotional Speech Databases." In *Proceedings of the Language Resources and Evaluation (LREC) 2002*.
**Huehnergard, John.** ***A Grammar of Akkadian***. 3rd edition. Winona Lake, IN: Eisenbrauns, 2011. (Huehnergard 2011)
**Izre'el, Shlomo, and Eran Cohen.** ***Literary Old Babylonian***. Muenchen: LINCOM GmbH, 2004. (Izre'el & Cohen 2004)
**Jacquignon, Titus.** 2023. "Une approche globale de l'expression : L'anthropologie du geste et du rythme de Marcel Jousse (1886-1961)." Séminaire, Laboratoire ERIMIT (EA4327), 2023–2024.
**Kavitskaya, Darya.** "Compensatory Lengthening: Phonetics, Phonology, Diachrony." PhD diss., University of California, Berkeley, 2001. (Kavitskaya 2001)
**Lambert, W. G.** ***Babylonian Creation Myths***. Mesopotamian Civilizations 16. Winona Lake, IN: Eisenbrauns, 2013. (Lambert 2013)
**Landschultz, Karen.** 1966. "Quantité vocalique en français – relations quantitatives des voyelles accentuées suivies d'une consonne fricative." *Revue Romane*.
**Liu, Yang.** 2022. "Addressing Outstanding Questions of the Mandarin Syllable." PhD diss., Stony Brook University.
**Lunden, Anya.** 2017. "Syllable Weight and Duration: A Rhyme/Intervals Comparison." *Proceedings of the Linguistic Society of America* 2: 33:1–12. https://doi.org/10.3765/plsa.v2i0.4084.
**Meynadier, Yohann, S. Dufour, and G. Vercherand.** 2019. "Interaction entre durée et position dans la perception des fricatives voisées chuchotées." *ACL Anthology*.
**Möbius, Bernd.** 2004. "Corpus-Based Investigations on the Phonetics of Consonant Voicing." *Folia Linguistica* 38 (1-2): 5–26.
**Morley, Rebecca L., and Bridget J. Smith.** 2022. "A Reanalysis of the Voicing Effect in English: With Implications for Featural Specification." Research Paper, The Ohio State University.
**Naeser, Margaret A.** 1970. "Influence of Initial and Final Consonants on Vowel Duration in CVC Syllables." Technical Report No. 130, Wisconsin Research and Development Center for Cognitive Learning, University of Wisconsin, Madison.
**Nazzi, Thierry, and Franck Ramus.** 2003. "Perception and Acquisition of Linguistic Rhythm by Infants." *Speech Communication* 41: 233–243.
**Omar, Margaret K.** ***Levantine and Egyptian Arabic: A Comparative Study***. Washington, D.C.: Foreign Service Institute, Department of State, 1976. (Omar 1976)
**Patel, Aniruddh D., and John R. Daniele.** 2003. "An Empirical Comparison of Rhythm in Language and Music." *Cognition* 87: B35–B45.
**Pellegrino, François, Christophe Coupé, and Egidio Marsico.** 2011. "A Cross-Language Perspective on Speech Information Rate." *Language* 87 (3): 539–558.
**Rathcke, Tamara, et al.** 2023. "Timing Anticipation in Adults and Children with Developmental Dyslexia: Evidence of an Inefficient Mechanism." In *Proceedings of the 20th International Congress of Phonetic Sciences (ICPhS 2023)*. Prague.
**Ryan, Kevin M.** 2014. "Onsets Contribute to Syllable Weight: Statistical Evidence from Stress and Meter." *Language* 90 (2): 309–341.
**Tavakoli, Parvaneh, and Sheryl Cooke.** ***Comprehensibility in Language Assessment: A Broader Perspective***. British Council Monographs in Modern Language Testing, 6. Sheffield: Equinox Publishing, 2024. (Tavakoli & Cooke 2024)
**Šturm, Pavel, and Jan Volín.** 2023. "Occurrence and Duration of Pauses in Relation to Speech Tempo and Structural Organization in Two Speech Genres." *Languages* 8: 23. https://doi.org/10.3390/languages8010023.
**Sugai, Kosuke.** 2017. "Mental Representation of Japanese Mora; Focusing on Its Intrinsic Duration." In *Proceedings of Interspeech 2017*, 1218–1222. Stockholm.
**Tauberer, Joshua, and Keelan Evanini.** 2009. "Intrinsic Vowel Duration and the Post-vocalic Voicing Effect: Some Evidence from Dialects of North American English." In *Proceedings of Interspeech 2009*. Brighton, UK.
**Wan, I-Ping, Yu-Ju Lai, and Pu Yu.** 2024. "Computational Approaches to Quantitative Analysis of Pause Duration in Taiwan Mandarin." *ACL Anthology*, 116–123.
**White, Laurence, and Sven L. Mattys.** 2007. "Calibrating Rhythm: First Language and Second Language Studies." *Journal of Phonetics*.
**Woolridge, Erica.** 2015. "A Metrical Stress Analysis of Mushuau Innu." In *Proceedings of the Workshop on Structure and Constituency in the Languages of the Americas 18 & 19*. University of British Columbia Working Papers in Linguistics 39.
**Zellner, Brigitte.** 1994. "Pauses and the Temporal Structure of Speech." In *Fundamentals of Speech Synthesis and Speech Recognition*, edited by Eric Keller, 41–62. Chichester: John Wiley & Sons.
**Zu, Yiqing, and Xiaoxia Chen.** 1999. "Segmental Durations and Lengthened Syllables." *International Phonetic Association*.

