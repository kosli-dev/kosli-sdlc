---
title: Infrastructure and Configuration as Code
weight: 50
control_code: SDLC-CTRL-0005
level: 1
doc-status: Draft
type: PREV
areas:
  - build
nist-sp-800-53r5_references:
  - id: cm-2
    note: Baseline configuration — infrastructure as code establishes and maintains a documented baseline for all environments.
  - id: cm-3
    note: Configuration change control — all infrastructure changes are tracked in version control with full audit trails.
  - id: cm-6
    note: Configuration settings — environment configurations are defined as code and enforced through automation.
  - id: cm-9
    note: Configuration management plan — infrastructure as code is a core component of the overall configuration management approach.
  - id: sa-10
    note: Developer configuration management — infrastructure definitions are subject to the same controls as application source code.
  - id: sc-28
    note: Protection of information at rest — infrastructure definitions include security configurations for data protection.
mitigates:
  - configuration_drift
  - insider_threat
  - audit_and_compliance_failure
related_mitigations:
  - SDLC-CTRL-0001
  - SDLC-CTRL-0018
---
# {{% param "title" %}}
{{< area_head >}}

## Summary
Infrastructure and configurations are defined as code, stored in version control, and applied through automation to ensure auditability and reproducibility.

## Description
Infrastructure setup, configuration, and evolution must be auditable, secure, and reproducible. Defining cloud environments as code and using automation tools to roll out changes ensures that infrastructure changes go through the same rigorous processes as application code — including version control, peer review, and automated testing.

Infrastructure as code eliminates manual configuration steps that are error-prone and difficult to audit. It enables teams to reproduce environments consistently across development, testing, and production, and provides a clear audit trail of what changed, when, and by whom.

## Requirements
* All production and test infrastructure MUST be defined as code and stored in version control
* Infrastructure changes MUST be rolled out via automated CI pipelines
* The appropriate tooling MUST be used for the type and level of change (e.g. Terraform for infrastructure, Docker for application runtimes)
* Infrastructure documentation MUST be maintained and kept up-to-date
* Infrastructure code MUST go through the same review process as application code

## How we implement this control

* We define all our production and test infrastructure using code. Changes are rolled out via CI pipelines in {{% param "gitProvider" %}}
* We use the appropriate tooling for the type and level of the change (e.g. Terraform for infrastructure, Docker for application runtimes)
* All documentation around our infrastructure, security approaches and automation is maintained and up-to-date in our [Knowledge Base](https://github.com/kosli-dev/knowledge-base)

## Links
- [Terraform by HashiCorp](https://www.terraform.io/)
- [Infrastructure as Code — Martin Fowler](https://martinfowler.com/bliki/InfrastructureAsCode.html)
