---
title: "Credential and Secret Exposure"
weight: 40
risk_id: SDLC-RISK-0004
risk_key: credential_and_secret_exposure
description: "Leaked or poorly managed secrets enable unauthorised access to production systems, customer data, or CI/CD pipelines."
mitigations:
  - name: "Secrets Management"
    url: "/controls/runtime/secrets_managment/"
  - name: "Version Control"
    url: "/controls/build/versioncontrol/"
  - name: "Security Vulnerability Scanning"
    url: "/controls/release/security/"
  - name: "System Access Controls"
    url: "/controls/runtime/system_access/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Credential and Secret Exposure occurs when sensitive authentication material—such as API keys, database passwords, service account tokens, encryption keys, or certificates—is inadvertently or deliberately exposed in locations where it can be accessed by unauthorised parties. This commonly happens through secrets committed to version control repositories, hardcoded credentials in application code, secrets leaked in CI/CD logs and artifacts, or credentials stored in insufficiently protected configuration management systems. Once exposed, credentials can be harvested by attackers and used to gain unauthorised access to production systems, customer data, and internal infrastructure.

- **Secrets committed to source control** - API keys, passwords, or tokens checked into Git repositories where they persist in history even after removal from the working tree
- **Hardcoded credentials in application code** - Database connection strings, service account passwords, or encryption keys embedded directly in source files rather than injected at runtime
- **CI/CD log leakage** - Build and deployment pipelines inadvertently printing secrets to log output, making them visible to anyone with access to pipeline logs
- **Insecure secret storage** - Credentials stored in plaintext configuration files, environment variables without encryption, shared documents, or messaging platforms
- **Overprivileged service credentials** - Service accounts or API keys granted excessive permissions, amplifying the blast radius if the credential is compromised

## Consequences
The consequences of credential and secret exposure materializing for a financial institution can be severe:

- **Unauthorised Access to Production Systems:** Exposed credentials provide attackers with direct access to databases, APIs, cloud infrastructure, and internal services, enabling data theft, transaction manipulation, or system compromise.

- **Customer Data Breach:** Compromised database credentials or API keys can be used to exfiltrate customer PII, account details, and financial records, triggering breach notification obligations under GDPR, CCPA, and GLBA.

- **CI/CD Pipeline Compromise:** Leaked pipeline credentials enable attackers to tamper with build and deployment processes, injecting malicious code into artefacts destined for production.

- **Regulatory Penalties:** Inadequate secrets management violates requirements under PCI DSS, SOX, and banking supervisory standards, exposing the institution to fines, enforcement actions, and mandated remediation programs.

- **Reputational Damage:** Public disclosure that customer-facing systems were compromised through leaked credentials—particularly if customer funds or data were affected—severely damages institutional trust.

- **Costly Remediation:** Responding to credential exposure requires emergency rotation of all potentially affected secrets, forensic investigation to determine the scope of compromise, and potential rebuilding of affected systems—all under significant time pressure.
