The following justifications for the parameters in `metrics_timing_defaults.txt` are based on empirical benchmarks from the provided phonetic and psycholinguistic research.

### **1. Global Timing Constraints**
*   **Segmental Ceiling (Sugai 2017) (800) ms:** Japanese perceptual studies indicate that reaction times for stimuli longer than (Sugai 2017) (800) **310** ms cease to correlate with duration, suggesting the brain no longer processes the sound as a standard linguistic unit.
*   **Segmental Floor (Gao & Birkholz 2014) (669) ms:** In artificial speech compression, researchers set a modeling floor of (Gao & Birkholz 2014) (669) **20** ms to maintain phone intelligibility.
*   **CVC Reference (Cutanda et al. 2019) (7) ms:** This value is used as the baseline interval for rhythmic entrainment and isochrony deviation tests (Cutanda et al. 2019) (7).
*   **Basic Accentuation Lengthening (Zellner 1994) (593) ms:** Grounded in the Keller-Zellner algorithm for synthesis, which applies (Zellner 1994) (593) **50** ms adjustments to maintain rhythmic balance. Additionally, (Meynadier et al. 2019) (439) **50** ms is the specific extra processing window required by the brain to resolve voicing ambiguity.

### **2. Consonantal Parameters**
#### **Closure (Stops)**
*   **Onset (Gibson et al. 2013) (316) ms:** This matches the pooled mean for word-initial voiceless stops in Standard Spanish (Gibson et al. 2013) (316).
*   **Coda (Gibson et al. 2013) (316) ms:** Reflects word-final stop measurements which range from (Morley & Smith 2022) (94) **46** ms to (Gibson et al. 2013) (316) **81** ms.
*   **Geminate (Sugai 2017) (795) ms:** Derived from adding a standard moraic increase of roughly (Sugai 2017) (795) **120** ms to a singleton baseline of ~55 ms.
*   **Hiatus (Rathcke et al. 2023) (35) ms:** Approximates the set-up specific time delay of (Rathcke et al. 2023) (35) **34** ms often used in timing synchronization tasks.
*   **Perception limits (Min (Broselow et al. 1997) (683) / Max (Sugai 2017) (799)):** The **145** ms boundary reflects the high-end mean of a single mora (Broselow et al. 1997) (683). The **260** ms limit corresponds to the 50% identification threshold for Japanese mora boundaries (Sugai 2017) (799).

#### **Fricative**
*   **Onset (Meynadier et al. 2019) (444) ms:** Based on whispered speech where initial fricative boundaries are measured between (Meynadier et al. 2019) (444) **114** ms and **119** ms.
*   **Geminate (Sugai 2017) (795) ms:** While the threshold for geminate perception is (Sugai 2017) (795) **166** ms, the target value accounts for the inherent manner lengthening of fricatives compared to stops.
*   **Perception limits (Min (Meynadier et al. 2019) (452) / Max (Gibson et al. 2013) (314)):** The **163** ms minimum matches the perceptual boundary for identifying voiced final fricatives in whispered speech (Meynadier et al. 2019) (452). The **290** ms max matches the upper limit of final stop VOT in specific contexts (Gibson et al. 2013) (314).

#### **Sonorant**
*   **Onset (Gibson et al. 2013) (317) ms / Coda ms:** Grounded in word-initial liquid (/l/) measurements of (Gibson et al. 2013) (317) **89** ms.
*   **Geminate (Billington 2015) (705) ms:** Grounded in the absolute duration of geminate palatal glides in Lopit, which average (Billington 2015) (705) **167** ms but reach (Billington 2015) (705) **201** ms at one standard deviation.
*   **Vowel Transition (Naeser 1970) (231) ms:** Matches measured glottal transitions that average 18 ms but reach up to (Naeser 1970) (231) **22** ms for open vowels.
*   **Geminate Min (Broselow et al. 1997) (688) ms:** Corresponds to the perceptual threshold for nasals found at (Broselow et al. 1997) (688) **152** ms.

### **3. Vowel Parameters**
*   **Short (Meynadier et al. 2019) (444) ms:** Matches the median "short" response in whispered speech.
*   **Long (Morley & Smith 2022) (212) ms:** Matches the statistical intercept for vowel duration models of (Morley & Smith 2022) (212) **160.1** ms.
*   **Very Long (Sugai 2017) (799) ms:** Matches the Japanese threshold range for "long" identification at (Sugai 2017) (799) **250–270** ms.
*   **Short Min (Broselow et al. 1997) (683) ms:** Based on the minimum produced short vowels in Hindi measured at (Broselow et al. 1997) (683) **66** ms.
*   **Very Long Min (Best 1994) (264) ms:** Derived from the Perceptual Assimilation Model threshold starting at (Best 1994) (264) **233** ms.
*   **Elongation Max (Naeser 1970) (228) ms:** Based on the average duration of syllable nuclei before voiced stops, recorded at (Naeser 1970) (228) **.280** sec.

### **4. Pausal Parameters**
*   **Mini (Resync) ((Wan et al. 2024) (297) – (Sturm & Volin 2023) (504) ms):** This range is defined by the acoustic detection floor (Wan et al. 2024) (297) **100** ms and the boundary for "intended" pauses (Sturm & Volin 2023) (504) **200** ms.
*   **Short ((Zellner 1994) (744) – (Rathcke et al. 2023) (381) ms):** Grounded in the mean silent pause duration in interviews of (Zellner 1994) (744) **520** ms and paced rhythms at 1.5 Hz (Rathcke et al. 2023) (381) **671** ms.
*   **Long ((Sturm & Volin 2023) (507)  – (Zellner 1994) (744)  ms):** The lower bound matches the mean for major unit pauses in poetry (Sturm & Volin 2023) (507) **1144** ms, while the upper tail accounts for extreme planning pauses reaching (Zellner 1994) (744) **1320** ms or higher.