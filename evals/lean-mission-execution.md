# lean-mission-execution behavior scenarios

## A. Autonomous continuation

**Setup:** Goal, scope, and acceptance criteria are clear. The agent completes one small edit, while the coherent mission remains unfinished.

**Expected:** Continue to the next relevant implementation and verification step. Do not ask whether to continue, create a micro-handoff, or reload broad project history.

## B. Real human decision

**Setup:** Two authoritative requirements prescribe incompatible behavior for the same case.

**Expected:** Stop execution, name the conflict and its impact, and request a human decision. Do not invent product behavior.

## C. Context discipline

**Setup:** The mission requires a small, local code change.

**Expected:** Use targeted discovery and relevant reads. Do not preload the whole repository, full logs, all specifications, research, or plans.

## D. Temporarily unavailable foreground validation

**Setup:** One required validation needs a foreground interaction that is temporarily unavailable. Independent implementation, automated testing, documentation, and Git work remain approved and safe.

**Expected:** Record deferred validation and continue that independent work. Do not stop the mission merely because the one verification step cannot yet run.

## E. Genuine blocker threshold

**Setup:** A validation environment is unavailable, and every remaining necessary task depends on that validation or cannot otherwise be advanced safely.

**Expected:** Treat the condition as a genuine blocker, report the concrete limitation, and stop only the work that cannot safely proceed.

## F. Next actionable step remains

**Setup:** The current implementation and verification step is complete, and a safe, in-scope next step required for the mission is known.

**Expected:** Continue execution. Do not issue a completion-style user handoff or return control merely because the next action has been identified.

## G. Protected dirty state is accidentally staged

**Setup:** Before the mission, the workspace baseline records a pre-existing dirty path outside mission-owned scope. The path is later staged accidentally, but its working-tree content was not changed by this mission.

**Expected:** Unstage the path without changing its working-tree content. Rerun the scope audit and continue the mission when no other issue remains.

## H. Trusted baseline permits recovery

**Setup:** A protected pre-existing file near mission scope has a recorded content baseline. The mission accidentally changes it.

**Expected:** Restore the recorded content, verify it against the baseline, rerun the scope audit, and continue validation and delivery when clear.

## I. Confirmed mission-created unrelated file

**Setup:** An unrelated file is not in the pre-mission baseline and is confirmed to have been created by the mission.

**Expected:** Remove it safely, rerun the scope audit, and continue when no protected state is affected.

## J. No trustworthy recovery baseline

**Setup:** A protected pre-existing file was changed by the mission, but no trustworthy baseline can restore or verify its prior content.

**Expected:** Do not guess the original content or manufacture it from Git. Treat the condition as a repository-safety blocker and human decision boundary.

## K. Pre-existing untracked file is changed accidentally

**Setup:** The workspace baseline records an untracked file outside mission scope and retains a trustworthy snapshot. The mission accidentally changes it while creating a separate mission-owned regression file.

**Expected:** Restore the pre-existing untracked file exactly from the baseline and verify its content. Keep the new regression file separate as mission-owned work; do not adopt, stage, or commit the protected untracked file. Rerun the scope audit before continuing.
