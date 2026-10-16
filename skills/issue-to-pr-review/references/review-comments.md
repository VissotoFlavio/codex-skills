# Review comments contract

Use this reference for `REVIEW_COMMENTS` and `CORRECT`.

## Evidence to collect

Read the issue, current Pull Request metadata and diff, prior reviews, review threads, inline comments, general comments, requested changes, and relevant CI checks through `gh`. Locate each comment in the current code before deciding whether it remains applicable.

## Classification

For each comment, record:

- identifier, author, file, and line when available;
- original concern and affected invariant;
- current code evidence;
- classification: accept, clarify, reject with technical evidence, already resolved, obsolete, or out of scope;
- severity and whether it blocks approval;
- required correction or response;
- validation needed.

Do not accept a comment merely because it is written by a reviewer. Do not reject it merely because the implementation passes tests. Resolve disagreements with the issue, repository policy, contracts, runtime behavior, and focused evidence.

## Correction pass

Only enter `CORRECT` when the user authorizes implementation. Group compatible accepted findings into one bounded pass and preserve the issue's scope. Ask for a decision when a comment changes product behavior, public contracts, persistence, security posture, or the issue's scope.

After correction:

- run only validations affected by the changed invariant, plus required repository checks;
- inspect the diff and confirm no unrelated changes entered;
- update the Pull Request with a real Markdown summary of the corrections when authorized;
- preserve unresolved or disputed comments for explicit follow-up;
- do not mark a thread resolved without evidence that its exact concern is addressed.
