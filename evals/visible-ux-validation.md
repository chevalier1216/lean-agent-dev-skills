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
