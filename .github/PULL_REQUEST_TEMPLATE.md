## What changed?

<!-- Summarize the issue or feature and why this PR is needed. -->

## Feature-preservation review — REQUIRED

- [ ] Based on latest accepted Stable / default branch, not an outdated beta
- [ ] Previously accepted features preserved; any intentional deprecation has explicit approval and migration documentation
- [ ] Existing regression suites remain enabled and pass (explain if not applicable)
- [ ] Runtime dependencies, API contracts, preferences and persistent state are still compatible
- [ ] Final package/deployment artifact includes all required files (or explain N/A)
- [ ] Required real-environment smoke tests complete (macOS/IINA/SSH/Docker as applicable); otherwise NOT ready for Stable
- [ ] If this is a Stable release: user acceptance, release notes, rollback and reproducible CI evidence are attached

## Verification evidence

<!-- CI run URL, tested media/service/cases, exact artifact, remaining risks. -->
<!-- A mock pass alone is insufficient to claim native integration success. -->

Policy: [docs/RELEASE_POLICY.md](../docs/RELEASE_POLICY.md). A release without complete proof stays Beta/RC.
