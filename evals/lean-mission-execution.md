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
