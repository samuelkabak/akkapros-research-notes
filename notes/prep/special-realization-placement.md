# Special Realization Placement

This note records the current reason for storing `hiatus` and `vowel_transition` inside class-specific `special_realization` blocks rather than as free-standing transition parameters.

## Current YAML Shape

The active timing model now places the two values here:

- `closure.special_realization.hiatus = 18 ms`
- `sonorant.special_realization.vowel_transition = 11 ms`

Both values remain part of the timing model, but they are no longer exposed as top-level consonant entries.

## Why This Placement Is Clearer

The main issue is not only duration, but control logic. In the current interpretation, both values describe **unstressed light realizations**.

- `hiatus` is realized as a light glottal stop in weak position
- `vowel_transition` is realized as a light glide in weak position

When stress forces fuller realization, the model should not simply lengthen those weak values. Instead, each case should hand off to the relevant class-level geminate logic.

- stressed `hiatus` should behave like a geminated glottal stop and therefore belongs with the closure row
- stressed `vowel_transition` should behave like a geminated glide and therefore belongs with the sonorant row

This makes the placement under closure and sonorant more transparent than a single free-standing Transition block.

## Why `special_realization`

The label should remain neutral. These values are not ordinary onset, coda, or geminate members of the lexical classes themselves. They are exceptional realization parameters associated with those classes.

`special_realization` is preferable to labels such as `transitions` or `weak_forms` for three reasons.

- It does not imply that both values form one homogeneous phonological transition class.
- It does not imply that the stressed realization is merely a stronger version of the weak one.
- It keeps the YAML readable while leaving the classificatory claim modest.

## Methodological Consequence

The practical consequence is that the YAML now expresses two distinct claims at once.

- The weak unstressed realization is short and class-adjacent.
- The stressed realization is governed by the fuller closure or sonorant timing row, not by direct scaling of the weak value.

That distinction matters because it prevents the timing model from treating `18 ms` or `11 ms` as if they were ordinary segmental anchors across all prosodic environments.