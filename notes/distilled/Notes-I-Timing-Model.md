# Research Notes - Akkadian Prosody Project
## Part I: Timing Model, Drift, Configuration

---

## I-142-Phonetizer-Timing-Model

**Domain:** Implementation / Timing Model

**WHAT:** The phonetizer timing model is a stability-first system organized around a heavy-syllable reference (`cvc_reference`) and a bounded running drift. Ordinary segment anchors remain the default realizations; small timing mismatch is carried forward in a bounded running drift; short pauses serve as strict reset points; long pauses provide wider discharge space.

**WHY:** The timing model operates through a three-pass solver:
1. **Phase 1** builds row structure from the `_tilde.txt` input, classifying each symbol as segment, accent mark, separator, or pause.
2. **Phase 2** realizes durations using the timing model: consonant anchors (closure, fricative, sonorant), vowel anchors (short, long, very long), pause bands (short, long, resync), and drift management.
3. **Phase 3** assigns intonation tokens.

The active synchronization basis is stream-aware:
* Accentuated stream with `mora_mode = bi`: `cvc_reference`
* Accentuated stream with `mora_mode = mono`: `0.5 × cvc_reference`
* Original stream (`_ophone.txt`): `0.5 × cvc_reference`

Nominal non-accentuated targets:
* `CV = 0.5 × cvc_reference`
* `CVC = 1.0 × cvc_reference`
* `CVV = 1.0 × cvc_reference`
* `CVVC = 1.5 × cvc_reference`

Accentuated shapes add exactly `0.5 × cvc_reference` beyond the matching non-accentuated target.

**THUS:** The phonetizer timing model is the computational heart of the toolkit. It transforms abstract prosodic decisions into concrete millisecond durations, enabling quantitative rhythm analysis through metricalc.

---

## I-143-Phonetizer-Drift-Mechanism

**Domain:** Implementation / Timing Model / Drift

**WHAT:** The phonetizer carries one signed running value, `drift_cursor`, that tracks cumulative timing mismatch. Negative drift means the stream is ahead of the beat; positive drift means it is behind. Synchronization is modulo the active synchronization basis.

**WHY:** Drift management is essential for realistic timing. Rather than forcing every syllable to match an exact target, the model allows bounded mismatch to accumulate and discharges it at prosodic boundaries.

Key behaviors:
* **Drift folding**: After a completed prosodic unit (`F` boundary), drift is folded to the nearest equivalent beat branch modulo the synchronization basis.
* **Long-vowel recovery**: Non-accented long vowels may be adjusted within `long_min .. very_long_min - 1` when drift exceeds `drift_tolerance`.
* **Accent-bearing recovery**: `CVV:` and `CVV:C` syllables apply accentuation first, then post-accent cleanup may run without the ordinary tolerance gate.
* **Resync pauses**: At eligible `F` boundaries, the solver may insert one non-punctuation resync pause (100-200 ms default band) to discharge drift exactly.
* **Short pauses**: Chosen from the short-pause band (520-680 ms) to bring drift as close to zero as the band allows.
* **Long pauses**: Chosen from the long-pause band (1100-1780 ms); usually discharge drift fully.

The drift tolerance parameter (`drift_tolerance: 19` ms) defines how much cumulative timing mismatch is tolerated before forced resynchronization. It is subject to the global duration scale.

**THUS:** The drift mechanism is what makes the timing model realistic. It allows the system to maintain overall rhythmic coherence without forcing every individual syllable to match an exact target.

---

## I-144-Confwriter-CLI

**Domain:** Implementation / CLI / Configuration

**WHAT:** `confwriter.py` is the schema-driven editor for the package-wide YAML config file. It works with full YAML-path keys and a small set of operations: `--set`, `--get`, `--list`, `--unset`, `--set-default`, and `--verify`.

**WHY:** The config file controls recurring options for all pipeline stages. Confwriter provides a programmatic interface for creating, updating, and verifying config files without manual YAML editing.

Key operations:
* `--set KEY=VALUE`: set one key (repeatable)
* `--get KEY`: print one effective value
* `--list [SUBSTRING]`: print schema-backed key inventory
* `--unset KEY`: write null for one key
* `--set-default KEY`: write schema default explicitly
* `--verify`: run shared phonetize semantic verification

The `--verify` operation runs the same shared semantic verification layer used by standalone phonetizer preflight, checking enum-like process-policy values, positive integer timing leaves, ordering constraints, and pause-band compatibility.

**THUS:** Confwriter is the recommended way to manage configuration files. It validates both key paths and values against the canonical schema before any file is modified.

---

## I-145-Configuration-Structure

**Domain:** Implementation / Configuration

