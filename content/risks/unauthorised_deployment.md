---
title: "Unauthorised Deployment"
weight: 30
risk_id: SDLC-RISK-0003
risk_key: unauthorised_deployment
description: "Software is deployed to production without passing required quality gates, security scans, or approval checks."
mitigations:
  - name: "Deployment Approvals"
    url: "/controls/release/deployment_approvals/"
  - name: "Binary Provenance"
    url: "/controls/build/binary_provenance/"
  - name: "Deployment Controls"
    url: "/controls/runtime/deployment_controls/"
  - name: "Workload Monitoring"
    url: "/controls/runtime/workload_monitoring/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Unauthorised Deployment occurs when software artefacts reach production environments without completing the required quality gates, security validations, or approval workflows. This can happen through misconfigured CI/CD pipelines, direct manual deployments that bypass automated controls, or exploitation of overly permissive deployment credentials. The risk is compounded in environments where deployment tooling lacks sufficient access controls or where emergency "break-glass" procedures are poorly governed and frequently abused.

- **Pipeline bypass** - Developers or operators deploying directly to production outside the sanctioned CI/CD pipeline, circumventing automated checks and approval gates
- **Incomplete quality gates** - Artefacts promoted to production despite failing tests, security scans, or compliance checks due to misconfigured or overridden pipeline stages
- **Unverified artefact provenance** - Deploying binaries or container images whose origin cannot be traced back to a verified source repository and build process
- **Abuse of emergency deployment procedures** - Overuse or misuse of break-glass mechanisms intended for critical incidents, resulting in unreviewed code reaching production
- **Credential and role misconfiguration** - Deployment service accounts or roles granting broader access than necessary, allowing unauthorised personnel to trigger production deployments

## Consequences
The consequences of an unauthorised deployment materializing for a financial institution can be severe:

- **Introduction of Untested Code into Production:** Software that has not passed security scans, functional tests, or compliance checks may contain vulnerabilities, logic errors, or regressions that directly impact transaction processing, account management, or customer-facing services.

- **Regulatory Non-Compliance:** Financial regulators require demonstrable change management controls. Deployments that bypass approval workflows violate requirements under SOX, PCI DSS, and banking supervisory standards, potentially triggering enforcement actions and mandatory remediation.

- **Loss of Audit Trail Integrity:** Unauthorised deployments create gaps in change records, making it impossible to reconstruct what was deployed, when, and by whom—undermining incident investigation and regulatory audit readiness.

- **Service Outages and Operational Disruption:** Unvalidated deployments increase the likelihood of production incidents, including service degradation, data corruption, or complete system outages affecting customers and downstream systems.

- **Security Exposure:** Code that has not undergone security review or vulnerability scanning may introduce exploitable weaknesses, creating entry points for attackers to access sensitive financial data or critical infrastructure.

- **Reputational Damage:** Customer-visible incidents caused by uncontrolled deployments—particularly those affecting account balances, payment processing, or data privacy—erode trust and can lead to customer attrition.
