---
name: visible-ux-validation
description: Use when an implemented user-facing interface, interaction flow, or visible state requires validation in the real application.
---

# Visible UX Validation

Validate an implemented user-facing flow through the actual interactive application.

Automated tests, builds, headless runs, and source inspection alone cannot prove visible UX has passed. This skill validates an implementation; it does not define product requirements or visual direction.

## Validation path

Identify the entry point, user goal, primary interaction path, expected visible states, success condition, and relevant blocked or failure states from authoritative requirements.

Run required targeted automated checks, launch the real application or suitable development build, and exercise the primary path using actual controls. Verify, where applicable:

- information hierarchy and control discoverability;
- enabled, disabled, loading, waiting, progress, success, empty, error, and blocked states;
- understandable reasons for blocked actions;
- expected visible state transitions; and
- the user's next reasonable action.

Complete the acceptance path end-to-end when technically possible. Capture a screenshot, recording, or equivalent visible evidence when the environment supports it.

Placeholders and temporary art do not block functional validation when requirements permit them.

## Result classification

A blocker prevents launch or completion of the required flow, shows an incorrect visible state, hides the next action, or causes crash, corruption, or unusable interaction. Fix in-scope blockers; do not expand the mission into unrelated polish.

If actual visible interaction cannot be performed, report visible validation as incomplete with the concrete limitation. Never claim it passed from automated evidence alone.

## Completion

Report the launch result, exercised flow, verified states, blockers found and resolved, remaining non-blocking issues, and visual evidence produced or the reason it was unavailable.

## When not to use

Do not use this skill to create requirements, choose a visual style, replace automated testing, or conduct full QA. Use it after or alongside an implementation workflow when real user-facing validation is required.
