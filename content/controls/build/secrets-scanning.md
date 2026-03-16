---
title: Secrets Scanning
weight: 60
control_code: SDLC-CTRL-0006
level: 1
doc-status: Draft
type: DET
areas:
  - build
nist-sp-800-53r5_references:
  - id: ia-5
    note: Authenticator management — secrets scanning detects credentials that have been improperly stored in source code or artefacts.
  - id: sc-12
    note: Cryptographic key establishment and management — scanning ensures cryptographic keys are not hardcoded in code or configuration.
  - id: sc-28
    note: Protection of information at rest — secrets must not be stored unprotected in source code repositories.
  - id: si-7
    note: Software and information integrity — detects embedded secrets that could compromise the integrity of the software supply chain.
  - id: cm-6
    note: Configuration settings — secrets scanning validates that configuration files do not contain hardcoded credentials.
mitigates:
  - credential_and_secret_exposure
  - insider_threat
related_mitigations:
  - SDLC-CTRL-0014
  - SDLC-CTRL-0001
---
# {{% param "title" %}}
{{< area_head >}}

## Summary
Source code, built binaries, and configuration files are scanned for secrets at multiple stages of the development lifecycle to prevent credential exposure.

## Description
Secrets — such as API keys, passwords, tokens, and certificates — must never be hardcoded in source code, configuration files, container images, or Infrastructure as Code. Hardcoded secrets in source code or built artefacts pose a significant security risk, potentially enabling unauthorised access and data breaches.

Automated secrets scanning is implemented at multiple stages of the development lifecycle: pre-commit hooks provide the earliest detection point, CI/CD pipeline scanning catches secrets during build, container image scanning ensures no secrets are baked into images, and IaC scanning verifies secrets are passed via secure parameter injection rather than hardcoded.

## Requirements
* CI/CD pipelines MUST scan for hardcoded secrets in source code and built artefacts
* Code and configuration files MUST NOT include secrets
* Secrets MUST be injected at runtime via secure secret management systems, not hardcoded or stored in source
* Secrets MUST be scoped per environment (dev, test, prod)
* Secrets MUST be rotated periodically with alerts on staleness
* Secrets access MUST be limited to specific CI/CD jobs or roles
* Container images MUST NOT contain hardcoded secrets; secure runtime secret injection MUST be used
* Infrastructure as Code MUST NOT contain hardcoded secrets; secure parameter injection MUST be used
* When secrets are detected in version control, they MUST be immediately revoked and removed from git history using secure rewrite tools
* Third-party integrations SHOULD be audited for secrets exposure

## How we implement this control

We implement secrets scanning through multiple layers of defence:

### Pre-commit Hooks
Developers use pre-commit hooks to scan for secrets before code enters version control. This provides the earliest detection point and prevents secrets from being committed.

### CI/CD Pipeline Scanning
Our CI/CD pipelines include automated secrets scanning at multiple stages:

* Source code scanning during build
* Binary and artefact scanning before deployment
* Container image scanning for embedded secrets

### Remediation Process
When secrets are detected:

1. **Immediate revocation** — compromised secrets are immediately rotated
2. **History cleanup** — if secrets entered version control, we use secure rewrite tools to remove them from git history
3. **Root cause analysis** — investigate how the secret bypassed controls
4. **Control enhancement** — update scanning rules and processes to prevent recurrence

## Links
- [OWASP Secrets Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html)
- [GitHub Secret Scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning)
- [Gitleaks](https://github.com/gitleaks/gitleaks)
