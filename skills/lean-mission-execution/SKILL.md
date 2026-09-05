---
name: lean-mission-execution
description: Use when an implementation mission has a clear goal, scope, acceptance criteria, and no unresolved product decision blocking execution.
---

# Lean Mission Execution

Complete one defined implementation mission while minimizing unnecessary context, coordination, and repeated verification.

## Use when

Establish the goal, scope, acceptance criteria, boundaries, and relevant authoritative sources from the mission brief or project sources. Do not invent unresolved product decisions.

Treat a coherent mission, not an individual edit, as the execution and reporting unit.

## Workspace baseline and scope

Before changing files, capture repository status. Record pre-existing tracked dirty paths and untracked paths as protected existing state, then define the files the mission owns. Do not absorb protected paths into mission scope.

For protected files near mission scope that may need recovery, retain a trustworthy baseline such as a content hash or temporary snapshot. Do not claim a baseline that cannot restore or verify the prior content.

## Execution discipline

- Load only the instructions, specifications, source, and dependencies needed for the active mission. Prefer targeted discovery and reads; treat history as lookup material.
- Make routine implementation decisions from existing requirements and continue through intermediate edits without turning them into handoffs, management events, or requests to continue.
- Do not emit a completion-style user handoff while the active mission remains executable. Discovery of the next actionable step requires continued execution, not a return of control to the user.
- Use targeted verification for affected behavior. Use broader verification at a meaningful mission checkpoint when risk warrants it.
- When one verification step is temporarily limited by its environment, record it as deferred validation and continue other safe, independent, approved work.
- Treat a condition as a genuine blocker only when no necessary work can be advanced safely; a single deferred validation is not a mission-level stop condition when other required work remains available.
- Preserve behavior outside scope. Prefer the smallest coherent diff and record optional improvements separately.
- Stop only at mission completion, a real technical blocker, a conflict between authoritative requirements, an explicit approval boundary, or a configured usage/resource threshold.

## Scope audit and safe recovery

Before committing, compare working-tree and staged paths with the workspace baseline and mission-owned scope. Keep unrelated protected state out of the commit.

Authorization to change a file does not authorize a destructive write method. Before replacing a whole file, inspect its current content, diff, and baseline. Prefer a targeted patch that preserves protected state. Replace a whole file only when it is proven mission-owned and no protected content can be discarded.

- If an unrelated file is only staged, unstage it without changing its working-tree content.
- If this mission changed a protected pre-existing file and a trustworthy baseline exists, restore it and verify the baseline hash or content.
- If an unrelated file is confirmed to have been created by this mission, remove it safely.
- If a protected pre-existing file was changed and no trustworthy baseline exists, do not guess or use Git to fabricate prior content. Treat this as a repository-safety blocker and human decision boundary.

After safe recovery, rerun the scope audit and continue validation, commit, and publication when clear. A mechanical, verified recovery is not a reason to stop the mission.

When a mission's delivery contract requires a Git remote, complete validation and scope audit before commit, push, and remote verification. Write a minimal handoff only after that delivery state is verified; explicitly record an unpushed or unverified state instead of implying publication.

Before using or publishing a mission artifact, verify that its filename, stated mission or revision, core content mapping, and authoritative reference agree. If they conflict, stop that artifact's use or publication until corrected; a filename does not establish content identity.

When filesystem indirection blocks a required write, first verify read-only the canonical root, target ownership, that the target remains inside the canonical worktree, and tracked-path equivalence. Do not delete, move, or recreate the indirection. If all checks establish safe equivalence, use the verified physical path; otherwise preserve the state as a repository-safety blocker with its evidence.

## Completion

At the mission checkpoint, report the outcome, changed files, verification, deferred validation, delivery reference when applicable, and any remaining blocker, risk, or required human decision.

## When not to use

Do not use this skill to define product requirements, plan an ambiguous mission, select architecture, perform security or code review, debug a failure, prescribe broad Git workflow, or manage subagents. Use the applicable specialized workflow for those needs.

## Composition

This skill complements established planning, executing-plans, test-driven-development, systematic-debugging, code-review, security-review, Git publication, and visible UX validation workflows. For continuity across multiple already-approved missions, use `continuous-mission-orchestration`; for an execution boundary that needs persistent recovery, use `durable-execution-handoff`. Apply those only when their own trigger condition exists; this skill does not replace or duplicate them.
