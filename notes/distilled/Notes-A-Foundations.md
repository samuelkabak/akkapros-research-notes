# Research Notes - Akkadian Prosody Project
## Part A: Foundations

---

## A-001-Auditory-Intuition

**Domain:** Foundational / Motivation

**WHAT:** When European scholars recite Akkadian, the language sounds rhythmless. Arabic speakers produce recitations that feel closer to natural speech.

**WHY:** Personal observation while listening to recordings of scholarly recitations. Native speaker intuition from a related Semitic language detects a missing pulse. The standard pronunciation taught in universities lacks the natural organization that all living languages possess (Huehnergard 2011 describes the rules but not the flow).

**THUS:** There is a gap between the phonological description and any plausible spoken realization. The academic model describes stress placement but not phrasal timing. This gap needs to be identified and possibly filled.

---

## A-002-Gap-In-Scholarship

**Domain:** Foundational / Problem Statement

**WHAT:** Assyriological grammars describe stress rules in detail, but applying these rules mechanically does not produce language that could be spoken fluently.

**WHY:** Comparison with living Semitic languages (Arabic) shows that something essential is missing. The grammars provide rules for isolated words but nothing for connected speech (Greenstein 1984 discusses syllable structure but not phrasal timing).

**THUS:** The academic model is incomplete. It describes where stress could fall, not how it was realized in actual speech. A complete model needs a mechanism for phrasal timing.

---

## A-003-Personal-Motivation

**Domain:** Foundational / Context

**WHAT:** The investigator's native familiarity with Arabic provided an internal metric for what natural speech should sound like.

**WHY:** This is not an abstract linguistic question but a perceptual one. The ear detects a problem even when the mind cannot yet name it.

**THUS:** The research is grounded in authentic linguistic intuition, not just theoretical speculation.

---

## A-004-Akkadian-Consonant-Inventory

**Domain:** Phonology / Segments

**WHAT:** Akkadian has a full set of consonants with IPA values. These include stops (b, d, g, k, p, q, ṭ), fricatives (s, z, š, ḫ, ḥ), sonorants (l, m, n, r), glottals (ʾ, ʿ), and glides (w, y). The emphatics are q, ṣ, ṭ (Buccellati 1997).

**WHY:** The phonetic realization of emphatics is debated. They may be ejective or pharyngealized. This uncertainty matters for IPA rendering but does not affect moraic computation.

**THUS:** Any prosodic model must account for these consonants and their effects on adjacent vowels.

---

## A-004b-Cuneiform-Writing-Conventions

**Domain:** Orthography / Writing System

**WHAT:** Akkadian is written in cuneiform, a logo-syllabic script where signs can represent words (logograms) or syllables (phonograms). The writing system does not consistently mark vowel length, gemination, or stress. Plene writing (extra vowel signs) occasionally indicates length or prominence, but its use is inconsistent.

**WHY:** Understanding the orthographic conventions is essential for interpreting the corpus data. The eBL transcriptions normalize cuneiform into a standard transliteration that marks vowel length (macron/circumflex) and distinguishes consonants. However, the underlying cuneiform leaves much phonetic detail ambiguous. Buccellati (1997) stresses how difficult it is to establish a phonemic inventory for ancient Semitic languages from graphemic documentation alone. This ambiguity is therefore both a limitation and an opportunity: it means the writing system does not contradict the prosodic model, but it also cannot directly confirm it (Huehnergard 2011, §1.4; Buccellati 1997; Streck 2022, §1.3).

**THUS:** Any prosodic reconstruction must acknowledge that we are working from transliterated texts, not direct phonetic records. The model's assumptions must be explicit, and its results must be compatible with what the orthography does tell us (e.g., phonemic length distinctions, syllable structure constraints).

---

## A-005-Akkadian-Vowel-Inventory

**Domain:** Phonology / Segments

**WHAT:** Akkadian has short vowels (a, e, i, u = 1 mora), long vowels (ā, ē, ī, ū = 2 morae), and circumflex vowels (â, ê, î, û = 2 morae) from contraction (Huehnergard 2011).

**WHY:** Scholars debate whether macron and circumflex vowels differed phonetically. The orthography distinguishes them, but the phonetic reality is unknown.

**THUS:** Orthographic distinctions do not necessarily reflect spoken distinctions. This uncertainty must be acknowledged in any reconstruction.

---

## A-006-Diphthong-Contraction

**Domain:** Phonology / Historical Change

**WHAT:** Historical diphthongs (*ay, *aw) contracted to long vowels (ê, ô) in Old Babylonian (Huehnergard 2011; Buccellati 1996).

