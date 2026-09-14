# Security Policy

Fideron takes the security of its software, infrastructure, and users seriously.

## Reporting a Vulnerability

Please do not disclose suspected security vulnerabilities through public GitHub issues, discussions, pull requests, or other public channels.

Where a repository supports GitHub Private Vulnerability Reporting, use that mechanism to report security issues privately.

If Private Vulnerability Reporting is not available, use the private contact method documented by the relevant repository or Fideron organisation profile.

When reporting a vulnerability, please include where possible:

* the affected repository, component, or version
* a clear description of the issue
* steps required to reproduce the behaviour
* the potential security impact
* any relevant logs, screenshots, or proof-of-concept information
* suggested mitigations, if known

Do not include secrets, credentials, personal data, or other sensitive information unless necessary to demonstrate the issue.

## Disclosure

Please allow reasonable time for a vulnerability to be investigated and remediated before public disclosure.

Fideron may coordinate disclosure timing where a vulnerability affects users, deployed systems, dependencies, or downstream consumers.

## Supported Versions

Security support is generally provided for the current released and maintained version represented by the repository's `main` branch.

Repositories may define additional support policies for older versions, release lines, or long-term support branches.

## Security in Development

Fideron repositories should apply security controls appropriate to their risk profile.

These may include:

* dependency scanning
* secret scanning
* code scanning
* static analysis
* security-focused testing
* protected branches
* restricted deployment permissions
* environment approval gates

Security requirements may vary between repositories and should be documented where additional controls are required.

## Scope

This policy defines Fideron's default security-reporting expectations.

Individual repositories may provide more specific security policies where their risk profile, deployment model, or user impact requires additional guidance.
