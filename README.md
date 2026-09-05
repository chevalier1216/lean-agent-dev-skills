# lean-agent-dev-skills

Experimental, reusable Codex skills for keeping defined implementation missions lean and for validating user-facing work through a real application.

## Status

Version `0.5.3` is experimental. The repository is the canonical source; user-level installs are copies for execution.

## Included skills

- `lean-mission-execution`: mission-level context, coordination, verification, and stop discipline for an already-defined implementation mission.
- `visible-ux-validation`: visible, interactive validation of an implemented user-facing flow.
- `continuous-mission-orchestration`: continuity and stop semantics across multiple already-approved coherent missions.
- `durable-execution-handoff`: durable execution checkpoints and minimal recovery handoffs across runtime boundaries.

The skills compose with planning, execution-plan, testing, debugging, review, security, and Git workflows. They do not replace them.

## Validation

Behavior scenarios are maintained in `evals/`. They define expected decisions and boundaries for this initial version; they are not claims of a production-grade benchmark.

## Installation

Install only the desired skill directory into the user-level agent skill location. Do not treat an installed copy as the source of truth; make reusable changes here first.

## Publication

This public GitHub repository is the canonical source for the included project-agnostic skills. They are released under the [MIT License](LICENSE) and remain experimental. User-level copies in `$HOME/.agents/skills/` are runtime installs, not the source of truth.
