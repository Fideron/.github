# Fideron Governance

This document defines the default governance model for Fideron's software repositories and organisation-wide engineering standards.

Its purpose is to make technical ownership, decision-making, repository autonomy, and governance changes clear enough that Fideron can operate consistently without depending on undocumented knowledge or continuous intervention from any single individual.

## Scope

This policy applies to:

* the Fideron GitHub organisation
* organisation-wide engineering standards
* shared development and release conventions
* repository ownership and maintainership
* changes to governance documentation
* escalation of cross-repository technical decisions

Individual repositories may define additional governance rules where appropriate.

Repository-specific governance must not conflict with organisation-wide requirements unless an explicit exception has been documented.

## Governance Principles

Fideron governance should favour:

* clear ownership
* documented decisions
* reviewable change
* technical autonomy within defined boundaries
* minimal unnecessary process
* traceable releases
* reversible decisions where practical
* automation over repeated manual enforcement
* repository-specific controls where risk differs
* organisation-wide consistency where shared standards provide value

Process should exist to reduce ambiguity and operational risk, not to create unnecessary bureaucracy.

## Organisation-Level Governance

The Fideron `.github` repository is the source of truth for organisation-wide GitHub governance and engineering conventions.

Organisation-level governance includes:

* contribution standards
* branch and pull request conventions
* release conventions
* Semantic Versioning policy
* shared issue and pull request templates
* security expectations
* shared automation
* organisation-wide workflow guidance
* future common repository standards

Changes to these standards should be made through the normal Fideron development workflow.

The released version of the `.github` repository on `main` represents the currently active governance standard.

The `next` branch represents the proposed governance standard for the next release.

## Repository Ownership

Each repository should have clearly identifiable maintainership.

Maintainers are responsible for:

* repository health
* review of proposed changes
* appropriate testing
* release readiness
* security considerations
* dependency maintenance
* documentation quality
* enforcement of repository-specific controls

Where multiple maintainers exist, ownership should be shared sufficiently to avoid unnecessary dependence on a single person.

Critical repositories should not remain indefinitely dependent on one maintainer where operational continuity requires broader access.

## Repository Autonomy

Repositories may define their own requirements for:

* test strategy
* integration testing
* staging
* release candidates
* deployment
* infrastructure
* code quality thresholds
* security controls
* environment approval
* operational monitoring

These requirements should reflect the technical and operational risk of the software.

Repository-specific processes may be stricter than organisation-wide defaults.

They should not weaken core Fideron guarantees such as protected release branches, traceable releases, required CI where defined, or accurate release history.

## Decision-Making

Technical decisions should be made at the lowest appropriate level.

Repository-local decisions should normally be owned by that repository's maintainers.

Cross-repository decisions, shared standards, or changes affecting organisation-wide engineering practice should be proposed through the Fideron `.github` repository.

Significant decisions should favour written rationale where they:

* affect multiple repositories
* introduce or remove a shared standard
* materially change architecture
* alter release or deployment expectations
* introduce significant operational or security risk
* are difficult or expensive to reverse

The level of documentation should be proportional to the importance of the decision.

## Governance Changes

Changes to organisation-wide governance should follow the same development model used by other Fideron repositories.

Typical flow:

`feature/*`, `fix/*`, `docs/*`, or other appropriate working branch
→ pull request
→ `next`
→ validation
→ release pull request
→ `main`

Working changes should be integrated into `next` through pull requests.

When a governance release is ready, `next` should be merged into `main` through a release pull request using a merge commit.

Release pull requests should not normally be squash-merged or rebased because preserving Git ancestry keeps the released and integration branches correctly related and maintains traceability between individual changes and the release that contains them.

The resulting release merge commit, Semantic Version tag, and GitHub Release together define the release boundary.

Governance changes are versioned using Semantic Versioning.

In general:

* `PATCH` — clarification, correction, or non-behavioural documentation change
* `MINOR` — new backward-compatible governance capability or standard
* `MAJOR` — breaking change to established governance expectations

Released governance changes should be documented through GitHub Releases and release notes.

## Exceptions

A repository may require an exception to an organisation-wide standard where technical, operational, regulatory, security, or platform constraints make the default inappropriate.

Exceptions should:

* be documented
* state the reason
* define the affected repository or scope
* identify any replacement control
* be reviewed periodically where the exception is expected to be temporary

Exceptions should not be used merely to avoid normal engineering process.

## Security and Risk

Security-sensitive decisions should favour least privilege, auditable change, and clearly defined responsibility.

Repositories with greater operational or user impact may require stricter controls than organisation defaults.

Where a security concern conflicts with process convenience, security requirements take precedence.

## Continuity and Delegation

Fideron governance should support delegation.

Important operational knowledge should be documented sufficiently that another authorised maintainer can:

* understand the repository
* review changes
* run required checks
* perform a release
* respond to urgent defects
* maintain deployment or publication workflows
* understand relevant governance constraints

Access, ownership, and process should be structured to reduce single-person dependency over time.

## Review of Governance

Governance should evolve with the organisation.

Policies should be changed when they no longer reflect how Fideron operates, create unnecessary friction, fail to address recurring problems, or need to support a new operating model.

Governance should not be changed solely for cosmetic consistency.

The goal is durable engineering practice, not process for its own sake.
