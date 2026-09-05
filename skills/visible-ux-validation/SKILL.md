---
name: visible-ux-validation
description: Use when an implemented user-facing interface, interaction flow, or visible state requires validation in the real application.
---

# Visible UX Validation

Validate an implemented user-facing flow through the actual interactive application.

Automated tests, builds, headless runs, and source inspection alone cannot prove visible UX has passed. This skill validates an implementation; it does not define product requirements or visual direction.

## Validation environment and interaction discipline

Prefer validation environments in this order:

1. background-safe real UI automation;
2. an isolated GUI session or VM; then
3. a shared foreground session only when necessary.

An active user on the primary workstation does not by itself block the mission. When the application can expose the needed evidence through internal UI events, state transitions, or viewport screenshots, prefer those methods over OS-level mouse, keyboard, or focus control.

Mark a check as **foreground-required validation** only when its acceptance evidence genuinely depends on shared foreground interaction. If that interaction is temporarily unavailable, record it as deferred validation and continue independent, approved implementation, testing, documentation, and Git work that is safe to perform. Do not treat the deferred check as complete.

## Validation path

Identify the entry point, user goal, primary interaction path, expected visible states, success condition, and relevant blocked or failure states from authoritative requirements.

Classify required evidence by layer and record each result separately:

1. functional or state checks validate data, state, contracts, and automatable behavior;
2. embedded or in-application visible checks validate screens, flows, and application interaction;
3. native integration checks validate operating-system behavior or external-application interaction;
4. experience-quality evaluation establishes whether the real user loop was exercised and assessed, when required; and
5. product approval records the authorized product decision, when required.

No layer substitutes for another. Passing technical or visible layers does not establish experience quality or product approval. If test or debug controls prove state transitions without exercising the real user loop, report experience quality as not evaluated. Native integration is a completion gate only when approved requirements reach that layer.

Run required targeted automated checks, launch the real application or suitable development build, and exercise the primary path using actual controls. Verify, where applicable:

- information hierarchy and control discoverability;
- enabled, disabled, loading, waiting, progress, success, empty, error, and blocked states;
- understandable reasons for blocked actions;
- expected visible state transitions; and
- the user's next reasonable action.

Complete the acceptance path end-to-end when technically possible. Capture a screenshot, recording, or equivalent visible evidence when the environment supports it.

Placeholders and temporary art do not block functional validation when requirements permit them.

For native OS or external integration, prefer a bounded deterministic automated harness over manual interaction. The harness should verify required input routing and lifecycle outcomes for the approved behavior. Check once for an existing safe harness. If safe automation is genuinely unavailable, create a minimal manual acceptance handoff with one action, its expected result, the evidence not covered, and a stop condition; do not rerun unaffected evidence.

## Result classification

A blocker prevents launch or completion of the required flow, shows an incorrect visible state, hides the next action, or causes crash, corruption, or unusable interaction. For a reproducible, in-scope implementation failure, record the evidence, return to the repair loop, and rerun affected acceptance before classifying the result. Do not treat a repairable defect as a human decision boundary or expand the mission into unrelated polish.

If actual visible interaction cannot be performed, report visible validation as incomplete with the concrete limitation. If foreground or native capability is unavailable, classify that layer as incomplete evidence rather than an implementation failure unless an implementation defect was observed. Never claim it passed from automated evidence alone.

If acceptance requires foreground-required validation, do not report a complete Visible UX pass until that validation has been performed successfully.

## Completion

Report the launch result, exercised flow, verified states, blockers found and resolved, deferred validation, remaining non-blocking issues, and visual evidence produced or the reason it was unavailable.

## When not to use

Do not use this skill to create requirements, choose a visual style, replace automated testing, or conduct full QA. Use it after or alongside an implementation workflow when real user-facing validation is required.
