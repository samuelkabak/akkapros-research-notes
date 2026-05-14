This note records the reduction choice now preferred for the computation layer of the project. The consonant system is reduced to two positional configurations only: `onset`, understood as post-consonantal or post-silence entry, and `post_vocalic`, understood as the consonantal interval that follows a vowel, whether word-internal or final. The point of this reduction is not to deny that intervocalic and coda consonants may differ. It is to keep only the positional contrast that seems most useful for corpus-scale metric computation while preserving a plausible path from non-geminate timing to gemination and from anchor values to perception floors.

The fuller evidential table remains unchanged in status. It still preserves onset, intervocalic, coda, and geminate values where the evidence warrants them. The present reduction simply asks which smaller system should carry the numerical burden of converting transliterated text into sequences of consonants, vowels, and pauses for the computation of `%V`, `DeltaC`, `VarcoC`, `VarcoV`, `nPVI-V`, and related measures.

## 1. Why The Two-Position System Is Preferable

Several considerations favor the onset versus post-vocalic distinction.

First, the empirical asymmetry is small but real in the strongest consonant row. Closure consonants are slightly longer in onset position than in coda position, while intervocalic timing is only modestly above both. If one keeps all three non-geminate positions, the system gains detail but also carries distinctions that are not equally well grounded outside the stop row. A two-position collapse retains the strongest structural contrast without pretending that all three positions are supported equally across all classes.

Second, the reduction interacts better with gemination than a pure onset-only collapse. If geminate duration is approximated as `onset + post_vocalic`, the closure row remains closer to the attested geminate zone than it does under the stronger rule `2 x onset`. The fricative row is also tolerably approximated under the additive rule, especially if the chosen post-vocalic default is set at the upper edge of the currently justified post-vocalic band.

Third, the two-position system is conceptually cleaner for interval modeling. The relevant difference is not merely word-internal versus word-final placement. It is whether the consonantal interval follows silence or another consonant on the left edge, or whether it follows a vowel on the right edge of a syllabic nucleus. That is the positional distinction most likely to matter when the project converts text into alternating consonantal and vocalic intervals.

## 2. Selection Principle For The Reduced Values

The reduction is guided by one narrow optimization criterion: within the currently justified ranges, choose onset and post-vocalic defaults that keep the additive geminate approximation as close as possible to the preferred geminate target. This does not mean that gemination is treated as a literal arithmetic law. It means that, once the system is reduced to two non-geminate positions, the chosen defaults should minimize unnecessary discrepancy.

Under that rule, the present best defaults are as follows.

| Class | Onset default | Post-vocalic default | Additive geminate | Reason for the post-vocalic choice |
| :--- | :--- | :--- | :--- | :--- |
| Closures | `108 ms` | `103 ms` | `211 ms` | the lower post-vocalic value is closer to the attested closure geminate band than `113 ms` would be |
| Fricatives | `137 ms` | `142 ms` | `279 ms` | the heavier post-vocalic value preserves the active fricative row and makes the capped additive geminate explicit |
| Liquide / Nasal / Glide | `89 ms` | `70 ms` | `159 ms` | the raised onset anchor follows the clearer liquid evidence, while the post-vocalic side remains at the structural minimum |

The transition row remains exceptional. It is a functional internal marker row for `˙` and `¨`, not an ordinary consonant class. `˙` marks onsetless entry or strict hiatus, while `¨` marks the stronger vowel-transition case. For that reason, the row should remain available in the file, but it should not govern the optimization logic of the main consonant rows.

## 3. Consequence For The Computation Layer

The preferred reduced computation system should therefore be defined as follows.

- one onset parameter per consonant class
- one post-vocalic parameter per consonant class
- one additive geminate comparison derived from those two values, even when the final geminate anchor is kept separately
- one short-vowel parameter and one long-vowel parameter as the base vocalic system
- one empirical `CVC` duration range, because the heavy closed syllable provides the most direct interval basis for the bimoraic accentuation layer
- one short-pause layer and one long-pause layer, anchored by an overall pause ratio and punctuation classification rules
- one compact limit layer containing the strongest currently justified perceptual floors and ceilings

This system is small enough to be operational and still rich enough to generate the interval sequences needed by the metrics. It also preserves a clear separation between the evidential layer, where fuller positional detail remains visible, and the computation layer, where the project needs one stable source of defaults. The current sonorant row shows why this matters. The additive comparison `89 + 70 = 159` is useful, but the exposed geminate anchor remains `163 ms` because the direct glide-geminate evidence is slightly stronger than the arithmetic shortcut.

For the heavy syllable basis itself, the file should keep only the grounded compositional `CVC` band `286-306 ms`, derived from stop onset `108 ms`, short vowel `75-95 ms`, and stop coda `103 ms`. That is the empirical interval basis to retain for bimoraic accentuation. No separate higher target needs to be stored in the computation layer.

## 4. Proposed Single Source Of Truth

The accompanying YAML file is intended as the user-facing computation configuration. It should contain only quantities that a user may legitimately tune: timing defaults, perception limits, pause assumptions, and any explicit override lists that the interface exposes. Internal symbols, fixed parser markers, and hardcoded algorithmic behavior should remain in code rather than in the YAML.

The file therefore stores the reduced onset versus post-vocalic timing system, not the fuller evidential table, and not the internal symbolic grammar of the pipeline. When the article needs evidential precision, the fuller notes should still be cited. When the software needs one compact set of user-adjustable defaults, the YAML file should be treated as the active computation layer.