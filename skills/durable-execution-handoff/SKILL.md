---
name: durable-execution-handoff
description: Use when execution may cross a resource, context, runtime, machine, or agent boundary and project work must remain resumable from persistent sources.
---

# Durable Execution Handoff

Preserve a minimal, durable execution checkpoint so project work can resume without the prior conversation or execution context.

This skill handles interruption and resumption boundaries. It does not define missions, implement work, manage a work queue, prescribe Git methodology, or replace backups and project logging.

## Checkpoint before interruption

When a resource, context, or environment boundary is approaching, do not begin a new coherent mission. Finish the nearest safe checkpoint, run necessary verification, and persist safely deliverable coherent work to the canonical remote. If dirty work is unavoidable, preserve it and record its ownership, intent, and affected scope.

Write a minimal resume handoff. Do not make conversation context the only project memory.

## Minimal handoff

Record only:

- repository, branch, HEAD, and remote status;
- current product state and paths to relevant authoritative sources;
- current approved work queue and deferred validation;
- dirty or in-progress work ownership; and
- genuine human decisions still required.

A handoff is an index and checkpoint, not a compressed conversation transcript. Exclude copied conversation, broad history, complete specifications, logs, Git history, and full skill contents.

## Resume

Use the existing repository; do not recreate it. Read project instructions, verify actual branch, HEAD, remote, and dirty state, then read the minimal handoff. Load only the authoritative sources and installed skills it points to, verify dirty-work ownership, and resume the highest-priority eligible approved mission.

When a handoff conflicts with an authoritative source or actual Git state, the authoritative source and actual Git state win. Record the handoff as stale rather than following the conflicting claim.

## Safety and boundaries

Do not reset, clean, discard, overwrite, or guess ownership of unrelated dirty work. Do not force-push, treat drafts or research as approved requirements, rebuild product requirements because a handoff is missing, or create a replacement repository for the canonical one.

Use `lean-mission-execution` within a mission, `continuous-mission-orchestration` for continuity across approved missions, and `visible-ux-validation` for user-facing validation. This skill only makes those workflows durable across execution boundaries.
