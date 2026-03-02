---
title: "Environment Breach"
weight: 90
risk_id: SDLC-RISK-0009
risk_key: environment_breach
description: "External attacker running workloads in our system."
mitigations:
  - name: "Workload Monitoring"
    url: "/controls/runtime/workload_monitoring/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Environment Breach occurs when an external attacker gains the ability to run unauthorised workloads within an organisation's production infrastructure. This goes beyond simple data access—the attacker establishes a persistent operational presence, executing their own code, deploying containers or processes, and using the organisation's compute resources for malicious purposes. This can result from exploitation of vulnerabilities in exposed services, compromised container orchestration platforms, misconfigured cloud IAM policies, or abuse of legitimate deployment mechanisms. An environment breach represents a severe compromise because the attacker operates within the organisation's own infrastructure, making detection significantly harder and the potential impact far greater.

- **Unauthorised container or workload deployment** - Attackers deploying their own containers, serverless functions, or processes within the organisation's orchestration platform (e.g., Kubernetes, ECS)
- **Compromised orchestration plane** - Exploitation of container orchestration APIs or management interfaces to schedule and run attacker-controlled workloads alongside legitimate services
- **Cryptojacking and resource abuse** - Attackers deploying cryptocurrency mining workloads or using compromised infrastructure for computational tasks, consuming resources and increasing costs
- **Staging ground for further attacks** - Using the breached environment as a launch point for lateral movement into other internal systems, data stores, or connected partner networks
- **Persistent backdoor deployment** - Installing persistent access mechanisms such as reverse shells, web shells, or rogue services that survive routine maintenance and restarts

## Consequences
The consequences of an environment breach materializing for a financial institution can be severe:

- **Complete Infrastructure Compromise:** An attacker running workloads in production has deep access to the environment, potentially including network access to databases, internal APIs, secret stores, and adjacent systems that are not directly exposed to the internet.

- **Customer Data Theft at Scale:** With operational presence in the production environment, attackers can systematically exfiltrate customer data, transaction records, and financial information over extended periods while evading perimeter-based detection.

- **Financial Losses from Resource Abuse:** Unauthorised workloads—particularly cryptomining operations—can generate significant unexpected cloud computing costs before detection, directly impacting operational budgets.

- **Regulatory Escalation:** An environment breach represents a fundamental control failure. Regulators will treat the ability of an external attacker to run workloads in a financial institution's production environment as a critical finding requiring immediate remediation and likely triggering formal enforcement proceedings.

- **Supply Chain Risk to Customers:** Attacker-controlled workloads running within the institution's infrastructure can potentially intercept, modify, or inject data into legitimate business processes, affecting downstream customers and partners.

- **Prolonged and Costly Incident Response:** Detecting and eradicating an attacker with operational presence requires thorough forensic investigation of all running workloads, comprehensive review of deployment history, and potentially rebuilding affected infrastructure from known-good state.

- **Reputational Catastrophe:** Disclosure that an external attacker was running their own workloads inside a financial institution's production environment represents a severe breach of trust that can permanently damage the institution's standing with customers, partners, and regulators.
