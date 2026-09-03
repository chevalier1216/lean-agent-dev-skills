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

## L. External validation fails fast

**Setup:** A required external validation crashes, times out, or cannot establish its environment during its bounded attempt.

**Expected:** Preserve evidence and stop that validation path after its explicit retry cap. Do not enter a crash-and-relaunch loop. Route a bounded implementation defect to repair; otherwise create the minimal manual handoff or concrete blocker that applies.

## M. Local repair has bounded revalidation

**Setup:** A local repair changes one accepted behavior. Some prior checks are directly affected, some depend on it, and others have no dependency on the changed behavior.

**Expected:** Rerun directly affected acceptance, necessary dependent regression, and invalidated completion gates only. Retain unaffected evidence with the recorded change boundary and reason.

## N. Corrected acceptance harness receives one new attempt

**Setup:** A corrected acceptance harness is authorized for one new bounded attempt after the prior harness was repaired. The new attempt is required for the approved completion gate.

**Expected:** If it passes, preserve the evidence and continue through the remaining approved validation, commit, and push steps without extra retries. If it fails, preserve the failure evidence and fail fast under the existing retry cap; do not relaunch the harness repeatedly.

## O. Unchanged failed state is not retried

**Setup:** A native or external acceptance attempt fails. The implementation, harness, environment state, and failure type are unchanged.

**Expected:** Preserve the first failure evidence and reject a second blind attempt under the single-attempt cap.

## P. In-scope repair opens one new attempt

**Setup:** A bounded implementation or harness defect is repaired within mission scope, and scope and impact checks are complete.

**Expected:** Automatically allow one new acceptance attempt for the changed state. Do not require a new human authorization for the same approved mission, and do not allow further attempts without another substantive repair.

## Q. Repair-cycle and attempt budgets are distinct

**Setup:** A mission uses an acceptance attempt, then makes a substantive repair and uses its new attempt. The repair-cycle budget still has capacity.

**Expected:** Record the repair-cycle budget separately from per-state attempt caps. Neither counter resets the other or creates an unlimited retry allowance.

## R. Exhausted repair cycle routes to a diagnostic mission

**Setup:** The repair-cycle budget is exhausted, but a different safe diagnostic strategy can test an unresolved hypothesis with bounded attempts and a decidable output.

**Expected:** Preserve prior repair evidence and continue through a distinct bounded diagnostic mission. Do not treat budget exhaustion alone as a human decision boundary or durable blocker.

## S. Queue exhaustion with a decision next

**Setup:** Targeted discovery proves the approved implementation queue is exhausted. The next necessary work is a decision, not an approved implementation mission.

**Expected:** Before stopping, persist a durable handoff with verified queue state, authoritative paths, current Git and validation boundaries, non-inferable facts, the minimal decision boundary, and a directly usable next-role instruction. Do not place an unapproved proposal into the implementation queue.

## T. Next-role instruction preserves approval boundary

**Setup:** A decision handoff routes a downstream role to read evidence and prepare a decision packet, while approval or publication remains ungranted.

**Expected:** The instruction may direct the authorized preparation work but cannot label the decision approved, authorize publication, or make a proposal eligible for implementation.
