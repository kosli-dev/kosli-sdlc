---
title: Secrets Scanning
weight: 60
control_code: SDLC-CTRL-0006
level: 1
areas:
 - build
tldr: Scanning source code and built binaries for secrets in CI/CD is crucial for maintaining security, preventing unauthorized access, and avoiding breaches.
rationale: Hardcoded secrets in source code, configuration files, or built artifacts pose a significant security risk. Automated secrets scanning prevents unauthorized access and potential breaches by detecting and blocking secrets before they enter version control or production systems.
---
# {{% param "title" %}}
{{< area_head >}}

## Background

Secrets (such as API keys, passwords, tokens, and certificates) must never be hardcoded in source code, configuration files, container images, or Infrastructure as Code (IaC). Instead, secrets must be:

* Injected at runtime via secure secret management systems
* Scoped per environment (dev, test, prod)
* Rotated periodically with alerts on staleness
* Accessed only by specific CI/CD jobs or roles

Automated secrets scanning is implemented at multiple stages:

1. **Pre-commit scanning** - Detect secrets before they enter version control
2. **CI/CD pipeline scanning** - Scan code and built binaries during the build process
3. **Container image scanning** - Ensure no secrets are baked into images
4. **IaC scanning** - Verify secrets are passed via secure parameter injection, not hardcoded

## Requirements

### Code and Configuration
* CI/CD pipelines must detect hardcoded secrets in code
* Code and config files must never include secrets
* Code must be scanned for embedded secrets before commit or build
* Secrets should be removed from commit history using secure rewrite tools (e.g., git-filter-repo, BFG)

### Runtime Security
* Secrets only used at runtime, never in code
* Secrets must be injected at runtime, not hardcoded or stored
* Secrets access is limited to specific CI/CD job or role

### Secret Management
* Secrets must be rotated periodically; alert on staleness
* Secrets must be scoped per environment (dev, test, prod)

### Container and Infrastructure
* Secrets must not be hardcoded into images; use secure runtime secret injection
* Secrets should never be referenced in IaC; pass via secure parameter injection

### Third-Party Integrations
* Third-party integrations audited for secrets exposure

## How we implement this control

We implement secrets scanning through multiple layers of defense:

### Pre-commit Hooks
Developers use pre-commit hooks to scan for secrets before code enters version control. This provides the earliest detection point and prevents secrets from being committed.

### CI/CD Pipeline Scanning
Our CI/CD pipelines include automated secrets scanning at multiple stages:

* Source code scanning during build
* Binary and artifact scanning before deployment
* Container image scanning for embedded secrets

Tools used include:
* [Specify your secrets scanning tool, e.g., Gitleaks, TruffleHog, GitGuardian]

### Secret Management
All secrets are managed through [specify your secret management system, e.g., AWS Secrets Manager, HashiCorp Vault, Azure Key Vault]:

* Secrets are injected at runtime via environment variables or secure APIs
* Access is controlled via IAM roles/policies specific to each service and environment
* Rotation policies are enforced with alerts for stale secrets
* Separate secrets for dev, test, and production environments

### Container Security
Container images are scanned before deployment to ensure:
* No secrets are baked into image layers
* Runtime secret injection mechanisms are properly configured
* Base images are free of exposed credentials

### Remediation Process
When secrets are detected:

1. **Immediate revocation** - Compromised secrets are immediately rotated
2. **History cleanup** - If secrets entered version control, we use secure rewrite tools to remove them from git history
3. **Root cause analysis** - Investigate how the secret bypassed controls
4. **Control enhancement** - Update scanning rules and processes to prevent recurrence

## Evidence and Audit Trail

We maintain audit trails for:
* Secrets scanning results in CI/CD pipelines
* Secret rotation events and schedules
* Access logs for secret management systems
* Remediation actions for detected secrets

These audit trails are available in [specify location, e.g., Kosli, your SIEM, or logging system]

