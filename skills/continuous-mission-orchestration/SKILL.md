---
name: continuous-mission-orchestration
description: Use when an orchestrator reaches a mission checkpoint or manages approved coherent missions and must decide whether work may continue.
---

# Continuous Mission Orchestration

Continue an approved sequence of coherent missions without treating an individual mission checkpoint as a project stop condition.

This skill decides mission-to-mission continuity. It does not define, plan, implement, test, review, publish, or expand an individual mission.

## Orchestration checkpoint

After a mission completes or reports deferred work, inspect the approved work queue. Continue with the next coherent mission when it is already approved, has authoritative specifications sufficient to establish its scope, requires no human decision, crosses no approval boundary, and has no unresolved dependency.

Before declaring the queue exhausted, perform targeted discovery from the current handoff and relevant authoritative sources. A completed mission, passing checks, or absence of a known next mission does not establish exhaustion.

At every orchestrator mission checkpoint, perform that targeted discovery before issuing a completion-style final response unless a currently valid stop condition has already been established.

Before an eligible mission starts, require its execution owner to capture a workspace baseline. Safe automatic recovery within that mission is not a stop condition; only damage to protected pre-existing state that cannot be safely recovered is a genuine blocker.

For native or external validation, use one bounded attempt with an explicit retry cap. On crash, timeout, or inability to establish the test environment, fail that validation path fast and preserve its evidence; do not enter a crash-and-relaunch loop. Route a bounded implementation failure back to repair. Use a minimal manual acceptance handoff or a concrete blocker only when the limitation is outside the executor's safe control.

After a local repair, determine its impact before rerunning validation. Rerun directly affected acceptance, necessary dependent regression, and any completion gate whose evidence the change invalidated. Retain unaffected evidence with its boundary and reason for not rerunning it.

Keep the single-attempt cap for an unchanged implementation, harness, and environment state separate from a bounded repair-cycle budget. A substantive in-scope implementation or harness repair that passes scope and impact checks opens one new single attempt automatically. Do not retry unchanged state or treat a new attempt after repair as unlimited retry.

When the repair-cycle budget is exhausted, preserve its evidence, attempted repairs, budget use, and unresolved assumptions. If a different safe diagnostic strategy exists, continue with a distinct bounded diagnostic mission that states its hypothesis, tool or harness, maximum attempts, decidable output, and stop condition. Route its evidence to repair, minimal manual acceptance, a genuine blocker, or a human decision boundary. Stop only when no such safe diagnostic strategy exists or the next step needs a human decision, approval, or unavailable external capability.

For a mission owner, `mission complete` may mean handoff. For an orchestrator, it means an orchestration checkpoint. Do not return control to the user merely because one mission completed when an eligible next mission exists.

## Deferred work and dependencies

Deferred validation is not a pipeline blocker by itself. Record it accurately and do not claim it passed. Block a downstream mission only when that mission's approved requirements or acceptance actually depend on the deferred result; shared workflow history, timing, or resources do not establish a dependency. If authoritative sources do not establish the relation, do not assume independence: treat the next mission as ineligible until it is clarified.

## Stop and final-response semantics

A human decision boundary is not an immediate stop. Before the final response, package the current boundary, persist the durable handoff, and provide the next role with a directly usable handoff instruction. Then stop without resolving, bypassing, or expanding past the decision.

When targeted discovery establishes that the approved implementation queue is exhausted and the next necessary step is a decision, package and persist the durable handoff before stopping. Include completed and verified queue state, relevant authoritative paths, current Git and validation boundaries, what cannot be inferred, the minimal decision boundary, and a directly usable next-role instruction. A proposal that is not already approved remains ineligible for the implementation queue.

Stop orchestration only when:

- the approved work queue is exhausted;
- a human decision boundary is reached;
- explicit approval is required;
- a genuine blocker prevents every approved mission from progressing safely;
- a configured usage or resource threshold is reached; or
- the execution platform forces a stop.

Do not create features, expand scope, convert optional improvements into approved missions, or generate backlog work merely to keep the pipeline active. Issue a completion-style final response only when one of the stop conditions applies; otherwise continue or report the current orchestration checkpoint as progress.

## Boundaries and composition

Use `lean-mission-execution` for execution within one coherent mission, `durable-execution-handoff` to package a human decision boundary, and `visible-ux-validation` when an individual mission requires real visible UX evidence. This skill only decides whether another already-approved mission may start.

Do not use this skill for implementation workflow, TDD, debugging, code review, Git workflow, planning methodology, backlog generation, or autonomous product design.
