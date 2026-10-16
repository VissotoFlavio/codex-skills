---
name: issue-to-pr-review
description: Execute a GitHub issue through implementation, validation, Pull Request review feedback, correction, and final verification with traceable authority boundaries.
metadata:
  short-description: Run the issue-to-PR review lifecycle
---

# Issue to PR Review

Run a bounded GitHub delivery lifecycle from an authoritative issue through Pull Request creation, review-comment analysis, correction, and verification. Use this skill when the user wants the complete issue-to-PR loop or one of its explicit phases.

This skill complements Asgard; it does not replace Asgard's intent classification, proportional orchestration, specialist routing, or final acceptance. When Asgard is requested, preserve its execution graph and review gates. Do not invoke Asgard recursively from specialist tasks.

## Route the request

Select the narrowest applicable mode:

- **DELIVER**: read an issue, implement its approved scope, validate the candidate, and open a Pull Request when requested by the user.
- **REVIEW_COMMENTS**: inspect existing Pull Request reviews and comments, classify required actions, and report without changing the candidate.
- **CORRECT**: implement explicitly authorized, valid review corrections and update the existing Pull Request.
- **VERIFY**: validate that corrections address the review findings and do not introduce regressions, without changing the candidate.

Do not infer that one mode authorizes the next. Opening a Pull Request is authorized only when requested as part of the delivery activity. Merge, deploy, release publication, migrations, data changes, infrastructure changes, dependency installation, and destructive actions require separate explicit authority.

## Common controls

Read repository instructions before acting. For GitHub, use only `gh` and run `gh auth status` before GitHub operations. If authentication, authorization, scopes, or a command fails, report the sanitized failure and stop; do not silently switch to a browser or another client.

Use the repository's issue, branch, changelog, Pull Request, and release policy. When the repository instructions require it:

- confirm that an authoritative issue exists before creating a delivery branch;
- confirm the branch base before creating any branch;
- synchronize the confirmed base branch with its remote before creating the delivery branch; do not start the activity from a stale base;
- never commit directly to protected branches;
- use the required branch naming convention and keep it within the repository limit;
- inspect the final diff before opening or updating a Pull Request;
- use Conventional Commits for local commits;
- include `Closes #<issue-number>` in eligible Pull Request descriptions;
- update an existing changelog when opening a Pull Request if the project has one;
- send GitHub Markdown with real line breaks, never literal `\\n` text.

Do not alter files, comments, issues, or Pull Requests during a read-only review or verification mode. Do not resolve review threads merely because a code change exists; verify the exact finding first.

## Delivery completion

For **DELIVER**, read the issue and applicable repository instructions, define a proportional Definition of Done, implement only the issue scope, validate the final candidate, inspect the diff, and open the Pull Request if authorized. The Pull Request must identify the issue, summarize the change, list validations, disclose relevant risks, and contain the required closing reference.

Read [delivery.md](references/delivery.md) for the detailed delivery contract.

## Review feedback and correction

For **REVIEW_COMMENTS**, read the issue, current Pull Request, previous reviews, general comments, inline comments, requested changes, current diff, and relevant checks. Classify each comment as actionable, ambiguous, rejected with evidence, already resolved, obsolete, or out of scope. Report the required action and do not modify the candidate.

For **CORRECT**, require explicit authority to change the candidate. Group compatible findings into one bounded correction pass, preserve the issue scope, run only affected validations, inspect the diff, and update the Pull Request with a real Markdown summary. After validating that an adjustment addresses a review finding, mark its GitHub review thread resolved. Do not resolve a thread without evidence that its exact concern was addressed.

Read [review-comments.md](references/review-comments.md) for comment classification and correction rules.

## Final verification

For **VERIFY**, compare the current candidate with the prior reviewed state and map every correction to its original finding. Confirm behavior, tests, contracts, security properties, compatibility, and absence of regressions proportional to risk. Re-run only validations affected by the correction or required by repository policy.

Read [verification.md](references/verification.md) for the verification contract.

## Reporting

Keep reports evidence-based and delta-focused. Include the selected mode, authority ceiling, issue and Pull Request identifiers, changed artifacts, validations and results, unresolved risks, blockers, and the final recommendation. For findings, include severity, file and line when available, impact, evidence, and recommended action.
