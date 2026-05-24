# Research Notes - Akkadian Prosody Project
## Part J: TTS Integration

---

## J-151-MBROLA-Overview

**Domain:** TTS / Speech Synthesis

**WHAT:** MBROLA (Multilingual BLAISE Articulatory Speech Synthesizer) is a diphone concatenation synthesizer. It requires a voice database of diphone samples, each with marked start, middle, and end sample numbers (Dutoit et al. 1996).

**WHY:** Creating a custom MBROLA voice for Akkadian would allow synthesized speech based on the prosody-realized texts. This would provide an audible test of the algorithm's perceptual plausibility.

**THUS:** The project includes tools for generating the necessary recording materials and segmentation data, laying the foundation for future voice development.

---

## J-152-Diphone-Recording-Pattern

**Domain:** TTS / Recording Script Design

**WHAT:** The key innovation enabling automatic segmentation is the rhythmic pattern: `_ V C C V C C V C _`. This pattern covers all diphone types in a single template:

* `_-V`: silence to vowel
* `V-C`: vowel to consonant (3 occurrences)
* `C-C`: consonant cluster (2 occurrences)
* `C-V`: consonant to vowel (2 occurrences)
* `C-_`: consonant to silence

**WHY:** With 5 consonants and 2 vowels, this pattern generates 9 diphones per word. A randomized script of 160 words ensures each CC pair appears 6-7 times, providing ample coverage.

**THUS:** The rhythmic pattern makes automatic segmentation possible by creating predictable acoustic events: silence at boundaries, high-amplitude vowel peaks, and characteristic low-amplitude consonant clusters.

---

## J-153-Diphone-Inventory-Calculation

**Domain:** TTS / Phonetics

**WHAT:** For a simplified inventory of 5 consonants (k, s, m, b, j) and 2 vowels (a, u), the complete diphone inventory includes:

* V-C: 10 diphones (2 vowels × 5 consonants)
* C-V: 10 diphones (5 consonants × 2 vowels)
* C-C: 25 diphones (5 × 5)
* V-V: 4 diphones (2 × 2)
* Boundaries ( _-C, C-_, _-V, V-_ ): 14 diphones

Total: 63 diphones

**WHY:** This manageable size demonstrates the feasibility of the approach. For the full Akkadian inventory, the numbers scale accordingly, but the same principles apply.

**THUS:** The diphone inventory calculation provides a clear target for recording coverage, ensuring that all necessary transitions are captured.

---

## J-154-Randomized-Recording-Script

**Domain:** TTS / Recording Script

**WHAT:** The recording script randomizes word order to prevent list fatigue. If every word started with the same pattern, articulation would become unnatural. Randomization ensures both vowels appear as V1, V2, V3, and all consonants appear in all positions.

**WHY:** Natural pronunciation requires variety. A randomized script produces more consistent, natural-sounding recordings across the 160-word corpus.

**THUS:** The script is organized into 8 blocks of 20 words each, with built-in breaks to manage vocal fatigue during recording sessions.

---

## J-155-Recording-Protocol

**Domain:** TTS / Recording

**WHAT:** The recording protocol specifies:

* Technical parameters: 16 kHz, 16-bit, mono, WAV format
* Speaking guidelines: natural pace, 1-second pause before and after each word
* Session structure: 4 sessions of 2 blocks each, with 5-minute breaks
* File naming: `diphone_recording_YYYYMMDD.wav`

**WHY:** Consistent recording conditions are essential for successful automatic segmentation. The 1-second silences provide clear word boundaries, and the technical specifications match MBROLA requirements.

**THUS:** The protocol ensures high-quality, consistent recordings suitable for downstream processing.

---

## J-156-Automatic-Segmentation-Strategy

**Domain:** TTS / Signal Processing

**WHAT:** The rhythmic pattern enables automatic segmentation through predictable acoustic events:

1. Silence detection identifies word boundaries
2. Vowel peaks (high amplitude, periodic structure) locate V1, V2, V3
3. Phoneme boundaries are placed midway between vowel peaks
4. Diphone segments are extracted based on the pattern positions

**WHY:** Manual segmentation of hundreds of diphones is tedious and error-prone. Automatic segmentation makes the process scalable and reproducible.

**THUS:** The segmentation strategy turns a challenging manual task into an automated process, making custom voice creation feasible for a single researcher.

---

## J-157-HTML-Recording-Assistant

**Domain:** TTS / User Interface

**WHAT:** The HTML recording assistant provides an interactive interface for guided recording sessions. It displays words one at a time, logs events, and ensures consistent naming and timing.

Key features:
* Keyboard controls: Space (start/stop chunk), Right Arrow (accept word), Left Arrow (repeat word)
* WAV naming: `<prefix>_NNN.wav` with zero-padded indices
* Event logging: timestamps, word indices, accepted counts, errors
* Copy Log function for segmentation manifest

**WHY:** A structured recording process reduces errors and produces the metadata needed for automatic segmentation. The assistant enforces the protocol and creates a complete audit trail.

**THUS:** The HTML assistant makes the recording process accessible to non-experts while ensuring the quality and consistency required for downstream processing.

---

## J-158-MBROLATOR-Workflow

**Domain:** TTS / Voice Building

**WHAT:** Once recordings and segmentation are complete, the MBROLATOR toolset builds the final MBROLA voice:

1. Prepare data: 16-bit, 16kHz diphone WAV files and segmentation (`.seg`) file
2. Compile MBROLATOR tools (AnaMBE, Resynthesis)
3. Generate parameter files (`.mbe` with FrameLength and FrameShift)
4. Run analysis (generate_make.pl and make)
5. Build database (database_build)
6. Test voice (mbrola test.pho test.wav)

**WHY:** MBROLATOR is the standard toolset for creating MBROLA voices. Following this workflow ensures compatibility with the MBROLA synthesizer.

**THUS:** The complete pipeline from phoneprep through segmentation to MBROLATOR provides a clear path from linguistic analysis to audible speech synthesis.

---

## J-159-Future-TTS-Integration

**Domain:** TTS / Roadmap

**WHAT:** The current implementation provides the foundation for future TTS integration. The IPA output from the printer can be fed to a speech synthesizer once a voice is built.

**WHY:** An audible Akkadian voice would allow perceptual testing of the prosody realization algorithm. Native speakers of related languages could evaluate whether the synthesized speech sounds natural.

**THUS:** TTS integration is a long-term goal that will provide external validation of the model and make Akkadian accessible to new audiences.

---

## References

**Dutoit, Thierry, et al.** "MBROLA: A High-Quality Speech Synthesizer Based on a Diphone Approach." *Proceedings of the 4th International Conference on Spoken Language Processing (ICSLP 1996)*, Philadelphia. (Dutoit et al. 1996)
