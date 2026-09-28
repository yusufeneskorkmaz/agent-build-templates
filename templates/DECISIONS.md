# [PROJECT] — append-only decision log template

Append a new numbered entry for every judgment that affects implementation, evidence eligibility, scope, or interpretation. Never erase a historical decision. If superseded, add a new entry that names the previous one. An amendment must preserve the old criterion and record when the change was authorized relative to reference freeze.

## [DECISION_ID]

- milestone: [MILESTONE]
- authority: [HUMAN | ORCHESTRATOR | LEAD_WITHIN_DIRECTIVE]
- stage: [EXPLORATION | PRE_FREEZE | POST_FREEZE]
- decision: [EXACT_RULE_OR_ACTION]
- prior rule, if amended: [EXACT_OLD_RULE_OR_NOT_APPLICABLE]
- effect on metrics, denominator, threshold, and scope: [EXPLICIT_EFFECT]
- alternatives considered: [OPTIONS]
- evidence inspected: [ARTIFACT_LABELS_AND_HASHES]
- in-authority remedies attempted and outcomes: [REMEDY_LEDGER_OR_NOT_APPLICABLE]
- rationale: [WHY_THIS_FOLLOWS_FROM_THE_EVIDENCE]
- delivery: [OWNER_RECEIVED_AND_ARTIFACT_OR_TASK_CREATED]
- result under prior rule preserved: [YES_OR_NOT_APPLICABLE]

A proposal in chat is not a delivered remedy. Record authorization, owner, delivery artifact, and verification separately.
