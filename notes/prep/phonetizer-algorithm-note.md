# Paper Note: Phonetizer Algorithm and Timing Logic

This note sets out one paper-facing description of the phonetizer algorithm. It is meant to support article prose, not to replace implementation documentation. The aim is to state clearly which parts of the model are comparatively grounded, which are algorithmic reductions, and where the argument should remain cautious.

## 1. What The Algorithm Does

The phonetizer does not attempt to reconstruct historical performance in all its phonetic detail. It implements a constrained realization model. Lexical stress theory supplies a candidate set. The phonetizer then selects among those candidates, applies a limited realization operation, and assigns durations through a stability-first timing regime. The result is not a claim about exactly how Akkadian sounded in every utterance. It is a reproducible model of how lexical eligibility may have been converted into connected-speech prominence under explicit assumptions.

Two distinctions matter throughout. First, lexical eligibility is not identical with realized phrasal prominence. Second, empirical comparative intervals are not identical with runtime control values. The algorithm depends on both, but it should not collapse them into one evidential layer.

## 2. Structural Outline

The paper can describe the algorithm in four stages.

1. Parse the input into syllabified and classed segmental structure.
2. Identify the lexically eligible prominence sites according to the adopted Akkadian stress hierarchy.
3. Select one realizable target within the relevant prosodic group.
4. Assign durations through a stability-first control model that keeps ordinary segment anchors as the default output.

This sequence is important because it prevents the phonetizer from looking like a free duration solver. The choice of target is constrained before timing is assigned, and timing control is itself bounded by category-specific floors and ceilings.

## 3. Selection Of The Prominence Site

The selection stage uses the lexical hierarchy as a candidate inventory, not as a full connected-speech realization rule. In paper prose, that point should be stated plainly. The academic model identifies where prominence may fall. The phonetizer then chooses a site that can be realized inside the current prosodic group.

This means that some lexically eligible syllables remain unrealized in connected speech. That is not a defect in the model. It is the main reason for having a realization algorithm at all. The Erra diagnostic is useful here because it shows that lexical eligibility alone yields too dense a prominence pattern to be transferred unchanged into phrase-level recitation.

## 4. Realization Operations

Once a target is selected, the phonetizer adds one mora by one of the operations already grounded in the phonological discussion: vowel lengthening or consonant gemination. The model does not license arbitrary deformation of the segmental string. It uses the narrowest operation needed to create a heavier realized syllable while preserving the phonological identity of the form as far as possible.

This is also why the model benefits from class-specific limits. A vowel may lengthen only within the bounds of its category system. A consonant may lengthen only within the bounds that still preserve the intended singleton or geminate interpretation. The algorithm is therefore constrained twice: first by where prominence may be realized, and second by how far the segmental material may be stretched or compressed before it changes category.

## 5. Stability-First Timing

The timing layer should be presented as stability-first. Segment anchors are the ordinary emitted values for a given speaker model. The algorithm does not try to force every local syllable into exact equality with one abstract foot target. Instead, it carries small mismatch forward in running drift and uses stronger boundary positions as recovery points.

This matters methodologically. A local exact-target solver would imply that the same speaker continually reshapes ordinary singleton consonants and ordinary vowels from syllable to syllable merely to satisfy a metrical arithmetic. That is phonetically weak. The stability-first formulation is more plausible because it preserves ordinary anchors and reserves stronger correction for the places where phrasing naturally offers temporal adjustment.

## 6. The Role Of `cvc_reference`

The heavy-syllable control value `cvc_reference = 305 ms` should be described as a runtime control chosen conservatively inside the grounded `CVC` interval `286-306 ms` and inside the empirical overlap created when the short-pause region `600-680 ms` is halved to `300-340 ms`. It is a control value, not a directly measured Akkadian average. The important point for the paper is not that `305` is magically exact, but that it states openly how the reduction was made.

That distinction is likely to matter to reviewers. It prevents the paper from presenting a tidy runtime constant as if it were itself the empirical observation.

## 7. Short Pause Logic

The short-pause discussion should be handled carefully. The present source base supports a comparative short-pause region around six hundred milliseconds. It does not, however, provide a study that directly measures short pause as a fixed multiple of the heavy-syllable control value. The paper should not imply otherwise.

The safer formulation is that the active short-pause band remains empirically grounded in the comparative short-pause region, here modeled as `600-680 ms`. This keeps the pause range anchored in the literature while preserving rhythmic compatibility with the heavy timing model, because the preferred reset target `610 ms` remains inside the band. It is therefore a grounded empirical band used by an algorithmic alignment choice, not a direct empirical identity.

Within that broader band, the preferred reset point may still be `2 * cvc_reference = 610 ms`. But the band itself should not be defined only as `target ± drift_tolerance`. Doing so would make the model look more exact than the evidence requires and would tie pause width too tightly to one solver parameter.

## 8. Long Pause Selection

Long pause should be described differently. The comparative literature gives a broad clause-boundary range, here modeled as `1200-1780 ms`. That range is empirical at the level of envelope, not at the level of one privileged realized point.

If the implementation wants a deterministic realized long pause inside that band, the algorithm can proceed as follows.

1. Compute the midpoint of the long-pause band.
2. Enumerate all admissible multiples `N * cvc_reference` that fall within the band.
3. Choose the candidate nearest the band midpoint.
4. If two candidates are equally near, choose the smaller one.

Under the current defaults, this yields `1480 ms`. The paper should make clear that this is a realization rule inside a broad empirical band. It is not a claim that Akkadian long pause was empirically measured at `1480 ms`.

## 9. Drift And Boundary Recovery

Running drift is part of the control system, not part of the empirical input. The paper should therefore avoid language that treats `drift_tolerance` as if it were itself a measured historical constant. It is a bounded solver parameter that limits how much mismatch may accumulate before stronger recovery is required.

The present default `12 ms` may remain usable because the pause band is grounded empirically rather than being defined by `target ± drift_tolerance`. That is a useful methodological simplification. It lets the paper defend a broader pause band without having to defend a broader ordinary mismatch budget at the same time.

## 10. Suggested Article Formulation

One concise paper-facing formulation could read as follows:

The realization algorithm begins from the lexical candidate set supplied by the standard Akkadian stress analysis, but it does not equate lexical eligibility with realized phrasal prominence. It selects one realizable target within the prosodic group, adds one mora through vowel lengthening or consonant gemination, and then assigns durations through a stability-first timing model. Ordinary segment anchors remain the default emitted values; small mismatch is carried forward in bounded running drift; short pause serves as a principal reset zone; and long pause provides a broader boundary interval whose realized value may be chosen deterministically from the admissible candidates inside the empirical band. The heavy-timing control `cvc_reference` is a conservative runtime value chosen inside the grounded `CVC` interval and the empirical pause-overlap zone rather than a directly measured historical constant, and the pause bands should likewise be understood as empirical ranges whose implementation use remains cautious and speech-rate-sensitive.

That formulation keeps the argument cautious while still explaining how the model actually works.