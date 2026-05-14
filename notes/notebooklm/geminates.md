Based on the empirical studies provided in the sources, while the most robust and precisely quantified data for gemination exists for **stops**, there is significant data regarding the durational behavior of **nasals**, **fricatives**, and **affricates** that can be used to refine your model.

### 1. Empirical Data for Geminate Nasals
There is specific cross-linguistic data comparing singleton and geminate nasals.
*   **Duration Ratios:** The ratio of a geminate nasal **/n:/** to a singleton **/n/** varies by language; it is notably greater in Finnish than in Japanese (Aoyama 2001 cited in University of Hawai'i Library) (523).
*   **Fortis vs. Lenis Nasals:** In Ghotuo nasals, research into the length-related opposition (fortis vs. lenis) found a **20 ms** displacement in perceptual crossover points, indicating that listeners are sensitive to subtle durational shifts in nasal consonants (Elugbe & Hombert 1975 cited in Hankamer et al.) (280).

### 2. Empirical Data for Fricatives and Affricates
The sources provide "intrinsic" durations for these classes in singleton form, which serve as the baseline for modeling their geminate (held) counterparts.
*   **Intrinsic Lengths:** Word-initial voiceless fricatives like **/ʃ/** have a mean duration of **171 ms**, while affricates like **/tʃ/** are significantly shorter at **85 ms** (Howell & Rosen 1983 cited in Grossberg) (405). 
*   **Akkadian Sibilant Realization:** In Literary Old Babylonian, sibilants (*s, z, s*) may have been realized as either affricates or fricatives; however, the script often represents "doubled" sibilants, which scholars interpret as a "holding of the articulation for a fraction of time" rather than a repetition of the sound (Izre'el & Cohen 2004) (33, 72).
*   **Trading Relations:** Perceptually, listeners can be induced to hear an affricate (like "chip") instead of a stop+fricative sequence ("great ship") by manipulating the "noise duration" and the preceding "silent interval" (Repp et al. 1978 cited in Grossberg) (380-381).

### 3. Empirical Data for Liquids and Approximants
Liquids and glides are defined more by their **transition durations** than by steady-state closure.
*   **Glides:** Transition durations of less than **40 ms** are perceived as stops (like **/b/** or **/d/**), while transitions longer than **100 ms** are perceived as diphthongs (LING 401) (231). 
*   **Liquids:** The distinction between **/l/** and **/r/** relies on a temporal cue: **/r/** has a **long transition** and short steady state, whereas **/l/** has a **short transition** and long steady state (LING 401) (232).

### Summary Table for Modeling Non-Stop Classes
Using the logic from the **Bimoraic Hypothesis** (Note 053) and the **Plausible Duration Approach** (Note 176), you can extrapolate the following multipliers for your model:

| Consonant Class | Singleton Baseline (ms) | Geminate Ratio / Evidence | Citation |
| :--- | :--- | :--- | :--- |
| **Stops** | **~70 ms** | **2.5x** (187–202 ms) | (Hankamer et al.) (290) |
| **Nasals** | **80–100 ms** | **Language-Specific** (Finnish > JP) | (Aoyama 2001) (523) |
| **Fricatives** | **171 ms** | **Held Duration** (Protracting) | (Howell & Rosen 1983) (405) |
| **Affricates** | **85 ms** | **Trading Relation** (Noise/Silence) | (Grossberg) (380) |
| **Glides** | **40–100 ms** | **Transition-based** | (LING 401) (231) |

**Conclusion for your model:** While you have the firm **2.5x multiplier** for stops (Hankamer et al.) (290), for other classes, the sources suggest you should model gemination as **"protracted articulation"** (Buccellati 1996) (72). For **nasals**, a multiplier similar to stops is empirically supported, while for **fricatives and affricates**, the baseline duration is already so high (**171 ms**) that a 2.5x multiplier might exceed human articulatory limits; a smaller multiplier or a fixed "moraic add-on" (approx. **+100-120 ms**) based on the **Sugai (2017)** moraic threshold would be more phonetically plausible (Sugai 2017) (234, 236).