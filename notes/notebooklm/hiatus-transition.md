The phonetic duration of a **hiatus** (a light glottal transition or stop between vowels) and a **vowel transition** (the intrinsic 'light glide' movement in a diphthong) are extremely brief temporal events that are typically much shorter than full segmental phonemes.

### **Duration of Hiatus (Glottal Transition)**
Based on acoustic analysis of English syllables, the "glottal transition period"—a phase of zero amplitude that can occur before a vowel or after a fricative—serves as the phonetic realization of the hiatus you described.

*   **Average Duration:** The overall average duration for these glottal transitions is (Margaret A. Naeser 1970) **(231) 18** ms (or 0.018 sec).
*   **Voicing Variation:** These transitions vary slightly based on the voicing of the surrounding environment, averaging (Margaret A. Naeser 1970) **(231) 16** ms in voiceless contexts and (Margaret A. Naeser 1970) **(231) 19** ms in voiced contexts.
*   **Maximum Duration:** The longest average duration for a hiatus transition was recorded reaching (Margaret A. Naeser 1970) **(231) 22** ms, specifically occurring after the open vowel /æ/ before voiced fricatives.
*   **Occurrence Frequency:** These light transitions are not universal; they were observed in approximately (Margaret A. Naeser 1970) **(231) 37**% of the measured fricative-vowel environments.

### **Duration of Vowel Transitions (Intrinsic Glide)**
The "vowel transition" or "intrinsic glide duration" represents the brief period of articulatory movement from an onset into the steady state of the vowel nucleus.

*   **Intrinsic Duration:** In Mandarin Chinese, the transition portion of a vocoid—the light glide element—is calculated to be approximately (Yang Liu 2022) **(468, 469) 11** ms.
*   **Comparative Vocoid Length:** This transition is a component of the total vocoid duration (glide + vowel), which averages (Yang Liu 2022) **(468, 469) 152.08** ms, compared to a plain vowel average of (Yang Liu 2022) **(468, 469) 141.33** ms.
*   **Manner Effects:** The duration of these transitions is highly dependent on the following segment; transitions from a vowel into a liquid are described as (Rebeka Campos-Astorkiza 2005) **(16) relatively long**, while transitions into trills and taps are (Rebeka Campos-Astorkiza 2005) **(16) short**.
*   **Perceptual Merging:** Because these transitions are so short, sequences like [ji] and [i] are often (Yang Liu 2022) **(403) not perceptually differentiated** by native speakers.

### **Comparison: Hiatus vs. Light Glide Transitions**
The empirical data indicates that a glottal hiatus is generally "stronger" (longer) than a light vowel transition:
*   A **hiatus** (glottal transition) of (Margaret A. Naeser 1970) **(231) 18** ms is roughly 1.6 times the duration of a **vowel transition** (intrinsic glide) of (Yang Liu 2022) **(468, 469) 11** ms.
*   Both are significantly "weaker" than full segmental glides; for comparison, a singleton palatal glide /j/ produced in isolation averages (Rosey Billington 2015) **(691) 93** ms, which is (Rosey Billington 2015; Yang Liu 2022) **(691, 468) eight** to **nine** times longer than the intrinsic transition.

### **Project-Facing Comment**
For the current timing model, these values seem to support a narrower interpretation than the earlier midpoint-style defaults. If the active parameters are meant to describe the **unstressed realization itself**, then a compact working pair around **`closure.special_realization.hiatus = 18 ms`** and **`sonorant.special_realization.vowel_transition = 11 ms`** is easier to defend than the earlier **`12 / 52 ms`** split. The earlier higher value for `vowel_transition` could still be retained as an abstract proxy between intrinsic transition and lexical glide duration, but that would be a different modeling claim from saying that the ordinary transition is realized as a light glide.

The same distinction matters for stress. Under stress, a hiatus probably should not remain a merely light transition that is stretched upward from its unstressed value; it is better treated as a fully featured geminated glottal stop. Likewise, a stressed vowel-transition case is better treated as a fully featured geminated glide rather than as a scaled-up light glide. In other words, the `special_realization` values should govern the weak, unstressed realization, while stressed cases should be handed off to the relevant geminate rows of the broader consonant timing model.

The present YAML placement also seems methodologically clearer than a free-standing Transition block. `hiatus` now sits with closures because its stressed realization is closure-like, and `vowel_transition` sits with sonorants because its stressed realization is glide-like. The `special_realization` label matters because it keeps that affinity visible without pretending that these markers are ordinary lexical members of the closure or sonorant classes.
*** Add File: c:\Users\samue\YandexDisk\GED\08 CONLANG\AKKADIAN\Akkadian Prosody Project\git-local\akkapros-research-notes\notes\prep\special-realization-placement.md
# Special Realization Placement

This note records the current reason for storing `hiatus` and `vowel_transition` inside class-specific `special_realization` blocks rather than as free-standing transition parameters.

## Current YAML Shape

The active timing model now places the two values here:

- `closure.special_realization.hiatus = 18 ms`
- `sonorant.special_realization.vowel_transition = 11 ms`

Both values remain part of the timing model, but they are no longer exposed as top-level consonant entries.

## Why This Placement Is Clearer

The main issue is not only duration, but control logic. In the current interpretation, both values describe **unstressed light realizations**.

- `hiatus` is realized as a light glottal stop in weak position
- `vowel_transition` is realized as a light glide in weak position

When stress forces fuller realization, the model should not simply lengthen those weak values. Instead, each case should hand off to the relevant class-level geminate logic.

- stressed `hiatus` should behave like a geminated glottal stop and therefore belongs with the closure row
- stressed `vowel_transition` should behave like a geminated glide and therefore belongs with the sonorant row

This makes the placement under closure and sonorant more transparent than a single free-standing Transition block.

## Why `special_realization`

The label should remain neutral. These values are not ordinary onset, coda, or geminate members of the lexical classes themselves. They are exceptional realization parameters associated with those classes.

`special_realization` is preferable to labels such as `transitions` or `weak_forms` for three reasons.

- It does not imply that both values form one homogeneous phonological transition class.
- It does not imply that the stressed realization is merely a stronger version of the weak one.
- It keeps the YAML readable while leaving the classificatory claim modest.

## Methodological Consequence

The practical consequence is that the YAML now expresses two distinct claims at once.

- The weak unstressed realization is short and class-adjacent.
- The stressed realization is governed by the fuller closure or sonorant timing row, not by direct scaling of the weak value.

That distinction matters because it prevents the timing model from treating `18 ms` or `11 ms` as if they were ordinary segmental anchors across all prosodic environments.