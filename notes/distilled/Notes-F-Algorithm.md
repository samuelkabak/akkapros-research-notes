# Research Notes - Akkadian Prosody Project
## Part F: Algorithm — Merge Logic, Diphthongs, Worked Examples

---

## F-066-Merge-Logic-Why-Needed

**Domain:** Algorithm / Merging

**WHAT:** Merge logic is needed because words with odd mora counts cannot resolve independently. They must merge with following words to achieve even mora counts.

**WHY:** The bimoraic hypothesis requires even mora counts within prosodic units. When a word has odd mora count and cannot be accentuated internally, it must merge.

**THUS:** Merge logic is a core component of the algorithm. It determines how words are grouped into prosodic units.

---

## F-067-Merge-Left-To-Right

**Domain:** Algorithm / Merging

**WHAT:** The algorithm processes text left to right, mimicking speech production. It never looks back unless necessary.

**WHY:** This mimics the online nature of speech production. Speakers do not plan entire utterances in advance.

**THUS:** Left-to-right processing is the default strategy.

---

## F-068-Merge-Forward

**Domain:** Algorithm / Merging

**WHAT:** When a word cannot be stress-realized internally, it merges with following words until an accentuation candidate is found or the merged unit becomes even.

**WHY:** Forward merging is the default strategy. It mimics natural speech production.

**THUS:** The algorithm prioritizes forward merging, only looking back when forward is impossible.

---

## F-069-Merge-Backward

**Domain:** Algorithm / Merging

**WHAT:** Backward merge is used when trailing function words occur before punctuation and need a content host. The algorithm may roll back prior stress realizations and rebuild a larger unit including the preceding content word plus trailing function words.

**WHY:** Function words cannot stand alone. At boundaries, forward merging is impossible. Backward merging ensures that even stranded function words are properly integrated into the prosodic structure.

**THUS:** Backward merging handles edge cases, ensuring the algorithm can process any input regardless of punctuation placement.

---

## F-070-Merge-Termination-Guarantee

**Domain:** Algorithm / Merging

**WHAT:** The merge process is guaranteed to terminate because every word has at least one syllable, and the last resort operation (onset gemination) can always resolve an odd unit.

**WHY:** This guarantee is important for algorithmic completeness. No input can cause infinite merging.

**THUS:** The algorithm is complete. Every input produces a valid output.

---

## F-071-Explicit-Plus-Linking

**Domain:** Algorithm / Merging

**WHAT:** The input `+` is treated as an explicit instruction that the linked sequence forms one mandatory prosodic unit. In strict mode (default, `only_last=True`), only the last linked word is eligible for stress realization. In relaxed mode (`--prosody-relax-last`), stress realization may propagate right-to-left across the linked chain.

**WHY:** Some sequences (construct chains, certain compounds) must be treated as units. The `+` marker allows the user to specify this. The strict mode preserves the integrity of construct chains; the relaxed mode tests alternative groupings.

**THUS:** The algorithm respects explicit linking, overriding default behavior when instructed. The option exists for experimentation, with the conservative strict mode as the default.

---

## F-072-Explicit-Plus-Strict-Mode

**Domain:** Algorithm / Merging

**WHAT:** In strict mode (default), only the last linked word in an explicit `+` chain is eligible for stress realization. All preceding linked words are locked.

**WHY:** This preserves the integrity of construct chains, where only the final element bears the primary stress.

**THUS:** Strict mode is the conservative default.

---

## F-073-Explicit-Plus-Relaxed-Mode

**Domain:** Algorithm / Merging

**WHAT:** In relaxed mode (`--prosody-relax-last`), stress realization may propagate right-to-left across the linked chain. The rightmost legal site in the whole explicit group is chosen.

**WHY:** This allows testing of alternative grouping hypotheses.

**THUS:** Relaxed mode is available for experimentation.

---

## F-074-Function-Word-Behavior

**Domain:** Algorithm / Merging

**WHAT:** Function words cannot be stress-realized independently. They must attach to adjacent content words. They merge forward when possible and backward when stranded.

**WHY:** Function words in stress-timed languages are cliticized, sharing a single stress unit with adjacent content words.

