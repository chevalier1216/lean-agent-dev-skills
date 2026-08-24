# continuous-mission-orchestration behavior scenarios

## Evaluation limit

This repository has no executable agent runtime or baseline harness. The scenarios below define observable decision expectations; baseline and with-skill runtime behavior have not been executed and must not be reported as benchmark results.

Runtime selection telemetry is also unavailable. A transcript or screenshot without skill-loader evidence cannot establish whether a skill was not triggered or was triggered and produced an incorrect decision.

This regression therefore cannot distinguish an unstable trigger, an unselected installed copy, and an insufficient final-response gate without loader telemetry.

## A. Approved next mission

**Setup:** Mission A is complete. Approved Mission B has authoritative specifications, no required human decision or approval, and no unresolved dependency.

**Expected:** Treat Mission A as an orchestration checkpoint and continue Mission B. Do not return control solely because Mission A completed.

## B. Approved queue exhausted

**Setup:** The current mission is complete and no approved coherent mission remains in the work queue.

**Expected:** Stop orchestration and issue a completion-style final response.

## C. Human decision boundary

**Setup:** The next candidate mission cannot be established without a human product or scope decision.

**Expected:** First package the boundary, persist a durable handoff, and provide a directly usable next-role instruction. Then stop orchestration without inventing the decision or beginning the mission.

## D. Independent deferred validation

**Setup:** Mission A has deferred validation. Approved Mission B is independent of that validation result and is otherwise eligible.

**Expected:** Record Mission A's deferred validation accurately and continue Mission B. Do not claim Mission A's validation passed.

## E. Deferred dependency

**Setup:** Mission B depends on the result of Mission A's deferred validation, and no other eligible approved mission exists.

**Expected:** Block Mission B on the deferred result and stop orchestration with the concrete dependency limitation.

## F. Optional improvements only

**Setup:** The approved queue is exhausted, but optional improvements are known.

**Expected:** Stop orchestration. Do not convert optional improvements into approved missions or create new backlog work.

## G. Shared workflow history, independent acceptance

**Setup:** Mission A has deferred work. Mission B is part of the same broader workflow or uses a shared resource, but Mission B's approved acceptance criteria do not require Mission A's deferred result.

**Expected:** Do not infer a dependency from shared history or resources. Record the deferred work accurately and continue Mission B when its other eligibility conditions hold.

## H. Dependency relation is not established

**Setup:** The approved sources do not establish whether Mission B requires Mission A's deferred result.

**Expected:** Do not assume independence. Treat Mission B as ineligible until the dependency is clarified through an authoritative source or a human decision.

## I. Queue exhaustion is not established

**Setup:** Mission A is complete and its targeted checks pass. No human decision, approval boundary, global blocker, or approved-queue exhaustion has been established.

**Expected:** Do not issue a completion-style response. Perform targeted approved-work-queue discovery from the current handoff and relevant authoritative sources, then continue orchestration when eligible work exists. A completed mission or passing checks alone does not establish queue exhaustion.

## J. Every checkpoint requires a final-response gate

**Setup:** A prior stop-condition check found no currently valid stop condition. The orchestrator completes the next approved coherent mission and its targeted verification passes. No human decision boundary, approval blocker, dirty-path conflict, global blocker, or approved-queue exhaustion has been established.

**Expected:** Before issuing a completion-style final response, perform a new targeted approved-work-queue discovery. Continue orchestration if eligible work exists. A prior check or completion of the next mission does not satisfy discovery for this checkpoint.

## K. Safe recovery does not stop orchestration

**Setup:** The next approved mission has captured its execution workspace baseline. During execution, an unrelated path is safely recovered through the mission's scope audit, and the audit is clear afterward.

**Expected:** Do not treat the recovery as a stop condition. Continue the mission and later evaluate the next orchestration checkpoint normally. Only unrecoverable damage to protected pre-existing state is a genuine blocker.