**WHAT:** The package-wide YAML configuration has a hierarchical structure with top-level sections: `common`, `atfparse`, `syllabify`, `prosody`, `phonetize`, `metrics`, and `print`. Override precedence is: `-t/--option` path override > dedicated CLI flag > YAML config value > built-in default.

**WHY:** The grouped config structure allows users to specify all pipeline options in one file and run with `--conf FILE`. Each stage section owns its relevant options:

* `common.run`: shared output naming (prefix, outdir, quiet, log)
* `prosody.process`: style, mora_mode, relax_last
* `phonetize.process`: timing_model (durations, geminate_policy, accentuation_distribution_policy, drift_tolerance), intonation (f0, stress, question, statement, exclamation, continuation), allow_experimental
* `metrics.run`: json, table
* `print.run`: acute, bold, ipa, xar, ipa_proto_semitic

The `phonetize` section is the largest and most important, owning the timing model parameters that control the phonetic realization: `durations.scale`, `durations.segmental_ceiling`, `durations.segmental_floor`, `durations.cvc_reference`, `durations.consonants.*`, `durations.vowels.*`, `durations.pauses.*`.

**THUS:** The configuration structure mirrors the pipeline architecture. Each stage owns its parameters, and the grouped config file provides a single point of control for reproducible runs.

---

## I-146-Default-YAML-Parameters

**Domain:** Implementation / Configuration / Timing Model

**WHAT:** The default YAML (`configs/default.yaml`) defines the complete timing model parameterization. Key parameters include:

**Global:**
* `durations.scale: 1.0` — global multiplier for all numeric duration leaves
* `durations.segmental_ceiling: 310` — validation ceiling for consonant gemination_max and vowel elongation_max
* `durations.segmental_floor: 20` — validation floor for vowel minima, consonant anchors
* `durations.cvc_reference: 300` — central heavy-syllable timing reference

**Consonants (closure, fricative, sonorant):**
* `onset`, `coda`, `coda_final` — positional anchors
* `geminate` — geminate target
* `geminate_coda_ratio` — corrective-only coda share
* `perception_limits.geminate_min`, `gemination_max` — class-local perceptual bounds

**Vowels:**
* `short: 110`, `long: 160`, `very_long: 260` — duration anchors
* `short_final`, `long_final` — pre-pausal final anchors
* `perception_limits.short_min`, `long_min`, `very_long_min`, `elongation_max` — perceptual bounds

**Pauses:**
* `short.min: 520`, `short.max: 680` — short-pause band
* `long.min: 1100`, `long.max: 1780` — long-pause band
* `resync.min: 100`, `resync.max: 200` — resync-pause band

**Process controls:**
* `geminate_policy: corrective` — same-consonant handling
* `accentuation_distribution_policy: 80_20` — primary/adjacent ratio
* `drift_tolerance: 19` — maximum tolerated timing mismatch

**WHY:** Each parameter is grounded in published phonetic, psycholinguistic, or perceptual research (see notes 231–250 for detailed justifications). The default values represent conservative choices within empirically attested ranges.

**THUS:** The default YAML provides a complete, defensible timing model that can be used directly for research or adjusted for sensitivity analysis.

---

## I-147-Phonetizer-Phone-Row-Format

**Domain:** Implementation / Data Format

**WHAT:** The phonetizer emits phone rows in a twelve-field pipe-delimited format:

```
label|category|type|length|position|boundary|accent|realization|duration|drift|intonation|text
```

Example:
```
SUD|C|F|S|O|N|F|SU|0137|+000|M0C|ṣ
AYA|V|L|S|N|F|F|AA|0110|+023|M0C|a
MEN|S|M|S|S|N|P|MP|0064|+000|M0C| 
ZEN|S|S|L|S|N|P|ZP|1525|+000|L2C|<EOL>
```

**WHY:** This format is the authoritative downstream analysis artifact. It carries all information needed for metrics computation and printer output: segment identity, timing class, position in syllable, boundary type, accentuation status, realized duration in milliseconds, drift token, intonation contour, and source text.

Key fields:
* `category`: C (consonant), V (vowel), S (silence)
* `type`: consonant subclass (H=hiatus, T=transition, C=closure, F=fricative, S=sonorant); vowel height (L=low, M=mid, H=high); pause type (Q=question, E=exclamation, S=statement, C=continuation, I=internal, M=resync)
* `position`: O (onset), C (coda), N (nucleus), S (silence)
* `boundary`: N (none), I (internal), E (enclitic), L (internal merge), X (explicit merge), F (prosodic unit end)
* `accent`: A (accentuated), F (flat), P (pause)
* `duration`: zero-padded milliseconds
* `drift`: signed beat-offset token (+000, -023, +023)
* `intonation`: row-level pitch-shape token (M0C, H2C, L2C, R1L, etc.)

