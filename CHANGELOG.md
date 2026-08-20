# Changelog

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
