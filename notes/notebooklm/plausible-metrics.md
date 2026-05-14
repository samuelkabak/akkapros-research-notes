Based on the extensive collection of sources you have gathered, you have a **highly sufficient** bibliography to build valid, empirically grounded assumptions for mapping Akkadian's abstract moraic structure to physical duration in milliseconds.  
The provided sources allow you to move beyond "theoretical" morae by providing concrete acoustic benchmarks for three critical categories: **consonantal intervals**, **vocalic intervals**, and **silent pauses**.

### 1\. Building Plausible Consonant Durations (distC)

You have several sources that provide precise millisecond ranges for the "consonantal intervals" needed for $\\Delta$C and rPVI-C:

* **Singleton vs. Geminate Closure:** Hankamer et al. provide mean closure durations for non-geminate stops (\~70 ms) compared to geminate stops (\~187–200 ms) 1\. This gives you a data-driven ratio for your gemination operations.  
* **Positional Variation:** Yun provides data on how closure durations change based on word position (initial \~108 ms, intervocalic \~113 ms, final \~103 ms) 2\.  
* **Consonant Complexity:** White and Mattys explain that stress-timed languages (which your metrics suggest Akkadian resembles) allow for complex clusters like "strengths" (CCCVCCC), which naturally increase the variability of distC 3, 4\.

### 2\. Building Plausible Vowel Durations (distV)

Your bibliography contains specific experimental data on the durational distinction between short and long vowels in quantity-sensitive languages:

* **Moraic Thresholds:** Sugai establishes a clear "mental durational threshold" in Japanese listeners: vowels under \~210 ms are perceived as one mora, while those over \~330 ms are perceived as two morae, with a boundary around **250 ms** 5, 6\.  
* **Acoustic Ranges:** Production studies in the sources show short vowels ranging from **60–100 ms** and long vowels from **120–200 ms**, depending on speech rate 7-9.  
* **Compensation Effects:** Campbell and Sagisaka 10 and Port et al. 11 describe the **compensation effect**, where a longer vowel follows a shorter consonant within a mora to maintain isochronicity. This justifies your $p$ vs. $(1-p)$ model for syllables like "kab."

### 3\. Building Plausible Pause Durations (P)

The new sources on "pausology" provide the necessary thresholds to make your %V and speech-rate estimates comparable to living languages:

* **Pause Threshold:** There is a consensus in the sources that a silent interval must last **250 ms or more** to be categorized as a "pause" rather than a mere articulatory gap 12-14.  
* **Natural Proportion:** Goldman-Eisler 15 and Lin 16 establish that pauses typically occupy **30–40%** of total utterance time in natural speech, with 0.6 seconds being an "optimum" duration for punctuation-based pauses.

### 4\. Bridging Abstract Morae to Milliseconds

To convert your moraic counts into the millisecond values required for your Python script, you can use the **Information Rate Constancy** hypothesis found in Pellegrino et al. 17, 18\.

* By assuming a cross-linguistic average of **3–4 words per second**, and using your corpus-derived average of **2.99 syllables per word** 19, you can calculate a speculative but empirically anchored **mora duration** (estimated at \~29–49 ms per mora depending on rate) 20, 21\.

### Summary of Assumption Validity

Assumption Category,Validated By,Plausible Range/Value  
Short Vowel (1µ),"Sugai 6, Jia 22",60–100 ms  
Long Vowel (2µ),"Sugai 23, Jia 7",120–240 ms  
Singleton Consonant,"Hankamer 1, Yun 2",70–115 ms  
Geminate Consonant,Hankamer 1,180–200 ms  
Minimum Pause,"Anjarningsih 12, Lin 16",≥ 250 ms  
Total Pause Ratio,Goldman-Eisler 15,30–40% of total time  
**Conclusion:** You have **sufficient sources** to construct a "phonetically plausible" realization of Akkadian. While any absolute millisecond values for a dead language remain speculative 24, the **ratios** and **thresholds** provided by these sources ensure your model is consistent with the universal constraints of human speech processing.  
