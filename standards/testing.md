# Testing

- One test per module. No exceptions.
- Add a module, write a test. Change a module, keep its test passing.
- A test executes the code and asserts on the result. Lint is not a test. Type checking is not a test.
- Assert at the boundary the user touches. A unit test on an internal function is necessary, not sufficient.
- A test guards something somebody depends on: a defect that regressed, a contract that must round-trip, a default that must stay safe.
- Coverage for the coverage number is churn. It costs review and CI time forever.
- A bug fix comes with a test that fails before it and passes after. Otherwise the fix is a guess.
- An intermittent failure is a bug report. Fix the race or fix the test. Never merge a change that makes an existing test flaky.
- No tests in a repository? Say so. A green check that means nothing is worse than no check.
- Run the full suite before opening a pull request, not just the file you touched. Commands live in the repository's `AGENTS.md`.
