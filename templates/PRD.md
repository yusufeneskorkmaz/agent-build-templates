# [PROJECT] — product rationale template

> Replace every bracketed field before using this document. This states *why* the claim matters. The build directive states *what* is required.

## Claim and user

- Intended user: [USER_ROLE]
- Decision this output supports: [DECISION]
- Claim to be tested: [CLAIM]
- Cost of a wrong but confident answer: [FAILURE_COST]
- Acceptable refusal: [WHEN_TO_SAY_UNKNOWN]

Describe the simplest output an expert could check. State what the system will never claim from the available evidence.

## Discovery before certification

List the evidence types available without privileged access. For each, record whether it contains the quantity, uncertainty, metadata, and independent comparison needed for the claim. Identify likely information limits before setting a certification threshold. Use small feasibility experiments; label their results provisional. Decide explicitly when exploration ends and a fixed claim begins.

| Question | Cheap falsification check | Evidence needed | Current status |
|---|---|---|---|
| [QUESTION] | [CHECK] | [EVIDENCE] | UNTESTED |

## Product boundaries

- In scope: [IN_SCOPE]
- Out of scope: [OUT_OF_SCOPE]
- External data allowed: [PUBLIC_OR_LICENSED_CLASSES]
- Private or restricted data: [POLICY]
- Failure and refusal behavior: [RULE]

## Evidence integrity

Reference entries must declare source, location within source, extraction method, measured quantity and unit, applicable context, uncertainty, licence, retrieval metadata, and a content hash. A result may be scored only against a compatible reference. Publish the method and all material negative findings. Do not claim validation from a synthetic test alone.

## Freeze policy

Before inspecting holdout values, register model inputs, prior or configuration ranges, comparison rules, development/holdout split, metrics, thresholds, and stopping rules. Freeze the manifest and record its hash. After freeze, report an unfavorable result against the original rules before proposing a later study. No revision silently changes the meaning of a prior result.

## Reproducibility promise

Identical input records and pinned artifacts must produce identical outputs on the declared reference environment. Every report lists relevant artifact versions and hashes. Unsupported, missing, or incomparable evidence produces an explicit status, never an invented estimate.

## Success and stop conditions

- Success requires: [MEASURABLE_SUCCESS]
- Evidence insufficiency is determined by: [COMPLETE_SEARCH_BOUNDARY_AND_MINIMUM]
- Stop after: [STOP_RULE]
- Human decisions reserved for: [AUTHORITY_BOUNDARY]
