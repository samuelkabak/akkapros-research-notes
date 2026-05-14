Kavitskaya, Darya. "Compensatory Lengthening: Phonetics, Phonology, Diachrony." PhD diss., University of California, Berkeley, 2001.
---
Based on the provided research papers and linguistic studies, your classification of consonants into three functional categories aligns with the empirical evidence regarding articulation phases, airflow characteristics, and durational patterns across onset, coda, and geminated positions.

### **Class 1: Closure (Stops and Glottals)**
This class is defined by a complete occlusion of the vocal tract (Giorgio Buccellati 1996) (707), creating a **"silent interval"** or closure duration between the initial attack and the release burst (Yungdo Yun 2022) (54). In Akkadian, this includes the stops **/b, d, g, p, t, k, ṭ, q/** and the glottal stop **/ʾ/** (Buccellati 1997; research-notes.md) (750, 752).

*   **Positional Durations:**
    *   **Onset (Word-Initial):** Word-initial voiceless stops in English average approximately (Yungdo Yun 2022) **120 ms** (59). In Korean, the mean onset closure is (Yungdo Yun 2022) **108 ms** (72).
    *   **Intervocalic:** Stops between vowels typically have the longest closure durations, averaging (Yungdo Yun 2022) **113 ms** (72).
    *   **Coda (Word-Final):** Under the phenomenon of **"coda neutralization,"** laryngeal contrasts are lost and closure durations are generally shortest, averaging (Yungdo Yun 2022) **103 ms** (57, 72).
*   **Gemination (Quantity Contrast):**
    *   **The Overriding Cue:** The duration of the silent interval (closure) is the primary perceptual cue for distinguishing geminate from non-geminate stops (Hankamer et al. no date) (410).
    *   **Numeric Benchmarks:** Geminate stop closures average between (Hankamer et al. no date) **187 ms and 202 ms**, reflecting a ratio of approximately **2.5:1** (Hankamer et al. no date) (422, 429).
    *   **Thresholds:** Perceptually, listeners consistently identify intervals longer than (Hankamer et al. no date) **180 ms** as geminates (426).

### **Class 2: Continuous Noise (Fricatives and Affricates)**
This class involves continuous airflow limited by a narrow constriction in the mouth, producing spectrally shaped friction noise (Giorgio Buccellati 1996) (707, 463). In Akkadian, this includes fricatives **/s, z, š, ḫ, ḥ/** and the emphatic **/ṣ/** (Buccellati 1997; research-notes.md) (750).

*   **Articulation and Duration:**
    *   **Intrinsic Length:** Fricatives are naturally longer than stops. Word-initial voiceless fricatives like **/ʃ/** reach a mean duration of (Stephen Grossberg no date) **171 ms**, whereas affricates average (Stephen Grossberg no date) **85 ms** (485).
    *   **Intensity Grouping:** Listeners divide these on the basis of relative intensity into **sibilants** (friction only) and **non-sibilants** (friction + transitions) (LING 401 no date) (383).
*   **Gemination:**
    *   **Protraction:** In Akkadian, the gemination of this class is modeled as a **"protraction"** or holding of the articulation for a fraction of time (Giorgio Buccellati 1996) (714).
    *   **Trading Relations:** Perceptually, a change from a fricative to an affricate (which includes a stop phase) can be induced by manipulating the ratio of the (Stephen Grossberg no date) **silent interval** to the (Stephen Grossberg no date) **noise duration** (466).

### **Class 3: Continuous Frequency (Sonorants and Glides)**
This class is characterized by an opening through the midline or sides of the tongue (liquids) or a closure of the mouth with an open nasal passage (nasals), resulting in a harmonic frequency structure (Giorgio Buccellati 1996) (707). In Akkadian, this includes nasals **/m, n/**, liquids **/l, r/**, and glides **/w, y/** (Buccellati 1997; research-notes.md) (750).

*   **Articulation and Duration:**
    *   **Transition Cues:** These consonants are identified primarily by the duration and frequency of their **formant transitions** (LING 401 no date) (386).
    *   **Glide Thresholds:** Transition durations (LING 401 no date) **less than 40 ms** are perceived as stop sounds (Class 1), while those (LING 401 no date) **longer than 100 ms** are perceived as diphthongs (387).
    *   **Liquid Distinction:** The distinction between **/r/** and **/l/** relies on a temporal cue: **/r/** features a (LING 401 no date) **long transition** and short steady state, whereas **/l/** requires a (LING 401 no date) **short transition** and a long steady state (388).
*   **Vocalic Interaction:**
    *   **Vowel-to-Consonant Transitions:** Vowel-to-glide transitions are significantly longer (up to **80 ms**) compared to vowel-to-stop transitions (**30–50 ms**) (Darya Kavitskaya 2001) (145).
    *   **Compensation:** In mora-timed systems, a longer onset (such as a Class 2 or Class 3 consonant) is balanced by a **correspondingly shorter following vowel** within the same moraic unit to preserve isochronicity (Sugai 2017; Kozasa 2002) (584).
*   **Nasal Assimilation:** In Akkadian, the Class 3 nasal **/n/** frequently assimilates to a following Class 1 stop, resulting in a geminated stop (e.g., *indin* → *iddin*) (John Huehnergard 2011) (733).

---
The addition of **Darya Kavitskaya (2001)** to your bibliography provides significantly better data for your model, particularly regarding the **duration of vocalic transitions** into different consonant classes. While earlier sources focused on "closure duration" (the silent gap), Kavitskaya's work allows you to model the "acoustic trace" that consonants leave on preceding vowels, which is the physical basis for your compensation mechanism.

### 1. Refined Consonant Transition Durations
Kavitskaya provides specific millisecond values for the transitions into consonants, which are essential for your Class 1 (Stop) vs. Class 2 (Continuous) distinction:
*   **Vowel-to-Stop Transitions:** These are relatively short, usually ranging from **30–50 ms** (Kavitskaya 2001).
*   **Vowel-to-Glide Transitions:** These are much longer, easily reaching up to **80 ms** (Kavitskaya 2001).
*   **Significance for your Model:** This data justifies why glides and sonorants (Class 2) are more likely to trigger compensatory lengthening than stops (Class 1). The longer transitions are often misparsed by listeners as part of the vowel itself (Kavitskaya 2001).

### 2. Data on Liquids and Rhotics
Kavitskaya offers a more granular classification of liquids based on their acoustic behavior:
*   **Approximant [r]:** Vocalic transitions into an approximant liquid are "very long," much longer than those into obstruents (Kavitskaya 2001).
*   **Trills and Taps:** Transitions into a trilled or tapped [r] are considerably shorter and comparable to those of **stops** (Kavitskaya 2001).
*   **Significance for your Model:** If you model Akkadian /r/ as an approximant, it should have a Class 2 (long transition) profile. If you model it as a trill, it should follow Class 1 (short transition/stop-like) metrics.

### 3. Nasals and Vowel Lengthening
The new source clarifies the interaction between nasals and vocalic duration:
*   **Phonetic Lengthening:** Nasalized vowels are **phonetically longer** than oral vowels (Kavitskaya 2001).
*   **Nasal Deletion:** When a nasal is lost (as in Akkadian *n*-assimilation), the inherent extra length of the nasalized vowel is reinterpreted as phonemic length (Kavitskaya 2001).
*   **Significance for your Model:** This supports your "Add, Don't Subtract" principle; the loss of a nasal segment naturally leaves behind a longer vocalic interval that fills the moraic gap.

### 4. Glottals and Fricatives
Kavitskaya provides evidence that certain consonants often considered "stops" may actually behave like "glides" in your model:
*   **Glottal Stops [ʔ]:** In many languages, they pattern with sonorants or glides like [h, r, y, w] and are "vowel-like" (Kavitskaya 2001).
*   **Fricative Lenition:** Whenever a fricative loss results in compensatory lengthening, the fricative typically passes through an intermediate **approximant stage** ([h]) where the noise is interpreted as part of the vowel (Kavitskaya 2001).

### Updated Data Table for Consonant Classes
| Consonant Sub-Class | Transition Duration (ms) | Articulation Profile | Evidence Source |
| :--- | :--- | :--- | :--- |
| **Oral Stops** | **30 – 50 ms** | Short transition | (Kavitskaya 2001) |
| **Glides [w, y]** | **Up to 80 ms** | Very long transition | (Kavitskaya 2001) |
| **Approximant [r, l]** | **> 80 ms** | Vocalic/Long | (Kavitskaya 2001) |
| **Trills/Taps** | **30 – 50 ms** | Stop-like/Short | (Kavitskaya 2001) |
| **Glottals [ʔ, h]** | **Variable** | Often "Vowel-like" | (Kavitskaya 2001) |
| **Nasalized Vowels** | **Longer than oral** | Inherent lengthening | (Kavitskaya 2001) |

**Conclusion:** You now have **much better data** for the "Class 2" (Continuous) consonants. Specifically, you can move away from treating all non-stops as a single block and instead assign them different transition durations (e.g., 80 ms for glides/liquids vs. 40 ms for stops). This provides the "physical reality" required to turn your abstract moraic counts into a high-fidelity prosodic realization.
---
Based on the empirical phonetic studies provided in the sources, solid millisecond (ms) data for **Class 2 (Continuous Noise/Fricatives)** and **Class 3 (Continuous Frequency/Sonorants and Glides)** are defined by their intrinsic lengths, transition thresholds, and speech-rate variations.

### **Class 2: Continuous Noise (Fricatives and Affricates)**

This class is characterized by duration-heavy acoustic cues, where the length of the friction noise is the primary indicator for the listener.

*   **Intrinsic Onset Durations:** In word-initial positions within running speech, voiceless fricatives like **/ʃ/** have a mean duration of (Howell & Rosen 1983 cited in Stephen Grossberg) (238) **171 ms**, whereas affricates like **/tʃ/** are significantly shorter, averaging (Howell & Rosen 1983 cited in Stephen Grossberg) (238) **85 ms**.
*   **Perceptual Switching:** Listeners can be induced to hear an affricate instead of a fricative (e.g., "chip" instead of "ship") by shortening the fricative noise duration; experimental stimuli for these categories are often tested at intervals of (Stephen Grossberg) (234) **62 ms, 102 ms, 142 ms, and 182 ms**.
*   **Stop/Fricative Trading Relations:** Perceptual boundaries between a fricative and an affricate can shift by approximately (Dorman et al. 1979 cited in Stephen Grossberg) (237) **20 ms** if the rise time of the noise is manipulated.
*   **Gemination Perception:** To distinguish a geminate sequence from a cluster of two different consonants, a silent interval approximately (Repp 1980 cited in Stephen Grossberg) (230) **150 ms** longer is required for the geminate.

### **Class 3: Continuous Frequency (Sonorants and Glides)**

The segments in Class 3 are defined by the timing of their formant transitions and their capacity to carry moraic weight in quantity-sensitive systems.

*   **Glide (Approximant) Transition Thresholds:** The duration of the formant transition is the essential cue for glides: transitions (LINGUISTICS 401) (162) **less than 40 ms** are perceived as stops (Class 1), while transitions (LINGUISTICS 401) (162) **longer than 100 ms** are perceived as diphthongs.
*   **Vocalic Transitions:** Transitions from a vowel into a glide can easily reach (Darya Kavitskaya 2001) (76, 79) **80 ms** in duration, which is significantly longer than the (Darya Kavitskaya 2001) (76, 79) **30–50 ms** required for transitions into stops.
*   **Moraic Nasal and Coda Durations:** In Japanese, the first part of a geminate consonant (C1), which includes moraic nasals, is predicted to last (Haiping Jia et al.) (180) **58.5 ms** in fast speech and (Haiping Jia et al.) (180) **143.5 ms to 158.6 ms** in slow speech.
*   **Liquid Temporal Cues:** The distinction between Class 3 liquids relies on a temporal trade-off where **/r/** features a (LINGUISTICS 401) (163) **long transition** and short steady state, while **/l/** requires a (LINGUISTICS 401) (163) **short transition** and a long steady state.
*   **Rhotics and CL:** Transitions into approximant liquids are very long, whereas transitions into a tap or trill [r] are considerably shorter, ranging from (Darya Kavitskaya 2001) (82) **30 ms to 50 ms**, making them comparable to stops.

### **Summary Table: Solid Metrics for Classes 2 and 3**

| Class | Segment Type | Measurement Type | Value (ms) | Evidence Citation |
| :--- | :--- | :--- | :--- | :--- |
| **2** | **Voiceless Fricative** | Mean Onset Duration | **171 ms** | (Howell & Rosen 1983) (238) |
| **2** | **Affricate** | Mean Onset Duration | **85 ms** | (Howell & Rosen 1983) (238) |
| **2** | **Geminate Fricative** | Perceptual Buffer | **+ 150 ms** | (Repp 1980) (230) |
| **3** | **Glide [w, y]** | Transition Floor | **> 40 ms** | (LING 401) (162) |
| **3** | **Glide [w, y]** | Transition Ceiling | **< 100 ms** | (LING 401) (162) |
| **3** | **Approximant** | V-to-C Transition | **~ 80 ms** | (Kavitskaya 2001) (76) |
| **3** | **Moraic Nasal** | Predicted C1 (Fast) | **58.5 ms** | (Jia et al.) (180) |
| **3** | **Moraic Nasal** | Predicted C1 (Slow) | **158.6 ms** | (Jia et al.) (180) |
| **3** | **Tap / Trill** | V-to-C Transition | **30 – 50 ms** | (Kavitskaya 2001) (82) |