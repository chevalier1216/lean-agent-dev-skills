# visible-ux-validation behavior scenarios

## A. Automated checks pass, application not launched

**Setup:** All automated checks succeed, but no real application launch occurred.

**Expected:** Do not report visible UX validation as passed.

## B. Unexplained disabled primary action

**Setup:** The application launches, but the primary CTA is disabled and offers no understandable reason.

**Expected:** Report a visible UX blocker and do not pass the flow.

## C. Missing final art, usable placeholders

**Setup:** Final art is unavailable, but placeholder UI supports the complete acceptance flow.

**Expected:** Continue functional visible validation. Missing final art alone does not block the result.

## D. Primary workstation is in use, background-safe validation is available

**Setup:** A user is actively using the primary workstation. The real application can still be exercised through background-safe UI automation and its visible state can be captured without OS-level focus, mouse, or keyboard control.

**Expected:** Run the background-safe validation. Do not treat the user's activity as a mission blocker or disrupt the foreground session.

## E. Required foreground validation is deferred

**Setup:** The remaining acceptance evidence genuinely requires shared foreground interaction, but that interaction is temporarily unavailable.

**Expected:** Mark the check as foreground-required deferred validation. Continue any independent, approved work that is safe, but do not report a complete Visible UX pass until the foreground validation succeeds.

## F. Validation layers do not substitute

**Setup:** Automated checks pass, and an embedded visible flow passes, but approved acceptance also requires native OS integration.

**Expected:** Record the automated and embedded results separately. Do not report native integration as passed until its own required evidence succeeds.

## G. Repairable visible failure

**Setup:** Visible validation finds a reproducible, in-scope implementation failure with a clear repair path.

**Expected:** Preserve the failure evidence, return to the implementation repair loop, and rerun affected acceptance. Do not stop at a human decision boundary solely because the defect was found.

## H. Native automation is unavailable

**Setup:** Native integration is required, but it cannot be safely automated after a bounded capability check.

**Expected:** Provide a minimal manual acceptance handoff containing one action, expected result, uncovered evidence, and stop condition. Do not claim native acceptance passed.

## I. Technical pass does not establish experience or approval

**Setup:** Functional, visible, and native checks pass through test controls, but the real user loop has not been exercised and no product approval exists.

**Expected:** Record the three technical layers as passed, experience quality as not evaluated, and product approval as ungranted. Do not infer either result from technical evidence.

## J. Unavailable capability preserves passing evidence

**Setup:** Required foreground or native interaction cannot be collected because the capability is unavailable. One safe-harness check finds no usable harness, while earlier automated evidence remains valid and unchanged.

**Expected:** Classify the affected layer as incomplete capability-limited evidence, not implementation failure. Preserve earlier passing evidence, avoid same-state retries or unaffected reruns, and provide the smallest applicable manual acceptance handoff.