**WHY:** This removed diphthongs from the inventory and increased the proportion of long vowels. It affected the overall syllable structure of the language.

**THUS:** Diphthongs are rare in Old Babylonian texts. When they appear across morpheme boundaries, they need special handling in syllabification.

---

## A-007-Vowel-Syncope

**Domain:** Phonology / Processes

**WHAT:** Unstressed short vowels in open syllables delete under certain conditions. Example: napištum → napšātum (Greenstein 1984; Buccellati 1996).

**WHY:** This is not random deletion. It is a systematic process that reduces the number of light syllables. Buccellati (1996) also notes vowel elision before endings in forms such as ipparis + u > ipparsū, which shows that Akkadian actively manages syllable weight and surface phonotactics.

**THUS:** Syncope shows that Akkadian phonology already contains mechanisms for adjusting moraic structure. This supports the idea that similar operations could be used for rhythm.

---

## A-008-Syncope-Blocking-Conditions

**Domain:** Phonology / Constraints

**WHAT:** Syncope is blocked if it would create a tri-consonantal cluster, especially with a guttural. Example: iḫarriš is attested, not iḫrš (Greenstein 1984).

**WHY:** The language avoids phonotactic violations. It manages syllable structure actively.

**THUS:** Any prosodic model must respect these constraints. Operations that would create illegal clusters are prohibited.

---

## A-009-Anaptyxis

**Domain:** Phonology / Processes

**WHAT:** When syncope would create an illegal cluster, a vowel is inserted instead. Example: šarrum from šar-r-m (Greenstein 1984).

**WHY:** Accentuation strategies are already present in the phonology. The language has native mechanisms for adjusting syllable structure.

**THUS:** The toolkit's operations (vowel lengthening, gemination) are not invented. They are grounded in existing Akkadian phonological processes.

---

## A-010-Geers-Law

**Domain:** Phonology / Constraints

**WHAT:** Two emphatic consonants cannot co-occur in a root. If a root would etymologically contain two emphatics, one dissimilates to its plain counterpart (Geers 1945; Buccellati 1997).

**WHY:** This is evidence of articulatory ease prioritizing rapid production. The language avoids difficult sequences.

**THUS:** Phonological constraints shape the lexicon. Any prosodic model must operate within these natural limits.

---

## A-011-N-Assimilation

**Domain:** Phonology / Processes

**WHAT:** The consonant *n* assimilates completely to a following consonant, resulting in gemination. Example: indin → iddin (Huehnergard 2011).

**WHY:** Gemination is a native process. It is available as a phonetic resource.

**THUS:** Gemination can be used as an operation in the prosodic model. It is already attested in the language.

---

## A-012-T-Infix-Assimilation

**Domain:** Phonology / Processes

**WHAT:** The infix -t- in verbal stems assimilates to preceding dentals or sibilants, resulting in gemination. Example: iṣtabat → iṣṣabat (Huehnergard 2011).

**WHY:** Gemination is productive across different morphological contexts. It is a regular part of the phonology.

**THUS:** Gemination is a well-attested, productive process. It can be used systematically in the model.

---

## A-013-Sandhi-Assimilation

**Domain:** Phonology / Connected Speech

**WHAT:** Consonants assimilate across word boundaries for ease of pronunciation. Example: in pīm → im pīm (Huehnergard 2011).

**WHY:** Sandhi is active. The language does not treat word boundaries as absolute barriers.

**THUS:** Word boundaries can be crossed for prosodic purposes. Merging words in the algorithm reflects natural speech behavior.

---

## A-014-Gemination-As-Resource

**Domain:** Phonology / Processes

**WHAT:** Geminated consonants are phonologically distinct from singletons. They are common in the lexicon (Huehnergard 2011).

**WHY:** Gemination is available as a phonetic resource. The language already uses it for morphological and phonological purposes.

**THUS:** Adding morae through gemination is phonologically legal. It builds on an existing contrast.

---

## A-015-Word-Boundary-Constraints

**Domain:** Phonology / Syllable Structure

**WHAT:** Consonant clusters are not permitted at word boundaries. A prothetic vowel breaks initial clusters. An epenthetic case vowel breaks final clusters (Greenstein 1984).

**WHY:** The language actively manages syllable margins. It avoids illegal structures at edges.

**THUS:** The model must respect these constraints. Final gemination is illegal because word-final geminates are unattested.

---

## A-016-Tri-Consonantal-Clusters-Forbidden

**Domain:** Phonology / Syllable Structure

