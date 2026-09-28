# [PROJECT] — build directive template

> Binding implementation order and acceptance contract. The PRD governs intent. Record amendments separately; do not edit historical criteria to make results pass.

## 0. Phase boundary

Complete a bounded feasibility review before certification work. Record the candidate evidence inventory, known information limits, simple baselines, and the claim to freeze. Mark exploratory results provisional. The human owner authorizes the transition to the fixed claim.

## 1. Hard invariants

Every active invariant has an executable assertion. Pending invariants have a named activation milestone and cannot be reported as passing.

| ID | Hard invariant | Test assertion | Activation |
|---|---|---|---|
| I-1 | [INVARIANT] | [TEST_NODE_OR_ASSERTION] | [MILESTONE] |
| I-2 | Holdout evidence cannot enter training, priors, or feature selection | [IMPORT_AND_DATA_BOUNDARY_TEST] | [MILESTONE] |
| I-3 | Incompatible quantity definitions fail closed | [MISMATCH_TEST] | [MILESTONE] |
| I-4 | Identical inputs plus pinned artifacts yield byte-identical reference outputs | [TWO_RUN_COMPARISON] | [MILESTONE] |
| I-5 | Every reported result pins source and artifact identities | [SCHEMA_AND_HASH_TEST] | [MILESTONE] |

Never weaken, skip, xfail, reduce sample count, widen tolerance, or lower a threshold to make a milestone pass. An independent oracle computes its expectation without calling the implementation under test. Golden outputs may check determinism; they are not independent scientific oracles.

## 2. Stack and data policy

- Reference runtime and platform: [RUNTIME]
- Approved dependencies: [DEPENDENCY_LIST]
- New dependency decision: add a reasoned entry to `DECISIONS.md` before use.
- Internal units and time convention: [UNITS_AND_TIME]
- Raw third-party data and generated artifacts remain outside version control.
- Credentials come from environment variables and never enter source, output, or logs.
- Long-running generation, training, and calibration jobs write logs to an ignored output area; reports contain summaries.

## 3. Milestone sequence

| Milestone | Goal | Exit criterion | Evidence command or artifact | Evaluation-data access |
|---|---|---|---|---|
| [MILESTONE] | [GOAL] | [VERBATIM_CRITERION] | [EVIDENCE] | NONE / DEV / AUTHORIZED_GATE |
| [MILESTONE] | [GOAL] | [VERBATIM_CRITERION] | [EVIDENCE] | NONE / DEV / AUTHORIZED_GATE |

One lead owns one milestone. Do not advance to the next until the orchestrator accepts the current one. Do not create later-milestone stubs. The lead integrates, runs the full required suite, and returns one completion report. Reviewer acceptance and state-file update close the milestone.

## 4. Reference evidence and pre-registration

Register the split rule, reference eligibility, quantity semantics, matching rules, uncertainty handling, metrics, denominators, thresholds, and stop rule before reference values are read. Freeze model configurations and priors first. Blindly re-extract a sample of reference records before freezing the manifest. Record content hashes and disagreements. Reference values must not appear in implementation source or agent briefs outside the authorized path.

For `INSUFFICIENT_EVIDENCE` or equivalent evidence insufficiency, a negative determination requires the bounded acquisition to be complete, a per-item acceptance or rejection ledger, numeric eligible counts for every required comparison, and zero `UNKNOWN` dispositions. A partial inventory is not a global absence claim.

## 5. Calibration and gate

Calibration uses a predeclared held-out or synthetic certification split, not the training set. Register statistical power, seed policy, metric aggregation, refusal handling, and uncertainty checks. Fail any criterion whose evidence is missing. Distinguish calibration from predictive accuracy.

The real-data gate is authorized one run at a time by the orchestrator. The ledger is append-only and capped at [MAX_GATE_RUNS]. Every run records the manifest hash, artifact hashes, run number, metrics, determination, and all prior run identifiers. Any post-gate artifact change is labelled `HOLDOUT_INFORMED: true` in the next record. A second-opinion review never authorizes a gate rerun. A terminal negative determination stops further remediation unless the human owner explicitly authorizes a new study and the prior result remains unchanged.

## 6. Blocker and amendment discipline

Classify every proposed block as exactly one of `SPEC_CONTRADICTION`, `AUTHORIZATION_REQUIRED`, `EXTERNAL_DEPENDENCY`, or `WORK_INCOMPLETE`. Only the first three can be escalated. Before a `BLOCKED` report, list every candidate remedy within the lead's authority and the outcome of attempting each. Any untried remedy means `WORK_INCOMPLETE`; do the work.

Two `BLOCKED` reports on the same criterion trigger a fresh-context read-only explorer. Give it only the criterion and the relevant artifacts, including a remedy ledger, without the previous reasoning. Request an independent verdict on whether the block is real and which class applies. Escalate the repeated criterion only if the verdict confirms `SPEC_CONTRADICTION` or `AUTHORIZATION_REQUIRED`. Quote the verdict verbatim, including disagreement. Verify that the artifact set itself is complete; reviewer agreement cannot repair missing evidence.

Every amendment records the old and new rule, timing relative to freeze, effect on metrics, alternatives, rationale, and human authority. After reference freeze, report results under frozen criteria first. Any proposed future change belongs to a separately named study.

## 7. Milestone completion report

```text
MILESTONE COMPLETION REPORT
milestone:        [MILESTONE] — [NAME]
status:           COMPLETE | BLOCKED
revision:         [REVISION_ID_AND_SUMMARY]
exit_criteria:
  - criterion:    [VERBATIM_CRITERION]
    status:       YES | NO
    evidence:     [COMMAND_OR_ARTIFACT] → [ONE_LINE_RESULT]
invariants:
  - id:           [INVARIANT]
    tests:        [TEST_NODE_IDS]
    status:       PASS | FAIL | NOT_YET_ACTIVE
tests:            passed [N] · failed [N] · skipped [N] ([REASON]) · xfail [N]
metrics:          [REGISTERED_METRICS_OR_NA]
artifacts:        [RELATIVE_ARTIFACT_LABEL] sha256:[CONTENT_HASH_PREFIX]
decisions:        [DECISION_IDS]
deviations:       [NONE_OR_EXPLICIT_RATIONALE]
scope_check:      [NO_LATER_MILESTONE_FILES_TOUCHED]
blockers:         [CLASS, REMEDY_LEDGER, OPTIONS_OR_NONE]
risks_next:       [UP_TO_THREE_LINES]
```

## 8. Never build

- [EXCLUDED_CAPABILITY]
- [OUT_OF_SCOPE_DEPENDENCY]
- Any private data path outside the approved evidence policy
- Any feature that would present an uncalibrated estimate as validated
