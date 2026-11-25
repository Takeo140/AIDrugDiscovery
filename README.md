# AI Drug Discovery — proof-verified models of drug-discovery methods

Lean 4 formalizations of the steps of a drug-discovery pipeline, each
with machine-checked guarantees. Core Lean only: no Mathlib, no
`sorry`, and the axioms of every headline theorem are printed at the
end of its file.

This repository is the dedicated home of the drug-discovery line that
began inside
[Mathematical-Medicine](https://github.com/Takeo140/Mathematical-Medicine).
The original files remain there; the line continues here, one new
verified file per week.

## Contents

| File | Step of the pipeline | Main guarantee |
|---|---|---|
| `AIDrugDiscovery.lean` | Screening | the search returns a non-toxic candidate, and no non-toxic candidate in the library scores better |
| `AIDrugDiscoveryExt.lean` | Selectivity and certificates | a multi-condition screen, plus a decidable certificate layer for checking proposed candidates |
| `AIDrugDiscoveryDescent.lean` | Lead optimization | descent strictly lowers the defect each step and reaches the target profile within the initial defect |
| `AIDrugDiscoveryCombo.lean` | Combination therapy | a combination's coverage defect is at most each single compound's, and the combination is non-toxic exactly when both compounds are |

## Method

Each file models one method of drug discovery in a deliberately
abstract, discrete form — compounds as bit fingerprints, a target as a
profile — and proves the correctness of the method *inside the
model*: that a search is optimal, that an optimization settles within
a bound, that a combination cannot cover less than its parts, that a
certificate is sound.

## Honest note

These are formal prototypes, not medicinal chemistry. They do not
discover drugs. They give drug-discovery *methods* a form in which
their correctness can be proved (Q.E.D.) and rechecked by anyone.
Judgement of the models themselves is left to the reader.

## Verification

CI compiles every `.lean` file in the repository root with Lean
4.36.0 on each push. The same check runs locally with:

    lean AIDrugDiscovery.lean

## Author and license

Takeo Yamamoto (GitHub: Takeo140)

Apache License 2.0 — see `LICENSE`.
