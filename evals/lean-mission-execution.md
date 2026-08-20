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
