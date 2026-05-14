Based on the research papers and notes provided, the **compensation mechanism** is a phonetic phenomenon where the durations of adjacent speech segments adjust inversely to maintain the stability of a rhythmic unit, such as a **mora**. This mechanism ensures that even when internal segments vary, the overall timing of the unit remains relatively constant for the listener.

### 1\. The Compensation Mechanism: Core Definition

The sources identify two primary levels of compensation:

* **Intra-moraic Compensation:** This occurs within a single mora, typically between an onset consonant and the following vowel. A longer onset consonant is balanced by a shorter following vowel, and vice versa (Kosuke Sugai 2017\) 1\.  
* **Inter-moraic (Phrasal) Compensation:** This occurs across adjacent morae or syllables. Individual segment durations are adjusted so that the total duration of a word or phrase is close to what is predicted by the number of morae it contains (Port et al. 1987 cited in Kosuke Sugai 2017\) 1, 2\.

### 2\. Empirical Parameters and Data

The bibliography provides specific numeric ranges to define how these trade-offs are realized in quantity-sensitive languages:

* **Moraic Durations:** In Japanese carrier sentences, the physical duration of a single mora ranges from **104.2 ms to 143.5 ms** (Han 1994 cited in Kosuke Sugai 2017\) 1\. Adding a single mora to a word typically increases the total word duration by approximately **120 ms** (Han 1962 cited in Kosuke Sugai 2017\) 1\.  
* **Vowel Ratios:** While theoretically a long vowel is two morae ($1:2$), empirical data shows the ratio is often lower. In Japanese accented vowels, the short-to-long ratio is **1.65:1** in fast speech and **1.77:1** in slow speech (Tomoko Kozasa 2004\) 3, 4\.  
* **Consonant Closure and Perception:** The "silent interval" of a stop consonant is the dominant cue for length. Singletons average **\~70 ms**, while geminates average **\~187–202 ms**, reflecting a ratio of approximately **1:2.5** (J. Hankamer et al. no date) 5\. Perceptually, listeners consistently identify intervals shorter than **100 ms** as singletons and those longer than **180 ms** as geminates (J. Hankamer et al. no date) 6\.  
* **The Onset Effect:** The presence of an onset consonant (like the /t/ in /tan/) slightly **lengthens the acceptable duration** of a single mora compared to a vowel-only mora (Kosuke Sugai 2017\) 7\.

### 3\. Specificities of the Mechanism

The "effectiveness" of compensation is influenced by phonological and environmental factors:

* **Pitch-Accent Interaction:** When pitch-accent (F0 fall) is available, listeners rely more on the pitch cue to determine length; however, in unaccented vowels where pitch cues are absent, speakers **magnify the durational distinction** (e.g., up to a **2.42:1** ratio in slow speech) to ensure the contrast is perceived (Tomoko Kozasa 2004\) 8, 9\.  
* **Moraic Threshold:** There exists a mental "durational threshold" for perceiving a second mora. For Japanese listeners, this boundary lies between **250 ms and 270 ms** (Kosuke Sugai 2017\) 10, 11\.  
* **Coda Neutralization:** Positional factors also constrain duration. For example, stop durations are generally shortest in the **word-final (coda) position** (**103 ms**) compared to the intervocalic position (**113 ms**) (Yungdo Yun 2022\) 12, 13\.

### 4\. Implementation in Modeling (Akkadian Context)

In your research notes, the compensation effect is used as a **methodological bridge** between abstract grammar and acoustic reality:

* **Heuristic Timing:** The goal is to justify why a syllable with a longer onset (like an affricate or stop) does not necessarily make the overall syllable proportionally longer, as the vowel "absorbs" the durational difference (Research Notes 187\) 14\.  
* **Tunable Range:** Rather than an absolute rule, compensation should be implemented as a **tunable parameter** in the realization algorithm to test if the resulting rhythm profile (VarcoC, %V) remains stable across different settings (Research Notes 188\) 15, 16\.

