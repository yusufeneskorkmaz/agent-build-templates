# [PROJECT] agent contract template

## Authority and memory

`BUILD_DIRECTIVE.md` controls what and in what order; `PRD.md` controls why. Do not silently edit either to accommodate failure. Read `PROJECT_STATE.md` for accepted status and `DECISIONS.md` for append-only judgments. If the specification is silent, choose a traceable, deterministic, conservative interpretation and log it.

## Universal standards

- Preserve every test, tolerance, sample count, denominator, and threshold unless an explicitly authorized amendment says otherwise.
- Give every touched hard invariant a real assertion in `tests/invariants/`.
- Derive scientific oracle expectations independently of production code.
- Keep work inside the assigned milestone and file ownership.
- Require identical inputs and pinned artifacts to yield byte-identical reference outputs.
- Keep credentials in environment variables. Do not commit third-party data or generated artifacts.

## Reference and gate hygiene

- Holdout reference values may be read only by disposable, explicitly authorized pre-freeze transcription roles or by the specifically authorized gate path. The orchestrator and later milestone roles never receive those values.
- Never set or shift priors, rules, or thresholds using holdout values.
- Make incompatible reference comparisons fail closed.
- Never run the gate without explicit orchestrator authorization for a specific ledger run.
- Record reference provenance, manifest hash, and artifact hashes without copying private values into reports.

## Blocker triage

Use exactly one class: `SPEC_CONTRADICTION`, `AUTHORIZATION_REQUIRED`, `EXTERNAL_DEPENDENCY`, or `WORK_INCOMPLETE`. `WORK_INCOMPLETE` is a task, not an escalation. Before `BLOCKED`, enumerate all remedies inside your authority and record the result of attempting each. An untried in-authority remedy makes the report incomplete. Evidence-insufficiency claims require full bounded acquisition, per-item rejection reasons, numeric eligibility counts, and no `UNKNOWN`.

After two `BLOCKED` reports on one criterion, obtain a fresh-context read-only second opinion using only the criterion and relevant artifacts. Include a remedy ledger, not the first reviewer's conclusion. The reviewer decides independently whether the block is real and assigns a class. Escalate the repeated criterion only if it confirms `SPEC_CONTRADICTION` or `AUTHORIZATION_REQUIRED`; report its exact verdict even if it disagrees. A second opinion cannot authorize a gate rerun.

## Roles

- Orchestrator: frames goals, controls gates, accepts or rejects milestones, maintains `PROJECT_STATE.md`; does not implement.
- Milestone lead: owns one milestone, decomposes tasks, integrates work, writes invariant and oracle tests, runs the suite, returns one report.
- Worker: implements one bounded chunk and reports to its lead.
- Explorer: read-only investigation and evidence inventory for its lead.
- Verifier: read-only adversarial review of report, tests, scope, and gate mechanics.
- Scientific reviewer: read-only independent derivation of mathematical and statistical expectations.

Do not pass raw logs or large payloads to the orchestrator. Use the completion report in `BUILD_DIRECTIVE.md`. Keep `PROJECT_STATE.md` accurate enough that a new session can resume from repository records, without private chat history.

## Review rules

The verifier compares changed tests against the previous accepted baseline and flags weaker assertions, skips, xfails, smaller samples, wider tolerances, and lower thresholds. The scientific reviewer checks independent closed forms, units, uncertainty, and calibration logic. Neither implements the reviewed work. A `CONFIRMED` verdict is conditional on the artifacts actually examined; missing evidence remains missing.
