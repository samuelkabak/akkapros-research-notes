Based on the provided research papers and the quantitative framework established in your methodology, here is a functional description of the primary rhythm metrics used for linguistic timing analysis.

### **1. %V (%): Proportion of Vocalic Intervals**
*   **Definition:** This metric is the percentage of the total utterance duration made up of vocalic intervals, which are defined as sequences of one or more contiguous vowels (Ramus et al. 1999) (442, 805, 818).
*   **Functional Role:** It measures the relative share of vocalic material in the speech stream and is a key discriminator of rhythm classes (research-notes.md) (723). **Stress-timed languages** (e.g., English) typically have a lower %V (approximately 38-40%) because of frequent vowel reduction, while **syllable-timed languages** (e.g., French) show higher values (approximately 45-48%) (White and Mattys 2007) (381, 808).

### **2. ΔC (ms): Standard Deviation of Consonantal Intervals**
*   **Definition:** ΔC represents the standard deviation of the durations of consonantal intervals (sequences of one or more contiguous consonants) (Ramus et al. 1999) (442, 805, 819).
*   **Functional Role:** It quantifies consonantal variability, which is driven by phonotactic complexity (research-notes.md) (724, 725). Languages with complex syllable structures (like English "strengths" [CCCVCCC]) have a high ΔC, whereas languages with simpler structures (like Japanese or Spanish) have low ΔC (Ramus et al. 1999; White and Mattys 2007) (366, 808).

### **3. ΔV (ms): Standard Deviation of Vocalic Intervals**
*   **Definition:** This is the standard deviation of the durations of vocalic intervals within an utterance (Ramus et al. 1999) (367, 442, 819).
*   **Functional Role:** It captures the durational consequences of **vowel reduction** and lexical length contrasts (research-notes.md) (448, 807). Stress-timed languages typically have a higher ΔV because they feature a large contrast between full, stressed vowels and reduced, unstressed vowels (Ramus et al. 1999; White and Mattys 2007) (366, 53).

### **4. VarcoC: Rate-Normalized Consonantal Variability**
*   **Definition:** VarcoC is calculated as the standard deviation of consonantal interval duration (ΔC) divided by the mean consonantal interval duration, multiplied by 100 (Dellwo 2006) (368, 726, 819).
*   **Functional Role:** Because raw ΔC is inversely related to speech rate, VarcoC provides a **rate-normalized percentage** that allows for more robust cross-linguistic and cross-speaker comparisons (research-notes.md) (368, 726). In your model, a VarcoC of 69.09 places Akkadian at the lower end of the **stress-timed range**, overlapping with Dutch (research-notes.md) (732, 739).

### **5. VarcoV: Rate-Normalized Vocalic Variability**
*   **Definition:** VarcoV is the standard deviation of vocalic interval duration (ΔV) divided by the mean vocalic interval duration, multiplied by 100 (White and Mattys 2007) (377, 819).
*   **Functional Role:** It provides a rate-normalized measure of vocalic variability and was found to be the **strongest predictor** for distinguishing native from non-native accents in perceptual studies (White and Mattys 2007) (364, 400).

### **6. nPVI-V: Normalized Pairwise Variability Index (Vocalic)**
*   **Definition:** nPVI-V measures the mean of the absolute differences between successive vocalic intervals, normalized by the local mean of each pair and multiplied by 100 (Low, Grabe and Nolan 2000) (369, 57, 819).
*   **Functional Role:** Unlike the standard deviation metrics (Δ), the nPVI-V focuses on **sequential contrast**, making it highly sensitive to the temporal order of speech and the alternation between stressed and reduced vowels (Patel and Daniele 2003) (61, 709). Prototypical stress-timed languages like British English have high nPVI-V scores (mean ≈ 67), while syllable-timed languages like French have lower scores (mean ≈ 49) (Patel and Daniele 2003) (60, 63).