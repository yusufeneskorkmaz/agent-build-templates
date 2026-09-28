# Rigorous multi-agent build templates

Reusable templates for running rigorous builds with AI coding tools. The roles are an orchestrator, milestone leads, implementation workers, read-only explorers, an adversarial verifier, and an independent scientific reviewer. The documents define how those roles share authority and preserve evidence.

These templates are for developers and technical leads using Codex or Claude Code on projects that need reproducible results, clear responsibilities, and evidence for acceptance. They complement spec-driven frameworks such as [GitHub Spec Kit](https://github.com/github/spec-kit) rather than replacing them.

## Key rules

- **Hard invariants:** Give each active invariant a real test. Do not weaken tests, tolerances, sample counts, or thresholds to obtain a pass.
- **Pre-registration:** Fix the evaluation split, metrics, thresholds, and stopping rules before inspecting holdout results. Freeze reference data and record artifact hashes.
- **Independent verification:** Reviewers check the reported evidence and compare tests with the last accepted baseline for weakened or skipped assertions and self-confirming oracles.
- **Blocker triage:** Classify a block as `SPEC_CONTRADICTION`, `AUTHORIZATION_REQUIRED`, `EXTERNAL_DEPENDENCY`, or `WORK_INCOMPLETE`. Before escalating, attempt and record every remedy within the agent's authority. Untried work is `WORK_INCOMPLETE`.
- **Fresh-context second opinions:** After two blocked reports on the same criterion, give an independent reviewer the criterion and artifacts without the earlier reasoning. Record its verdict, including disagreement.
- **Gate ledger:** Authorize evaluation runs one at a time. Keep an append-only, bounded ledger and disclose changes informed by holdout results.
- **Phase fit:** Heavy governance suits proving a defined result. Use a lighter feasibility phase while exploring whether a claim is viable.

## Use the templates

1. Fill in [PRD.md](templates/PRD.md) first: define the user, claim, evidence inventory, refusal conditions, and feasibility questions.
2. Once the claim is viable, fill in [BUILD_DIRECTIVE.md](templates/BUILD_DIRECTIVE.md): milestones, invariant tests, frozen evaluation rules, acceptance criteria, and gate policy.
3. Adapt [AGENTS.md](templates/AGENTS.md) and [orchestrator_kickoff.md](templates/orchestrator_kickoff.md) to your authority model. Keep [PROJECT_STATE.md](templates/PROJECT_STATE.md) current and [DECISIONS.md](templates/DECISIONS.md) append-only.
4. Adapt the five [agent definitions](templates/agents/). For **Codex**, use the TOML definitions under `.codex/agents/` and put the adapted `AGENTS.md` at the project root. For **Claude Code**, convert each TOML definition to a Markdown subagent file under `.claude/agents/`: move `name` and `description` into YAML frontmatter, use `developer_instructions` as the body, and restrict the explorer and reviewer roles to read-only tools. The TOML files are not directly loadable by Claude Code; see its [subagent format](https://code.claude.com/docs/en/sub-agents).

Replace bracketed placeholders and set domain-specific thresholds from your own evidence before certification. Review each agent's available tools and permissions in the target runtime.

## Licence

Code and configuration, including the TOML agent definitions and executable configuration snippets, are covered by the [MIT licence](LICENSE). Markdown documentation and templates, including this README, are covered by [CC-BY-4.0](LICENSE-docs).

Copyright (c) 2026 yusufeneskorkmaz.
