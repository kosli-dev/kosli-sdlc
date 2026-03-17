---
title: Penetration Testing
summary: "Penetration testing is conducted periodically to identify exploitable vulnerabilities in applications and infrastructure that automated scanning may not detect."
weight: 40
control_code: SDLC-CTRL-0019
level: 1
doc-status: Draft
type: DET
areas:
  - lifecycle
nist-sp-800-53r5_references:
  - id: ca-8
    note: Penetration testing — requires organisations to conduct penetration testing on systems and applications.
  - id: ra-5
    note: Vulnerability monitoring and scanning — penetration testing complements automated scanning by testing for exploitable vulnerabilities.
  - id: sa-11
    note: Developer testing and evaluation — includes security testing as part of the development process.
  - id: si-2
    note: Flaw remediation — findings from penetration tests must be tracked to resolution.
soc2-type2_references:
  - id: cc4.1
    note: Requires ongoing monitoring to ascertain whether controls are functioning; penetration testing provides independent validation of security control effectiveness.
  - id: cc7.1
    note: Requires detection of vulnerabilities; penetration testing identifies exploitable weaknesses that automated scanning may miss.
mitigates:
  - vulnerable_software_in_production
  - environment_breach
related_mitigations:
  - SDLC-CTRL-0020
  - SDLC-CTRL-0021
  - SDLC-CTRL-0015
---
# {{% param "title" %}}
{{< area_head >}}

## Description
Penetration testing simulates real-world attack scenarios against applications and infrastructure to identify exploitable vulnerabilities. Unlike automated scanning tools (SAST, SCA), penetration testing assesses the actual exploitability of vulnerabilities in context, tests for business logic flaws, and evaluates the effectiveness of security controls as a whole.

Penetration testing serves as the organisation's approach to dynamic application security testing (DAST), providing assurance that systems are resilient against attack when viewed from an external perspective.

## Requirements
* Penetration testing MUST be conducted at least annually against customer-facing applications and critical infrastructure
* Penetration testing scope MUST include both application-layer and infrastructure-layer testing
* Findings MUST be classified by severity and tracked to resolution
* Critical and high severity findings MUST be remediated within defined SLAs
* Penetration test reports and remediation evidence MUST be retained for audit purposes
* Penetration testing SHOULD be conducted by qualified personnel, either internal or external

## How we implement this control

* We conduct periodic penetration testing against our production applications and infrastructure
* Findings are tracked and remediated according to severity
* Penetration test reports are retained for compliance and audit purposes

{{< compliance_refs >}}

## Links
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [NIST SP 800-53r5 CA-8: Penetration Testing](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
- [PTES — Penetration Testing Execution Standard](http://www.pentest-standard.org/)
