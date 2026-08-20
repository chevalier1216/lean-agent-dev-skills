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
