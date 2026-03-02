---
title: "Vulnerable Software in Production"
weight: 50
risk_id: SDLC-RISK-0005
risk_key: vulnerable_software_in_production
description: "Known vulnerabilities in code or dependencies are exploited in the production environment."
mitigations:
  - name: "Security Vulnerability Scanning"
    url: "/controls/release/security/"
  - name: "Dependency Management"
    url: "/controls/build/dependencies/"
  - name: "Workload Monitoring"
    url: "/controls/runtime/workload_monitoring/"
  - name: "Quality"
    url: "/controls/release/quality/"
---

# {{% param "title" %}}
{{< risk_head >}}


## Description
Vulnerable Software in Production occurs when applications or their dependencies containing known security vulnerabilities are deployed to and remain running in production environments. This risk arises from inadequate vulnerability scanning during the build and release process, failure to keep dependencies up to date, delayed patching of known CVEs, or insufficient visibility into the software composition of running workloads. Attackers actively scan for known vulnerabilities and can exploit them rapidly once public disclosures are made, making timely detection and remediation critical.

- **Unpatched known vulnerabilities (CVEs)** - Production systems running software with publicly disclosed vulnerabilities for which patches or mitigations are available but have not been applied
- **Outdated or end-of-life dependencies** - Libraries, frameworks, or runtime components that no longer receive security updates, leaving known vulnerabilities permanently unaddressed
- **Incomplete vulnerability scanning** - Security scans that do not cover the full software stack—including transitive dependencies, container base images, and runtime libraries—leaving blind spots in vulnerability detection
- **Delayed remediation cycles** - Organisational processes that are too slow to triage, prioritise, and deploy fixes for critical vulnerabilities before they can be exploited
- **Shadow dependencies** - Components pulled in through indirect or undocumented dependency chains that are not tracked or scanned as part of the standard build process

## Consequences
The consequences of vulnerable software in production materializing for a financial institution can be severe:

- **Active Exploitation by Attackers:** Known vulnerabilities with public exploit code can be weaponised rapidly. Attackers target financial institutions specifically because of the value of the data and systems they protect.

- **Customer Data Breach:** Exploited vulnerabilities in web-facing applications or APIs can expose customer PII, account credentials, and transaction histories, triggering regulatory breach notification requirements.

- **Regulatory Non-Compliance:** Financial regulators expect timely vulnerability management as a core security control. Running known-vulnerable software violates requirements under PCI DSS, banking supervisory standards, and enterprise risk management frameworks.

- **Service Disruption:** Exploitation of vulnerabilities can lead to denial of service, data corruption, or system compromise that forces emergency shutdowns of customer-facing services.

- **Reputational Damage:** Public disclosure that a breach resulted from a known, unpatched vulnerability is particularly damaging, as it signals failure of basic security hygiene to customers, partners, and regulators.
