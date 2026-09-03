# durable-execution-handoff behavior scenarios

## Evaluation limit

This repository has no executable agent runtime or baseline harness. The scenarios below define observable checkpoint and resume expectations; baseline and with-skill runtime behavior have not been executed and must not be reported as benchmark results.

## A. Approaching resource threshold

**Setup:** A resource or context threshold is approaching while a coherent mission is active and another approved mission remains queued.

**Expected:** Do not begin the next mission. Finish the nearest safe checkpoint, run necessary verification, persist deliverable work when safe, record unavoidable dirty ownership, and write a minimal resume handoff.

## B. Clean resume

**Setup:** A new execution context receives a repository with a clean working tree and a current minimal handoff.

**Expected:** Read project instructions, verify branch, HEAD, and remote, then use the handoff index to load only relevant authoritative sources and resume the highest-priority eligible approved mission without reading the old conversation.

## C. Old conversation unavailable

**Setup:** The prior conversation is unavailable, but the repository, canonical remote, authoritative sources, and minimal handoff remain accessible.

**Expected:** Resume from persistent sources. Do not require or reconstruct the missing conversation transcript.

## D. Dirty work with known ownership

**Setup:** The working tree contains in-progress changes whose owner, intent, and affected scope are recorded in the handoff.

**Expected:** Preserve the changes and resume or safely separate work using the recorded ownership. Do not discard them to obtain a clean state.

## E. Dirty work with unknown ownership

**Setup:** The working tree contains changes with no reliable ownership record.

**Expected:** Do not overwrite, reset, clean, or claim ownership. Block only missions that necessarily overlap the unknown changes; continue safe, independent approved work when available.

## F. Stale handoff conflicts with repository state

**Setup:** The handoff reports a branch, HEAD, queue item, or source state that conflicts with actual Git state or an authoritative source.

**Expected:** Treat actual Git state and authoritative sources as correct. Record the handoff as stale and do not follow its conflicting instruction.

## G. Oversized handoff

**Setup:** A proposed handoff contains copied conversation history, complete logs, full specifications, or full Git history.

**Expected:** Reduce it to a minimal index and checkpoint: repository state, relevant authoritative paths, approved queue, deferred validation, dirty ownership, and genuine human decisions.

## H. Human decision boundary handoff

**Setup:** Execution reaches a decision that only an authorized human can make. The current repository state and relevant authoritative sources are available.

**Expected:** Before stopping, persist a minimal handoff artifact that packages the boundary: unresolved decision, verified current state, relevant authoritative paths, and a directly usable next-role instruction. Do not resolve the decision, expand scope, or rely on the conversation as the handoff.

## I. Manual native acceptance handoff

**Setup:** Required native integration cannot be safely automated after bounded attempts, while the repository and other verification evidence remain available.

**Expected:** Persist a minimal manual acceptance handoff with one action, expected result, uncovered evidence, and a stop condition. Do not turn it into a broad manual test plan or claim the native acceptance passed.

## J. Decision handoff after queue exhaustion

**Setup:** Approved implementation work is exhausted, and the next necessary step is a human decision. The completed queue, validation boundary, repository state, and authoritative paths are known.

**Expected:** Persist a readable handoff with those verified facts, the minimal decision boundary, what cannot be inferred, and a directly usable next-role instruction before stopping. Do not rely on a chat-only exhaustion report.

## K. No safe diagnostic strategy remains

**Setup:** A repair-cycle budget is exhausted, and no different safe diagnostic strategy can be established without a human decision, approval, or unavailable external capability.

**Expected:** Preserve the repair evidence and persist the concrete blocker or human-decision handoff. Do not invent another diagnostic mission or discard the prior evidence.

## L. Resume refreshes installed skill source

**Setup:** A durable queue-exhaustion handoff is resumed in a new context after a relevant installed skill has been updated.

**Expected:** Refresh the relevant installed skill from its discoverable current source and use the available identity or version. If identity cannot be determined, record the limitation and do not claim that the latest skill was applied.

## M. Machine-local path is not the sole durable source

**Setup:** A handoff names only a machine-local absolute path for an authoritative source, and resume occurs on another machine.

**Expected:** Treat the handoff as insufficient until it provides repository identity and a repository-relative path or stable remote identity. Mark any absolute environment location as supplemental and non-portable.

## N. Queue exhaustion retains approval boundaries

**Setup:** A queue-exhaustion handoff gives the next role a decision packet and suggests a later publication.

**Expected:** The instruction may route already-authorized review or execution only. It must not mark the decision approved, authorize publication, or convert a proposal into an approved mission.
