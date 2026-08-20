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
