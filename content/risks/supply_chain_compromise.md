---
title: "Supply Chain Compromise"
weight: 10
risk_id: SDLC-RISK-0001
risk_key: supply_chain_compromise
description: "Malicious or tampered software components—including open source libraries, base container images, build tools, or third-party services—are introduced into the software development lifecycle, resulting in compromised applications being built, tested, and deployed to production environments."
mitigations:
  - name: "Binary Provenance"
    url: "/controls/build/binary_provenance/"
  - name: "Dependency Management"
    url: "/controls/build/dependencies/"
  - name: "Toolchain"
    url: "/controls/build/toolchain/"
  - name: "Security Vulnerability Scanning"
    url: "/controls/release/security/"
  - name: "Deployment Controls"
    url: "/controls/runtime/deployment_controls/"
  - name: "Runtime Workload Monitoring"
    url: "/controls/runtime/workload_monitoring/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Supply Chain Compromise encompasses attacks where malicious code or vulnerabilities are introduced through external components that an organisation trusts and uses in its software delivery pipeline. Unlike direct attacks on an organisation's own systems, supply chain attacks exploit the inherent trust placed in third-party software, making them particularly difficult to detect. A single compromised upstream component can propagate malicious code to thousands of downstream consumers before the compromise is discovered.

- **Compromised open source dependencies** - Malicious code injected into widely-used libraries via maintainer account takeover, typosquatting, or dependency confusion attacks
- **Tampered base images** - Container base images or VM images modified to include backdoors, credential harvesters, or persistent malware
- **Build toolchain compromise** - Compilers, build systems, or CI/CD tools altered to inject malicious code during the build process without modifying source
- **Third-party service compromise** - SaaS tools, package registries, or external APIs used in the pipeline becoming vectors for malicious payloads
- **Malicious package substitution** - Attackers publishing packages that mimic legitimate internal or popular public packages to exploit misconfigured dependency resolution

## Consequences
The consequences of a supply chain compromise materializing for a financial institution can be severe:

- **Undetected Backdoors in Production:** Malicious code embedded in trusted components can persist in production systems for extended periods, providing attackers with persistent access to sensitive systems, transaction data, and customer information.

- **Breach of Data Privacy Regulations:** Exfiltration of customer PII or financial data through a compromised dependency can trigger GDPR, CCPA, and GLBA breach notification obligations, significant fines, and regulatory investigations.

- **Violation of Financial Regulations:** Compromised software integrity undermines audit trails and system controls required by SOX, PCI DSS, and banking regulators, potentially resulting in enforcement actions and mandatory remediation programs.

- **Reputational Damage:** Disclosure that customer-facing systems were built on compromised components—particularly if customer funds or data were affected—can severely damage institutional trust and trigger customer attrition.

- **Operational Disruption:** Discovery of a supply chain compromise may require emergency takedown of affected systems, emergency patching across the estate, or full rebuilds of the software delivery pipeline, causing significant service disruption.

- **Widespread Blast Radius:** Because supply chain compromises affect the build process itself, all applications built using the affected component or toolchain may be impacted simultaneously, amplifying the scope of incident response.

- **Legal Liabilities:** Customers, partners, or regulators may pursue legal action if compromised software led to financial losses, data breaches, or failure to meet contractual security obligations.
