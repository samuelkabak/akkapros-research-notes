Based on the provided sources, there is specific information regarding measurement discrepancies, technical resolution limits, and inter-transcriber reliability that define the "error bars" for duration data.

### **Inter-Transcriber and Segmentation Errors**
The most direct data on measurement error comes from studies assessing how much two different human annotators vary when marking the same sound boundary. 

*   **Buckeye Corpus Reliability:** For a unanimously transcribed subset of the Buckeye Corpus, segmentation boundaries for stops and fricatives differed by an average of (Morley and Smith 2022) **(16)** ms. 
*   **Segment Length Correlation:** Transcription consistency is lower for shorter sounds. For phones longer than average, agreement was found within (Morley and Smith 2022) **(20)**% of the segment length for (Morley and Smith 2022) **(73)**% of tokens. However, for shorter phones, this agreement level dropped to (Morley and Smith 2022) **(50)**%.
*   **Internal Verification Study:** In a specific verification check of CVC tokens, absolute vowel measurements differed by an average of (Morley and Smith 2022) **(12)** ms, while total consonant durations differed by an average of (Morley and Smith 2022) **(21)** ms.
*   **Effect of Discrepancies:** When comparing voiced vs. voiceless pairs, discrepancies in the measured "voicing effect" (the difference between segments) were (Morley and Smith 2022) **(13)** ms for vowels and (Morley and Smith 2022) **(30)** ms for total consonant duration. 
*   **Net Bias:** Because measurement errors often fluctuate (some longer, some shorter), the actual net effect on the data in that sample was smaller: (Morley and Smith 2022) **(6)** ms shorter for vowels and (Morley and Smith 2022) **(12)** ms shorter for total consonant duration.

### **Technical Resolution and Processing Limits**
The digital processing methods used to measure speech also impose a "resolution floor" on how precise a measurement can be.

*   **Frame Rates:** In objective acoustic modeling, cepstral coefficients are often calculated at a frame rate of (Hozjan and Kacic 2002) **(2.5)** ms.
*   **F0 Estimation:** Pitch estimation is typically calculated once every (Hozjan and Kacic 2002) **(10)** ms.
*   **Energy Windows:** RMS energy is often calculated in windows (Hozjan and Kacic 2002) **(10)** ms long at a frame rate of (Hozjan and Kacic 2002) **(5)** ms.
*   **Systematic Setup Delay:** In sensorimotor studies, setup-specific time delays (e.g., between a tap and a recorded sound) can be as high as (Rossi et al. 2023) **(34)** ms and must be subtracted to ensure accuracy.

### **Perceptual Error and Thresholds**
Perceptual studies provide a sense of the "biological" error bar—the point at which a human brain can no longer reliably distinguish two durations.

*   **Perceptual Threshold Variance:** In Japanese, the 50% threshold for a second mora boundary was found to have a standard deviation of (Sugai 2017) **(6.9)** ms among a group of participants.
*   **Manipulation Step Size:** Perception experiments often use a digital step size of (Sugai 2017) **(20)** ms to distinguish categories, suggesting that smaller differences may be negligible for phonological classification.

### **Conclusion for your Example**
If you see a liquid onset measured at **70 ms**, the empirical data suggests an error range closer to **+/- 12 to 16 ms** for manual human transcription (Morley and Smith 2022) **(16)** ms, rather than a precision of +/- 3 or 5 ms. However, the technical resolution of the equipment itself is much finer, often at (Hozjan and Kacic 2002) **(2.5)** ms.