**THUS:** The algorithm treats function words specially, enforcing clitic-like prosodic dependence.

---

## F-075-Function-Word-Inventory

**Domain:** Algorithm / Merging

**WHAT:** Function words cannot be stress-realized independently. The inventory includes:

* Prepositions: ana, ina, ištu, itti, eli
* Negative particles: ul, ula, lā
* Determinative-relative pronoun: ša
* Coordinating conjunctions: u, ū, lū
* Independent personal pronouns: anāku, nīnu, atta, atti, attunu, attina, šū, šī, šunu, šina

**WHY:** These categories are standard in Assyriological descriptions (Huehnergard 2011, Buccellati 1996).

**THUS:** The algorithm treats function words specially, merging them forward when possible and backward when stranded.

---

## F-075b-Function-Word-Philological-Grounding

**Domain:** Article / Algorithm / Function Words

**WHAT:** The function-word classification in Section 8.5 of the article is now grounded in explicit philological citations from the NotebookLM source `notes/notebooklm/function-words.md`:

- **Prepositions** (*ana*, *ina*, *eli*, *adi*, *kīma*, *ištu*, *ultu*, *aššum*): Consistently described as non-metrical words that do not carry independent word stress and typically govern the genitive case (Huehnergard 2011; Caplice and Snell 2002).
- **Conjunction *u*** ('and'): Treated as an independent word that connects nouns or clauses but remains unaccented (Izre'el and Cohen 2004).
- **Enclitic *-ma***: Functions as a connective or focus particle; characteristically attracts word stress to the penultimate syllable of its host (Huehnergard 2011; Izre'el and Cohen 2004).
- **Determinative-relative *ša***: A grammatical operator that does not bear independent prosodic weight (Huehnergard 2011).
- **Preposition *eli***: Undergoes phonological lengthening of its final vowel before pronominal suffixes (Greenstein 1984).
- **Preposition *aššum***: Etymologically derived from *ana* + *šumum* ('for the name of'), confirming its status as a grammaticalized function word rather than a content word (Buccellati 1996).

**WHY:** The reviewer's remark "8. The function-word list (Section 8.5) needs philological justification" required explicit citations for each category. The new source provides these citations.

**THUS:** Section 8.5 now includes a paragraph with these citations, and the article's References have been updated with Caplice and Snell (2002) and Izre'el and Cohen (2004).

---

## F-076-Diphthong-Processing-Problem

**Domain:** Algorithm / Diphthongs

**WHAT:** Diphthongs create a problem for syllabification because adjacent vowels must be split for unambiguous parsing. The algorithm inserts a temporary hiatus consonant (glottal stop) during processing.

**WHY:** The syllabifier needs unambiguous syllable boundaries. Diphthongs blur these boundaries.

**THUS:** Diphthongs are resolved by inserting a temporary consonant, which is removed after processing.

---

## F-077-Diphthong-Processing-Solution

**Domain:** Algorithm / Diphthongs

**WHAT:** The solution is to insert a temporary hiatus consonant (glottal stop) during processing, then restore the diphthong after stress realization.

**WHY:** This allows the algorithm to process all syllables uniformly while preserving the original diphthongal spelling.

**THUS:** Diphthong restoration is the final step in the algorithm, applied after all accentuation decisions are made.

---

## F-078-Diphthong-Constraint

**Domain:** Algorithm / Diphthongs

**WHAT:** Diphthong restoration must preserve any `~` added by prosody realization. The tilde is attached to the restored diphthong.

**WHY:** The tilde marks the accentuation target. It must be preserved in the final output.

**THUS:** Diphthong restoration is a string operation that preserves prosodic markers.

---

## F-079-Diphthong-Restoration-Rules

**Domain:** Algorithm / Diphthongs

**WHAT:** Diphthong restoration rules specify how adjacent vowels are merged back into diphthongs after processing. The rules depend on the vowel sequence.

**WHY:** Different vowel sequences produce different diphthongs. The rules must be explicit.

**THUS:** The restoration rules are part of the algorithm specification.

---

## F-080-Diphthong-Same-Base-Rules

**Domain:** Algorithm / Diphthongs

**WHAT:** When two adjacent vowels share the same base (e.g., a-a, i-i), they are merged into a single long vowel with a tilde if accentuated.

**WHY:** Same-vowel sequences represent a single long vowel that was split for processing.

**THUS:** Same-base restoration produces a long vowel.

---

## F-081-Diphthong-Different-Base-Rules

**Domain:** Algorithm / Diphthongs

**WHAT:** When two adjacent vowels have different bases (e.g., a-i, u-a), they are restored as a diphthong with a tilde on the first vowel if accentuated.

**WHY:** Different-vowel sequences represent true diphthongs.

**THUS:** Different-base restoration produces a diphthong.

---

## F-082-Diphthong-Restoration-Ordering

**Domain:** Algorithm / Diphthongs

**WHAT:** Diphthong restoration is applied after all accentuation decisions are made, as the final step in the algorithm.

**WHY:** This ensures that the algorithm operates on unambiguous syllable boundaries during processing.

**THUS:** Restoration ordering is critical for correctness.

---

## F-083-Worked-Example-First-Line-Transliteration

**Domain:** Algorithm / Worked Example

**WHAT:** The first line of Enūma Eliš (Tablet I) in transliteration: "enūma eliš lā nabû šamāmū" (When on high the heavens had not been named).

**WHY:** This is the most famous line of Akkadian literature. It serves as a clear worked example. Note that the article (v10/v11) uses Erra lines 59–62 as its worked example instead. The Enūma Eliš example here is retained in the research notes as an additional illustration of the algorithm's behavior on a different text.

**THUS:** The worked example demonstrates the algorithm on a well-known text.

---

## F-084-Worked-Example-Syllabification

**Domain:** Algorithm / Worked Example

**WHAT:** The syllabified form: e.nū.ma e.liš lā na.bû ša.ma.mū.

**WHY:** Syllabification follows standard Assyriological rules (Huehnergard 2011).

**THUS:** The syllabified form is the input to the prosody realization algorithm.

---

## F-085-Worked-Example-First-Line-Enuma-Elish

**Domain:** Algorithm / Worked Example

**WHAT:** The prosody-realized output for the first line: e~.nū.ma e.liš lā na.bû ša.ma.mū~.

**WHY:** The algorithm adds one mora to "e" (onset gemination) and one mora to "mū" (vowel lengthening) to achieve even mora counts.

**THUS:** The worked example shows the algorithm in action on a real text.

---

## F-086-Worked-Example-Final-Output

**Domain:** Algorithm / Worked Example

**WHAT:** The final output with merge markers and accentuation: e~·nū·ma e·liš lā na·bû ša·ma·mū~.

**WHY:** The output preserves all lexical information while adding prosodic markers.

**THUS:** The final output is the pivot format for downstream processing.

---

## F-087-Worked-Example-All-Lines

**Domain:** Algorithm / Worked Example

**WHAT:** The complete worked example for all lines of the first passage shows consistent application of the algorithm.

**WHY:** A single line could be coincidental. Multiple lines demonstrate systematic behavior.

**THUS:** The full worked example provides stronger evidence for the algorithm's correctness.

---

## References

**Buccellati, Giorgio.** *A Structural Grammar of Babylonian*. Wiesbaden: Harrassowitz, 1996. (Buccellati 1996)

**Buccellati, Giorgio. "Akkadian."** In *The Semitic Languages*, edited by Robert Hetzron, 69–99. London: Routledge, 1997. (Buccellati 1997)

**Caplice, Richard, with Daniel Snell.** *Introduction to Akkadian*. 4th edition. Rome: Editrice Pontificio Istituto Biblico, 2002. (Caplice and Snell 2002)

**Greenstein, Edward L.** "The Phonology of Akkadian Syllable Structure." *Afroasiatic Linguistics* 9 (1): 1–18, 1984. (Greenstein 1984)

**Huehnergard, John.** *A Grammar of Akkadian*. 3rd edition. Winona Lake, IN: Eisenbrauns, 2011. (Huehnergard 2011)

**Izre'el, Shlomo, and Eran Cohen.** *Literary Old Babylonian*. Muenchen: LINCOM GmbH, 2004. (Izre'el and Cohen 2004)
