# [PROJECT] — orchestration state template

This file is the current operational state, updated by the orchestrator after each accepted milestone or human ruling. It is a restart point, not a narrative transcript. Keep historical decisions in `DECISIONS.md`.

## Current state

- Project determination: [EXPLORING | BUILDING | CERTIFIED | NOT_CERTIFIED | CLOSED]
- Current milestone: [MILESTONE_OR_NONE]
- Last accepted revision: [REVISION_ID_OR_NONE]
- Active authority: [WHAT_THE_LEAD_MAY_DO_NOW]
- Explicitly prohibited action: [GATE_OR_LATER_STAGE_BOUNDARY]
- Next permitted action: [NEXT_ACTION]

## Milestones

| Milestone | Status | Exit evidence | Accepted revision |
|---|---|---|---|
| [MILESTONE] | NOT_STARTED | [EVIDENCE_OR_NONE] | [REVISION_OR_NONE] |

## Invariants

| ID | Status | Test evidence | Activation milestone |
|---|---|---|---|
| [INVARIANT] | NOT_YET_ACTIVE | [TEST_OR_NONE] | [MILESTONE] |

## Frozen artifacts

| Artifact label | Version | Content hash | Frozen before reference inspection? |
|---|---|---|---|
| [ARTIFACT] | [VERSION] | [HASH_OR_NONE] | YES / NO |

## Reference and gate status

- Split rule registered: [YES_OR_NO]
- Reference manifest frozen: [YES_OR_NO]
- Manifest hash: [HASH_OR_NONE]
- Gate runs used: [N] of [MAX_GATE_RUNS]
- Latest determination: [NONE_OR_DETERMINATION]
- All gate records preserved: [YES_OR_NO]
- Post-gate artifact changes disclosed: [YES_OR_NOT_APPLICABLE]

## Evidence sufficiency

- Acquisition boundary: [BOUNDED_SEARCH]
- Items inventoried: [N]
- Items dispositioned: [N]
- `UNKNOWN` count: [N]
- Eligible comparison counts by metric: [COUNTS]
- Per-item ledger status: [COMPLETE_OR_INCOMPLETE]

## Open items

| Item | Owner | Class | Remedies attempted | Next action |
|---|---|---|---|---|
| [ITEM] | [OWNER] | [BLOCKER_CLASS_OR_TASK] | [LEDGER_REFERENCE] | [ACTION] |

## Session recovery

Read `PRD.md`, `BUILD_DIRECTIVE.md`, `AGENTS.md`, this file, `DECISIONS.md`, and the gate ledger's record count and determinations. Verify current revision and frozen hashes. Do not read holdout values. Resume only the next permitted action above.
