Based on the provided research papers and notes, the following table maps the empirical evidence to your model classes. To enhance the clarity of the model, classes have been grouped into major categories: **Obstruents**, **Sonorants**, **Vocalic Segments**, and **Pauses**.

### **Normalized Timing and Structural Model**

| Model Class | Major Class | Empirical Range (ms) | Ratio / Multiplier | Evidence Citation |
| :--- | :--- | :--- | :--- | :--- |
| **Onset Stop** | Obstruent | 75 – 120 ms | Baseline (1.0) | (Yungdo Yun 2022) |
| **Onset Affricate** | Obstruent | 85 ms | ~0.7x Stop (English) | (Stephen Grossberg no date) |
| **Onset Fricative** | Obstruent | 171 ms | ~1.4x Stop (English) | (Stephen Grossberg no date) |
| **Onset Nasal/Liquid** | Sonorant | 80 – 100 ms | ~0.8x Stop | (Beckman 1982 cited in Research Notes) |
| **Onset Glide** | Sonorant | 40 – 100 ms | Transition-dependent | (Stephen Grossberg no date) |
| **Coda (Singleton)** | Coda | 103 ms | ~0.9x Onset | (Yungdo Yun 2022) |
| **Geminate (Stop)** | Coda/Onset | 187 – 202 ms | **2.5x** Singleton | (J. Hankamer et al. no date) |
| **Short Vowel (Open)** | Short Vowel | 60 – 100 ms | 1 Mora (1µ) | (Tomoko Kozasa 2002); (Kosuke Sugai 2017) |
| **Short Vowel (Coda)**| Short Vowel | 60 – 100 ms | 1 Mora (1µ) | (Kosuke Sugai 2017) |
| **Long Vowel (Open)** | Long Vowel | 120 – 200 ms | **1.65x – 1.93x** Short | (Tomoko Kozasa 2002) |
| **Long Vowel (Coda)** | Long Vowel | 120 – 200 ms | 2 Morae (2µ) | (Tomoko Kozasa 2002); (Research Notes) |
| **Very Long Vowel** | Long Vowel | 200 – 240+ ms | **2.42x** Short | (Tomoko Kozasa 2002) |
| **Short Pause (,)** | Pause | 600 – 680 ms | Baseline Pause | (Mingji Lin 2021); (Harwintha Y. Anjarningsih 2024) |
| **Long Pause (.)** | Pause | 1200 – 1780 ms | **2.0x – 2.6x** Short | (Mingji Lin 2021); (Harwintha Y. Anjarningsih 2024) |
| **Compensation Coeff.**| Rhythmic | Inverse V/C | Tunable Parameter | (Kosuke Sugai 2017); (Research Notes) |

---

### **Analysis of Model Classes based on the Sources**

#### **1. Consonants: Manner and Position**
The sources confirm that manner of articulation is a primary determinant of duration. Onset **fricatives** (171 ms) are significantly longer than **stops** (75-120 ms) or **affricates** (85 ms) (Stephen Grossberg no date). While your model seeks distinct coda classes, the data suggests a **Positional Hierarchy**: durations are longest intervocalically (113 ms), followed by onsets (108 ms), and are shortest in the coda position (103 ms) (Yungdo Yun 2022).

#### **2. Multipliers: Singleton vs. Geminate**
The most stable multiplier in the research is for gemination. Across Turkish and Bengali, a geminate stop is consistently **2.5 times longer** than a singleton stop (J. Hankamer et al. no date). Perceptually, any stop closure exceeding **180 ms** is categorized as a geminate by listeners (J. Hankamer et al. no date).

#### **3. Vowels: Quantity and Perception**
The sources suggest that while the theoretical ratio of short (1µ) to long (2µ) vowels is 1:2, the physical realization varies by speech rate and accent:
*   **Accented Vowels:** Show a smaller ratio of **1.65x** to **1.77x** (Tomoko Kozasa 2002).
*   **Unaccented Vowels:** Speakers rely purely on duration, increasing the ratio to **1.93x** or even **2.42x** (Very Long) in slow speech (Tomoko Kozasa 2002).
*   **Categorical Threshold:** Japanese listeners perceive the "boundary" between 1 and 2 morae at approximately **250 ms** (Kosuke Sugai 2017).

#### **4. Pauses: Syntactic Tiering**
The sources reject a single fixed value for all punctuation. Instead, they support a two-tier system:
*   **Short Pauses (In-clause):** These average **680 ms** and are associate with hesitation or word-finding (Harwintha Y. Anjarningsih 2024).
*   **Long Pauses (Clause-boundary):** These average **1,780 ms** and are required for "thought organization" and structural planning (Harwintha Y. Anjarningsih 2024).
*   **Perceptual Minimum:** Any silence below **250 ms** is not perceived as a functional pause (Harwintha Y. Anjarningsih 2024).

#### **5. Compensation Coefficient**
The **compensation effect** justifies your model’s $p$ vs. $(1-p)$ logic. In Japanese, a longer onset consonant (like a stop or affricate) causes the following vowel within the mora to be **correspondingly shorter** to preserve the overall unit duration (Kosuke Sugai 2017). This mechanism should be a **tunable parameter** in your algorithm to prevent syllables with long onsets from becoming artificially elongated (Research Notes).