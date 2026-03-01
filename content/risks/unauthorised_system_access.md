---
title: "Unauthorised System Access"
weight: 70
risk_id: SDLC-RISK-0007
risk_key: unauthorised_system_access
description: "Production environments are accessed by personnel without appropriate authorisation or without full audit trails."
mitigations:
  - name: "System Access Controls"
    url: "/controls/runtime/system_access/"
  - name: "Secrets Management"
    url: "/controls/runtime/secrets_managment/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Unauthorised System Access occurs when individuals gain access to production environments, infrastructure, or sensitive systems without appropriate authorisation or without their access being fully recorded and auditable. This includes scenarios where access controls are too broad, where former employees or contractors retain active credentials, where shared accounts obscure individual accountability, or where privileged access is granted without time-bound restrictions or proper justification. The risk extends to both external attackers who exploit weak access controls and internal personnel whose access exceeds their legitimate operational needs.

- **Overprivileged access** - Users or service accounts granted broader permissions than required for their role, providing unnecessary access to sensitive systems, data, or infrastructure
- **Stale access credentials** - Former employees, contractors, or rotated team members retaining active access to production systems after their need for access has ended
- **Shared and generic accounts** - Use of shared credentials or service accounts that obscure which individual performed a given action, undermining accountability and audit trails
- **Insufficient access logging** - Systems that do not record who accessed what, when, and from where, making it impossible to detect or investigate unauthorised access
- **Lack of time-bound or just-in-time access** - Persistent privileged access that remains active indefinitely rather than being granted on-demand for specific, justified operational needs

## Consequences
The consequences of unauthorised system access materializing for a financial institution can be severe:

- **Data Breach and Exfiltration:** Unauthorised access to production databases, customer records, or internal systems enables theft of sensitive financial data, PII, and intellectual property.

- **Fraudulent Transactions:** Access to transaction processing systems, payment infrastructure, or account management tools can be exploited to initiate unauthorised transfers, manipulate account balances, or conduct fraudulent activities.

- **Regulatory Violations:** Financial regulators require strict access controls and audit trails for production systems. Inadequate access governance violates requirements under SOX, PCI DSS, and banking supervisory standards, triggering enforcement actions.

- **Loss of Accountability:** Shared accounts and insufficient logging make it impossible to attribute actions to specific individuals, undermining incident investigation, forensic analysis, and regulatory reporting obligations.

- **Lateral Movement by Attackers:** Overly broad access permissions enable attackers who compromise a single account to move laterally across the environment, escalating from low-value systems to critical infrastructure.

- **Reputational Damage:** Disclosure that customer data or financial systems were accessed by unauthorised individuals—particularly through preventable access control failures—severely erodes customer trust and market confidence.

- **Prolonged Undetected Compromise:** Without comprehensive access logging and monitoring, unauthorised access can persist undetected for extended periods, increasing the scope and severity of potential damage.
