# Related work and boundaries

Existing agent-engineering practices already address planning, plan execution, test-driven development, systematic debugging, code review, security review, and Git publication. This repository does not attempt to recreate those workflows.

`lean-mission-execution` focuses on avoiding mission-level context and coordination amplification when an implementation mission is already defined. It composes with specialized workflows when their triggers apply.

`visible-ux-validation` focuses on the gap between automated correctness evidence and actual user-visible, interactive usability. It complements automated testing and does not replace full QA, requirements, or visual design.

`continuous-mission-orchestration` focuses on whether an orchestrator should continue from one approved coherent mission to another. It does not plan or execute individual missions, generate backlog work, or replace approval decisions.

`durable-execution-handoff` focuses on preserving and restoring execution state across runtime boundaries. It does not decide which mission to run or replace mission execution, orchestration, Git workflows, or backup systems.
