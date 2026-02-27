---
title: "Insider Threat"
weight: 20
risk_id: SDLC-RISK-0002
risk_key: insider_threat
description: "Authorized personnel (developers, contractors, administrators, or other trusted users) with legitimate access to source code repositories, development environments, production systems, or sensitive data may intentionally or unintentionally compromise the confidentiality, integrity, or availability of software assets."
mitigations:
  - name: "Code Review"
    url: "/controls/release/code_review/"
  - name: "Deployment Approvals"
    url: "/controls/release/deployment_approvals/"
  - name: "Version Control"
    url: "/controls/build/versioncontrol/"
  - name: "System Access Controls"
    url: "/controls/runtime/system_access/"
  - name: "Change Records"
    url: "/controls/runtime/change_records/"
  - name: "Secrets Management"
    url: "/controls/runtime/secrets_managment/"
  - name: "Runtime Workload Monitoring"
    url: "/controls/runtime/workload_monitoring/"
  - name: "Deployment Controls"
    url: "/controls/runtime/deployment_controls/"
  - name: "Training"
    url: "/controls/lifecycle/training/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Insider Threat includes risks of malicious code injection, unauthorized data exfiltration, credential misuse, sabotage of build/deployment pipelines, or negligent security practices that expose systems to exploitation. Additionally, insider threat encompasses scenarios where external attackers have compromised the credentials of legitimate users, enabling them to conduct attacks while masquerading as trusted personnel with valid access. The trusted position and technical knowledge of insiders—or attackers leveraging insider credentials—makes detection difficult and potential impact significant.

- **Malicious code injection** - Inserting backdoors, vulnerabilities, or malicious logic into applications or infrastructure
- **Compromised credentials** - Attackers using stolen or phished developer/admin credentials to access systems and data
- **Data exfiltration** - Stealing source code, intellectual property, customer data, or sensitive business information
- **CI/CD pipeline manipulation** - Tampering with build processes, deployment pipelines, or supply chain components to inject malicious code
- **Cloud/infrastructure misconfiguration** - Accidentally or intentionally exposing databases, storage, or services to unauthorized access

## Consequences
The consequences of an insider threat materializing for a financial institution can be severe:

- **Direct Financial Losses:** Fraudulent transactions, theft of funds, unauthorized wire transfers, or manipulation of accounts can result in immediate monetary losses to the institution and its customers.

- **Breach of Data Privacy Regulations:** Unauthorized access to or exfiltration of customer PII can lead to significant fines under regulations like GDPR, CCPA, and GLBA, alongside mandated breach notifications and regulatory scrutiny.

- **Violation of Financial Regulations:** Insider actions compromising system integrity, audit trails, or customer data can breach banking regulations (e.g., SOX, PCI DSS, Basel III) and trigger enforcement actions from regulatory bodies.

- **Reputational Damage:** Public disclosure of insider attacks—particularly those involving customer funds or data—can severely erode customer trust, leading to account closures, deposit flight, and long-term brand damage.

- **Operational Disruption:** Sabotage of critical banking systems, payment processing infrastructure, or core applications can halt operations, impacting customer service and transaction processing capabilities.

- **Loss of Competitive Advantage:** Theft of proprietary trading algorithms, risk models, customer insights, or strategic plans can benefit competitors and undermine market position.

- **Legal Liabilities:** The institution may face lawsuits from affected customers, shareholders, or partners, as well as potential criminal investigations if insider actions involve fraud or data breaches.