**THUS:** The phone-row format is the canonical representation of the phonetizer's output. It is the input contract for both metricalc and printer.

---

## I-148-Phonetizer-Config-Ownership

**Domain:** Implementation / Configuration / Phonetizer

**WHAT:** The phonetizer is the canonical owner of the top-level `phonetize` config section. This includes:

**Process controls:**
* `phonetize.process.allow_experimental`: must be true to enable experimental features
* `phonetize.process.intonation.*`: f0, stress, question, statement, exclamation, continuation presets
* `phonetize.process.timing_model.geminate_policy`: corrective or cumulative
* `phonetize.process.timing_model.accentuation_distribution_policy`: 100_0 through 70_30
* `phonetize.process.timing_model.drift_tolerance`: maximum tolerated timing mismatch

**Timing model durations:**
* `phonetize.process.timing_model.durations.scale`: global multiplier
* `phonetize.process.timing_model.durations.segmental_ceiling`: validation ceiling
* `phonetize.process.timing_model.durations.segmental_floor`: validation floor
* `phonetize.process.timing_model.durations.cvc_reference`: central timing reference
* `phonetize.process.timing_model.durations.consonants.<class>.*`: class-specific anchors
* `phonetize.process.timing_model.durations.vowels.*`: vowel anchors and perception limits
* `phonetize.process.timing_model.durations.pauses.*`: pause bands

**No longer user-configurable:**
* `phonetize.process.timing_model.short_pause_policy`: fixed internally
* `phonetize.process.timing_model.drift_policy`: fixed internally
* `phonetize.process.timing_model.speech`: removed from active contract

**WHY:** Clear config ownership ensures that each stage controls its own parameters. The phonetizer's config section is the largest because the timing model is the most complex part of the pipeline. Runtime overrides use the same canonical paths via `-t/--option KEY=VALUE`.

**THUS:** The phonetize config section is the authoritative source for all timing model parameters. Changes to these parameters affect the phonetizer output and, through it, the metrics and printer outputs.

---

## I-149-Phonetizer-Semantic-Verification

**Domain:** Implementation / Validation

**WHAT:** Before runtime realization begins, the phonetizer runs a shared semantic verification layer against the effective config. This preflight checks:

* Enum-like process-policy values (geminate_policy, accentuation_distribution_policy)
* Positive integer timing leaves
* Validation-only segmental_floor lower bounds for vowel minima, consonant anchors, and hiatus/transition special realizations
* Class-local consonant gemination_max ordering and segmental_ceiling checks
* Consonant and vowel ordering constraints
* Pause-band ordering
* Short- and long-pause compatibility against active synchronization bases derived from cvc_reference
* Non-negative integer requirement for drift_tolerance
* Experimental-feature guard: limit_emphatic_coloring or enable_resync_pause requires allow_experimental: true

**WHY:** Semantic verification catches configuration errors before runtime, preventing the generation of invalid phone-row artifacts. The same verification layer is used by `confwriter --verify`, ensuring consistency between config editing and runtime execution.

**THUS:** The verification layer is a safety net that ensures the timing model is internally consistent before any processing begins. It reports blocking failures and warning-only conditions distinctly.

---

## I-150-Phonetizer-Unit-Drift-Reporting

**Domain:** Implementation / Diagnostics

**WHAT:** The phonetizer reports a unit-drift summary in the front matter of each emitted phone-row artifact. This includes:

* `metadata.data.phonetize.unit_drift.max`, `mean`, `stddev`, `current`, `label`
* `unit_drift_extension_count`, `unit_drift_extension_rate`
* `max_unit_drift_extension`
* `syllable_count`, `pause_count`, `resync_pause_count`, `total_unit_count`
* `non_accented_long_vowel_count`, `left_as_is_non_accented_long_vowel_count`, `drift_tolerance_effect`
* `inserted_resync_pause_count`, `eligible_resync_pause_count`, `resync_pause_insertion_rate`
* `pause_with_residual_drift_count`, `pause_with_residual_drift_rate`
* `duration_scale`

**WHY:** These diagnostics allow researchers to audit the timing model's behavior at the corpus level. They answer questions like: How often does drift exceed tolerance? How often are resync pauses inserted? What is the average drift magnitude? This information is essential for evaluating the model's plausibility.

**THUS:** The unit-drift reporting provides transparency into the timing model's internal behavior, supporting both debugging and research evaluation.

---

## References

(No additional references beyond those cited in the main text.)
