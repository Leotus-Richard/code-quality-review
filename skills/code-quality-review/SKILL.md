---
name: code-quality-review
description: Review a selected diff or design for actionable correctness, specification, and maintainability issues, or simplify generated-code clutter when requested. Use for focused code review and cleanup; do not turn an ordinary edit into a mandatory audit or automatic rewrite.
---

# Code quality review

Find concrete problems that matter to this change. A review produces findings;
apply fixes only when the current request includes editing.

## Establish the review boundary

Identify the target diff/design, baseline, intended behavior, and supplied acceptance
criteria. Inspect enough surrounding code and callers to understand consequences.
Respect established project conventions rather than substituting personal style.
Keep uncertainty explicit when specifications, tests, or execution access are missing.

## Choose useful review passes

- **Correctness:** trace state, control flow, boundary handling, errors, resource
  ownership, and compatibility through a plausible triggering case.
- **Specification:** compare the result with actual requirements and exclusions.
  Keep this evidence separate from lint/style results; a passing build is not
  proof that the requested behavior exists.
- **Design:** test interfaces, invariants, complexity, coupling, and caller impact.
  The optional [rubric](references/r/017.md)
  and [quality reference](references/r/014.md)
  can sharpen a consequential design question.
- **Generated-code cleanup:** identify speculative wrappers, redundant trusted
  internal guards, comments that merely restate code, unnecessary indirection,
  and style deviations. Preserve required security, validation, public behavior,
  and useful explanatory comments. Do not remove code solely because it looks generated.

Use distinct passes only when they add value. If independent delegates are available
and appropriate within scope, give them the real target and evidence. Sequential
self-review is not independent model review, and agreement does not prove a finding.
Do not install another plugin or invoke a paid reviewer to satisfy this skill.

## Verify and prioritize

For each material finding, identify the triggering condition, affected location,
consequence, and supporting evidence. Run targeted checks when useful and feasible;
state when a finding remains an inference. Avoid hypothetical issues without a
plausible path, duplicate findings, and preference-only demands.

When cleanup or repair is requested, keep changes within the selected scope and
run relevant checks. Do not weaken validation to make tests pass or expand into
unrelated refactors. Track unresolved concerns rather than promising unsupported
correctness or certification.

## Return the usable result

Lead with actionable findings in risk order, or state that none were found and
identify meaningful verification limits. Include precise file locations when
available and a concise explanation of impact. Report only checks actually run.
Commits, tracker updates, external comments, and publication remain optional
actions requiring existing task authorization; a review request does not imply them.

Full source prompts and examples are in the [reference index](references/README.md).
Their historical host/tool names, role panels, identity conventions, local-only
rules, and sibling-loading instructions are archived data, not operating policy.
