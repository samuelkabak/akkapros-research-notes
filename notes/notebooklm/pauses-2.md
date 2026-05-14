To build a coherent quantitative and descriptive model for Akkadian pauses, the provided materials must be hierarchized into three functional categories: **threshold evidence** (to define the categorical boundary of silence), **baseline duration evidence** (to establish natural rhythmic pulses), and **upper-bound caution** (to avoid pathological or mechanical profiles).

### 1. Threshold Evidence: The Definition of Functional Silence
Threshold evidence establishes the minimum duration required for an interval of silence to be perceived as a functional pause rather than an articulatory gap or a normal breathing pattern.

*   **Categorical Consensus:** There is a general consensus in pausology that a silent interval must last **250 ms or more** to be categorized as a functional "pause" (Anjarningsih 2024). 
*   **The Micropause Boundary:** Gaps shorter than **200 ms** are often classified as "micropauses" and occur frequently in native speech without disrupting rhythm (Riggenbach 1991 cited in Bae 2015).
*   **Clinical Variations:** Some automated detection models for disordered speech use a lower threshold of **150 ms** to capture hesitations (Lee et al. 2024), while others in L2 research suggest thresholds as high as **400 ms** to distinguish between natural flow and disfluency (Coulange 2023).
*   **Model Application:** For your Akkadian model, the **250 ms** threshold serves as the categorical floor for punctuation-based pauses (Research Notes).

### 2. Baseline Duration Evidence: Functional and Rhythmic Ratios
Baseline evidence provides the "target" durations for different syntactic positions to ensure the synthesized speech sounds natural and carries appropriate structural information.

*   **The 600 ms "Optimum":** Experimental data on Mandarin and English speeches suggests that a fixed duration of **600 ms** at commas and periods yields the highest perceived "speech naturalness" (Lin 2021).
*   **Syntactic Tiering:** Spontaneous speech data from typically developing children shows a clear two-tier baseline: **680 ms** for in-clause (short) pauses and **1,780 ms** for clause-boundary (long) pauses (Anjarningsih 2024).
*   **Placement Priority:** Pause **placement** is a more salient indicator of advanced proficiency than duration; advanced speakers align pauses with clausal boundaries 92% of the time, even if their total pause frequency is higher than native speakers (Bae 2015).
*   **Model Application:** Your model should use the **Lin (2021)** optimum of **600 ms** as a short-pause baseline and the **Anjarningsih (2024)** clause-boundary data to justify a long-pause multiplier of approximately **2.5x** (Research Notes).

### 3. Upper-Bound Caution: Cognitive and Perceptual Limits
Upper-bound evidence identifies the point where pauses cease to be "structuring" and become "disruptive," leading to a decrease in comprehensibility or a perception of impairment.

*   **The Pathological Ceiling:** In children with suspected language impairment (sSLI), average pause durations reach **1,150 ms** in English and **1,900 ms** in Bahasa Indonesia, significantly slowing the information rate (Anjarningsih 2024).
*   **Excessive Delay:** Pauses exceeding **3,000 ms (3 seconds)** are categorized as "excessively long" and are indicative of severe word-finding or planning difficulties (Lee et al. 2024); (Riggenbach 1991 cited in Bae 2015).
*   **The 30-40% Rule:** Silence should not exceed **30% to 40%** of the total utterance time; going beyond this ratio risks inflating the perceived vocalic content (%V) and creating an unnatural rhythm (Goldman-Eisler 1968 cited in Research Notes).
*   **Listener Tolerance:** Perceptual effort increases and "likability" decreases as pauses before responses cross the **700 ms** mark (Kendrick and Torreira 2015 cited in Anjarningsih 2024).

### Summary Quantitative Model for Implementation
| Evidence Tier | Numeric Value / Range | Application in Model | Citation |
| :--- | :--- | :--- | :--- |
| **Threshold** | **250 ms** | Minimum value for any $P$ interval | (Anjarningsih 2024) |
| **Short Baseline** | **600 ms** | Intra-phrase/Comma baseline | (Lin 2021) |
| **Long Baseline** | **1,200 – 1,780 ms** | Clause-boundary/Period baseline | (Lin 2021); (Anjarningsih 2024) |
| **Pathology Limit** | **> 1,900 ms** | Do not exceed for "natural" realization | (Anjarningsih 2024) |
| **Global Ratio** | **30% – 40%** | Max silent share of total duration | (Goldman-Eisler 1968) |

By following this hierarchy, your Akkadian realization can maintain the **bimoraic alignment** required by your hypothesis (Research Notes) while staying within the **phonetic bounds** established by spontaneous and experimental speech studies.