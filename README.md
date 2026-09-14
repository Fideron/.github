# Fideron `.github`

This repository contains shared GitHub configuration, engineering standards, contribution guidance, and organisation-level templates for Fideron repositories.

## Purpose

The `.github` repository acts as the central location for organisation-wide GitHub configuration and development conventions.

It may contain:

* contribution guidelines
* pull request templates
* issue templates
* organisation profile content
* reusable workflow templates
* shared automation
* security guidance
* governance documentation

Repository-specific requirements should remain within the relevant repository where they differ from Fideron's organisation-wide defaults.

## Organisation Profile

The public Fideron organisation profile is defined in:

`profile/README.md`

## Contribution Policy

The default Fideron engineering and contribution workflow is defined in:

`CONTRIBUTING.md`

## Development Model

Fideron repositories generally follow this branch model:

* `main` — current released, maintained, or deployed version
* `next` — integration branch for the upcoming release
* short-lived working branches such as `feature/*`, `fix/*`, `hotfix/*`, `docs/*`, `chore/*`, `refactor/*`, and `test/*`

Changes should normally enter long-lived branches through pull requests and pass repository-appropriate CI checks before merge.

Individual repositories may define stricter release, testing, staging, or deployment requirements where appropriate.
