# Contributing to Fideron

Fideron repositories follow a consistent development and release workflow designed to keep changes reviewable, tested, and traceable.

Individual repositories may define additional requirements where appropriate, but the standards in this document form the default engineering workflow across the organisation.

## Branch Model

Fideron uses two long-lived branches:

* `main` — the current released, maintained, or deployed version of the software.
* `next` — the integration branch for the next release, patch, or deployment.

The `main` branch should always represent software that has already been released or is currently considered the maintained production version.

The `next` branch may contain completed work that has not yet been released.

Direct commits to `main` and `next` should be avoided. Changes should normally enter these branches through pull requests.

## Working Branches

Changes should be developed on short-lived branches created from the appropriate base branch.

Recommended branch prefixes include:

* `feature/` — new functionality
* `fix/` — bug fixes intended for the next release
* `hotfix/` — urgent fixes based directly on the current release
* `docs/` — documentation-only changes
* `chore/` — maintenance, tooling, dependency, or repository housekeeping changes
* `refactor/` — internal restructuring without intended behavioural change
* `test/` — test-only changes where appropriate

Example branch names:

* `feature/github-provider`
* `fix/null-project-state`
* `hotfix/authentication-regression`
* `docs/api-overview`

## Pull Requests

All meaningful changes should be submitted through a pull request.

Pull requests should:

* describe what changed
* explain why the change is required
* identify any relevant issues
* include tests where appropriate
* update documentation where behaviour or usage changes
* pass all required repository-specific CI checks before merge

Pull requests should remain focused and reasonably scoped.

Large changes may be split into multiple pull requests where doing so improves reviewability.

## Stacked Pull Requests

Stacked pull requests may be used when a larger change contains multiple independently reviewable layers.

Example:

```text
next
└── feature/domain-layer
    └── feature/api-layer
        └── feature/ui-layer
```

Each pull request should target the branch directly beneath it.

As lower branches are merged, dependent pull requests should be rebased or retargeted toward `next`.

Stacked pull requests should not be used merely to avoid keeping a pull request appropriately scoped.

## Merge Strategy

Fideron preserves meaningful Git ancestry accross the development and release lifecycle.

Unless a repository documents a different requirement:

* working branches are merged into `next` through pull requests
* release pull requests merge `next` into `main` using a merge commit
* release pull requests should not be squash-merged or rebased
* hotfix pull requests should preserve sufficient history for the fix to be propagated into `next`

Individual repositories may choose an appropriate merge strategy for working branches where doing so does not interfere with release traceability.

The release boundary itself is represented by the merge commit from `next` into `main`, the corresponding Semantic Version tag, and the associated GitHub Release.
## Review

Pull requests should be reviewed before merge where practical.

Review should consider:

* correctness
* maintainability
* test coverage
* architecture
* compatibility
* security implications
* documentation impact
* whether the change belongs in the intended release

Repositories may define additional review requirements.

## Continuous Integration

Each repository defines its own required CI checks based on the software it contains.

Typical checks may include:

* unit tests
* integration tests
* linting
* formatting checks
* compilation or build validation
* static analysis
* security scanning
* dependency validation

A pull request should not be merged while required checks are failing.

## Release Readiness

Release-readiness requirements are repository-specific.

Depending on the project, these may include:

* integration testing
* end-to-end testing
* staging deployment
* release candidates
* manual verification
* smoke testing
* security review
* deployment approval gates

Repositories should document their own release-readiness requirements where they differ from the organisation default.

## Releases

When the contents of `next` are considered ready for release, a release pull request should be opened from:

`next` → `main`

This pull request represents the complete difference between the currently released version and the upcoming release.

The release pull request should:

* pass all required checks
* contain or reference the intended release notes
* use the appropriate Semantic Version
* confirm that repository-specific release requirements have been satisfied

Release pull requests should be merged using a merge commit.

They should not normally be squash-merged or rebased into `main`.

Preserving the ancestry of `next` ensures that:

* the individual pull requests and commits that formed the release remain part of the released history
* `main` and `next` retain a common Git ancestry after release
* subsequent comparisons between the released and upcoming versions remain accurate
* a separate post-release synchronisation merge from `main` back into `next` is not normally required

The release merge commit provides the boundary between releases on `main`.

Once merged, `main` becomes the new released or maintained version and should be tagged with the corresponding Semantic Version.

Development may then continue from `next`, which already contains the complete history of the newly released version.

## Semantic Versioning

Versioned Fideron software should follow Semantic Versioning:

`MAJOR.MINOR.PATCH`

Examples:

* `1.0.0`
* `1.4.0`
* `1.4.1`
* `2.0.0`

In general:

* `MAJOR` — incompatible or breaking changes
* `MINOR` — backward-compatible functionality
* `PATCH` — backward-compatible fixes

Repositories may use pre-release identifiers where release candidates or preview versions are appropriate.

Examples:

* `2.0.0-rc.1`
* `2.0.0-beta.2`

## GitHub Releases

Released versions should use GitHub Releases where versioned releases are applicable.

A release should normally include:

* a Semantic Version tag
* generated or curated release notes
* a summary of significant changes
* references to relevant pull requests or issues where useful

The repository's `main` branch should correspond to the latest maintained release.

## Changelog

Release history should be traceable through Git history and GitHub Releases.

Where a repository maintains a `CHANGELOG.md`, entries should describe user-visible or operationally significant changes rather than duplicating every individual commit.

Release notes may be generated automatically from merged pull requests where appropriate.

## Hotfixes

Urgent production fixes should branch from `main`.

Example:

```text
main
└── hotfix/critical-auth-fix
```

The hotfix should be submitted to `main` through a pull request and released as the appropriate patch version.

After release, the fix must also be propagated into `next` so that the upcoming release does not reintroduce the resolved issue.

This may be achieved through merge, cherry-pick, or another appropriate Git operation depending on repository history.

## Repository-Specific Rules

Repositories may extend this policy with their own documentation.

Repository-specific rules take precedence where they define stricter requirements, including:

* required test suites
* staging requirements
* deployment gates
* release candidate processes
* environment promotion rules
* platform-specific contribution requirements

Repositories should not weaken the core guarantees that:

1. `main` represents released or maintained software.
2. `next` represents the upcoming release line.
3. changes should be reviewed through pull requests.
4. required CI checks should pass before merge.
5. releases should remain traceable through Git history and release metadata.

## Questions and Discussions

For repository-specific questions, open an issue or discussion in the relevant repository where enabled.

Organisation-wide engineering process changes should be proposed through the Fideron `.github` repository.