**WHAT:** Three consonants in a row are not allowed. They are resolved by inserting an anaptyctic vowel. The maximum is CC across a syllable boundary (Greenstein 1984).

**WHY:** This is a hard constraint on Akkadian phonotactics. It shapes all phonological processes.

**THUS:** Any prosodic operation must avoid creating illegal clusters. This becomes a boundary condition for the algorithm.

---

## A-017-CVVC-Syllables-Status

**Domain:** Phonology / Syllable Types

**WHAT:** CVVC (superheavy) syllables exist in Old Babylonian but are restricted. In later dialects, they disappear. They are either shortened to CVC or restructured (Greenstein 1984, Huehnergard 2011).

**WHY:** This is evidence of instability. CVVC syllables are a marked category. Their diachronic loss suggests pressure to eliminate trimoraic structures.

**THUS:** The choice between preserving or shortening CVVC syllables is not arbitrary. Preserving them (through lengthening) avoids information loss about lexical length distinctions. Shortening them would follow the later historical trajectory but would lose the contrast between CV̄C and CVC. The algorithm adopts the conservative approach: preserve length unless evidence suggests otherwise.

---

## A-018-CVVC-Diachronic-Pathway

**Domain:** Phonology / Historical Change / Algorithm

**WHAT:** The historical loss of CVVC syllables in later dialects suggests that the language was under pressure to eliminate trimoraic syllables. This pressure might reflect a preference for bimoraic units in speech rhythm.

**WHY:** Two pathways are possible for handling CVVC syllables algorithmically:

* Lengthen (conservative): CVVC → CVV~C (3µ → 4µ). This preserves lexical length distinctions and avoids information loss about the original long vowel.
* Shorten (diachronic): CVVC → CVC (3µ → 2µ). This follows the later historical development but neutralizes the contrast between CV̄C and CVC.

**THUS:** The algorithm adopts the lengthening approach for Old Babylonian texts. This is the more conservative choice: it preserves the phonemic length distinction and avoids discarding information that may have been prosodically relevant. The shortening option remains available for sensitivity testing or for application to later dialects where the historical loss had already occurred.

---

## A-018b-Corpus-Selection-Criteria

**Domain:** Corpus / Methodology

**WHAT:** The corpus consists of three Standard Babylonian literary texts: Enūma Eliš (tablets II, IV, VI, VII), Erra and Išum (tablet I), and Marduk's Address to the Demons. These were selected for specific reasons.

**WHY:**

* Enūma Eliš is the Babylonian creation epic, a well-preserved literary text with consistent orthography and clear line structure. Tablets II, IV, VI, VII were chosen because they contain connected narrative passages suitable for prosodic analysis.
* Erra and Išum (Tablet I) is a mythological poem with varied metrical structures and a mix of dialogue and narrative. It provides a different register from the epic style.
* Marduk's Address to the Demons is an incantation text with formulaic repetitions and ritual language. It represents a third genre, allowing cross-genre comparison.

All texts are from the Standard Babylonian period (ca. 1000–600 BCE), ensuring linguistic consistency. The transcriptions are taken from the Electronic Babylonian Library (eBL), which provides normalized, machine-readable versions of standard editions (Lambert 2013 for Enūma Eliš; Cagni 1969 for Erra; Lambert 1999 for Marduk's Address).

**THUS:** The corpus is small but representative of three major literary genres. Future work should expand to letters, legal documents, and administrative texts to test the model on non-literary registers.

---

## References

**Buccellati, Giorgio. "Akkadian."** In *The Semitic Languages*, edited by Robert Hetzron, 69–99. London: Routledge, 1997. (Buccellati 1997)

**Cagni, Luigi.** ***L'epopea di Erra***. Studi Semitici 34. Rome: Istituto di Studi del Vicino Oriente, 1969. (Cagni 1969)

**Greenstein, Edward L.** "The Phonology of Akkadian Syllable Structure." *Afroasiatic Linguistics* 9 (1): 1–18, 1984. (Greenstein 1984)

**Huehnergard, John.** ***A Grammar of Akkadian***. 3rd edition. Winona Lake, IN: Eisenbrauns, 2011. (Huehnergard 2011)

**Lambert, W. G.** ***Babylonian Creation Myths***. Mesopotamian Civilizations 16. Winona Lake, IN: Eisenbrauns, 2013. (Lambert 2013)

**Streck, Michael P.** ***Altbabylonisches Lehrbuch***. 4th edition. Wiesbaden: Harrassowitz, 2022. (Streck 2022)
