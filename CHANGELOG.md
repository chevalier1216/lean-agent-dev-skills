# Changelog

## 0.4.0 - 2026-08-24

- Added workspace baseline, mission-owned file scope, pre-commit scope audit, and bounded safe recovery to `lean-mission-execution`.
- Added minimal `continuous-mission-orchestration` integration: safe recovery is not a stop condition, while unrecoverable protected-state damage is a genuine blocker.
- Added project-agnostic behavior scenarios for staged protected state, trusted-baseline recovery, mission-created unrelated files, unrecoverable state, and orchestration continuation.

## 0.3.2 - 2026-08-20

- Required targeted approved-work-queue discovery at every orchestrator mission checkpoint before a completion-style final response, unless a currently valid stop condition is established.
- Added regression coverage for repeated checkpoint false-stops and retained the runtime trigger/invocation telemetry limitation.

## 0.3.1 - 2026-08-20

- Clarified the `continuous-mission-orchestration` trigger at a mission checkpoint and required targeted discovery before declaring an approved queue exhausted.
- Added a regression scenario for a completed mission whose approved queue has not been proven exhausted, plus a limitation for missing runtime selection telemetry.

## 0.3.0 - 2026-08-20

- Added the experimental `durable-execution-handoff` skill and behavior scenarios for durable checkpoints, minimal resume handoffs, dirty-work ownership, and stale-handoff precedence.
- Added a minimal `lean-mission-execution` composition reference for interruption recovery.
- Recorded that the repository has no executable baseline or with-skill runtime harness; the new scenarios are decision specifications, not benchmark results.

## 0.2.1 - 2026-08-20

- Clarified deferred-dependency propagation for `continuous-mission-orchestration`: shared workflow history, timing, or resources do not by themselves block an otherwise eligible mission, while an unestablished dependency cannot be assumed independent.
- Added project-agnostic eval scenarios for false-block and false-continue risks around deferred work.

## 0.2.0 - 2026-08-20

- Added the experimental `continuous-mission-orchestration` skill and behavior scenarios for approved queues, deferred dependencies, and stop boundaries.
- Added a composition reference from `lean-mission-execution` for approved multi-mission continuity.
- Recorded that the repository has no executable baseline or with-skill runtime harness; the new scenarios are decision specifications, not benchmark results.
- Changed the canonical repository publication license to MIT for public reuse.

## 0.1.2 - 2026-08-20

- Clarified that an executable mission continues when its next actionable step is known; agents must not emit a completion-style handoff prematurely.

## 0.1.1 - 2026-08-20

- Added background-safe and non-disruptive validation guidance to `visible-ux-validation`.
- Added deferred-validation and genuine-blocker execution semantics to `lean-mission-execution`.
- Added behavior scenarios for background-safe execution, deferred foreground validation, and incomplete required foreground validation.

## 0.1.0 - 2026-08-20

- Added the initial experimental `lean-mission-execution` skill.
- Added the initial experimental `visible-ux-validation` skill.
- Added minimal behavior scenarios and scope references.
