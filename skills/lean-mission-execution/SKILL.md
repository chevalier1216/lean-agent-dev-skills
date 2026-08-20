---
name: lean-mission-execution
description: Use when an implementation mission has a clear goal, scope, acceptance criteria, and no unresolved product decision blocking execution.
---

# Lean Mission Execution

Complete one defined implementation mission while minimizing unnecessary context, coordination, and repeated verification.

## Use when

Establish the goal, scope, acceptance criteria, boundaries, and relevant authoritative sources from the mission brief or project sources. Do not invent unresolved product decisions.

Treat a coherent mission, not an individual edit, as the execution and reporting unit.

## Execution discipline

- Load only the instructions, specifications, source, and dependencies needed for the active mission. Prefer targeted discovery and reads; treat history as lookup material.
- Make routine implementation decisions from existing requirements and continue through intermediate edits without turning them into handoffs, management events, or requests to continue.
- Do not emit a completion-style user handoff while the active mission remains executable. Discovery of the next actionable step requires continued execution, not a return of control to the user.
- Use targeted verification for affected behavior. Use broader verification at a meaningful mission checkpoint when risk warrants it.
- When one verification step is temporarily limited by its environment, record it as deferred validation and continue other safe, independent, approved work.
- Treat a condition as a genuine blocker only when no necessary work can be advanced safely; a single deferred validation is not a mission-level stop condition when other required work remains available.
- Preserve behavior outside scope. Prefer the smallest coherent diff and record optional improvements separately.
- Stop only at mission completion, a real technical blocker, a conflict between authoritative requirements, an explicit approval boundary, or a configured usage/resource threshold.

## Completion

At the mission checkpoint, report the outcome, changed files, verification, deferred validation, delivery reference when applicable, and any remaining blocker, risk, or required human decision.

## When not to use

Do not use this skill to define product requirements, plan an ambiguous mission, select architecture, perform security or code review, debug a failure, prescribe a Git workflow, or manage subagents. Use the applicable specialized workflow for those needs.

## Composition

This skill complements established planning, executing-plans, test-driven-development, systematic-debugging, code-review, security-review, Git publication, and visible UX validation workflows. Apply those only when their own trigger condition exists; this skill does not replace or duplicate them.
