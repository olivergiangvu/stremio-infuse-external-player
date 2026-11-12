# Stable Release Governance — Feature Preservation

**Effective 12 November 2026 · Applicable to every current and future repository under `olivergiangvu`.**

This policy addresses a real release regression: the verified IINA Episode Info Plus macOS Now Playing poster feature worked on beta.3, but a later v1.3.4 release omitted the module and its installable package. That build was reclassified as historical pre-release; v1.3.5 restored functionality with CI regression/package checks.

## Mandatory policy (MUST)

1. **Stable is a superset of accepted functionality.** Changes may improve or fix behavior, but may not silently remove a previously tested and approved feature. Removal/deprecation requires an explicit owner-approved decision and documented migration/impact.
2. **Branch from the latest Stable baseline.** Compare candidate source against the current `main` (or `master`) and the last accepted release. Never blindly promote an older parallel branch that lacks newer fixes.
3. **Define and retain protected feature contracts.** Every shipped feature that caused a bug/regression or was explicitly accepted must have a regression test or an unambiguous manual acceptance gate. No feature may be treated as "gone" merely because a new task focuses on something else.
4. **Test the actual deliverable.** CI must test packaging integrity (the real Docker image, app bundle, `.iinaplgz`, distribution ZIP, binary or other output), including runtime dependencies, scripts, configs and entry points. Passing source-code checks alone is not a release gate.
5. **Protect integration and configuration contracts.** Keep API compatibility, environment variables, persistent storage, credentials handling, stream/metadata interfaces, existing user options, and consuming clients intact unless a documented migration is approved.
6. **Require real-environment acceptance** for relevant functionality. An isolated unit mock is insufficient proof for IINA/macOS Now Playing, Apple media controls, SSH/Docker services, streaming endpoints or external client integrations.
7. **No missing proof → no Stable.** A candidate without a complete regression matrix, successful CI and required real-world smoke tests stays Beta/RC. Do not label it Stable or `latest`.
8. **Rollback and traceability.** Preserve historical Git tags and source. If a published Stable is discovered to be non-compliant, immediately replace it with an accepted fixed Stable and demote the old GitHub release to pre-release / historical; do not silently rewrite or erase source history.
9. **One-way release workflow.** PR → full existing test suite + protected capability checks → real package verification → affected integration smoke tests → explicit owner acceptance → Stable tag / release. The same checklist applies to hotfixes.
10. **Every new repo adopts this document before its first Stable release.** Repository-specific `docs/RELEASE_GATES.md` or equivalent must list its actual feature inventory and test commands. Do not invent a test status: explicitly identify untested capabilities.

## PR / Stable acceptance checklist

- [ ] Based on latest accepted Stable; changes reviewed against last accepted feature list
- [ ] Existing functionality preserved; any intentional removals approved and documented
- [ ] All applicable unit, integration and previous regression tests pass
- [ ] Final installable/deployable artifact verified, including required modules
- [ ] Manual smoke tests for OS/native/external/Docker behavior documented where applicable
- [ ] No regressions to configuration, state/data persistence, permissions or other services
- [ ] Version/tag/release notes and rollback route are consistent
- [ ] Only then: owner approves Stable promotion; CI evidence linked

## Enforcement scope

This document is a mandatory project policy; the **mechanical CI guard** must be implemented per repository using its actual technology and artifact format. A policy text or checked checkbox alone cannot prove no regression. Until a repository-specific CI gate and acceptance evidence exist, its release candidate must not be promoted to Stable.

Reference implementation: [Episode Info Plus v1.3.5 release gates](https://github.com/olivergiangvu/iina-episode-info-plus/blob/main/docs/RELEASE_GATES.md).
